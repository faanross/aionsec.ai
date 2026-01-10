<script lang="ts">
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	let mounted = $state(false);
	let heroRevealed = $state(false);
	let formSubmitted = $state(false);
	let formLoading = $state(false);

	onMount(() => {
		mounted = true;
		setTimeout(() => {
			heroRevealed = true;
		}, 1200);
	});

	async function handleSubmit(event: Event) {
		event.preventDefault();
		const form = event.target as HTMLFormElement;
		const formData = new FormData(form);

		formLoading = true;

		try {
			const response = await fetch(form.action, {
				method: 'POST',
				body: formData,
				mode: 'no-cors'
			});
			formSubmitted = true;
		} catch (error) {
			console.error('Form submission error:', error);
			formSubmitted = true; // Show success anyway since no-cors doesn't give us response
		} finally {
			formLoading = false;
		}
	}
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
				<h2>The craft is changing</h2>
				<div class="problem-grid">
					<div class="problem-item">
						<span class="problem-label">Same intuition</span>
						<p>now amplified</p>
					</div>
					<div class="problem-item">
						<span class="problem-label">Same creativity</span>
						<p>now scalable</p>
					</div>
					<div class="problem-item">
						<span class="problem-label">Same expertise</span>
						<p>now multiplied</p>
					</div>
				</div>
				<p class="problem-statement">
					The question is whether you evolve with it—or get left behind.
				</p>
			</div>
		{/if}
	</div>
</section>

<section class="waitlist" id="waitlist">
	<div class="container">
		<div class="glass-card waitlist-card" class:visible={mounted}>
			<h2>Get Ahead of the Curve</h2>
			<p>
				Be first to know when we launch.
				<br />Waitlist members get <strong>20% off</strong> at launch.
			</p>

			{#if !formSubmitted}
				<form
					class="waitlist-form"
					action="https://assets.mailerlite.com/jsonp/1462037/forms/152012474066929011/subscribe"
					method="post"
					onsubmit={handleSubmit}
				>
					<div class="form-fields">
						<input
							type="email"
							name="fields[email]"
							placeholder="Email"
							required
							autocomplete="email"
						/>
						<input
							type="text"
							name="fields[name]"
							placeholder="Name (Optional)"
							autocomplete="given-name"
						/>
					</div>
					<input type="hidden" name="ml-submit" value="1" />
					<input type="hidden" name="anticsrf" value="true" />
					<button type="submit" class="btn-submit" disabled={formLoading}>
						{#if formLoading}
							<span class="loading-spinner"></span>
							Joining...
						{:else}
							Join Waitlist
						{/if}
					</button>
				</form>
			{:else}
				<div class="form-success">
					<p class="success-title">You're on the list</p>
					<p class="success-message">You'll receive one email when the course launches (Q2 2026).</p>
					<p class="success-link">In the meantime: <a href="https://www.linkedin.com/company/aionsec" target="_blank" rel="noopener noreferrer">AionSec on LinkedIn</a></p>
				</div>
			{/if}

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
						<li>Run 24/7 with low monthly API costs</li>
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
						<li>Affordable: $299, lifetime access</li>
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
					<p>Low monthly API costs — typically under $100. The architecture offloads routine tasks to local models; premium LLMs kick in only when deeper reasoning is needed.</p>
				</div>
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1600 }}>
					<h3>Will this work with my existing tools?</h3>
					<p>Yes. The pattern is tool-agnostic. We use Sysmon + Zeek as examples, but the architecture adapts to any telemetry source.</p>
				</div>
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1700 }}>
					<h3>When does it launch?</h3>
					<p>Q2 2026. Waitlist members get notified first and receive 20% early bird pricing.</p>
				</div>
				<div class="glass-card faq-item" in:fly={{ y: 40, duration: 600, delay: 1800 }}>
					<h3>Do I get lifetime access?</h3>
					<p>Yes. One payment, permanent access — including all future updates to the course content.</p>
				</div>
			</div>
		{/if}
	</div>
