<script lang="ts">
    export let value : number = 0;

    export function change(delta : number) {
        value += delta;
    }
</script>

<slot/>