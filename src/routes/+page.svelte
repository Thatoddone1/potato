<script>
	import Potato from './Potato.svelte';
	import ExplodedPotato from './ExplodedPotato.svelte';
	import Explosion from './Explosion.svelte';
	import { fly } from 'svelte/transition';

	let amountOfPotatoes = 110;
	let exploded = Array(amountOfPotatoes).fill(false);
	let explosion = Array(amountOfPotatoes).fill(false);
	let growing = Array(amountOfPotatoes).fill(false);

	function handleExplode(number) {
		// First, trigger growth
		growing[number] = true;

		// After growth, trigger explosion
		setTimeout(() => {
			growing[number] = false;
			explosion[number] = true;

			// Then show exploded state
			setTimeout(() => {
				exploded[number] = true;
				explosion[number] = false;
			}, 100);
		}, 500); // Growth duration
	}

	function handleUnExplode(number) {
		exploded[number] = false;
	}

	function explodeTransition(node, { duration = 500 }) {
		return {
			duration,
			css: (t) => `
                transform: scale(${1 + (1 - t)}) rotate(${(1 - t) * 360}deg);
                opacity: ${t};
            `
		};
	}
</script>

<div class="grid grid-cols-3 sm:grid-cols-5">
	{#each exploded as state, i}
		<div class="relative">
			{#if explosion[i]}
				<div class="absolute inset-0 z-10">
					<div transition:fly={{ y: 100, duration: 250 }}>
						<Explosion />
					</div>
				</div>
			{/if}
			{#if exploded[i]}
				<div transition:explodeTransition>
					<button on:click={() => handleUnExplode(i)}>
						<ExplodedPotato />
					</button>
				</div>
			{:else}
				<div class:growing={growing[i]}>
					<button on:click={() => handleExplode(i)}>
						<Potato />
					</button>
				</div>
			{/if}
		</div>
	{/each}
</div>

<style>
	button {
		transition: transform 0.2s;
	}
	button:hover {
		transform: scale(1.1);
	}

	.growing {
		animation: grow 0.5s ease-in;
	}

	@keyframes grow {
		0% {
			transform: scale(1);
		}
		100% {
			transform: scale(1.5);
		}
	}

	.relative {
		position: relative;
	}

	.absolute {
		position: absolute;
	}
</style>
