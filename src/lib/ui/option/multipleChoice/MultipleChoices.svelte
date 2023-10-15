<script lang="ts">
    import Stackable from "$lib/ui/structure/Stackable.svelte";
    import Option from "../Option.svelte";
    import OptionChoices from "../OptionChoices.svelte";
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

<OptionChoices let:selected let:select>
    <Stackable>
        <div class="buttonsTitle">
            {name}
        </div>
    </Stackable>
    {#each options as option, id}
        <Option id={id} handleClick={select}>
            <Stackable stack>
                <MultipleChoice id={id} selected={selected}>
                    {option}
                </MultipleChoice>
            </Stackable>
        </Option>
    {/each}
</OptionChoices>