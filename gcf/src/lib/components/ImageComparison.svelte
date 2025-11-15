<script lang="ts">
	import { onMount } from 'svelte';
	
	interface Props {
		beforeImage: string;
		afterImage: string;
		beforeLabel?: string;
		afterLabel?: string;
		alt?: string;
	}
	
	let { 
		beforeImage, 
		afterImage, 
		beforeLabel = "1871", 
		afterLabel = "Today",
		alt = "Historical comparison"
	}: Props = $props();
	
	let sliderPosition = $state(50);
	let containerRef: HTMLDivElement | undefined = $state();
	let isDragging = $state(false);

	function handleMove(clientX: number) {
		if (!containerRef) return;
		const rect = containerRef.getBoundingClientRect();
		const x = clientX - rect.left;
		const percentage = Math.max(0, Math.min(100, (x / rect.width) * 100));
		sliderPosition = percentage;
	}

	function handleMouseMove(e: MouseEvent) {
		if (isDragging) {
			handleMove(e.clientX);
		}
	}

	function handleTouchMove(e: TouchEvent) {
		if (isDragging && e.touches[0]) {
			handleMove(e.touches[0].clientX);
		}
	}

	function startDrag() {
		isDragging = true;
	}

	function stopDrag() {
		isDragging = false;
	}

	onMount(() => {
		document.addEventListener('mouseup', stopDrag);
		document.addEventListener('touchend', stopDrag);
		
		return () => {
			document.removeEventListener('mouseup', stopDrag);
			document.removeEventListener('touchend', stopDrag);
		};
	});
</script>

<svelte:window 
	on:mousemove={handleMouseMove}
	on:touchmove={handleTouchMove}
/>

<div 
	bind:this={containerRef}
	class="comparison-container"
	role="img"
	aria-label={alt}
>
	<!-- After image (background) -->
	<div class="image-layer after-image">
		<img src={afterImage} alt="{alt} - {afterLabel}" />
		<span class="image-label after-label">{afterLabel}</span>
	</div>
	
	<!-- Before image (clipped overlay) -->
	<div class="image-layer before-image" style="clip-path: inset(0 {100 - sliderPosition}% 0 0);">
		<img src={beforeImage} alt="{alt} - {beforeLabel}" />
		<span class="image-label before-label">{beforeLabel}</span>
	</div>
	
	<!-- Slider handle -->
	<div 
		class="slider-handle" 
		style="left: {sliderPosition}%"
		onmousedown={startDrag}
		ontouchstart={startDrag}
		role="slider"
		aria-valuenow={sliderPosition}
		aria-valuemin={0}
		aria-valuemax={100}
		tabindex="0"
	>
		<div class="handle-line"></div>
		<div class="handle-button">
			<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
				<path d="M15 18l-6-6 6-6"></path>
				<path d="M9 18l6-6-6-6"></path>
			</svg>
		</div>
	</div>
</div>

<style>
	.comparison-container {
		position: relative;
		width: 100%;
		aspect-ratio: 16 / 10;
		overflow: hidden;
		border-radius: 8px;
		box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
		cursor: ew-resize;
		user-select: none;
	}

	.image-layer {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}

	.image-layer img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		display: block;
	}

	.before-image {
		z-index: 2;
	}

	.after-image {
		z-index: 1;
	}

	.image-label {
		position: absolute;
		top: 20px;
		padding: 8px 16px;
		background: rgba(0, 0, 0, 0.75);
		color: white;
		font-weight: 600;
		font-size: 14px;
		text-transform: uppercase;
		letter-spacing: 1px;
		border-radius: 4px;
		backdrop-filter: blur(8px);
		z-index: 3;
	}

	.before-label {
		left: 20px;
	}

	.after-label {
		right: 20px;
	}

	.slider-handle {
		position: absolute;
		top: 0;
		bottom: 0;
		width: 4px;
		transform: translateX(-50%);
		z-index: 10;
		cursor: ew-resize;
	}

	.handle-line {
		position: absolute;
		top: 0;
		bottom: 0;
		left: 50%;
		width: 2px;
		background: white;
		transform: translateX(-50%);
		box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
	}

	.handle-button {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 48px;
		height: 48px;
		background: white;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
		color: #333;
		transition: transform 0.2s ease;
	}

	.handle-button:hover {
		transform: translate(-50%, -50%) scale(1.1);
	}

	.slider-handle:active .handle-button {
		transform: translate(-50%, -50%) scale(0.95);
	}
</style>
