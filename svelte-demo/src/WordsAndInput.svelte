<script>
    import {words} from "./top200words.js";

    let words_array = words;
    export let user_input = "";
    export let hint;
   

    function keyPress(e) {
        if (e.key === ' ' || e.key === 'Spacebar') {

            
        }
    }


</script>

<style>
    .display-style{
        list-style-type: none;
        display: flex;
        flex-wrap: wrap;
    }
    .display-style li {
        margin-right: 3%;
    }
</style>

<div id="words_area">
    <ul id="words_list" class="display-style">
        {#each words_array as thisWord}
            <li value={thisWord}>{thisWord}</li>
        {/each}
    </ul>
</div>
<!-- <p>{words_array.join('、')}</p> -->
<input id="user_input" on:keypress={keyPress} type="text" placeholder={hint} value={user_input}>