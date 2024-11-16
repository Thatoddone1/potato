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

<div
	class="z-50 duration-800 group fixed right-1 top-1 m-3 w-16 rounded-3xl bg-blue-400 p-3 transition-all ease-in-out hover:w-80"
>
	<div class="flex gap-3">
		<!-- svelte-ignore a11y_img_redundant_alt -->
		<img src="/potatoes/potato.png" alt="a potato" class="rounded-full h-10 w-10" />
		<a
			class="text-md invisible flex items-center justify-center rounded-md bg-slate-100 p-1 font-semibold group-hover:visible"
			href={homeURL}
		>
			Home
		</a>
		<a
			class="text-md invisible flex items-center justify-center rounded-md bg-slate-100 p-1 font-semibold group-hover:visible"
			href={aboutURL}
		>
			About
		</a>
		<a
			class="text-md invisible flex items-center justify-center rounded-md bg-slate-100 p-1 font-semibold group-hover:visible"
			href={potatoTacToeURL}
		>
			Potato-Tac-Toe
		</a>
	</div>
</div>
{@render children()}
