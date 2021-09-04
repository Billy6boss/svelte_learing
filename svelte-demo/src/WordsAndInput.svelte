<script>
    import { words } from "./top200words.js";
    import Timer from "./timer.svelte";
    import { beforeUpdate,afterUpdate } from "svelte";

    let words_array = words;
    let user_input_text = "";
    let user_input;
    let correct = 0;
    let worng = 0;
    let min, mic_sec;
    let testOvertime = 1;
    let timerControl;
    let code_color_bule = "#2e7dd6";
    let closeInput = false;
    // let code_color_yellow = "#DCDCAAFF";
    // let code_color_white = "#FFFFFFFF";
    // let code_text_color = [code_color_bule,code_color_white,code_color_yellow];

    $: isWordMatch = user_input_text === words_array[0];
    $: closeInput = min >= testOvertime;
    $: if (closeInput) {
        timerControl.stopTimer();
        user_input_text = "";
    }

    

    export let hint;

    function keyPress(e) {
        timerControl.startTimer();

        if (e.key === " " || e.key === "Spacebar") {
            e.preventDefault();
            if (isWordMatch) {
                correct++;
            } else {
                worng++;
            }

            words_array = words_array.slice(1);
            user_input_text = document.getElementById("user_input").value = "";
        }
    }

    function resetWords() {
        words_array = words;
        shuffle(words_array);
        timerControl.resetTimer();
    }

    function shuffle(array) {
        for (let i = array.length - 1; i > 0; i--) {
            let j = Math.floor(Math.random() * (i + 1));
            [array[i], array[j]] = [array[j], array[i]];
        }
    }
</script>

<div
    id="words_area"
    class="border border-warning border-3 my-5"
    style="color:{code_color_bule}"
>
    <span class="user_text">{user_input_text}</span>
    <ul id="words_list" class="display-style">
        {#each words_array as thisWord, i}
            <li class:correct="{isWordMatch}" value={i}>{thisWord}</li>
        {/each}
    </ul>
</div>
<!-- <p>{words_array.join('、')}</p> -->


<input
    id="user_input"
    type="text"
    disabled={closeInput}
    placeholder={hint}
    bind:this={user_input}
    on:keypress={keyPress}
    bind:value={user_input_text}
/>
<button id="reset_btn" on:click={resetWords} class="btn btn-primary">↻</button>

<h5>✔:{correct} ❌:{worng}</h5>
<Timer bind:this={timerControl} bind:min bind:mic_sec hideButton={true} />
<div class="input-group mb-3 justify-content-center">
    <span class="input-group-text">Test Time</span>
    <input id="overTime" class="" type="number" min="1" bind:value={testOvertime}/>
    <span class="input-group-text">Min.</span>
</div>

<style>
    #words_area {
        position: relative;
        background-color: #1e1e1eff;
        max-height: 4.8em;
        overflow: hidden;
        font-size: 1.4em;
        font-weight: bolder;
    }
    .user_text {
        position: absolute;
        top: 1.4em;
        left: 2rem;
        background-color: #303841ff;
        color: #d8dee9ff;
    }

    .display-style {
        list-style-type: none;
        display: flex;
        flex-wrap: wrap;
    }
    .display-style li {
        margin-right: 3%;
    }
    #words_list li.correct:nth-of-type(1) {
        color: #dcdcaaff;
    }
</style>
