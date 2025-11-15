<script lang="ts">
	import { onMount } from 'svelte';
	
	interface Props {
		children?: any;
		delay?: number;
		threshold?: number;
	}
	
	let { children, delay = 0, threshold = 0.2 }: Props = $props();
	
	let isVisible = $state(false);
	let elementRef: HTMLDivElement | undefined = $state();
	
	onMount(() => {
		if (!elementRef) return;
		
		const observer = new IntersectionObserver(
			([entry]) => {
				if (entry.isIntersecting) {
					setTimeout(() => {
						isVisible = true;
					}, delay);
				}
			},
			{ threshold }
		);
		
		observer.observe(elementRef);
		
		return () => observer.disconnect();
	});
</script>

<div 
	bind:this={elementRef}
	class="scroll-reveal"
	class:visible={isVisible}
>
	{@render children?.()}
</div>

<style>
	.scroll-reveal {
		opacity: 0;
		transform: translateY(40px);
		transition: opacity 0.8s cubic-bezier(0.4, 0, 0.2, 1),
		            transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
	}
	
	.scroll-reveal.visible {
		opacity: 1;
		transform: translateY(0);
	}
</style>
