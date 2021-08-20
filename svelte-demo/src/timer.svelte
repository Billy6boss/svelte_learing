<script>
    let mic_sec = 0;
    let min = 0;
    let hour = 0;

    // $:  mean depent on ...

    $: blink = mic_sec % 100 > 50 ? "　" : "：";

    $: if (min >= 60) {
        hour++;
        min = 0;
    }

    let timer;

    function startTimer() {
        timer = window.setInterval(function () {
            mic_sec += 1;
            if (mic_sec / 100 >= 60) {
                min++;
                mic_sec = 0;
            }
        }, 10);
    }

    function stopTimer() {
        window.clearTimeout(timer);
    }

    function resetTimer() {
        mic_sec = 0;
        min = 0;
        hour = 0;
    }
</script>

<button class="btn btn-success" on:click={startTimer}>開始</button>
<button class="btn btn-danger" on:click={stopTimer}>Stop</button>
<button class="btn btn-secondary" on:click={resetTimer}>Reset</button>
<h5>
    Time in: {hour}{blink}{min}{blink}<span class="sec-box"
        >{(mic_sec / 100).toFixed(2)}</span
    >
</h5>

<style>
    .sec-box {
        display: inline-block;
        min-width: 50px;
    }
</style>
