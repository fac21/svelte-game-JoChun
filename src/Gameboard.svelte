<script>
	// export let name;
    import Cat from './Cat.svelte';
    import Fish from './Fish.svelte';
    import Block from './Block.svelte';
    let cat = './../public/cat.svg';
    let blocks = [null, null, null, null, null, null, null, null, null];

    let xIsNext = true;
    $: status = "Next Player: " + (xIsNext ? 'cat' : "fish");

    function handleClick(i) {
    if (!blocks[i]) {
      blocks[i] = xIsNext ? "cat" : "fish";
      xIsNext = !xIsNext;
    }
  }

</script>

<div class="gameboard">
    {#each blocks as block, i}
    <Block value={block} handleClick={() => handleClick(i)}/>
    {/each}
    <Cat/>
    <Fish/>
</div>

<h3>{status}</h3>

<style>
	.gameboard {
		border: solid 1px black;
		height: 80vh;
		width: 80vw;
        display: flex;
    flex-wrap: wrap;
    /* width: 300px; */
	}

	@media (min-width: 640px) {
		/* div {
			max-width: none;
		} */
	}
</style>