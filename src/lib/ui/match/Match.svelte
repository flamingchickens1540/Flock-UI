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

    .team {
        border-radius: 20px;
        width: 4em;
        text-align: center;
        margin: 0.1em;
        padding: 0.2em;
        font-size: 100%;
        color:white;
    }

    .tag {
        background-color: #aa55ff;
        color: white;
        border-radius: 10px;
        padding: 3.5px;
        font-size: 75%;
        width: fit-content;
    }

    .match {
        background-color: black;
        border-radius: 20px;
        width: fit-content;
        padding: 10px;
    }
</style>

<div class="match darkTheme">
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
            <div class="team tag">
                <slot alliance={"purple"} teamNumber={teamNumber} index={index}/>
            </div>
        {/each}
    {/if}

    <div class="alliance">
        {#each redAlliance as teamNumber, index}
            <div class="team" style="background-color: red;">
                <!-- slot used so that the team numbers are changeable in admin dashboard -->
                <slot alliance={"red"} teamNumber={teamNumber} index={index}/>
            </div>
        {/each}
    </div>

    <div class="alliance">
        {#each blueAlliance as teamNumber, index}
            <div class="team" style="background-color: blue;">
                <slot alliance={"blue"} teamNumber={teamNumber} index={index}/>
            </div>
        {/each}
    </div>
</div>