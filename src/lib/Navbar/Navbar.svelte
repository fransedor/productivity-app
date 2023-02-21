<script lang="ts">
	import { page } from '$app/stores';
	import Home from 'svelte-material-icons/Home.svelte';
	import Information from 'svelte-material-icons/Information.svelte';

	let currentUrl = ""
	let menus = [
		{
			id: 'home',
			href: '/',
			label: 'Home',
			icon: Home,
		},
		{
			id: 'about',
			href: '/about',
			label: 'About',
			icon: Information,
		}
	];
	$: currentUrl = $page.url.pathname
</script>

<div class="navbar">
	<nav>
		<ul>
			{#each menus as menu}
				<li class:active={menu.href === currentUrl}>
					<a href={menu.href} >
						<svelte:component
							this={menu.icon}
							size="24px"
							color={menu.href === currentUrl ? 'white' : '#1db954'}
							class="menu-icon active"
						/>
					</a>
					<p class="menu-label">{menu.label}</p>
				</li>
			{/each}
		</ul>
	</nav>
</div>

<style>
	.active {
		background-color: #1db954;
	}
	li {
		position: relative;
		border-radius: 8px;
		background-color: white;
		padding: 8px;
	}
	li:hover {
		box-shadow: 1px 2px 5px #fff;
	}
	.menu-label {
		opacity: 0;
		position: absolute;
		color: #1db954;
		font-weight: bold;
		top: 50%;
		transform: translateY(-50%);
		padding: 8px 12px;
		border-radius: 4px;
		right: -72px;
		box-shadow: 2px 2px 3px #ccc;
		font-size: 12px;
		background-color: white;
	}
	.menu-label::after {
		content: '';
		position: absolute;
		top: 50%; /* At the bottom of the tooltip */
		left: 0;
		transform: translateY(-50%);
		margin-left: -13px;
		border-width: 8px;
		border-style: solid;
		border-color: transparent white transparent transparent;
	}
	a {
		display: flex;
		align-items: center;
		width: 100%;
		height: 100%;
	}
	a:hover + .menu-label {
		opacity: 1;
		transition: 0.2s;
	}
	.navbar {
		width: 60px;
		height: 100vh;
		position: fixed;
		left: 0;
		top: 0;
		z-index: 20;
		background-color: black;
		box-shadow: 1px 2px 5px #444;
	}
	nav {
		width: 100%;
		height: 100%;
	}
	ul {
		list-style-type: none;
		padding: 0px;
		padding-top: 80px;
		margin: 0px;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 20px;
	}
</style>
