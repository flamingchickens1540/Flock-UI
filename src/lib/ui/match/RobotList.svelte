<script lang="ts">
    export let robotNumbers : string[];
</script>

{#each robotNumbers as robotNumber}
    <slot robotNumber={robotNumber}/>
{/each}