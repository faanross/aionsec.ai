<script lang="ts">
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	let mounted = $state(false);

	onMount(() => {
		mounted = true;
	});
</script>

<svelte:head>
	<title>About | AionSec</title>
</svelte:head>

<section class="about-hero">
	<div class="container">
		{#if mounted}
			<h1 in:fly={{ y: 30, duration: 800, delay: 200 }}>Never Stop Hunting</h1>
			<p class="lead" in:fly={{ y: 20, duration: 600, delay: 400 }}>
				Human-Centric, Agent-Driven Threat Hunting
			</p>
		{/if}
	</div>
</section>

<section class="mission">
	<div class="container">
		{#if mounted}
			<div class="content-grid">
				<div class="content-block" in:fly={{ y: 30, duration: 600, delay: 500 }}>
					<p>
						At <strong>AionSec</strong>, we believe that in an era of autonomous adversaries,
						a static defense is a failed defense.
					</p>
					<p>
						Our name is inspired by the Hellenic deity <em>Aion</em>, representing unbounded,
						eternal time. It reflects our mission: to move cybersecurity away from reactive
						"point-in-time" alerts and toward a state of <strong>continuous, relentless pursuit</strong>.
					</p>
				</div>
				<div class="content-block" in:fly={{ y: 30, duration: 600, delay: 600 }}>
					<p>
						We are the pioneers of <strong>Human-Centric, Agent-Driven Threat Hunting</strong>.
						We don't build tools to replace the hunter; we build the agentic systems that empower them.
					</p>
					<p>
						By fusing the unmatched intuition of the human practitioner with the processing power
						and infinite scale of agentic intelligence, we are democratizing elite defense.
					</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="philosophy">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 700 }}>Our Philosophy</h2>
			<div class="philosophy-grid">
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 800 }}>
					<h3>Symbiosis Over Replacement</h3>
					<p>
						AI won't replace analysts. Analysts using AI will replace analysts who don't.
						The craft remains — intuition, creativity, adversarial thinking are irreplaceable.
						But now they're amplified.
					</p>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 900 }}>
					<h3>Continuous Over Episodic</h3>
					<p>
						The adversary operates on unbounded time. They persist across days, weeks.
						They adapt. They wait. Your defenses should match their tempo — not business hours.
					</p>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1000 }}>
					<h3>Sovereignty Over Dependency</h3>
					<p>
						Your telemetry. Your logic. Your deployment. No vendor SaaS. No black boxes.
						Modular, adaptable, community-driven.
					</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="quote-section">
	<div class="container">
		{#if mounted}
			<blockquote class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1100 }}>
				<p>The adversary never stops.<br />With AionSec, the hunt is eternal.</p>
			</blockquote>
		{/if}
	</div>
</section>

<style>
	.about-hero {
		padding: 80px 0 60px;
		text-align: center;
	}

	.about-hero h1 {
		margin-bottom: 16px;
	}

	.lead {
		font-size: clamp(18px, 2vw, 24px);
		color: var(--aion-purple);
		font-weight: 500;
	}

	.mission {
		padding: 60px 0;
	}

	.content-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
		gap: 48px;
	}

	.content-block p {
		font-size: 18px;
		line-height: 1.8;
		margin-bottom: 24px;
	}

	.content-block strong {
		color: var(--aion-yellow);
	}

	.content-block em {
		color: var(--aion-purple);
	}

	.philosophy {
		padding: 80px 0;
	}

	.philosophy h2 {
		text-align: center;
		margin-bottom: 48px;
	}

	.philosophy-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: 24px;
	}

	.philosophy-grid h3 {
		color: var(--aion-yellow);
		margin-bottom: 16px;
		font-size: 18px;
	}

	.philosophy-grid p {
		line-height: 1.7;
	}

	.quote-section {
		padding: 60px 0 120px;
	}

	blockquote {
		max-width: 800px;
		margin: 0 auto;
		text-align: center;
		padding: 48px;
	}

	blockquote p {
		font-size: clamp(20px, 2.5vw, 28px);
		font-weight: 500;
		color: var(--white);
		line-height: 1.5;
	}

	@media (max-width: 768px) {
		.content-grid {
			grid-template-columns: 1fr;
			gap: 32px;
		}

		.content-block p {
			font-size: 16px;
		}

		blockquote {
			padding: 32px 24px;
		}
	}
</style>
