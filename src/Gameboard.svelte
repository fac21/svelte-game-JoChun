<script>
  // export let name;
  import Cat from './Cat.svelte';
  import Fish from './Fish.svelte';
  import Block from './Block.svelte';
  let cat = {
    name: 'cat',
    image: 'cat.svg',
  };
  let fish = {
    name: 'fish',
    image: 'fish.svg',
  };
  let blocks = [null, null, null, null, null, null, null, null, null];

  let catIsNext = true;
  $: status = 'Next Player: ' + (catIsNext ? 'cat' : 'fish');

  let winner = null;

  function handleClick(i) {
    if (!blocks[i]) {
      blocks[i] = catIsNext ? cat.image : fish.image;
      catIsNext = !catIsNext;
    }
    winner = calculateWinner(blocks);
  }

  function calculateWinner(blocksArray) {
    const winningCombo = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8],
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8],
      [0, 4, 8],
      [2, 4, 6],
    ];
    for (let i = 0; i < winningCombo.length; i++) {
      const [a, b, c] = winningCombo[i];
      if (
        blocksArray[a] &&
        blocksArray[a] === blocksArray[b] &&
        blocksArray[a] === blocksArray[c]
      )
        return `Winner: ${blocksArray[a].slice(0, -4)}`;
    }

    const isDraw = blocks.every((block) => block !== null);
    return isDraw ? "It's a draw" : null;
  }

  function restartGame() {
    blocks = [null, null, null, null, null, null, null, null, null];
    catIsNext = true;
    winner = null;
  }
</script>

{#if winner}
  <h3>{winner}</h3>
  <button on:click={restartGame}>Restart Game</button>
{:else}
  <h3>{status}</h3>
{/if}

<div class="gameboard">
  {#each blocks as block, i}
    <Block value={block} handleClick={() => handleClick(i)} />
  {/each}
</div>

<style>
  .gameboard {
    border: solid 1px transparent;
    height: 70vh;
    width: 70vw;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(10rem, 1fr));
    grid-template-rows: repeat(auto-fit, minmax(10rem, 1fr));
    margin: auto;
    text-align: center;
  }

  @media (min-width: 640px) {
    /* div {
			max-width: none;
		} */
  }
</style>
