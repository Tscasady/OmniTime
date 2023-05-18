<script lang='ts'>
  let count = 0;

  function handleClick() {
    return count += 1
  }

  export let text: string;
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
