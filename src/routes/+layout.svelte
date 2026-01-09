<script lang="ts">
	import '$lib/styles/global.css';
	import Nav from '$lib/components/Nav.svelte';
	import Background from '$lib/components/Background.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<title>AionSec | Never Stop Hunting</title>
	<meta name="description" content="Human-Centric, Agent-Driven Threat Hunting. Building sovereign, continuous threat hunting capability." />
	<link rel="icon" href="/images/aionsec.png" />
</svelte:head>

<Background />
<Nav />

<main>
	{@render children()}
</main>

<footer>
	<div class="container">
		<p>&copy; 2026 AionSec</p>
		<div class="footer-links">
			<a href="/contact" class="footer-link">Contact</a>
			<a href="/privacy" class="footer-link">Privacy</a>
			<a href="https://www.linkedin.com/company/aionsec" target="_blank" rel="noopener noreferrer" class="footer-link">
				LinkedIn
			</a>
		</div>
	</div>
</footer>

<style>
	main {
		position: relative;
		z-index: 10;
		min-height: calc(100vh - 140px);
		padding-top: 48px;
	}

	footer {
		position: relative;
		z-index: 10;
		padding: 20px 0;
		text-align: center;
		border-top: 1px solid rgba(189, 147, 249, 0.1);
	}

	footer .container {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 24px;
	}

	.footer-links {
		display: flex;
		gap: 16px;
	}

	footer p {
		font-size: 12px;
		color: rgba(255, 255, 255, 0.5);
	}

	:global(.footer-link) {
		font-size: 11px;
		color: var(--aion-yellow);
		text-transform: uppercase;
		letter-spacing: 0.05em;
	}

	:global(.footer-link:hover) {
		color: var(--aion-yellow-light);
	}
</style>
