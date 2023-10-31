<script lang="ts">
    export let value : number = 0;

    function change(delta : number) {
        value += delta;
    }
</script>

<slot change={change} value={value}/>