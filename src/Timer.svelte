<script>
    import ProgressBar from './ProgressBar.svelte';
    const totalSeconds = 5;
    let secondsLeft = totalSeconds;
    let isRunning = false;
    let timerInterval = null;
    $: progress = ((totalSeconds - secondsLeft) / totalSeconds) * 100;
    
    function startTimer() {
        timerInterval= setInterval(decreaseSeconds, 1000);
    }

    function decreaseSeconds() {
        secondsLeft -= 1;
        isRunning = true;
        if (secondsLeft == 0) {
            clearInterval(timerInterval);
            isRunning = false;
            resetSecondsLeft();
        }  
    }

    function resetSecondsLeft() {
        secondsLeft = totalSeconds;
    }
</script>

<style>
    h2 {
        margin:0;
    }
    .start {
        background-color: rgb(154, 73, 73);
        width: 100%;
        margin: 10px 0;
    }

    .start[disabled] {
        background-color: rgb(194,194, 194);
        cursor: not-allowed;
    }
</style>

<div bp="grid">
    <h2 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondsLeft}</h2>
</div>

<ProgressBar {progress}></ProgressBar>


<div bp="grid">
    <button bp="offset-5@md 4@md 12@sm" disabled={isRunning} class="start" on:click={startTimer}>Start</button>
    </div> 