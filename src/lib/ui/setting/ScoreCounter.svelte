<script lang="ts">
    let value : number = 0;

    function change(delta : number) {
        value += delta;
    }
</script>

<slot change={change} value={value}/>