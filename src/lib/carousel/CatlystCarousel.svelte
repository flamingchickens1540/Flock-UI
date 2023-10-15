<!-- Catlyst Carousel named such because...  -->

<script lang="ts">
    import { onMount } from "svelte";

    export let speed : number = 1;

    export let width : string = "100vw";

    let snaps : number[];

    let content : HTMLDivElement;

    let margin = 0;

    let mouseup = false;

    let lastMouseX : number;

    function snap() {
        let closest : number = 0;
        for(const snap of snaps) {
            if(Math.abs(margin - snap) < Math.abs(margin - closest)) closest = snap;
        }
        
        margin = closest;
    }

    function handlemousedown(mouse : MouseEvent) {
        lastMouseX = mouse.x;
        mouseup = false;
    }

    function handlemouseup() {
        snap();
        mouseup = true;
    }

    function handlemousemove(mouse : MouseEvent) {
        if(mouseup) return;

        margin = Math.min(margin + (mouse.x - lastMouseX) * speed, 0);

        lastMouseX = mouse.x;
    }

    function calculateSnaps() {
        snaps = [];
        let snapX = 0;
        for(const child of content.children) {
            snaps.push(snapX);
            snapX -= child.clientWidth;
        }
        
        snap();
    }

    onMount(() => {
        addEventListener("resize", calculateSnaps);
        calculateSnaps();
    });
</script>

<style>
    #carousel {
        height: 100vh;
        display:flex;
        flex-direction: row;
        overflow-x: hidden;
    }

    .mouseup {
        transition: margin 0.2s ease-in-out;
    }

    #carouselFrame {
        width: 50vw;
        overflow-x: hidden;
    }
</style>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div id="carouselFrame" style="width:{width}">
    <div on:mousedown={handlemousedown} on:mouseup={handlemouseup} on:mousemove={handlemousemove} class:mouseup id="carousel" style="margin-left:{margin}px;" bind:this={content}>
        <slot/>
    </div>
</div>