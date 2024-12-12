<script>
	import '../app.css';
	import { page } from '$app/stores';
	let { children } = $props();
	function url_for(path) {
		const baseUrl = $page.url.origin;
		const url = new URL(path, baseUrl);
		return url.href;
	}
	let homeURL = url_for('/');
	let aboutURL = url_for('/about');
	let potatoTacToeURL = url_for('/potato-tac-toe');
	let factsURL = url_for('/facts');
	let wikipotatoURL = url_for('/wikipotato');
	let showNavBar = $state(false);
	function mouseHover() {
		showNavBar = true;
	}
	function mouseUnHover() {
		showNavBar = false;
	}
</script>

<svelte:head>
	<title>potato</title>
	<meta name="description" content="potato themed activites, learn about potatoes!" />
	<meta name="keywords" content="potato, educational" />
	<meta name="author" content="thatoddone1" />
</svelte:head>
<div class="flex mb-2 bg-gray-300 z-50 w-full justify-between items-center">
	<a href={homeURL} class="p-2 m-2 text-lg rounded-lg bg-blue-400">Home</a>
	<div>
		<a href={potatoTacToeURL} class="p-2 m-2 rounded-lg text-md bg-cyan-400">Potato-Tac-Toe</a>
		<a href={factsURL} class="p-2 m-2 rounded-lg text-md bg-cyan-400">Facts</a>
		<a href={wikipotatoURL} class="p-2 m-2 rounded-lg text-md bg-cyan-400">WikiPotato</a>
	</div>
	<a href={aboutURL} class="p-2 m-2 text-lg rounded-lg bg-violet-400">About</a>
</div>
{@render children()}
