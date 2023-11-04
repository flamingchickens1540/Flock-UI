<script lang="ts">
    import Options from "$lib/ui/structure/Options.svelte";

    export let options : string[];
    export let selected : number[] = [];

    function handleSelect(index : number) {
        selected.includes(index) ? selected.splice(selected.indexOf(index), 1) : selected.push(index);
    }
</script>

<Options handleSelect={handleSelect} options={options} let:option let:index>
    <slot option={option} index={index}/>
</Options>