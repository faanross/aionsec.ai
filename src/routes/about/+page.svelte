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
			<h1 in:fly={{ y: 30, duration: 800, delay: 200 }}>Democratizing Elite Defense</h1>
			<p class="lead" in:fly={{ y: 20, duration: 600, delay: 400 }}>
				Building the future of threat hunting — together.
			</p>
		{/if}
	</div>
</section>

<section class="origin">
	<div class="container">
		{#if mounted}
			<div class="content-block" in:fly={{ y: 30, duration: 600, delay: 500 }}>
				<h2>Why AionSec Exists</h2>
				<p>
					For too long, advanced threat hunting has been locked behind enterprise budgets
					and dedicated teams. The tools existed, but they required six-figure investments
					and specialized ML expertise.
				</p>
				<p>
					That changed. Foundation models and open-source infrastructure created a
					leapfrog moment. What cost $500K five years ago can now be built for
					$10-50/month in API costs.
				</p>
				<p>
					<strong>AionSec exists to make that accessible.</strong> Not as a vendor selling
					black boxes, but as practitioners sharing a pattern that works.
				</p>
			</div>
		{/if}
	</div>
</section>

<section class="name-meaning">
	<div class="container">
		{#if mounted}
			<div class="glass-card meaning-card" in:fly={{ y: 40, duration: 600, delay: 700 }}>
				<h2>The Name</h2>
				<p>
					<em>Aion</em> (Αἰών) — the Hellenic deity of unbounded, eternal time.
					Not the ticking clock of Chronos, but cyclical, infinite presence.
				</p>
				<p>
					The adversary never stops. They persist across days and weeks. They adapt. They wait.
					<br /><strong>The hunt should match their tempo.</strong>
				</p>
			</div>
		{/if}
	</div>
</section>

<section class="philosophy">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 800 }}>What We Believe</h2>
			<div class="philosophy-grid">
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 900 }}>
					<h3>Amplification, Not Replacement</h3>
					<p>
						AI won't replace hunters. Hunters using AI will outpace those who don't.
						The craft remains — intuition, creativity, adversarial thinking.
						These are irreplaceable. Now they're amplified.
					</p>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1000 }}>
					<h3>Open by Default</h3>
					<p>
						The pattern is the product. Open-source means full transparency,
						community-driven improvement, and shared ownership.
						When one practitioner makes it better, everyone benefits.
					</p>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1100 }}>
					<h3>Practitioners First</h3>
					<p>
						We're not building for Fortune 500 procurement cycles. We're building for
						the solo practitioner, the small team, the defender who needs to punch
						above their weight.
					</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="quote-section">
	<div class="container">
		{#if mounted}
			<blockquote class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1200 }}>
				<p>The adversary never stops.<br />Neither do we.</p>
			</blockquote>
		{/if}
	</div>
</section>

<section class="cta-section">
	<div class="container">
		{#if mounted}
			<div class="cta-content" in:fly={{ y: 30, duration: 600, delay: 1300 }}>
				<h2>Ready to Join the Hunt?</h2>
				<div class="cta-buttons">
					<a href="/course" class="btn-primary btn-cta">Join the Waitlist</a>
					<a href="/blog" class="btn-primary">Read the Blog</a>
				</div>
			</div>
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

	.origin {
		padding: 60px 0;
	}

	.origin .content-block {
		max-width: 700px;
		margin: 0 auto;
	}

	.origin h2 {
		margin-bottom: 32px;
		text-align: center;
	}

	.origin p {
		font-size: 18px;
		line-height: 1.8;
		margin-bottom: 24px;
		color: rgba(255, 255, 255, 0.85);
	}

	.origin strong {
		color: var(--aion-yellow);
	}

	.name-meaning {
		padding: 60px 0;
	}

	.meaning-card {
		max-width: 700px;
		margin: 0 auto;
		padding: 48px;
		text-align: center;
	}

	.meaning-card h2 {
		margin-bottom: 24px;
	}

	.meaning-card p {
		font-size: 18px;
		line-height: 1.8;
		margin-bottom: 16px;
	}

	.meaning-card em {
		color: var(--aion-purple);
		font-style: normal;
		font-weight: 500;
	}

	.meaning-card strong {
		color: var(--aion-yellow);
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
		padding: 60px 0;
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

	.cta-section {
		padding: 40px 0 120px;
	}

	.cta-content {
		text-align: center;
	}

	.cta-content h2 {
		margin-bottom: 32px;
	}

	.cta-buttons {
		display: flex;
		gap: 16px;
		justify-content: center;
		flex-wrap: wrap;
	}

	@media (max-width: 768px) {
		.origin p {
			font-size: 16px;
		}

		.meaning-card {
			padding: 32px 24px;
		}

		.meaning-card p {
			font-size: 16px;
		}

		blockquote {
			padding: 32px 24px;
		}
	}
</style>
