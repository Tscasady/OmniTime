<script lang='ts'>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let count = 0;
  export let text: string;

  function handleClick() {
    count += 1;
    dispatch('message', {
      count: count 
    })
  }

</script>

<button on:click={handleClick}>
  {text} {count}   
</button>

<style>
  button {
    color: gainsboro;
    background-color: sienna;
    border: 1px solid blue;
    border-radius: .35rem;
    padding: 1rem;
  }
</style>
