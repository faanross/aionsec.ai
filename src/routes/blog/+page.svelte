<script lang="ts">
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	let mounted = $state(false);
	let currentSlide = $state(0);

	// Featured posts for carousel
	const featuredPosts = [
		{
			slug: 'hunt-begins',
			title: 'The Hunt Begins in 2026',
			subtitle: 'Building AionSec and the Future of Threat Hunting',
			excerpt: 'What if your defensive posture never slept? Agents reasoning over telemetry 24/7, building threat narratives in real-time.',
			date: 'January 2026',
			readTime: '12 min read'
		}
	];

	// All posts (including featured)
	const posts = [
		{
			slug: 'what-is-agentic-threat-hunting',
			title: 'What is Agentic Threat Hunting?',
			excerpt: 'Defining the new category where agents hunt and humans orchestrate. Learn how agentic threat hunting inverts the traditional model — continuous, scalable, human-directed.',
			date: 'January 2026',
			readTime: '8 min read',
			tags: ['Foundational', 'Agentic AI', 'Threat Hunting']
		},
		{
			slug: 'why-open-source-matters',
			title: 'Why Open-Source Matters for Security',
			excerpt: 'Open-source isn\'t a feature. It\'s a philosophy. For security tooling, where trust is everything and adversaries are always adapting, it\'s the only approach that makes sense.',
			date: 'January 2026',
			readTime: '6 min read',
			tags: ['Philosophy', 'Open-Source', 'Sovereignty']
		},
		{
			slug: 'continuous-vs-episodic-hunting',
			title: 'The Continuous vs. Episodic Hunting Gap',
			excerpt: 'Episodic hunting leaves gaps. Adversaries live in those gaps. The solution isn\'t hunting harder — it\'s hunting continuously, statefully, proactively.',
			date: 'January 2026',
			readTime: '7 min read',
			tags: ['Problem Definition', 'Threat Hunting', 'Foundational']
		},
		{
			slug: 'the-leapfrog-moment',
			title: 'The Leapfrog Moment',
			excerpt: 'The economics of advanced security capabilities inverted. What cost $500K five years ago costs $50/month today. This is the leapfrog moment.',
			date: 'January 2026',
			readTime: '8 min read',
			tags: ['Why Now', 'Economics', 'Foundational']
		},
		{
			slug: 'hunt-begins',
			title: 'The Hunt Begins in 2026: Building AionSec and the Future of Threat Hunting',
			excerpt: 'What if your defensive posture never slept? Agents reasoning over telemetry 24/7, building threat narratives in real-time, escalating high-fidelity leads while your team focuses on strategy.',
			date: 'January 2026',
			readTime: '12 min read',
			tags: ['Agentic AI', 'Threat Hunting', 'Launch']
		}
	];

	function nextSlide() {
		currentSlide = (currentSlide + 1) % featuredPosts.length;
	}

	function prevSlide() {
		currentSlide = (currentSlide - 1 + featuredPosts.length) % featuredPosts.length;
	}

	onMount(() => {
		mounted = true;

		// Auto-advance carousel every 8 seconds (if more than one post)
		if (featuredPosts.length > 1) {
			const interval = setInterval(nextSlide, 8000);
			return () => clearInterval(interval);
		}
	});
</script>

<svelte:head>
	<title>Blog | AionSec</title>
</svelte:head>

