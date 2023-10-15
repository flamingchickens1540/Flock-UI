<script lang="ts">
    import { onMount } from "svelte";

    let content : HTMLSpanElement;

    export let stack : boolean = false;

    function getPixels(pixels : string) {
        return Number(pixels.slice(0, pixels.length-2));
    }

    if(stack) onMount(() => {
        const element = content.children[0] as HTMLElement;
        const style = element.style;
        const computedStyle = getComputedStyle(element);

        style.paddingTop = `${getPixels(computedStyle.paddingBottom) - (getPixels(computedStyle.borderRadius) + getPixels(computedStyle.borderTopWidth))/2}px`
        style.marginTop = `${-getPixels(computedStyle.borderRadius) - 1}px`;
        style.borderTopLeftRadius = style.borderTopRightRadius = "0px";
    });
</script>
<div bind:this={content}>
    <slot/>
</div>