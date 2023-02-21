<script>
	import Navbar from "../lib/Navbar/Navbar.svelte";
</script>

<div class="layout">
	<Navbar />
	<div class="page-content">
		<slot></slot>
	</div>
</div>


<style>
	.layout {
		display: flex;
	}
	.page-content {
		margin-left: 60px;
	}
</style>
