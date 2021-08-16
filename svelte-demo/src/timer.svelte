<script>
    let mic_sec = 0;

    let timer;

    function startTimer() {
        timer = window.setInterval(function () {
            mic_sec+=1;
        }, 10);
    }

    function stopTimer() {
        window.clearTimeout(timer);
    }

    function resetTimer() {
        mic_sec = 0;
    }
</script>

<button class="btn btn-success" on:click={startTimer}>開始</button>
<button class="btn btn-danger" on:click={stopTimer}>Stop</button>
<button class="btn btn-secondary" on:click={resetTimer}>Reset</button>
<p>Time in: {mic_sec/100}</p>
