<script lang="ts">
    import CatlystCarousel from "$lib/carousel/CatlystCarousel.svelte";
    import SingleChoices from "$lib/template/singleChoice/SingleChoices.svelte";
    import MultipleChoices from "$lib/template/multipleChoice/MultipleChoices.svelte";
</script>

<style>
    .carriage {
        min-width: 95vw;
        max-width: 95vw;
    }
</style>

<CatlystCarousel speed={2.5} style="margin:2.5vw">
    <div class="carriage">
        <SingleChoices/>
        <MultipleChoices/>
    </div>
    <div class="carriage">
        <SingleChoices/>
        <MultipleChoices/>
    </div>
    <div class="carriage">
        <SingleChoices/>
        <MultipleChoices/>
    </div>
    <div class="carriage">
        <SingleChoices/>
        <MultipleChoices/>
    </div>
</CatlystCarousel>