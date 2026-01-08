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
					Human-Centric, Agent-Driven
				</div>
				<h1 in:fly={{ y: 30, duration: 800, delay: 400 }}>
					<span class="glow-text">Never Stop</span> Hunting
				</h1>
				<p class="subtitle" in:fly={{ y: 20, duration: 600, delay: 600 }}>
					Sovereign, continuous threat hunting capability powered by agentic AI.
					The adversary never stops. Neither should your defenses.
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
					<p>Hunters become orchestrators. One practitioner managing a team of autonomous agents achieves coverage previously requiring dedicated teams.</p>
				</div>
				<div class="glass-card pillar" in:fly={{ y: 40, duration: 600, delay: 1100 }}>
					<h3>Continuous</h3>
					<p>Agents hunt 24/7, building narratives in real-time — not reconstructing timelines post-incident. The eternal hunt.</p>
				</div>
				<div class="glass-card pillar" in:fly={{ y: 40, duration: 600, delay: 1200 }}>
					<h3>Sovereign</h3>
					<p>Your data stays yours. Your logic is auditable. Deploy anywhere — on-prem, cloud, air-gapped. No vendor black boxes.</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="launch">
	<div class="container">
		{#if mounted}
			<div class="glass-card launch-card" in:fly={{ y: 40, duration: 600, delay: 1300 }}>
				<span class="badge">Coming Soon</span>
				<h2>The Hunt Begins Q2 2026</h2>
				<p>Learn to build your own open-source agentic threat hunting platform from scratch. Course + open-source platform launching together.</p>
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
		font-size: clamp(10px, 1vw, 12px);
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
		font-size: clamp(13px, 1.2vw, 15px);
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
