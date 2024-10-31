<script>
    import Potato from './Potato.svelte';
    import ExplodedPotato from './ExplodedPotato.svelte';
    
    let amountOfPotatoes = 15;

    let exploded = Array(amountOfPotatoes).fill(false)
    
    console.log(exploded)
    
    function handleExplode(number) {
        exploded[number]=true;
        console.log("Exploded!");
    }
    function handleUnExplode(number) {
        exploded[number]=false;
        console.log("unExploded!");
    }
</script>

<div class="grid grid-cols-3">
{#each exploded as state, i}
{#if exploded[i]}
    <a onclick={handleUnExplode(i)}><ExplodedPotato></ExplodedPotato></a>
{:else}
    <a onclick={handleExplode(i)}><Potato></Potato></a>
{/if}
{/each}
</div>