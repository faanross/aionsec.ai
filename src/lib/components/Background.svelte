<script lang="ts">
	import { onMount } from 'svelte';

	// Check if animation already played this session
	const alreadyBlurred = typeof sessionStorage !== 'undefined' && sessionStorage.getItem('bgBlurred') === 'true';
	let blurred = $state(alreadyBlurred);
	let skipTransition = $state(alreadyBlurred);

	onMount(() => {
		if (alreadyBlurred) {
			// Already blurred, no animation needed
			return;
		}
		// First visit - play animation and store state
		setTimeout(() => {
			blurred = true;
			sessionStorage.setItem('bgBlurred', 'true');
		}, 800);
	});
</script>

<div class="animated-bg" class:blurred class:skip-transition={skipTransition}></div>
<div class="gradient-orb orb-1"></div>
<div class="gradient-orb orb-2"></div>
<div class="gradient-orb orb-3"></div>
<div class="gradient-orb orb-4"></div>

<style>
	.animated-bg {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: 1;
		background-image: url('/images/bg_aionsec.png');
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		opacity: 0.5;
		filter: blur(0px);
		pointer-events: none;
		transition: filter 1.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
	}

	.animated-bg.blurred {
		filter: blur(4px);
	}

	.animated-bg.skip-transition {
		transition: none;
	}

	.gradient-orb {
		position: fixed;
		border-radius: 50%;
		filter: blur(80px);
		opacity: 0.25;
		z-index: 2;
		animation: float 12s ease-in-out infinite;
		pointer-events: none;
	}

	.orb-1 {
		width: 300px;
		height: 300px;
		background: linear-gradient(135deg, #F5E663 0%, #D4C44A 100%);
		top: 10%;
		left: 10%;
		animation-delay: -2s;
	}

	.orb-2 {
		width: 400px;
		height: 400px;
		background: linear-gradient(135deg, #5A5A66 0%, #3D3D47 100%);
		top: 55%;
		right: 15%;
		animation-delay: -4s;
	}

	.orb-3 {
		width: 250px;
		height: 250px;
		background: linear-gradient(135deg, #F5E663 0%, #D4C44A 100%);
		bottom: 15%;
		left: 25%;
		animation-delay: -1s;
		opacity: 0.2;
	}

	.orb-4 {
		width: 200px;
		height: 200px;
		background: linear-gradient(135deg, #5A5A66 0%, #3D3D47 100%);
		top: 30%;
		right: 35%;
		animation-delay: -3s;
		opacity: 0.15;
	}

	@keyframes float {
		0%, 100% { transform: translate(0px, 0px) scale(1); }
		33% { transform: translate(30px, -30px) scale(1.1); }
		66% { transform: translate(-20px, 20px) scale(0.9); }
	}
</style>
