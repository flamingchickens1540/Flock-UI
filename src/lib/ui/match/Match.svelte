<script lang="ts">
    export let subHeader : string[] | number;

    export let redAlliance : string[];
    export let blueAlliance : string[];
</script>

<style>
    .subHeader {
        color: white;
        text-align: left;
    }

    .alliance {
        flex-direction: row;
        display: flex;
    }

    .match {
        background-color: black;
        border-radius: 20px;
        width: fit-content;
        padding: 10px;
    }
</style>

<div class="match">
    {#if typeof subHeader == "number"}
        <slot name="comingUpHeader"/>
    {:else}
        <slot name="header"/>
    {/if}

    {#if typeof subHeader == "number"}
        <div class="subHeader">
            <!-- match in milliseconds to minutes -->
            Game starts in {(subHeader - Date.now()) / 60000}m
        </div>
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