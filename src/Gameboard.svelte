<script>
	// export let name;
    import Cat from './Cat.svelte';
    import Block from './Block.svelte';
    export let blocks = [        
        {height: 10, width: 50},
        {height: 50, width: 200},
        {height: 80, width: 100},
]   
</script>

<div class="gameboard">
	Action happens here
    <Cat/>
    {#each blocks as block}
        <Block height={block.height} width={block.width}></Block>
    {/each}
</div>

<style>
	.gameboard {
		border: solid 1px black;
		height: 80vh;
		width: 80vw;
	}

    div {
        border: solid 1px black;
    }

	@media (min-width: 640px) {
		/* div {
			max-width: none;
		} */
	}
</style>