<section class="blog-hero">
	<div class="container">
		{#if mounted}
			<h1 in:fly={{ y: 30, duration: 800, delay: 200 }}>Blog</h1>
			<p class="lead" in:fly={{ y: 20, duration: 600, delay: 400 }}>
				Thoughts on agentic AI, threat hunting, and the future of security
			</p>
		{/if}
	</div>
</section>

{#if featuredPosts.length > 0}
	<section class="featured">
		<div class="container">
			{#if mounted}
				<h2 in:fly={{ y: 30, duration: 600, delay: 500 }}>Featured</h2>
				<div class="carousel" in:fly={{ y: 40, duration: 600, delay: 600 }}>
					{#each featuredPosts as post, index}
						{#if index === currentSlide}
							<a href="/blog/{post.slug}" class="featured-card glass-card" in:fade={{ duration: 500 }}>
								<div class="featured-content">
									<span class="badge">{post.date}</span>
									<h3>{post.title}</h3>
									<p class="subtitle">{post.subtitle}</p>
									<p class="excerpt">{post.excerpt}</p>
									<span class="read-more">Read Article →</span>
								</div>
							</a>
						{/if}
					{/each}

					{#if featuredPosts.length > 1}
						<div class="carousel-nav">
							<button onclick={prevSlide} aria-label="Previous">←</button>
							<div class="dots">
								{#each featuredPosts as _, index}
									<button
										class="dot"
										class:active={index === currentSlide}
										onclick={() => currentSlide = index}
										aria-label="Go to slide {index + 1}"
									></button>
								{/each}
							</div>
							<button onclick={nextSlide} aria-label="Next">→</button>
						</div>
					{/if}
				</div>
			{/if}
		</div>
	</section>
{/if}

<section class="all-posts">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 700 }}>All Posts</h2>
			<div class="posts-grid">
				{#each posts as post, index}
					<a
						href="/blog/{post.slug}"
						class="glass-card post-card"
						in:fly={{ y: 40, duration: 600, delay: 800 + index * 100 }}
					>
						<div class="post-meta">
							<span class="date">{post.date}</span>
							<span class="read-time">{post.readTime}</span>
						</div>
						<h3>{post.title}</h3>
						<p>{post.excerpt}</p>
						<div class="tags">
							{#each post.tags as tag}
								<span class="tag">{tag}</span>
							{/each}
						</div>
					</a>
				{/each}
			</div>

			{#if posts.length === 0}
				<div class="empty-state" in:fly={{ y: 30, duration: 600, delay: 800 }}>
					<p>More posts coming soon. Stay tuned.</p>
				</div>
			{/if}
		{/if}
	</div>
</section>

<style>
	.blog-hero {
		padding: 80px 0 40px;
		text-align: center;
	}

	.blog-hero h1 {
		margin-bottom: 16px;
	}

	.lead {
		font-size: clamp(16px, 1.8vw, 20px);
		color: rgba(255, 255, 255, 0.7);
	}

	.featured {
		padding: 40px 0 60px;
	}

	.featured h2 {
		margin-bottom: 24px;
		font-size: 16px;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		color: var(--aion-purple);
		background: none;
		-webkit-text-fill-color: var(--aion-purple);
	}

	.carousel {
		position: relative;
	}

	.featured-card {
		display: block;
		padding: 48px;
		text-decoration: none;
		border-color: rgba(255, 121, 198, 0.3);
	}

	.featured-card:hover {
		border-color: rgba(255, 121, 198, 0.5);
	}

	.featured-content .badge {
		margin-bottom: 16px;
	}

	.featured-content h3 {
		font-size: clamp(24px, 3vw, 36px);
		color: var(--white);
		margin-bottom: 12px;
		line-height: 1.3;
	}

	.featured-content .subtitle {
		font-size: clamp(16px, 1.5vw, 20px);
		color: var(--aion-purple);
		margin-bottom: 20px;
	}

	.featured-content .excerpt {
		font-size: 16px;
		line-height: 1.7;
		margin-bottom: 24px;
		max-width: 700px;
	}

	.read-more {
		color: var(--aion-purple);
		font-weight: 600;
		font-size: 14px;
		text-transform: uppercase;
		letter-spacing: 0.05em;
	}

	.carousel-nav {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 16px;
		margin-top: 24px;
	}

	.carousel-nav button {
		background: rgba(255, 255, 255, 0.1);
		border: 1px solid rgba(255, 255, 255, 0.2);
		color: var(--white);
		padding: 8px 16px;
		border-radius: 8px;
		cursor: pointer;
		font-family: inherit;
		transition: all 0.3s ease;
	}

	.carousel-nav button:hover {
		background: rgba(255, 255, 255, 0.2);
	}

	.dots {
		display: flex;
		gap: 8px;
	}

	.dot {
		width: 10px;
		height: 10px;
		border-radius: 50%;
		background: rgba(255, 255, 255, 0.3);
		padding: 0;
	}

	.dot.active {
		background: var(--aion-purple);
	}

	.all-posts {
		padding: 60px 0 120px;
	}

	.all-posts h2 {
		margin-bottom: 32px;
		font-size: 16px;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		color: var(--aion-purple);
		background: none;
		-webkit-text-fill-color: var(--aion-purple);
	}

	.posts-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
		gap: 24px;
	}

	.post-card {
		display: block;
		text-decoration: none;
		padding: 32px;
	}

	.post-meta {
		display: flex;
		gap: 16px;
		margin-bottom: 16px;
		font-size: 13px;
		color: rgba(255, 255, 255, 0.5);
	}

	.post-card h3 {
		font-size: 18px;
		color: var(--white);
		margin-bottom: 12px;
		line-height: 1.4;
	}

	.post-card p {
		font-size: 14px;
		line-height: 1.6;
		margin-bottom: 16px;
		display: -webkit-box;
		-webkit-line-clamp: 3;
		line-clamp: 3;
		-webkit-box-orient: vertical;
		overflow: hidden;
	}

	.tags {
		display: flex;
		flex-wrap: wrap;
		gap: 8px;
	}

	.tag {
		font-size: 12px;
		padding: 4px 10px;
		background: rgba(189, 147, 249, 0.1);
		border-radius: 12px;
		color: var(--aion-purple);
	}

	.empty-state {
		text-align: center;
		padding: 60px 0;
	}

	.empty-state p {
		font-size: 18px;
		color: rgba(255, 255, 255, 0.5);
	}

	@media (max-width: 768px) {
		.featured-card {
			padding: 32px 24px;
		}

		.posts-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
