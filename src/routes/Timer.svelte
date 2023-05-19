<script lang="ts">
	export let duration: number;
	let timeElapsed = 0;
	let timeRemaining = 0;
	let seconds = duration % 60;
	let minutes = duration / 60;
	$: timeRemaining = duration - timeElapsed;
	$: seconds = timeRemaining % 60;
	$: minutes = Math.floor(timeRemaining / 60);
	let appendSeconds = '0' + seconds.toString();
	let appendMinutes = minutes.toString();

	function start() {
		startTimer();
		setInterval(startTimer, 1000);
	}

	async function incrementTime() {
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

	function pause() {}

	function disable() {}
</script>

<div>
	<p>I'm a timer with time: {appendMinutes}:{appendSeconds}</p>
	<button on:click={start}> START </button>
</div>

<style></style>
