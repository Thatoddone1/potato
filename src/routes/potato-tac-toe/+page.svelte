<script>
	let potatos = Array(9).fill(0);
	let currentPlayer = 1;

	function checkWin() {
		if (potatos[0] == potatos[1] && potatos[1] == potatos[2] && potatos[0] != 0) return true;
		if (potatos[3] == potatos[4] && potatos[4] == potatos[5] && potatos[3] != 0) return true;
		if (potatos[6] == potatos[7] && potatos[7] == potatos[8] && potatos[6] != 0) return true;
		if (potatos[0] == potatos[3] && potatos[3] == potatos[6] && potatos[0] != 0) return true;
		if (potatos[1] == potatos[4] && potatos[4] == potatos[7] && potatos[1] != 0) return true;
		if (potatos[2] == potatos[5] && potatos[5] == potatos[8] && potatos[2] != 0) return true;
		if (potatos[0] == potatos[4] && potatos[4] == potatos[8] && potatos[0] != 0) return true;
		if (potatos[2] == potatos[4] && potatos[4] == potatos[6] && potatos[2] != 0) return true;
		return false;
	}

	function potatoClicked(potatoNumber) {
		if (currentPlayer == 1) {
			potatos[potatoNumber] = 1;
			currentPlayer = 2;
		} else {
			potatos[potatoNumber] = 2;
			currentPlayer = 1;
		}
		if (checkWin()) {
			if (currentPlayer === 1) {
				alert('Angry Potato wins!');
			} else {
				alert('Happy Potato wins!');
			}
		}
	}
</script>

<button class="fixed left-0 m-2 rounded-xl bg-cyan-300 p-2" onclick={() => location.reload()}>
	Play again
</button>
<div class="p-3 pb-6">
	<h1 class="text-center font-mono text-3xl">Potato-tac-toe</h1>
	<p class="text-center font-mono text-sm text-gray-400">tic-tac-toe, but potato</p>
</div>
<div class="grid grid-cols-3">
	{#each potatos as potato, i}
		{#if potato == 0}
			<img src="/potatoes/potato.png" onclick={potatoClicked(i)} />
		{/if}
		{#if potato == 1}
			<img src="/potatoes/happy_potato.png" />
		{/if}
		{#if potato == 2}
			<img src="/potatoes/angry_potato.png" />
		{/if}
	{/each}
</div>
