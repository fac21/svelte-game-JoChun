<script>

	export let value;
	export let handleClick;
</script>

<button class="block" on:click={handleClick}>{value || ""}</button>

<style>
	.block {
		/* position: absolute; */
		/* height: 32px;
		width: 32px; */
		background-color: #f0ac2e;
		transition: transform 200ms;
		flex: 1 0 25%;
    width: 50px;
    height: 70px;
    border: 2px solid black;
    margin: 5px;
    padding: 5px;
    font-size: 20px;
    text-align: center;
	}

	 .block:hover {
    border: 2px solid red;
  }

	/* @media (min-width: 640px) {
		div {
			max-width: none;
		}
	} */
</style>