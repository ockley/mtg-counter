<script>
  import Team from './Team.svelte';

  let redScore = 20;
  let blueScore = 20;

  $: redWon = blueScore === 0;
  $: blueWon = redScore === 0;
  $: gameOver = redWon || blueWon;
  
  function newGame() {
    redScore = 20;
    blueScore = 20;
  }
</script>

<div class="row mt-2">
  <div class="col">
    <h1 class="text-center">MTG Counter</h1>
  </div>
</div>

<div class="row">
  <Team {gameOver} team="Red" bind:score={redScore} />
  <Team {gameOver} team="Blue" bind:score={blueScore}/>
</div>

{#if !gameOver}
<div class="row">
  <div class="col">
    <button class="btn btn-warning mt-3 w-100" on:click={newGame}><h2>Reset Game</h2></button>
  </div>
</div>
{:else}
<div class="rov mt-3">
  <div class="col">
    {#if blueWon}
      <h2 class="text-center text-primary">Blue Won!</h2>
      {:else}
      <h2 class="text-center text-danger">Red Won!</h2>
    {/if}
    
  </div>
</div>
<div class="row">
  <div class="col">
    <button class="btn btn-success mt-3 w-100" on:click={newGame}><h2>New Game</h2></button>

  </div>
</div>
{/if}


