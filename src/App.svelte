<script>
	import Timer from './Timer.svelte';
	import HowTo from './HowTo.svelte';
	let audio;

	function timerEnds(e) {
		audio.play();
	}
</script>

<style>
	h1, h3{
		text-align: center;
	}
</style>

<h1>Handwashing App</h1>

<Timer on:end={timerEnds}></Timer>
<HowTo></HowTo>

<h3>
	<a href="https://www.who.int/gpsc/clean_hands_protection/en/">Picture Source</a><br>
	<a href="https://freesound.org/people/metrostock99/sounds/345086/">Sound Source</a>
</h3>

<!-- svelte-ignore a11y-media-has-caption -->
<audio src="sound.wav" bind:this={audio}></audio>