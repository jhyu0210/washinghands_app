<!-- <h1> Test1</h1> -->
<script>
	import Timer from "./Timer.svelte"
	import HowTo from "./HowTo.svelte";
	let audio;
	function timerEnds(e){
		audio.play();
	}
</script>

<style>
	h1 {
		text-align:center
	}
</style>
<h1>HandWashing App</h1>

<Timer on:end={timerEnds}/>
<HowTo/>

<h3>
	<a href="https:/www.who.int/gpsc/clean_hands_protection/en/">Picture Source</a>
	<a href="https://freesound.org/people/metrostock99/sounds/345086/">Sound Source</a>
</h3>

<!-- <audio bind:this={audio}>
	<source src="oh_ye.wav" type="audio/wav"/>
</audio>	 -->

<!-- svelte-ignore a11y-media-has-caption -->
<audio bind:this={audio}>
  <source src="oh_ye.wav" type="audio/wav">
</audio>