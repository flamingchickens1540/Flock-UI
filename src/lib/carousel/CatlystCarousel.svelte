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

    function handlemousedown(x : number) {
        lastMouseX = x;
        mouseup = false;
    }

    function handlemouseup() {
        snap();
        mouseup = true;
    }

    function handlemousemove(x : number) {
        if(mouseup) return;

        margin = Math.max(Math.min(margin + (x - lastMouseX) * speed, 0), snaps[snaps.length - 1]);

        lastMouseX = x;
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

    function snap() {
        let closest : number = 0;
        for(const snap of snaps) {
            if(Math.abs(margin - snap) < Math.abs(margin - closest)) closest = snap;
        }
        
        margin = closest;
    }

    onMount(() => {
        addEventListener("resize", calculateSnaps);
        calculateSnaps();
    });
</script>

<style>
    #carousel {
        display:flex;
        flex-direction: row;
    }

    .mouseup {
        transition: margin 0.2s ease-in-out;
    }

    #carouselFrame {
        overflow: hidden;
    }
</style>

<div id="carouselFrame" style="width:{width}">
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <!-- svelte-ignore a11y-mouse-events-have-key-events -->
    <div 
    on:touchstart={touch => handlemousedown(touch.touches[0].pageX)} 
    on:touchmove={touch => handlemousemove(touch.touches[0].pageX)} 
    on:touchend={handlemouseup} 

    on:mousedown={mouse => handlemousedown(mouse.x)} 
    on:mousemove={mouse => handlemousemove(mouse.x)} 
    on:mouseup={handlemouseup} 

    on:mouseleave={handlemouseup}
    class:mouseup id="carousel" style="margin-left:{margin}px;carousel" bind:this={content}>
        <slot/>
    </div>
</div>