<script>
	import Navbar from "../lib/Navbar/Navbar.svelte";
</script>

<div class="layout">
	<Navbar />
	<slot></slot>
</div>


<style>
	.layout {
		display: flex;
	}
	
</style>
