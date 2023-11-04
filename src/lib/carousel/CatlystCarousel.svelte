<!-- 
    @component

    Adds carousel carriage behaviors to the child element in this component.

    ```svelte
    <CatlystCarousel style="margin:2.5vw" speed={2} snapSeconds={0.2} shouldSnap>
        {elements}
    </CatlystCarousel>
    ```
     - speed : speed of the carousel
     - snapSeconds : how long it takes for the carousel to snap 
     - shouldSnap : if the carousel should snap (defaults true)

    Notes:
    If the child element/carriages move are resizing when they are not meant to do so, define a min-width and a max-width in the style of the child elements.
 -->

<script lang="ts">
    import { onMount } from "svelte";

    /**
     * The style of the frame for the carousel.
     */
    export let style : string = "";

    export let speed : number = 2;

    export let snapSeconds : number = 0.2;

    export let shouldSnap : boolean = true;

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

        margin = Math.max(Math.min(margin + (x - lastMouseX) * speed, 0), -content.clientWidth);

        lastMouseX = x;
    }

    function snap() {
        let closest : number = 0;
        for(const child of content.children) {
            const left = child.getBoundingClientRect().left - content.children[0].getBoundingClientRect().x;
            if(Math.abs(margin + left) < Math.abs(margin + closest)) closest = left;
        }
        
        margin = -closest;
    }

    onMount(() => {
        addEventListener("resize", snap);
        snap();
    });
</script>

<style>
    #carousel {
        display:flex;
        flex-direction: row;
        width: 100%;
        height: 100%;
    }

    #carouselFrame {
        overflow: hidden;
        transition-property: margin;
        transition-timing-function: ease-in-out;
    }
</style>

<div id="carouselFrame" style={style}>
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
    id="carousel" style="
    transition-duration:{mouseup ? snapSeconds : 0}s;
    margin-left:{margin}px;
    " bind:this={content}>
        <slot/>
    </div>
</div>