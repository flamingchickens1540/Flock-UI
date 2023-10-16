<script lang="ts">
    import Stackable from "$lib/ui/structure/Stackable.svelte";
    import Option from "$lib/ui/option/Option.svelte";
    import OptionChoices from "$lib/ui/option/OptionChoices.svelte";
    import MultipleChoice from "./MultipleChoice.svelte";

    export let options : string[] = ["one", "two", "three", "four"];
    export let name : string = "Numbers";
</script>

<style>
    .buttonsTitle {
        border-color: black;
        border-width: 2px;
        margin:0px;
        border-style: solid;
        border-radius: 4px;
        padding: 5px;
        background-color: #efdcdc;
        text-align: center;
        font-weight: 700;
        font-family: 'Poppins';
        font-size: 23px;
        border-color: black;
    }
</style>

<div style="flex-direction:column;display:flex">
    <Stackable>
        <div class="buttonsTitle">
            {name}
        </div>
    </Stackable>
    {#each options as option, id}
        <Stackable stack>
            <MultipleChoice id={id}>
                {option}
            </MultipleChoice>
        </Stackable>
    {/each}
</div>