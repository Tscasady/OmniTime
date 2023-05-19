<script lang="ts">
	//add functionality for timed turns instead of timed game
	import Timer from './Timer.svelte';

	let current_timer;
	export let numberOfPlayers: number;
	// let timerIds = Array.from({ length: numberOfPlayers }, (_, index) => index + 1);
	let timerIds = [1, 2, 3];
	let activeTimers = [];
	let deactivatedTimers = [];

	function startGame() {
		current_timer = activeTimers[0];
		console.log(current_timer);
		current_timer.enable();
	}

	function next() {
		current_timer.disable();
		let index = (activeTimers.indexOf(current_timer) + 1) % activeTimers.length;
		current_timer = activeTimers[index];
		current_timer.enable();
		// set newcurrent timer
		// start new currentTimer
	}

	function reset() {}

	function pauseAll() {}

	function disableTimer() {}
</script>

<div>
	<button on:click={startGame}>START GAME</button>
	<button on:click={next}>NEXT PLAYER</button>
	{#each timerIds as timerId, i}
		<Timer bind:this={activeTimers[i]} id={timerId} duration={600} />
	{/each}
</div>

<style></style>
