<script lang='ts'>

  export let duration: number;
  let timeElapsed = 0; 
  let timeRemaining = 0;
  let seconds = 0;
  let minutes = 0;
  $: timeRemaining = duration - timeElapsed;
  $: seconds = 60 - timeRemaining % 60 
  $: minutes = 60 - timeRemaining / 60 
  let appendSeconds = "0" + seconds.toString(); 
  let appendMinutes = "0" + minutes.toString(); 
  
  function start(){
    setInterval(startTimer, 1000);
  }

  function reset() {
    seconds = 0;
    appendSeconds = seconds.toString();
  }
   
  
  function startTimer() {
    timeRemaining++;

    if (seconds < 10) {
      appendSeconds = "0" + seconds;
    } else {
      appendSeconds = seconds.toString();
    }
  }

  export let id: number;

  function pause(){
         
  } 
  
  function disable(){

  }
  
</script>

<div>
  <p>I'm a timer with time: {appendMinutes}:{appendSeconds}</p>  
  <button on:click={start}>
    START
  </button>
</div>

<style></style>


