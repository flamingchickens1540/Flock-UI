<!-- Catlyst Carousel named such because...  -->

<script lang="ts">
    import { onMount } from "svelte";

    export let style : string = "";

    export let speed : number = 2;

    export let snapSeconds : number = 0.2;

    export let shouldSnap : boolean = true;

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
        if(shouldSnap) snap();
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

    #carouselFrame {
        overflow: hidden;
        transition-property: margin;
        transition-timing-function: ease-in-out;
    }
</style>

<div  id="carouselFrame" style={style}>
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
    id="carousel" style="transition-duration:{mouseup ? snapSeconds : 0}s;margin-left:{margin}px;carousel" bind:this={content}>
        <slot/>
    </div>
</div>