<script>
  // export let name;
  import Cat from './Cat.svelte';
  import Fish from './Fish.svelte';
  import Block from './Block.svelte';
  let cat = './../public/cat.svg';
  let blocks = [null, null, null, null, null, null, null, null, null];

  let xIsNext = true;
  $: status = 'Next Player: ' + (xIsNext ? 'cat' : 'fish');

  let winner = null;

  function handleClick(i) {
    if (!blocks[i]) {
      blocks[i] = xIsNext ? 'cat' : 'fish';
      xIsNext = !xIsNext;
    }
    winner = calculateWinner(blocks);
  }

  function calculateWinner(blocks) {
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
      if (blocks[a] && blocks[a] === blocks[b] && blocks[a] === blocks[c])
        return `Winner: ${blocks[a]}`;
    }

    const isDraw = blocks.every((block) => block !== null);
    return isDraw ? "It's a draw" : null;
  }

  function restartGame() {
    blocks = [null, null, null, null, null, null, null, null, null];
    xIsNext = true;
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
  <Cat />
  <Fish />
</div>

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
