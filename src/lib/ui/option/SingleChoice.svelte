<script lang="ts">
    export let selected : number = 0;

    export let id : number;
</script>

<style>
    div {
        border-color: black;
        border-width: 2px;
        margin:0px;
        border-style: solid;
        border-radius: 7px;
        padding: 5px;
        background-color: white;
    }

    .selected {
        background-color: #7ed957;
        font-weight: bold;
    }
</style>

<div class:selected={selected == id}><slot/></div>