</section>

<section class="instructor">
	<div class="container">
		{#if mounted}
			<h2 in:fly={{ y: 30, duration: 600, delay: 1900 }}>Your Instructor</h2>
			<div class="instructor-content" in:fly={{ y: 40, duration: 600, delay: 2000 }}>
				<div class="instructor-image">
					<img src="/images/moi.png" alt="Faan Rossouw" />
				</div>
				<div class="instructor-bio glass-card">
					<h3>Faan Rossouw</h3>
					<p class="instructor-tagline">Threat Hunting + Agentic AI</p>
					<p>
						I'm a security researcher focused on the intersection of threat hunting and agentic AI.
						The convergence of these fields is unlocking what was impossible before: continuous hunting
						at machine speed with human intuition.
					</p>
					<p>
						I do research at <a href="https://www.activecountermeasures.com" target="_blank" rel="noopener noreferrer">Active Countermeasures</a>
						and instruct at <a href="https://www.antisyphontraining.com/instructor/faan-ross/" target="_blank" rel="noopener noreferrer">AntiSyphon</a>,
						teaching threat hunting and offensive security tooling.
					</p>
					<p>
						AionSec is where my life's journey aligns — everything I've learned,
						built, and obsessed over, now channeled into making elite threat hunting accessible to everyone.
					</p>
					<div class="instructor-links">
						<a href="https://github.com/faanross" target="_blank" rel="noopener noreferrer" class="instructor-link">
							<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
								<path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
							</svg>
						</a>
						<a href="https://www.youtube.com/@FaanRoss" target="_blank" rel="noopener noreferrer" class="instructor-link">
							<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
								<path d="M19.615 3.184c-3.604-.246-11.631-.245-15.23 0-3.897.266-4.356 2.62-4.385 8.816.029 6.185.484 8.549 4.385 8.816 3.6.245 11.626.246 15.23 0 3.897-.266 4.356-2.62 4.385-8.816-.029-6.185-.484-8.549-4.385-8.816zm-10.615 12.816v-8l8 3.993-8 4.007z"/>
							</svg>
						</a>
						<a href="https://x.com/faanross" target="_blank" rel="noopener noreferrer" class="instructor-link">
							<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
								<path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
							</svg>
						</a>
						<a href="https://www.linkedin.com/in/faan-rossouw" target="_blank" rel="noopener noreferrer" class="instructor-link">
							<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
								<path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
							</svg>
						</a>
					</div>
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

	.problem-label {
		display: block;
		font-size: clamp(18px, 2.5vw, 24px);
		font-weight: 600;
		color: var(--aion-purple);
		line-height: 1.2;
		margin-bottom: 8px;
	}

	.problem-item p {
		font-size: clamp(20px, 3vw, 28px);
		font-weight: 700;
		color: var(--aion-yellow);
		margin: 0;
		text-shadow: 0 0 20px rgba(245, 230, 99, 0.3);
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

	.waitlist-card strong {
		color: var(--aion-yellow);
	}

	.note {
		margin-top: 24px;
		font-size: 14px;
		color: rgba(255, 255, 255, 0.5);
	}

	/* Custom Form Styles */
	.waitlist-form {
		display: flex;
		flex-direction: column;
		gap: 16px;
		margin: 24px 0;
	}

	.form-fields {
		display: flex;
		gap: 12px;
		flex-wrap: wrap;
		justify-content: center;
	}

	.waitlist-form input[type="email"],
	.waitlist-form input[type="text"] {
		background: rgba(255, 255, 255, 0.05);
		border: 1px solid rgba(255, 255, 255, 0.15);
		padding: 14px 18px;
		font-family: 'JetBrains Mono', monospace;
		font-size: 14px;
		color: var(--white);
		min-width: 200px;
		flex: 1;
		transition: all 0.3s ease;
	}

	.waitlist-form input[type="email"]:focus,
	.waitlist-form input[type="text"]:focus {
		outline: none;
		border-color: var(--aion-purple);
		background: rgba(255, 255, 255, 0.08);
	}

	.waitlist-form input::placeholder {
		color: rgba(255, 255, 255, 0.4);
	}

	.btn-submit {
		background: var(--aion-yellow);
		color: var(--black);
		padding: 14px 32px;
		font-family: 'JetBrains Mono', monospace;
		font-weight: 600;
		font-size: 14px;
		border: none;
		cursor: pointer;
		transition: all 0.3s ease;
		display: inline-flex;
		align-items: center;
		justify-content: center;
		gap: 8px;
	}

	.btn-submit:hover:not(:disabled) {
		transform: translateY(-2px);
		box-shadow: 0 8px 30px rgba(255, 214, 0, 0.3);
	}

	.btn-submit:disabled {
		opacity: 0.7;
		cursor: not-allowed;
	}

	.loading-spinner {
		width: 16px;
		height: 16px;
		border: 2px solid rgba(0, 0, 0, 0.2);
		border-top-color: var(--black);
		border-radius: 50%;
		animation: spin 0.8s linear infinite;
	}

	@keyframes spin {
		to {
			transform: rotate(360deg);
		}
	}

	.form-success {
		padding: 24px;
		text-align: center;
	}

	.success-title {
		font-size: 20px;
		font-weight: 600;
		color: var(--aion-yellow);
		margin-bottom: 12px;
	}

	.success-message {
		font-size: 14px;
		color: rgba(255, 255, 255, 0.8);
		margin-bottom: 16px;
	}

	.success-link {
		font-size: 14px;
		color: rgba(255, 255, 255, 0.6);
	}

	.success-link a {
		color: var(--aion-purple);
		text-decoration: none;
	}

	.success-link a:hover {
		text-decoration: underline;
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

	/* Instructor */
	.instructor {
		padding: 80px 0;
	}

	.instructor h2 {
		text-align: center;
		margin-bottom: 48px;
	}

	.instructor-content {
		display: flex;
		align-items: center;
		gap: 48px;
		max-width: 900px;
		margin: 0 auto;
	}

	.instructor-image {
		flex-shrink: 0;
	}

	.instructor-image img {
		width: 200px;
		height: 200px;
		border-radius: 50%;
		object-fit: cover;
		border: 3px solid rgba(189, 147, 249, 0.4);
	}

	.instructor-bio {
		padding: 32px;
		flex: 1;
	}

	.instructor-bio h3 {
		color: var(--white);
		font-size: 24px;
		margin-bottom: 8px;
	}

	.instructor-tagline {
		font-size: 13px;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		color: var(--aion-yellow);
		margin-bottom: 20px !important;
	}

	.instructor-bio p {
		font-size: 15px;
		color: rgba(255, 255, 255, 0.8);
		line-height: 1.7;
		margin-bottom: 16px;
	}

	.instructor-bio a {
		color: var(--aion-purple);
		text-decoration: none;
		transition: color 0.3s ease;
	}

	.instructor-bio a:hover {
		color: var(--aion-purple-light);
	}

	.instructor-links {
		display: flex;
		gap: 16px;
		margin-top: 24px;
	}

	.instructor-link {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 40px;
		height: 40px;
		border-radius: 8px;
		background: rgba(189, 147, 249, 0.1);
		color: var(--aion-purple);
		transition: all 0.3s ease;
	}

	.instructor-link:hover {
		background: rgba(189, 147, 249, 0.2);
		color: var(--aion-purple-light);
		transform: translateY(-2px);
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

		.form-fields {
			flex-direction: column;
		}

		.waitlist-form input[type="email"],
		.waitlist-form input[type="text"] {
			min-width: 100%;
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

		.instructor-content {
			flex-direction: column;
			text-align: center;
		}

		.instructor-image img {
			width: 160px;
			height: 160px;
		}

		.instructor-bio {
			padding: 24px;
		}

		.instructor-links {
			justify-content: center;
		}
	}
</style>
