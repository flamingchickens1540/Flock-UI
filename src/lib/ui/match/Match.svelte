<script lang="ts">
    export let subHeader : string[] | number;

    export let redAlliance : string[];
    export let blueAlliance : string[];
</script>

<style>
    .alliance {
        flex-direction: row;
        display: flex;
    }
</style>

<div class="match">
    {#if typeof subHeader == "number"}
        <slot name="comingUpHeader"/>
    {:else}
        <slot name="header"/>
    {/if}

    {#if typeof subHeader == "number"}
        <!-- match in milliseconds to minutes -->
        <slot name="gameStartsIn"/>
    {:else}
        {#each subHeader as teamNumber, index}
            <slot alliance={"purple"} teamNumber={teamNumber} index={index}/>
        {/each}
    {/if}

    <div class="alliance">
        {#each redAlliance as teamNumber, index}
            <!-- slot used so that the team numbers are changeable in admin dashboard -->
            <slot alliance={"red"} teamNumber={teamNumber} index={index}/>
        {/each}
    </div>

    <div class="alliance">
        {#each blueAlliance as teamNumber, index}
            <slot alliance={"blue"} teamNumber={teamNumber} index={index}/>
        {/each}
    </div>
</div>