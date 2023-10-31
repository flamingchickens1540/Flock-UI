<script lang="ts">
    export let redAlliance : string[];
    export let blueAlliance : string[];
</script>

{#each redAlliance as teamNumber}
    <slot teamNumber={teamNumber} redAlliance={true}/>
{/each}

{#each blueAlliance as teamNumber}
    <slot teamNumber={teamNumber} redAlliance={false}/>
{/each}