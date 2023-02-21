<script>
	import { page } from '$app/stores';
	import { browser } from '$app/environment';
	import axios from 'axios';
	import Cookies from 'js-cookie';

	let code = $page.url.searchParams.get('code');
	if (browser) {
		axios
			.get('http://localhost:8080/callback?code=' + code)
			.then((res) => {
				Cookies.set('spotify_access', res.data.data.access_token);
				Cookies.set('spotify_refresh', res.data.data.refresh_token);
				window.location.assign('/');
			})
			.catch((err) => {
				console.error(err);
			});
	}
</script>

<h1>Loading...</h1>
