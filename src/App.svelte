<script>
	const title = "Chun and Jo's Tic Tac Toe";
	import Gameboard from './Gameboard.svelte';
</script>


<svelte:head>
	<title>{title}</title>
</svelte:head>

<h1>{title}</h1>
<Gameboard/>

<style>

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
		text-align: center;
	}

	@media (min-width: 640px) {

	}
</style>