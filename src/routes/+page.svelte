<script lang='ts'>
  import Counter from './Counter.svelte';
  import TimerContainer from './TimerContainer.svelte';
  let count: number; 

  function handleMessage(event){
    count = event.detail.count     
  }
  
</script>
<h1>Welcome to OmniTime</h1>
<Counter on:message={handleMessage} text="Select number of players" count={count}/>
<TimerContainer numberOfPlayers={count}/>
