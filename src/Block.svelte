<script>
  export let value;
  export let handleClick;
</script>

<button class="block" on:click={handleClick}>
  <img src={value || ''} alt="" />
</button>

<style>
  .block {
    background-color: #f0ac2e;
    transition: transform 200ms;
    flex: 0 0 33%;
    width: 150px;
    height: 150px;
    border: 2px solid black;
    margin: 5px;
    padding: 5px;
    font-size: 20px;
    text-align: center;
  }

  .block:hover {
    border: 2px solid red;
  }

  img {
    height: auto;
    max-width: 100%;
  }
  /* @media (min-width: 640px) {
		div {
			max-width: none;
		}
	} */
</style>
