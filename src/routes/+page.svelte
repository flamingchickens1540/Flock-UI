<script lang="ts">
    import CatlystCarousel from "$lib/carousel/CatlystCarousel.svelte";
    import SingleChoices from "$lib/template/singleChoice/SingleChoices.svelte";
    import MultipleChoices from "$lib/template/multipleChoice/MultipleChoices.svelte";

    let teamNumbers1 = ["1540", "100", "78"];
    let teamNumbers2 = ["1541", "200", "88"];
</script>

<style>
    .carriage {
        min-width: 95vw;
        max-width: 95vw;
    }

    .TeamNumber {
        color:white;
        border-radius: 10px;
        border-width: 3px;
        border-color:black;
        border-style: solid;
        padding:10px;
        width:100px;
        text-align: center;
    }
</style>

<CatlystCarousel speed={2.5} style="margin:2.5vw;">
    <div class="carriage">
        <SingleChoices/>
        <MultipleChoices/>
    </div>
    <div class="carriage">
        <SingleChoices/>
        <MultipleChoices/>
        <img src="src\routes\FC.png" alt="" width="100px" height="100px"/>
    </div>
    <div class="carriage">
        <SingleChoices/>
        <MultipleChoices/>
    </div>
</CatlystCarousel>
<CatlystCarousel style="margin:2.5vw;">
    {#each [1, 1, 1] as h}
        <div class="carriage">
            <div style="display:flex;flex-direction:row;">
                
            </div>
            <div style="display:flex;flex-direction:row;">
            </div>
        </div>
    {/each}
</CatlystCarousel>