<script>

	import { fly } from 'svelte/transition';
	function handleClick() {
        console.log("clicked")
		// moving = !moving;
	}
	
</script>

<div transition:fly={{ y: 200, duration: 2000}} class="block" on:click={handleClick}></div>

<style>
	.block {
        border: solid 1px black;
		height: 75px;
		width: 200px;
        background-color: red;
		/* position: absolute; */
		/* height: 32px;
		width: 32px; */
		background-color: #f0ac2e;
		transition: transform 200ms;
	}

	/* @media (min-width: 640px) {
		div {
			max-width: none;
		}
	} */
</style>