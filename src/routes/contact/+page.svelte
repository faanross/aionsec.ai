<script lang="ts">
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';

	let mounted = $state(false);
	let formSubmitted = $state(false);
	let formLoading = $state(false);

	onMount(() => {
		mounted = true;
	});

	async function handleSubmit(event: Event) {
		event.preventDefault();
		const form = event.target as HTMLFormElement;
		formLoading = true;

		// Simple mailto fallback - opens email client
		const formData = new FormData(form);
		const name = formData.get('name') as string;
		const email = formData.get('email') as string;
		const message = formData.get('message') as string;

		const subject = encodeURIComponent(`Contact from ${name}`);
		const body = encodeURIComponent(`From: ${name} (${email})\n\n${message}`);

		window.location.href = `mailto:info@aionsec.ai?subject=${subject}&body=${body}`;

		formLoading = false;
		formSubmitted = true;
	}
</script>

<svelte:head>
	<title>Contact | AionSec</title>
	<meta name="description" content="Get in touch with AionSec. Questions about the course, platform, or consulting? We'd love to hear from you." />
</svelte:head>

<section class="contact">
	<div class="container">
		{#if mounted}
			<header class="contact-header" in:fly={{ y: 30, duration: 800, delay: 200 }}>
				<h1>Contact</h1>
				<p class="lead">Questions? Ideas? Just want to connect? Reach out.</p>
			</header>

			<div class="contact-content" in:fly={{ y: 30, duration: 600, delay: 400 }}>
				<div class="glass-card contact-card">
					<div class="contact-info">
						<p><strong>Email:</strong> <a href="mailto:info@aionsec.ai">info@aionsec.ai</a></p>
						<p><strong>LinkedIn:</strong> <a href="https://www.linkedin.com/company/aionsec" target="_blank" rel="noopener noreferrer">AionSec</a></p>
					</div>

					<div class="divider"></div>

					{#if !formSubmitted}
						<form class="contact-form" onsubmit={handleSubmit}>
							<div class="form-group">
								<label for="name">Name</label>
								<input type="text" id="name" name="name" required />
							</div>
							<div class="form-group">
								<label for="email">Email</label>
								<input type="email" id="email" name="email" required />
							</div>
							<div class="form-group">
								<label for="message">Message</label>
								<textarea id="message" name="message" rows="5" required></textarea>
							</div>
							<button type="submit" class="btn-submit" disabled={formLoading}>
								{formLoading ? 'Opening...' : 'Send Message'}
							</button>
						</form>
					{:else}
						<div class="form-success">
							<p class="success-title">Email client opened</p>
							<p class="success-message">Complete sending in your email app, or email us directly at <a href="mailto:info@aionsec.ai">info@aionsec.ai</a></p>
						</div>
					{/if}
				</div>
			</div>
		{/if}
	</div>
</section>

<style>
	.contact {
		padding: 80px 0 120px;
	}

	.container {
		max-width: 600px;
	}

	.contact-header {
		text-align: center;
		margin-bottom: 48px;
	}

	.contact-header h1 {
		margin-bottom: 16px;
	}

	.lead {
		font-size: 18px;
		color: rgba(255, 255, 255, 0.7);
	}

	.contact-card {
		padding: 48px;
	}

	.contact-info {
		text-align: center;
		margin-bottom: 32px;
	}

	.contact-info p {
		margin: 12px 0;
		font-size: 16px;
	}

	.contact-info strong {
		color: rgba(255, 255, 255, 0.6);
	}

	.contact-info a {
		color: var(--aion-purple);
	}

	.divider {
		height: 1px;
		background: linear-gradient(90deg, transparent, rgba(189, 147, 249, 0.3), transparent);
		margin: 32px 0;
	}

	.contact-form {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.form-group {
		display: flex;
		flex-direction: column;
		gap: 8px;
	}

	.form-group label {
		font-size: 14px;
		color: rgba(255, 255, 255, 0.6);
	}

	.form-group input,
	.form-group textarea {
		background: rgba(255, 255, 255, 0.05);
		border: 1px solid rgba(255, 255, 255, 0.15);
		padding: 14px 18px;
		font-family: 'JetBrains Mono', monospace;
		font-size: 14px;
		color: var(--white);
		transition: all 0.3s ease;
	}

	.form-group input:focus,
	.form-group textarea:focus {
		outline: none;
		border-color: var(--aion-purple);
		background: rgba(255, 255, 255, 0.08);
	}

	.form-group textarea {
		resize: vertical;
		min-height: 120px;
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
		align-self: flex-start;
	}

	.btn-submit:hover:not(:disabled) {
		transform: translateY(-2px);
		box-shadow: 0 8px 30px rgba(255, 214, 0, 0.3);
	}

	.btn-submit:disabled {
		opacity: 0.7;
		cursor: not-allowed;
	}

	.form-success {
		text-align: center;
		padding: 24px;
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
	}

	.success-message a {
		color: var(--aion-purple);
	}

	@media (max-width: 768px) {
		.contact {
			padding: 60px 0 80px;
		}

		.contact-card {
			padding: 32px 24px;
		}
	}
</style>
