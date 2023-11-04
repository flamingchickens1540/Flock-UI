<script lang="ts">
    export let options : string[];

    export let handleSelect : (index : number) => void;
</script>

{#each options as option, index}
    <button style="display:contents;" on:click={() => handleSelect(index)}>
        <slot option={option} index={index}/>
    </button>
{/each}
