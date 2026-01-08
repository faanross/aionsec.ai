<script lang="ts">
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	let mounted = $state(false);

	onMount(() => {
		mounted = true;
	});
</script>

<svelte:head>
	<title>Course | AionSec</title>
</svelte:head>

<section class="course-hero">
	<div class="container">
		{#if mounted}
			<span class="badge" in:fly={{ y: 20, duration: 600, delay: 200 }}>Launching Q2 2026</span>
			<h1 in:fly={{ y: 30, duration: 800, delay: 300 }}>Build Your Own Agentic Threat Hunting Platform</h1>
			<p class="lead" in:fly={{ y: 20, duration: 600, delay: 500 }}>
				Learn to build sovereign, continuous threat hunting capability from scratch.
				No vendor lock-in. No black boxes. 100% open-source.
			</p>
		{/if}
	</div>
</section>

<section class="waitlist">
	<div class="container">
		<div class="glass-card waitlist-card" class:visible={mounted}>
			<h2>Join the Waitlist</h2>
			<p>
				Be the first to know when enrollment opens.
				Waitlist members get <strong>20% early bird discount</strong>.
			</p>

			<div class="ml-embedded" data-form="jSWmMO"></div>

			<p class="note">
				No spam, no aggressive emails — just one notification when the course has a set launch date.
			</p>
		</div>
	</div>
</section>

<section class="course-details">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 700 }}>What You'll Build</h2>
			<div class="details-grid">
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 800 }}>
					<h3>Level 1: Foundation</h3>
					<ul>
						<li>Deploy the Receptor (stateful memory core)</li>
						<li>Integrate Sysmon + Zeek telemetry</li>
						<li>Orchestrate multi-model LLM agents</li>
						<li>Implement clinical reasoning over telemetry</li>
						<li>Build autonomous action loops with safety rails</li>
					</ul>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 900 }}>
					<h3>Who It's For</h3>
					<ul>
						<li>Threat hunters looking to evolve</li>
						<li>Detection engineers ready for the next frontier</li>
						<li>Security leaders wanting continuous hunting</li>
						<li>Solo practitioners punching above their weight</li>
					</ul>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1000 }}>
					<h3>What Makes It Different</h3>
					<ul>
						<li>Hands-on deployment (not theory)</li>
						<li>Open-source stack (no vendor lock-in)</li>
						<li>Sovereign architecture (you control everything)</li>
						<li>Cost-optimized design (local + premium LLM strategy)</li>
					</ul>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="timeline">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 1100 }}>The Roadmap</h2>
			<div class="timeline-grid">
				<div class="glass-card timeline-item" in:fly={{ y: 40, duration: 600, delay: 1200 }}>
					<span class="badge">Q2 2026</span>
					<h3>Level 1 Course Launch</h3>
					<p>Build the foundational agentic threat hunting system</p>
				</div>
				<div class="glass-card timeline-item" in:fly={{ y: 40, duration: 600, delay: 1300 }}>
					<span class="badge">Q3-Q4 2026</span>
					<h3>Platform Launch</h3>
					<p>Open-source platform on GitHub, free for everyone</p>
				</div>
				<div class="glass-card timeline-item" in:fly={{ y: 40, duration: 600, delay: 1400 }}>
					<span class="badge">2027-2028</span>
					<h3>Levels 2 & 3 + Certification</h3>
					<p>Advanced courses and CAATH certification program</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<style>
	.course-hero {
		padding: 80px 0 60px;
		text-align: center;
	}

	.course-hero .badge {
		margin-bottom: 24px;
	}

	.course-hero h1 {
		margin-bottom: 24px;
		max-width: 900px;
		margin-left: auto;
		margin-right: auto;
	}

	.lead {
		font-size: clamp(16px, 1.8vw, 20px);
		color: rgba(255, 255, 255, 0.8);
		max-width: 700px;
		margin: 0 auto;
		line-height: 1.7;
	}

	.waitlist {
		padding: 60px 0;
	}

	.waitlist-card {
		max-width: 600px;
		margin: 0 auto;
		text-align: center;
		padding: 48px;
		opacity: 0;
		transform: translateY(40px);
		transition: opacity 0.6s ease, transform 0.6s ease;
		transition-delay: 0.6s;
	}

	.waitlist-card.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.waitlist-card h2 {
		margin-bottom: 16px;
	}

	.waitlist-card > p {
		margin-bottom: 32px;
		font-size: 16px;
	}

	.waitlist-card strong {
		color: var(--aion-yellow);
	}

	.note {
		margin-top: 24px;
		font-size: 14px;
		color: rgba(255, 255, 255, 0.5);
	}

	/* MailerLite form styling */
	:global(.ml-embedded) {
		margin: 24px 0;
	}

	:global(.ml-form-embedWrapper) {
		font-family: 'JetBrains Mono', monospace !important;
	}

	.course-details {
		padding: 80px 0;
	}

	.course-details h2 {
		text-align: center;
		margin-bottom: 48px;
	}

	.details-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: 24px;
	}

	.details-grid h3 {
		color: var(--aion-yellow);
		margin-bottom: 20px;
		font-size: 18px;
	}

	.details-grid ul {
		list-style: none;
	}

	.details-grid li {
		padding: 8px 0;
		padding-left: 20px;
		position: relative;
		color: rgba(255, 255, 255, 0.85);
		font-size: 14px;
		line-height: 1.6;
	}

	.details-grid li::before {
		content: '>';
		position: absolute;
		left: 0;
		color: var(--aion-purple);
		font-weight: 600;
	}

	.timeline {
		padding: 60px 0 120px;
	}

	.timeline h2 {
		text-align: center;
		margin-bottom: 48px;
	}

	.timeline-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: 24px;
		max-width: 900px;
		margin: 0 auto;
	}

	.timeline-item {
		text-align: center;
		padding: 32px;
	}

	.timeline-item .badge {
		margin-bottom: 16px;
	}

	.timeline-item h3 {
		color: var(--white);
		margin-bottom: 12px;
		font-size: 18px;
	}

	.timeline-item p {
		font-size: 14px;
	}

	@media (max-width: 768px) {
		.waitlist-card {
			padding: 32px 24px;
		}

		.timeline-item {
			padding: 24px;
		}
	}
</style>
