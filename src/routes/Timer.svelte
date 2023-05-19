<script lang="ts">
	export let duration: number;
	let timeElapsed = 0;
	let timeRemaining = 0;
	let interval: number;

	let seconds = duration % 60;
	let minutes = duration / 60;

	$: timeRemaining = duration - timeElapsed;
	$: seconds = timeRemaining % 60;
	$: minutes = Math.floor(timeRemaining / 60);

	let appendSeconds = '0' + seconds.toString();
	let appendMinutes = minutes.toString();

	function start() {
		startTimer();
		interval = window.setInterval(startTimer, 1000);
		console.log('interval', interval);
	}

	function incrementTime() {
		timeElapsed++;
	}

	function startTimer() {
		incrementTime();
		setTimeout(formatTime, 0);
	}

	function formatTime() {
		if (seconds < 10) {
			appendSeconds = '0' + seconds;
		} else {
			appendSeconds = seconds.toString();
		}

		if (minutes < 10) {
			appendMinutes = '0' + minutes;
		} else {
			appendMinutes = minutes.toString();
		}
	}

	function reset() {
		seconds = 0;
		appendSeconds = seconds.toString();
	}

	export let id: number;

	function pause() {
		clearInterval(interval);
	}

	let status = false;

	function disable() {
		pause();
		status = true;
	}
</script>

<div>
	<p>I'm a timer with time: {appendMinutes}:{appendSeconds}</p>
	<button class="startBtn" on:click={start} disabled={status}> START </button>
	<button on:click={pause}> PAUSE </button>
	<button on:click={disable}> DISABLE </button>
</div>

<!-- Timer Container's Concerns: -->
<!-- Timer/s disabled because not the timer's turn -->

<!-- Timer's Concerns: -->
<!-- Am I on or off? -->

<style>
	.startBtn {
		color: blue;
	}

	.startBtn:disabled {
		color: gray;
	}
</style>
