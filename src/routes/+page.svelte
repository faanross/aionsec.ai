<script lang="ts">
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	let mounted = $state(false);

	onMount(() => {
		mounted = true;
	});
</script>

<section class="hero">
	<div class="container">
		{#if mounted}
			<div class="hero-content" in:fade={{ duration: 800, delay: 200 }}>
				<div class="tagline" in:fly={{ y: 20, duration: 600, delay: 300 }}>
					While You Sleep, Threats Don't
				</div>
				<h1 in:fly={{ y: 30, duration: 800, delay: 400 }}>
					<span class="glow-text">Never Stop</span> Hunting
				</h1>
				<p class="subtitle" in:fly={{ y: 20, duration: 600, delay: 600 }}>
					Build AI systems that hunt threats 24/7.
					<br />Open-source. Sovereign. Unbounded.
				</p>
				<div class="cta-group" in:fly={{ y: 20, duration: 600, delay: 800 }}>
					<a href="/course" class="btn-primary btn-cta">Join the Hunt</a>
					<a href="/about" class="btn-primary">Learn More</a>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="pillars">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 900 }}>Built on Three Pillars</h2>
			<div class="pillar-grid">
				<div class="glass-card pillar" in:fly={{ y: 40, duration: 600, delay: 1000 }}>
					<h3>Human-Centric</h3>
					<p>Your judgment guides the hunt. Agents handle the repetitive work at machine speed. The craft stays human — now it scales.</p>
				</div>
				<div class="glass-card pillar" in:fly={{ y: 40, duration: 600, delay: 1100 }}>
					<h3>The Eternal Hunt</h3>
					<p>Agents hunt continuously, building threat narratives in real-time. Not reconstructing timelines post-incident.</p>
				</div>
				<div class="glass-card pillar" in:fly={{ y: 40, duration: 600, delay: 1200 }}>
					<h3>Your Data, Your Control</h3>
					<p>Your telemetry. Your logic. Deploy anywhere — on-prem, cloud, air-gapped. No vendor SaaS. No black boxes. Fully auditable.</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="launch">
	<div class="container">
		{#if mounted}
			<div class="glass-card launch-card" in:fly={{ y: 40, duration: 600, delay: 1300 }}>
				<span class="badge">Coming Q2 2026</span>
				<h2>The Hunt is Evolving. Join Us.</h2>
				<p>Learn to build your own agentic threat hunting system. Waitlist members get 20% off.</p>
				<a href="/course" class="btn-primary btn-cta">Join the Waitlist</a>
			</div>
		{/if}
	</div>
</section>

<style>
	.hero {
		min-height: calc(100vh - 80px);
		display: flex;
		align-items: center;
		padding: 60px 0;
	}

	.hero-content {
		max-width: 800px;
	}

	.tagline {
		font-size: clamp(12px, 1.2vw, 14px);
		font-weight: 500;
		color: var(--aion-purple);
		text-transform: uppercase;
		letter-spacing: 0.15em;
		margin-bottom: 12px;
	}

	.hero h1 {
		margin-bottom: 16px;
	}

	.subtitle {
		font-size: clamp(16px, 1.5vw, 18px);
		color: rgba(255, 255, 255, 0.8);
		line-height: 1.7;
		margin-bottom: 28px;
		max-width: 500px;
	}

	.cta-group {
		display: flex;
		gap: 12px;
		flex-wrap: wrap;
	}

	.pillars {
		padding: 60px 0;
	}

	.pillars h2 {
		text-align: center;
		margin-bottom: 32px;
	}

	.pillar-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
		gap: 16px;
	}

	.pillar h3 {
		color: var(--aion-yellow);
		margin-bottom: 10px;
	}

	.pillar p {
		line-height: 1.65;
		font-size: 13px;
	}

	.launch {
		padding: 60px 0 80px;
	}

	.launch-card {
		max-width: 550px;
		margin: 0 auto;
		text-align: center;
		padding: 32px;
	}

	.launch-card .badge {
		margin-bottom: 14px;
	}

	.launch-card h2 {
		margin-bottom: 14px;
	}

	.launch-card p {
		margin-bottom: 24px;
		font-size: 13px;
	}

	@media (max-width: 768px) {
		.hero {
			padding: 40px 0;
		}

		.launch-card {
			padding: 32px 24px;
		}
	}
</style>
