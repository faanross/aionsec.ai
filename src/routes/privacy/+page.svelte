<script lang="ts">
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';

	let mounted = $state(false);

	onMount(() => {
		mounted = true;
	});
</script>

<svelte:head>
	<title>Privacy Policy | AionSec</title>
	<meta name="description" content="AionSec privacy policy. How we collect, use, and protect your information." />
</svelte:head>

<section class="privacy">
	<div class="container">
		{#if mounted}
			<header class="privacy-header" in:fly={{ y: 30, duration: 800, delay: 200 }}>
				<h1>Privacy Policy</h1>
				<p class="meta">Last updated: January 2026</p>
			</header>

			<div class="privacy-content" in:fly={{ y: 30, duration: 600, delay: 400 }}>
				<h2>Overview</h2>
				<p>AionSec ("we", "our", or "us") respects your privacy. This policy explains how we collect, use, and protect your information when you use our website and services.</p>

				<h2>Information We Collect</h2>
				<h3>Information You Provide</h3>
				<ul>
					<li><strong>Waitlist signup:</strong> Email address and optionally your name when you join the course waitlist</li>
					<li><strong>Contact form:</strong> Name, email, and message content when you contact us</li>
					<li><strong>Course purchase:</strong> Payment and billing information when you purchase the course (processed by our payment provider)</li>
				</ul>

				<h3>Automatically Collected Information</h3>
				<ul>
					<li><strong>Analytics:</strong> We may collect basic analytics (page views, referral source) to understand how visitors use our site</li>
					<li><strong>Technical data:</strong> Browser type, device type, and IP address for security and troubleshooting</li>
				</ul>

				<h2>How We Use Your Information</h2>
				<ul>
					<li>To send you course launch announcements and updates (waitlist)</li>
					<li>To respond to your inquiries (contact form)</li>
					<li>To provide access to purchased courses and materials</li>
					<li>To improve our website and services</li>
					<li>To comply with legal obligations</li>
				</ul>

				<h2>What We Don't Do</h2>
				<ul>
					<li>We don't sell your personal information to third parties</li>
					<li>We don't send spam or share your email with marketers</li>
					<li>We don't use your data for advertising profiles</li>
				</ul>

				<h2>Email Communications</h2>
				<p>If you join our waitlist, you'll receive:</p>
				<ul>
					<li>One email when the course launches</li>
					<li>Occasional updates about AionSec (you can unsubscribe anytime)</li>
				</ul>
				<p>We use MailerLite to manage our email list. You can unsubscribe from any email with one click.</p>

				<h2>Data Storage and Security</h2>
				<p>We use industry-standard security measures to protect your data. Email addresses are stored with MailerLite. Payment information is processed by our payment provider and is never stored on our servers.</p>

				<h2>Third-Party Services</h2>
				<p>We use the following third-party services:</p>
				<ul>
					<li><strong>MailerLite:</strong> Email list management</li>
					<li><strong>GitHub Pages:</strong> Website hosting</li>
					<li><strong>Payment processor:</strong> Course payments (details provided at checkout)</li>
				</ul>
				<p>Each service has its own privacy policy governing their use of your data.</p>

				<h2>Your Rights</h2>
				<p>You have the right to:</p>
				<ul>
					<li>Access the personal data we hold about you</li>
					<li>Request correction of inaccurate data</li>
					<li>Request deletion of your data</li>
					<li>Unsubscribe from email communications</li>
				</ul>
				<p>To exercise these rights, contact us at <a href="mailto:info@aionsec.ai">info@aionsec.ai</a>.</p>

				<h2>Cookies</h2>
				<p>We use minimal cookies necessary for website functionality. We don't use tracking cookies for advertising.</p>

				<h2>Changes to This Policy</h2>
				<p>We may update this policy occasionally. Significant changes will be noted on this page with an updated date.</p>

				<h2>Contact</h2>
				<p>Questions about this privacy policy? Contact us at <a href="mailto:info@aionsec.ai">info@aionsec.ai</a>.</p>
			</div>
		{/if}
	</div>
</section>

<style>
	.privacy {
		padding: 80px 0 120px;
	}

	.container {
		max-width: 800px;
	}

	.privacy-header {
		margin-bottom: 48px;
	}

	.privacy-header h1 {
		margin-bottom: 16px;
	}

	.meta {
		font-size: 14px;
		color: rgba(255, 255, 255, 0.5);
	}

	.privacy-content {
		font-size: 16px;
		line-height: 1.8;
	}

	.privacy-content h2 {
		margin-top: 40px;
		margin-bottom: 16px;
		font-size: 24px;
	}

	.privacy-content h3 {
		margin-top: 24px;
		margin-bottom: 12px;
		font-size: 18px;
		color: var(--aion-yellow);
	}

	.privacy-content p {
		margin-bottom: 16px;
		color: rgba(255, 255, 255, 0.85);
	}

	.privacy-content ul {
		margin: 16px 0;
		padding-left: 0;
		list-style: none;
	}

	.privacy-content li {
		padding: 6px 0 6px 24px;
		position: relative;
		color: rgba(255, 255, 255, 0.85);
	}

	.privacy-content li::before {
		content: '>';
		position: absolute;
		left: 0;
		color: var(--aion-purple);
		font-weight: 600;
	}

	.privacy-content strong {
		color: var(--aion-yellow);
	}

	.privacy-content a {
		color: var(--aion-purple);
	}

	@media (max-width: 768px) {
		.privacy {
			padding: 60px 0 80px;
		}

		.privacy-content {
			font-size: 15px;
		}
	}
</style>
