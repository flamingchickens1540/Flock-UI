<!-- 
    @component
    Component to make a list of team numbers
 -->

<script lang="ts">
    export let teamNumbers : string[];
</script>

{#each teamNumbers as teamNumber, index}
    <slot teamNumber={teamNumber} index={index}/>
{/each}