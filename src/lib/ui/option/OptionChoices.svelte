<script lang="ts">
    export let selected : number = 0;

    function select(id : number) {
        selected = -1;
        selected = id;
    }
</script>

<slot selected={selected} select={select}/>