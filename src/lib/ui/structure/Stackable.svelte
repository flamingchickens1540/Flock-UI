<script lang="ts">
    import { onMount } from "svelte";

    let content : HTMLSpanElement;

    export let stack : boolean = false;

    export let horizontal : boolean = false;

    function getPixels(pixels : string) {
        return Number(pixels.slice(0, pixels.length-2));
    }

    if(stack) onMount(() => {
        const element = content.children[0] as HTMLElement;
        const style = element.style;
        const computedStyle = getComputedStyle(element);

        style[horizontal ? "paddingLeft" : "paddingTop"] = `${getPixels(computedStyle[horizontal ? "paddingRight" : "paddingBottom"]) - (getPixels(computedStyle.borderRadius) + getPixels(computedStyle[horizontal ? "borderLeftWidth" : "borderTopWidth"]))/2}px`
        style[horizontal ? "marginLeft" : "marginTop"] = `${-getPixels(computedStyle.borderRadius) - 1}px`;
        style.borderTopLeftRadius = style[horizontal ? "borderBottomLeftRadius" : "borderTopRightRadius"] = "0px";
    });
</script>
<div bind:this={content} style="display:contents">
    <slot/>
</div>