<script lang='ts'>
  //add functionality for timed turns instead of timed game 
  import Timer from './Timer.svelte';

  let current_timer;
  export let numberOfPlayers: number;
  $: activeTimers = Array.from({length: numberOfPlayers}, (_, index) => index + 1)
  let deactivatedTimers = [];


  function reset(){

  }

  function pauseAll(){

  } 

  function startGame(){

  } 

  function next(){

  }
  
  function disableTimer(){

  }

</script>

<div>
  {#each activeTimers as timerId}
    <Timer id={timerId} duration={600}/>
  {/each}
</div>

<style></style>
