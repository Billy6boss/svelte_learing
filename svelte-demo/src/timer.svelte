<script>


    export let mic_sec = 0;
    export let min = 0;
    let hour = 0;
    export let count = 0;
    export let hideButton = false;

    // $:  mean depent on ...

    $: blink = mic_sec % 100 > 50 ? "　" : "：";

    $: if (min >= 60) {
        hour++;
        min = 0;
    }

    let timer;

    export function startTimer() {
        
        if(!timer){
            timer = window.setInterval(function () {
                mic_sec += 1;
                if (mic_sec / 100 >= 60) {
                    min++;
                    mic_sec = 0;
                }
            }, 10);
        }

    }

    export function stopTimer() {
        window.clearInterval(timer);
        timer = null;
    }

    export function resetTimer() {
        count++;
        mic_sec = 0;
        min = 0;
        hour = 0;
    }
</script>

{#if !hideButton}
    <button class="btn btn-success" on:click={startTimer}>開始</button>
    <button class="btn btn-danger" on:click={stopTimer}>Stop</button>
    <button class="btn btn-secondary" on:click={resetTimer}>Reset</button>
{/if}
<h5>
    Time in: {hour}{blink}{min}{blink}<span class="sec-box"
        >{(mic_sec / 100).toFixed(2)}</span
    >
</h5>
<label for="">
    <input type="checkbox" bind:checked ={hideButton}>
    Hide the button
</label>

<style>
    .sec-box {
        display: inline-block;
        min-width: 50px;
    }
</style>
