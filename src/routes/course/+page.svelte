<script lang="ts">
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	let mounted = $state(false);
	let heroRevealed = $state(false);

	onMount(() => {
		mounted = true;
		// Delay the reveal for dramatic effect
		setTimeout(() => {
			heroRevealed = true;
		}, 1200);
	});
</script>

<svelte:head>
	<title>Course | AionSec</title>
</svelte:head>

<section class="course-hero">
	<div class="container">
		{#if mounted}
			<span class="badge" in:fly={{ y: 20, duration: 600, delay: 200 }}>Launching Q2 2026</span>
			<h1 in:fly={{ y: 30, duration: 800, delay: 400 }}>
				Soon, the best threat hunters won't hunt.
			</h1>
			{#if heroRevealed}
				<p class="reveal-line" in:fly={{ y: 20, duration: 600 }}>
					They'll orchestrate.
				</p>
			{/if}
			<p class="lead" in:fly={{ y: 20, duration: 600, delay: 1800 }}>
				Learn to build autonomous hunting systems that work while you sleep.
				Join the practitioners who are getting ahead of the curve.
			</p>
		{/if}
	</div>
</section>

<section class="problem">
	<div class="container">
		{#if mounted}
			<div class="problem-content" in:fly={{ y: 30, duration: 600, delay: 2000 }}>
				<h2>The reality you know too well</h2>
				<div class="problem-grid">
					<div class="problem-item">
						<span class="problem-number">500+</span>
						<p>alerts per day. You catch maybe 5%.</p>
					</div>
					<div class="problem-item">
						<span class="problem-number">$100K+</span>
						<p>per year for SIEM. Still misses slow attacks.</p>
					</div>
					<div class="problem-item">
						<span class="problem-number">24/7</span>
						<p>adversaries run autonomous C2. You work 9-5.</p>
					</div>
				</div>
				<p class="problem-statement">
					The industry is shifting to agentic systems. The question isn't <em>if</em> you'll need these skills—it's whether you'll build them now or scramble to catch up later.
				</p>
			</div>
		{/if}
	</div>
</section>

<section class="waitlist">
	<div class="container">
		<div class="glass-card waitlist-card" class:visible={mounted}>
			<h2>Get Ahead of the Curve</h2>
			<p>
				Be first to know when we launch.
				<br />Waitlist members get <strong>20% off</strong> at launch.
			</p>

			<div class="ml-embedded" data-form="jSWmMO"></div>

			<p class="note">
				One email when we launch. That's it. No spam, no drip campaigns.
			</p>
		</div>
	</div>
</section>

<section class="course-details">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 700 }}>What You'll Build</h2>
			<p class="section-lead" in:fly={{ y: 20, duration: 600, delay: 800 }}>
				A production-ready agentic threat hunting system. No vendor lock-in. 100% open-source.
			</p>
			<div class="details-grid">
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 900 }}>
					<h3>The System</h3>
					<ul>
						<li>Deploy stateful memory that tracks threats over weeks</li>
						<li>Integrate endpoint + network telemetry (Sysmon, Zeek)</li>
						<li>Orchestrate LLM agents that reason about evidence</li>
						<li>Build autonomous action loops with safety rails</li>
						<li>Run 24/7 for $10-50/month in API costs</li>
					</ul>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1000 }}>
					<h3>This Is For You If...</h3>
					<ul>
						<li>You're drowning in alerts and want a way out</li>
						<li>You've heard "agentic AI" but don't know where to start</li>
						<li>You want to build, not just buy another black box</li>
						<li>You're a solo practitioner punching above your weight</li>
						<li>You want skills that matter in 2027, not just today</li>
					</ul>
				</div>
				<div class="glass-card" in:fly={{ y: 40, duration: 600, delay: 1100 }}>
					<h3>What Makes It Different</h3>
					<ul>
						<li>Hands-on: you deploy a working system by module 12</li>
						<li>Open-source: no vendor lock-in, ever</li>
						<li>Affordable: $299 course + $10-50/month to run</li>
						<li>Practical: built on Sysmon, Zeek, MITRE ATT&CK</li>
						<li>Future-proof: agentic skills transfer everywhere</li>
					</ul>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="faq">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 1200 }}>Common Questions</h2>
			<div class="faq-grid">
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1300 }}>
					<h3>Do I need coding experience?</h3>
					<p>Helpful, but not required. The agentic paradigm empowers anyone to build powerful systems without years of traditional development experience. If you can follow instructions and think logically, you can do this.</p>
				</div>
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1400 }}>
					<h3>Do I need ML or AI expertise?</h3>
					<p>No. You'll use pre-trained models and learn the orchestration patterns. The hard AI work is already done—you're learning to direct it.</p>
				</div>
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1500 }}>
					<h3>What does it cost to run the system?</h3>
					<p>$10-50/month in API costs. The architecture uses local models for 95% of work, premium LLMs only when needed.</p>
				</div>
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1600 }}>
					<h3>Will this work with my existing tools?</h3>
					<p>Yes. The pattern is tool-agnostic. We use Sysmon + Zeek as examples, but the architecture adapts to any telemetry source.</p>
				</div>
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1700 }}>
					<h3>When does it launch?</h3>
					<p>Q2 2026. Waitlist members get notified first and receive 20% early bird pricing.</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="timeline">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 1800 }}>The Roadmap</h2>
			<div class="timeline-grid">
				<div class="glass-card timeline-item" in:fly={{ y: 40, duration: 600, delay: 1900 }}>
					<span class="badge">Q2 2026</span>
					<h3>Level 1 Launch</h3>
					<p>Build the foundational agentic threat hunting system</p>
				</div>
				<div class="glass-card timeline-item" in:fly={{ y: 40, duration: 600, delay: 2000 }}>
					<span class="badge">Q3-Q4 2026</span>
					<h3>Platform Goes Open-Source</h3>
					<p>Full platform on GitHub, free for everyone</p>
				</div>
				<div class="glass-card timeline-item" in:fly={{ y: 40, duration: 600, delay: 2100 }}>
					<span class="badge">2027+</span>
					<h3>Levels 2 & 3</h3>
					<p>Advanced courses and CAATH certification</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="final-cta">
	<div class="container">
		{#if mounted}
			<div class="glass-card cta-card" in:fly={{ y: 40, duration: 600, delay: 2200 }}>
				<h2>The shift is happening.</h2>
				<p>Those who learn to orchestrate agents will lead. Those who don't will chase alerts forever.</p>
				<a href="#waitlist" class="btn-primary">Join the Waitlist</a>
			</div>
		{/if}
	</div>
</section>

<style>
	.course-hero {
		padding: 80px 0 40px;
		text-align: center;
	}

	.course-hero .badge {
		margin-bottom: 24px;
	}

	.course-hero h1 {
		margin-bottom: 0;
		max-width: 900px;
		margin-left: auto;
		margin-right: auto;
	}

	.reveal-line {
		font-size: clamp(28px, 4vw, 48px);
		font-weight: 700;
		color: var(--aion-yellow);
		margin: 16px 0 32px;
		text-shadow: 0 0 30px rgba(255, 214, 0, 0.4);
	}

	.lead {
		font-size: clamp(16px, 1.8vw, 20px);
		color: rgba(255, 255, 255, 0.8);
		max-width: 600px;
		margin: 0 auto;
		line-height: 1.7;
	}

	/* Problem Section */
	.problem {
		padding: 60px 0;
	}

	.problem-content {
		max-width: 900px;
		margin: 0 auto;
		text-align: center;
	}

	.problem h2 {
		margin-bottom: 40px;
		color: rgba(255, 255, 255, 0.9);
	}

	.problem-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
		gap: 32px;
		margin-bottom: 40px;
	}

	.problem-item {
		text-align: center;
	}

	.problem-number {
		display: block;
		font-size: clamp(36px, 5vw, 56px);
		font-weight: 700;
		color: var(--aion-purple);
		line-height: 1;
		margin-bottom: 8px;
	}

	.problem-item p {
		font-size: 14px;
		color: rgba(255, 255, 255, 0.7);
		margin: 0;
	}

	.problem-statement {
		font-size: clamp(16px, 1.8vw, 20px);
		color: rgba(255, 255, 255, 0.85);
		line-height: 1.7;
		max-width: 700px;
		margin: 0 auto;
	}

	.problem-statement em {
		color: var(--aion-yellow);
		font-style: normal;
	}

	/* Waitlist */
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
		line-height: 1.8;
	}

	.waitlist-count {
		color: var(--aion-yellow);
		font-size: 18px;
	}

	.waitlist-card strong {
		color: var(--aion-yellow);
	}

	.note {
		margin-top: 24px;
		font-size: 14px;
		color: rgba(255, 255, 255, 0.5);
	}

	:global(.ml-embedded) {
		margin: 24px 0;
	}

	:global(.ml-form-embedWrapper) {
		font-family: 'JetBrains Mono', monospace !important;
	}

	/* Course Details */
	.course-details {
		padding: 80px 0;
	}

	.course-details h2 {
		text-align: center;
		margin-bottom: 16px;
	}

	.section-lead {
		text-align: center;
		color: rgba(255, 255, 255, 0.7);
		margin-bottom: 48px;
		font-size: 16px;
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

	/* FAQ Section */
	.faq {
		padding: 80px 0;
	}

	.faq h2 {
		text-align: center;
		margin-bottom: 48px;
	}

	.faq-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: 24px;
		max-width: 900px;
		margin: 0 auto;
	}

	.faq-item {
		padding: 24px;
	}

	.faq-item h3 {
		color: var(--aion-yellow);
		font-size: 16px;
		margin-bottom: 12px;
	}

	.faq-item p {
		font-size: 14px;
		color: rgba(255, 255, 255, 0.75);
		line-height: 1.6;
		margin: 0;
	}

	/* Timeline */
	.timeline {
		padding: 60px 0;
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

	/* Final CTA */
	.final-cta {
		padding: 40px 0 120px;
	}

	.cta-card {
		max-width: 600px;
		margin: 0 auto;
		text-align: center;
		padding: 48px;
	}

	.cta-card h2 {
		margin-bottom: 16px;
	}

	.cta-card p {
		font-size: 16px;
		color: rgba(255, 255, 255, 0.8);
		margin-bottom: 32px;
		line-height: 1.7;
	}

	.btn-primary {
		display: inline-block;
		background: var(--aion-yellow);
		color: var(--black);
		padding: 16px 32px;
		font-weight: 600;
		font-size: 16px;
		border: none;
		cursor: pointer;
		transition: all 0.3s ease;
		text-decoration: none;
	}

	.btn-primary:hover {
		transform: translateY(-2px);
		box-shadow: 0 8px 30px rgba(255, 214, 0, 0.3);
	}

	@media (max-width: 768px) {
		.waitlist-card {
			padding: 32px 24px;
		}

		.timeline-item {
			padding: 24px;
		}

		.cta-card {
			padding: 32px 24px;
		}

		.problem-grid {
			gap: 24px;
		}
	}
</style>
