<div class="layout">
	<nav>
		<a href="/about">About</a>
		<a href="/tasks">Tasks</a>
		<a href="/timeline">Timeline</a>
	</nav>
	<slot></slot>
</div>


<style>
	.layout {
		display: flex;
	}
	nav {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}
	a {
		text-decoration: none;
	}
</style>
