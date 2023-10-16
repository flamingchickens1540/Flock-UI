<script lang="ts">
    export let toggled : boolean = false;

    function handleClick() {
        toggled = !toggled;
    }
</script>

<style>
    button {
        border-color: black;
        border-width: 2px;
        margin:0px;
        border-style: solid;
        border-radius: 4px;
        padding: 5px;
        background-color: #efdcdc;
    }

    .toggled {
        background-color: aqua;
        font-weight: bold;
    }
</style>

<button class:toggled on:click={handleClick}><slot/></button>