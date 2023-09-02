<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let team;
  export let score;
  export let gameOver;

  function addPoint() {
    score++;
  }
  function subtractPoint() {
    score--;

    if (score === 0) {
      dispatch('lostEvent', { team });
    }
  }
</script>

<div style="border: dashed {team.toLowerCase()} 3px" class="col">
  <h2 class:text-danger={team === 'Red'} class:text-primary={team === 'Blue'}>
    Team {team}: {score}
  </h2>

  <button disabled={gameOver} on:click={addPoint} class="btn btn-success">+</button>
  <button disabled={gameOver} on:click={subtractPoint} class="btn btn-danger">-</button>
</div>

<style>
  div.col {
    padding: 20px;
    text-align: center;
  }
</style>
