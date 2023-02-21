<script>
	let client_id = import.meta.env.VITE_SPOTIFY_CLIENT_ID;
	let redirect_url = import.meta.env.VITE_SPOTIFY_REDIRECT_URI;
	import { generateRandomString } from '../../helper/helper';

	const loginButtonHandler = () => {
		const scope =
			'user-read-private user-read-email user-read-playback-state user-modify-playback-state streaming';
		const state = generateRandomString(16);
		var auth_query_parameters = new URLSearchParams({
			response_type: 'code',
			client_id: client_id,
			scope: scope,
			redirect_uri: redirect_url,
			state: state
		});
		window.location.assign(
			'https://accounts.spotify.com/authorize/?' + auth_query_parameters.toString()
		);
	};
</script>

<div class="spotify-login-container">
	<h2>Login to Spotify</h2>
	<button on:click={loginButtonHandler}>LOGIN</button>
</div>

<style>
	.spotify-login-container {
		border: 4px solid #1db954;
		border-radius: 16px;
		padding: 16px 24px;
		display: flex;
		gap: 16px;
		flex-direction: column;
		align-items: center;
	}
	button {
		padding: 12px 24px;
		border-radius: 24px;
		border: none;
		font-weight: bold;
		color: white;
		background-color: #1db954;
	}
	button:hover {
		cursor: pointer;
		opacity: 0.8;
	}
</style>
