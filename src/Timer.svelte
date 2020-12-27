<script>
  import Progressbar from "./Progressbar.svelte";
  import {createEventDispatcher} from "svelte";
  
  const totalSeconds = 4;
  let secondsLeft = totalSeconds;
  let isRunning= false;
  $: progress = (totalSeconds-secondsLeft)/totalSeconds*100;
  const dispatch = createEventDispatcher();

  function startTimer(){
    const timer = setInterval(()=>{
      isRunning = true;
      secondsLeft -= 1;
      if(secondsLeft ==0){
        isRunning = false;
        clearInterval(timer);
        secondsLeft = totalSeconds;
        dispatch('end','end timer');
      }
    },1000);
  }
</script>
<style>
  h2 {
    margin:0;
  }
  .start {
    background-color: rgb(154,73,73);
    width:100%;
    margin: 10px,0;
  }
  .start[disabled]{
    background-color: rgb(194,194,194);
  }
</style>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">
    Seconds Left : {secondsLeft}
  </h2>
</div>
<!-- <h4>{progress}</h4> -->
<Progressbar {progress}/>
<div bp="grid">
  <button on:click={startTimer} disabled={isRunning} bp="offset-5@md 4@md 12@sm" class='start'>Start</button>
</div>


