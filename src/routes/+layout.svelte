<script>
	import '../app.css';
	import { page } from "$app/stores";
	let { children } = $props();
	function url_for(path) {
    const baseUrl = $page.url.origin;
    const url = new URL(path, baseUrl);
    return url.href;
  }
  let homeURL = url_for("/");
  let aboutURL = url_for("/about");
</script>
<div class="fixed right-0 rounded-xl bg-gradient-to-r from-indigo-600 to-cyan-600 p-3 m-2 z-50">
<a href={homeURL} class="rounded-xl bg-cyan-400 p-2 m-2">Home</a>
<a href={aboutURL} class="rounded-xl bg-cyan-400 p-2 m-2">About</a>
</div>
{@render children()}
