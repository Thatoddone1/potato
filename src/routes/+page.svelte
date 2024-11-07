<script>
    import Potato from './Potato.svelte';
    import ExplodedPotato from './ExplodedPotato.svelte';
    import { fly } from 'svelte/transition';
    
    let amountOfPotatoes = 110;
    let exploded = Array(amountOfPotatoes).fill(false);
    
    function handleExplode(number) {
        exploded[number] = true;
    }
    
    function handleUnExplode(number) {
        exploded[number] = false;
    }

    function explodeTransition(node, {
        duration = 500
    }) {
        return {
            duration,
            css: t => `
                transform: scale(${1 + (1-t)}) rotate(${(1-t) * 360}deg);
                opacity: ${t};
            `
        };
    }
</script>

<div class="grid grid-cols-3">
    {#each exploded as state, i}
        {#if exploded[i]}
            <div transition:explodeTransition>
                <button on:click={() => handleUnExplode(i)}>
                    <ExplodedPotato />
                </button>
            </div>
        {:else}
            <div>
                <button on:click={() => handleExplode(i)}>
                    <Potato />
                </button>
            </div>
        {/if}
    {/each}
</div>

<style>
    button {
        transition: transform 0.2s;
    }
    button:hover {
        transform: scale(1.1);
    }
</style>