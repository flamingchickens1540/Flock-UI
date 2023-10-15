<script lang="ts">
    export let selected : number = 0;

    export let id : number;

    export let toggled : boolean = false;

    $: {
        if(selected == id) {
            toggled = !toggled;
        }
    }
</script>

<style>
    div {
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

<div class:toggled><slot/></div>