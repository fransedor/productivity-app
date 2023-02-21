<script>
	import SpotifyLogin from '$lib/SpotifyLogin/SpotifyLogin.svelte';
	import SpotifyPlayer from '$lib/SpotifyPlayer/SpotifyPlayer.svelte';
	import Cookies from 'js-cookie';
</script>

<div class="">
	{#if Cookies.get('spotify_access')}
		<SpotifyPlayer />
	{:else}
		<SpotifyLogin />
	{/if}
</div>

<style>
</style>
