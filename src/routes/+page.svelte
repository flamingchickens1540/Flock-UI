<script lang="ts">
    import CatlystCarousel from "$lib/carousel/CatlystCarousel.svelte";
import Options from "$lib/ui/structure/Options.svelte";

    let teamNumbers1 = ["1540", "100", "78"];
    let teamNumbers2 = ["1541", "200", "88"];
</script>

<style>
    div {
        font-size:x-large;
    }
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

<CatlystCarousel style="width:15px; height:100px;">
<div>d</div>
<div>b</div>
</CatlystCarousel>