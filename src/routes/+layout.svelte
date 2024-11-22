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
<div class="group fixed right-0 m-2 flex flex-auto flex-row rounded-xl bg-gray-500 z-50 transition-all duration-300 transform w-10 h-10 hover:w-auto hover:h-auto">
	<a href={homeURL} class="flex p-2 m-2 rounded-full text-md bg-cyan-600 transition-all duration-300 transform scale-0 group-hover:scale-100">Home</a>
	<a href={aboutURL} class="flex p-2 m-2 rounded-full text-md bg-cyan-600 transition-all duration-300 transform scale-0 group-hover:scale-100">About</a>
	<a href={potatoTacToeURL} class="flex p-2 m-2 rounded-full text-md bg-cyan-600 transition-all duration-300 transform scale-0 group-hover:scale-100">Potato-Tac-Toe</a>
</div>
{@render children()}
