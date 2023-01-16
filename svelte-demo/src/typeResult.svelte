<script>
    import { result_word } from "./top200words";
    let action_between = [" ", ";<br>"];
    let word_color_list = ["","blue","yellow","light_yellow"];
    let number1_0;

    function  getRandomNumber() {
        number1_0 = Math.floor(Math.random());
    }
    
    
</script>


<section>
    <div class="container sublime-style">
        
        {#each $result_word as thisWord ,i}
            {#if thisWord.result}
                <span class="{word_color_list[thisWord.color]}">
                    {thisWord.word}{@html action_between[0]}
                </span>
            {:else}
                <span class="red">
                    {thisWord.word}{action_between[0]}
                </span>
            {/if}
        {/each}
    </div>
</section>

<style>
    .sublime-style{
        font-size: 24px;
        font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
        background-color: #303841FF;
        color:#D8DEE9FF;
    }

    .sublime-style .red{
        color:#EC5A56FF;
    }
    .sublime-style .blue{
        color:#C695C6FF;
    }
    .sublime-style .yellow{
        color:#E2AE57FF;
    }
    .sublime-style .light_yellow{
        color:#8CC794FF;
    } 

</style>