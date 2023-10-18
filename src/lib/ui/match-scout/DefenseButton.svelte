<script lang="ts">
    export let defenseTimes : number[] = [];

    let pressStartTime : number;

    function handlePress() {
        pressStartTime = Date.now();
    }

    function handleUnpress() {
        defenseTimes.push(Date.now() - pressStartTime);
    }
</script>

<button on:mousedown={handlePress} on:touchstart={handlePress} on:mouseup={handleUnpress}>
    <slot/>
</button>