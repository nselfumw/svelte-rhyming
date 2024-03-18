<script>
    export let rhymeData;

    function buildSize (score) {
        return "font-size: " + score / 10 + "px";
    }
</script>

<p>Rhyme list goes here, we have {rhymeData.length} rhymes</p>

{#each rhymeData as rhyme, i}
    <p style="{buildSize(rhyme.score)}">{rhyme.word}</p>
{/each}

