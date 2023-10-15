<script lang="ts">
    export let id : number;
    export let handleClick : (id : number) => void;
</script>

<button style="display:contents;" on:click={() => handleClick(id)}>
    <slot/>
</button>