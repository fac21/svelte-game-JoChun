<script>
	// export let name;
    import Cat from './Cat.svelte';
    import HorizontalBlock from './HorizontalBlock.svelte';
    import VerticalBlock from './VerticalBlock.svelte';

    let moving = false;
    let clientWidth;

    // if click is false

    // const gameboardWidth;
    // const gameboardHeight;

    function handleClick() {
        console.log("clicked")
		moving = !moving;
	}
</script>

<div class="gameboard" bind:clientWidth>
    {console.log("clientwidth", clientWidth)}
    <Cat/>
    <div class="blob" on:click={() => console.log("clicked")}></div>
    <HorizontalBlock class="blob" on:click={() => console.log("clicked")}></HorizontalBlock>
    <!-- {#if moving == true} -->
        <HorizontalBlock on:click={() => console.log("clicked")}/>

    <HorizontalBlock/>
    <VerticalBlock/>
</div>

<style>
	.gameboard {
		border: solid 1px black;
		height: 80vh;
		width: 80vw;
	}

    .blob {
        background-color: red;
        height: 300px;
        width: 300px;
    }

	@media (min-width: 640px) {
		/* div {
			max-width: none;
		} */
	}
</style>