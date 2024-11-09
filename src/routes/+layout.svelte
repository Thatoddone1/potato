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
	let showNavBar = $state(false);
	function mouseHover() {
		showNavBar = true;
	}
	function mouseUnHover() {
		showNavBar = false;
	}
</script>

<div
	class="fixed right-0 z-50 m-2 rounded-xl bg-gradient-to-r from-indigo-600 to-cyan-600"
	class:p-3={showNavBar}
	class:p-1={!showNavBar}
	onmouseover={mouseHover}
	onmouseout={mouseUnHover}
>
	{#if showNavBar}
		<a href={homeURL} class="m-2 rounded-xl bg-cyan-400 p-2">Home</a>
		<a href={aboutURL} class="m-2 rounded-xl bg-cyan-400 p-2">About</a>
	{:else}
		<img src="/potatoes/potato.png" class="size-6" />
	{/if}
</div>
{@render children()}
