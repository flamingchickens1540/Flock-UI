<script>
    import CatlystCarousel from "$lib/carousel/CatlystCarousel.svelte";

</script>

<style>
    div {
        min-width: 100vw;
        max-width: 100vw;
        user-select: none;
    }
</style>

<CatlystCarousel speed={5}>
    <div>
        <h1>page 1</h1>
        <thing>sdfkjn</thing>
    </div>
    <div>
        <h1>page 2</h1>
        <thing>ewjkfs</thing>
    </div>
    <div>
        <h1>page 3</h1>
        <thing>ewjkfs</thing>
    </div>
    <div>
        <h1>page 4</h1>
        <thing>ewjkfs</thing>
    </div>
    <div>
        <h1>page 5</h1>
        <thing>ewjkfs</thing>
        <button on:click={() => console.log('clicked!')}>click me</button>
    </div>
    <div>
        <h1>page 6</h1>
        <thing>ewjkfs</thing>
    </div>
</CatlystCarousel>