<script lang="ts">
	import ImageComparison from '$lib/components/ImageComparison.svelte';
	import ScrollReveal from '$lib/components/ScrollReveal.svelte';
	
	// Image paths
	const images = {
		cowLithograph: '/chicago-fire/cow-lithograph.jpg',
		courthouseRuins: '/chicago-fire/courthouse-ruins.jpg',
		courthouseNow: '/chicago-fire/courthouse-now.jpg',
		waterTowerAfter: '/chicago-fire/water-tower-after.jpg',
		waterTowerNow: '/chicago-fire/water-tower-now.jpg',
		methodistSketch: '/chicago-fire/methodist-church-sketch.jpg',
		methodistNow: '/chicago-fire/methodist-church-now.jpg'
	};
	
	let scrollProgress = $state(0);
	
	function handleScroll() {
		const winScroll = document.documentElement.scrollTop;
		const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
		scrollProgress = (winScroll / height) * 100;
	}
</script>

<svelte:window onscroll={handleScroll} />

<div class="progress-bar" style="width: {scrollProgress}%"></div>

<main class="exhibit">
	<!-- Hero Section -->
	<section class="hero">
		<div class="hero-content">
			<h1 class="exhibit-title">
				<span class="title-line">The Chicago Fire</span>
				<span class="title-sub">Setbacks and Rebuilding</span>
			</h1>
			<p class="hero-date">October 8–10, 1871</p>
			<div class="hero-divider"></div>
			<p class="hero-intro">
				A transformative tragedy that shaped Chicago from a rapidly expanding trade hub 
				into a resilient metropolis, rebuilt stronger than before.
			</p>
		</div>
		<div class="scroll-indicator">
			<span>Scroll to explore</span>
			<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor">
				<path d="M12 5v14M19 12l-7 7-7-7"/>
			</svg>
		</div>
	</section>

	<!-- Introduction -->
	<section class="content-section intro-section">
		<ScrollReveal>
			<div class="section-content">
				<h2>The Inferno That Changed Everything</h2>
				<p class="lead-text">
					The Great Chicago Fire was a transformative tragedy in 1871 that shaped the then expanding 
					hub of trade into a better-than-before city after restorative efforts. The start of Chicago 
					was rapid, which meant cheap building materials like wood. This, combined with the elements 
					of October 9, 1871 made a small fire turn into a multi-mile inferno.
				</p>
				<p>
					In this exhibit I showcase the immediate effects of the fire and the then and now of Chicago 
					with examples of primary source photographs and current Google Earth reenactments of the same locations.
				</p>
			</div>
		</ScrollReveal>
	</section>

	<!-- The Scale of Destruction -->
	<section class="content-section map-section">
		<ScrollReveal delay={100}>
			<div class="section-content">
				<h2>The Scale of Destruction</h2>
				<div class="map-wrapper">
					<div class="luna-embed-container">
						<img src="/chicago-fire/map-burnt-district.jpg" alt="Map of the Burnt District, ca. 1871" />

                    </div>
					<div class="map-caption">
						<p class="caption-title">Map of the Burnt District, ca. 1871</p>
						<p class="caption-text">
							The absolute scale of how large this fire is displayed here in this map. The origin is unknown; 
							however, we can infer that the map was made during 1871. The fire went as far north as Old Town's 
							North Avenue and as far south as current-day China Town and Cermak Road.
						</p>
						<p class="caption-note">
							<strong>Critical detail:</strong> The fire could have been halved if wind hadn't taken the fire across the river.
						</p>
					</div>
				</div>
			</div>
		</ScrollReveal>
	</section>

	<!-- The Origin Story -->
	<section class="content-section origin-section">
		<ScrollReveal delay={150}>
			<div class="section-content split-layout">
				<div class="text-column">
					<h2>A Scapegoat for the City</h2>
					<p>
						The definitive source of the Chicago Fire is unknown; however, it is known that it started 
						near Mrs. O'Leary's farm. This satirical comic shows a cow stomping on a kerosene lamp along 
						with Mrs O'Leary looking casual about the incident.
					</p>
					<p>
						The perspective of the artwork is also off given the legs of the chair not appearing correctly. 
						Kellogg and Buckley created other lithographs of the Fire, attempting to capitalize off the 
						incident given they were located in Hartford, Connecticut.
					</p>
					<blockquote class="historical-note">
						Chicago needed a scapegoat to pin the Fire on, and a Catholic, Irish immigrant was a target that would stick.
					</blockquote>
				</div>
				<div class="image-column">
					<div class="image-wrapper">
						<img src="/chicago-fire/cow-lithograph.jpg" alt="Satirical lithograph showing Mrs. O'Leary's cow kicking over a lantern" />
						<p class="image-credit">Kellogg & Buckeley, ca. 1872</p>
					</div>
				</div>
			</div>
		</ScrollReveal>
	</section>

	<!-- Courthouse Comparison -->
	<section class="content-section comparison-section dark-section">
		<ScrollReveal delay={200}>
			<div class="section-content">
				<h2>The Court House: Then and Now</h2>
				<p class="section-intro">
					The aftermath of the Fire was grim. The only buildings that survived were ones that were not 
					built out of wood. The photo shows an East-ward view taken a few dozen feet North of Randolph 
					and right before the river on Market street (now Wacker Drive).
				</p>
				<div class="comparison-wrapper">
					<ImageComparison 
						beforeImage="/chicago-fire/courthouse-ruins.jpg"
						afterImage="/chicago-fire/courthouse-now.jpg"
						beforeLabel="1871 - Ruins"
						afterLabel="Today"
						alt="Court House location comparison"
					/>
				</div>
				<p class="comparison-note">
					The City of Chicago City Hall replaced the old Court House and reaches all the way to the edge of Randolph.
				</p>
			</div>
		</ScrollReveal>
	</section>

	<!-- Water Tower -->
	<section class="content-section comparison-section">
		<ScrollReveal delay={250}>
			<div class="section-content">
				<h2>The Resilient Water Tower</h2>
				<p class="section-intro">
					The resiliency of Chicago is shown in the Water Tower. This photo taken shortly after the fire 
					shows the surviving Water Tower and Pumping Station, along with a few trees. Originally called 
					the North Division, the area was primarily residential until the early 1920s.
				</p>
				<div class="comparison-wrapper">
					<ImageComparison 
						beforeImage="/chicago-fire/water-tower-after.jpg"
						afterImage="/chicago-fire/water-tower-now.jpg"
						beforeLabel="Post-Fire 1871"
						afterLabel="Magnificent Mile Today"
						alt="Water Tower comparison"
					/>
				</div>
				<blockquote class="resilience-quote">
					Though the Water Tower sits on prime real estate in Chicago's Magnificent Mile today, 
					tearing it down would mean acting worse than the Chicago Fire itself.
				</blockquote>
			</div>
		</ScrollReveal>
	</section>

	<!-- Methodist Church / Moody Bible Institute -->
	<section class="content-section final-section">
		<ScrollReveal delay={300}>
			<div class="section-content">
				<h2>Faith and Rebuilding</h2>
				<div class="split-layout reverse">
					<div class="image-column">
					<div class="image-wrapper sketch-wrapper">
						<img src="/chicago-fire/methodist-church-sketch.jpg" alt="Sketch of preaching at Methodist Church corner of LaSalle and Chicago Avenue" />
							<p class="image-credit">Alfred R. Waud, October 15, 1871</p>
						</div>
					</div>
					<div class="text-column">
						<p>
							The sketch of LaSalle and Chicago's Methodist Church shows the mood after the fire. 
							In the aftermath, the city was somber but also showed resilience because building 
							started immediately after.
						</p>
						<p>
							Alfred's sketch shows the reliance on finding meaning through religion. The plot of 
							land on this intersection later became the Moody Bible Institute.
						</p>
					</div>
				</div>
				<div class="comparison-wrapper" style="margin-top: 3rem;">
					<ImageComparison 
						beforeImage="/chicago-fire/methodist-church-sketch.jpg"
						afterImage="/chicago-fire/methodist-church-now.jpg"
						beforeLabel="Methodist Church, 1871"
						afterLabel="Moody Bible Institute"
						alt="Methodist Church location transformation"
					/>
				</div>
			</div>
		</ScrollReveal>
	</section>

	<!-- Rebuilding & World's Columbian Exposition -->
	<section class="content-section rebuild-section">
		<ScrollReveal delay={320}>
			<div class="section-content">
				<h2>Rebuilding and the 1893 World's Columbian Exposition</h2>
				<p class="section-intro">
					Chicago's rapid recovery after the Fire set the stage for the city's spectacular rebirth and the
					1900s-era civic pride that culminated in the 1893 World's Columbian Exposition.
				</p>
				<div class="image-wrapper">
					<img src="/chicago-fire/court-of-honor-1893.jpg" alt="The Court of Honor at World's Columbian Exposition, 1893" />
					<p class="image-credit">Chicago History Museum, ICHi-061668; J. Maul, photographer</p>
				</div>
				<!-- <div class="map-caption" style="margin-top:1rem;">
					<p class="caption-title">The Court of Honor at World's Columbian Exposition</p>
					<p class="caption-text">Looking east toward Grand Basin and the Court of Honor at the World's Columbian Exposition, Chicago, Illinois, 1893. Photographic print, 8 x 10 in.</p>
				</div> -->
			</div>
		</ScrollReveal>
	</section>

	<!-- Bibliography -->
	<section class="bibliography-section">
		<ScrollReveal delay={350}>
			<div class="section-content">
				<h2>Sources & Further Reading</h2>
				<div class="bibliography">
					<div class="bib-entry">
						<p>"View of the Chicago Avenue Water Tower and pumping station after the Great Fire of 1871, Chicago, Illinois." Photograph, post-1871. Chicago History Museum (Identifier: ICHi-002792). Accessed November 14, 2025. <a href="https://images.chicagohistory.org/asset/3869/#:~:text=ICHi%2D002792,Extent%3A%2011%20x%2013.5%20in." target="_blank">View Source</a></p>
					</div>
					<div class="bib-entry">
						<p>"Court House ruins after the fire." Photograph, 1871. Chicago History Museum (Identifier: ICHi-176626). Accessed November 13, 2025. <a href="https://images.chicagohistory.org/cdn/chicagohistorymuseum/previews/647/4ac4b22081d5ba3470148d009026d361/5/4acc4557ce33f4b9dd9c7fcf2bcd0a4d/193850.jpg" target="_blank">View Source</a></p>
					</div>
					<div class="bib-entry">
						<p>"Map of Chicago showing the burnt district." [ca. 1871]. The University of Chicago Library Map Collection. Accessed November 13, 2025. <a href="https://luna.lib.uchicago.edu/luna/servlet/detail/UCHICAGO~2~2~383~1231861:Map-of-Chicago-showing-the-burnt-di" target="_blank">View Source</a></p>
					</div>
					<div class="bib-entry">
						<p>Kellogg & Buckeley. "The Cause of the Great Chicago Fire Oct. 9th 1871." Lithograph, ca. 1872. Chicago History Museum. Accessed November 13, 2025. <a href="https://greatchicagofire.org/item/ichi-34703/" target="_blank">View Source</a></p>
					</div>
					<div class="bib-entry">
						<p>"The Court of Honor at World's Columbian Exposition" [ca. 1893]. Chicago History Museum (Identifier: ICHi-061668). Accessed November 14, 2025. <a href="https://images.chicagohistory.org/cdn/chicagohistorymuseum/previews/334/65734f507062c549741d27855b7b4ee1/5/c4559e476cd3ad81e44b230bbf0ce666/99920.jpg" target="_blank">View Source</a></p>
					</div>
					<div class="bib-entry">
						<p>Waud, Alfred R. "Preaching at the Methodist church cor. of LaSalle St. and Chicago Avenue Sunday Oct 15th." Pencil and Chalk Drawing, 1871. Chicago History Museum (Identifier: ichi-64139). Accessed November 13, 2025. <a href="https://greatchicagofire.org/item/ichi-64139/" target="_blank">View Source</a></p>
					</div>
				</div>
				<div class="author-credit">
					<p>Digital Exhibit by Eric Spencer</p>
					<p class="date">November 14, 2025</p>
				</div>
			</div>
		</ScrollReveal>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		background: #0a0a0a;
		color: #e8e8e8;
		font-family: 'Georgia', 'Times New Roman', serif;
		overflow-x: hidden;
	}

	.progress-bar {
		position: fixed;
		top: 0;
		left: 0;
		height: 3px;
		background: linear-gradient(90deg, #d97706, #dc2626);
		z-index: 1000;
		transition: width 0.1s ease-out;
	}

	.exhibit {
		max-width: 100%;
		margin: 0 auto;
	}

	/* Hero Section */
	.hero {
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		text-align: center;
		padding: 2rem;
		background: 
			linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.85)),
			radial-gradient(circle at 50% 50%, rgba(217, 119, 6, 0.15), transparent 70%);
		position: relative;
	}

	.hero-content {
		max-width: 900px;
		z-index: 2;
	}

	.exhibit-title {
		font-size: clamp(3rem, 8vw, 6rem);
		font-weight: 700;
		margin: 0 0 1rem 0;
		line-height: 1.1;
		text-transform: uppercase;
		letter-spacing: -0.02em;
	}

	.title-line {
		display: block;
		background: linear-gradient(135deg, #fbbf24, #dc2626);
		-webkit-background-clip: text;
		background-clip: text;
		-webkit-text-fill-color: transparent;
		text-shadow: 0 0 40px rgba(251, 191, 36, 0.3);
	}

	.title-sub {
		display: block;
		font-size: 0.4em;
		font-weight: 400;
		color: #a8a8a8;
		letter-spacing: 0.1em;
		margin-top: 0.5rem;
	}

	.hero-date {
		font-size: 1.25rem;
		color: #d97706;
		font-style: italic;
		margin: 0.5rem 0;
		letter-spacing: 0.05em;
	}

	.hero-divider {
		width: 100px;
		height: 2px;
		background: linear-gradient(90deg, transparent, #d97706, transparent);
		margin: 2rem auto;
	}

	.hero-intro {
		font-size: 1.25rem;
		line-height: 1.8;
		color: #c8c8c8;
		max-width: 700px;
		margin: 0 auto;
	}

	.scroll-indicator {
		position: absolute;
		bottom: 3rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 0.5rem;
		color: #888;
		font-size: 0.875rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		animation: bounce 2s infinite;
	}

	@keyframes bounce {
		0%, 100% { transform: translateY(0); }
		50% { transform: translateY(-10px); }
	}

	/* Content Sections */
	.content-section {
		padding: 6rem 2rem;
		position: relative;
	}

	.section-content {
		max-width: 1200px;
		margin: 0 auto;
	}

	.content-section h2 {
		font-size: clamp(2.5rem, 5vw, 4rem);
		margin: 0 0 2rem 0;
		font-weight: 700;
		line-height: 1.2;
		border-left: 6px solid #d97706;
		padding-left: 1.5rem;
	}

	.lead-text {
		font-size: 1.4rem;
		line-height: 1.8;
		color: #d8d8d8;
		margin-bottom: 2rem;
	}

	.content-section p {
		font-size: 1.125rem;
		line-height: 1.9;
		margin-bottom: 1.5rem;
		color: #c8c8c8;
	}

	.section-intro {
		font-size: 1.25rem;
		color: #d8d8d8;
		margin-bottom: 3rem;
		max-width: 800px;
	}

	/* Dark Section Variant */
	.dark-section {
		background: linear-gradient(180deg, #0a0a0a 0%, #1a1410 50%, #0a0a0a 100%);
	}

	/* Split Layout */
	.split-layout {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 4rem;
		align-items: center;
		margin-top: 3rem;
	}

	.split-layout.reverse {
		direction: rtl;
	}

	.split-layout.reverse > * {
		direction: ltr;
	}

	@media (max-width: 900px) {
		.split-layout {
			grid-template-columns: 1fr;
			gap: 2rem;
		}
		.split-layout.reverse {
			direction: ltr;
		}
	}

	/* Images */
	.image-wrapper {
		position: relative;
		margin: 2rem 0;
	}

	.image-wrapper img {
		width: 100%;
		height: auto;
		display: block;
		border-radius: 4px;
		box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
	}

	.sketch-wrapper img {
		border: 3px solid #4a4a4a;
		background: #f8f8f8;
		padding: 1.5rem;
	}

	.image-credit {
		margin-top: 0.75rem;
		font-size: 0.875rem;
		color: #888;
		font-style: italic;
		text-align: center;
	}

	.map-wrapper {
		position: relative;
		margin: 2rem 0;
	}

	.luna-embed-container {
		position: relative;
		width: 100%;
		margin-bottom: 2rem;
		border-radius: 8px;
		overflow: hidden;
		box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
	}

	.luna-embed-container iframe {
		display: block;
		width: 100%;
		border: none;
	}

	.map-caption {
		background: rgba(26, 20, 16, 0.8);
		padding: 2rem;
		margin-top: 0;
		border-left: 4px solid #d97706;
		backdrop-filter: blur(10px);
	}

	.caption-title {
		font-weight: 700;
		font-size: 1.25rem;
		color: #fbbf24;
		margin-bottom: 1rem;
	}

	.caption-text {
		margin-bottom: 1rem;
	}

	.caption-note {
		margin-top: 1.5rem;
		padding: 1rem;
		background: rgba(217, 119, 6, 0.1);
		border-radius: 4px;
		border: 1px solid rgba(217, 119, 6, 0.3);
	}

	.caption-note strong {
		color: #fbbf24;
	}

	/* Blockquotes */
	blockquote {
		margin: 2rem 0;
		padding: 2rem;
		background: rgba(217, 119, 6, 0.05);
		border-left: 6px solid #d97706;
		font-size: 1.3rem;
		font-style: italic;
		line-height: 1.7;
		color: #e8e8e8;
	}

	.historical-note {
		background: rgba(220, 38, 38, 0.1);
		border-left-color: #dc2626;
	}

	.resilience-quote {
		margin-top: 3rem;
		text-align: center;
		border: none;
		background: linear-gradient(135deg, rgba(217, 119, 6, 0.1), rgba(220, 38, 38, 0.1));
		padding: 3rem;
		border-radius: 8px;
		font-size: 1.5rem;
	}

	/* Comparison Wrapper */
	.comparison-wrapper {
		margin: 3rem 0;
	}

	.comparison-note {
		margin-top: 1.5rem;
		text-align: center;
		font-style: italic;
		color: #a8a8a8;
	}

	/* Bibliography */
	.bibliography-section {
		background: linear-gradient(180deg, #0a0a0a, #1a1410);
		padding: 6rem 2rem;
		border-top: 2px solid #2a2a2a;
	}

	.bibliography {
		display: grid;
		gap: 2rem;
		margin: 3rem 0;
	}

	.bib-entry {
		padding: 1.5rem;
		background: rgba(255, 255, 255, 0.03);
		border-left: 3px solid #d97706;
		border-radius: 4px;
	}

	.bib-source {
		font-weight: 700;
		color: #fbbf24;
		margin-bottom: 0.5rem;
		font-size: 0.9rem;
		text-transform: uppercase;
		letter-spacing: 0.05em;
	}

	.bib-entry p:last-child {
		margin-bottom: 0;
		font-size: 1rem;
	}

	.author-credit {
		margin-top: 4rem;
		padding-top: 2rem;
		border-top: 1px solid #2a2a2a;
		text-align: center;
		color: #888;
	}

	.author-credit p {
		margin: 0.5rem 0;
	}

	.author-credit .date {
		font-style: italic;
		font-size: 0.9rem;
	}

	/* Intro Section Styling */
	.intro-section {
		background: radial-gradient(ellipse at top, rgba(217, 119, 6, 0.05), transparent 70%);
	}

	:global(a[target="_blank"]) {
		color: #dc2626; /* Matches the exhibit's red/orange theme */
		text-decoration: none;
		font-weight: bold;
	}

	:global(a[target="_blank"]:hover) {
		text-decoration: underline;
	}
</style>
