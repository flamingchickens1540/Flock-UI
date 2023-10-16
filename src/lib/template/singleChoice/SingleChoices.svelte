<script lang="ts">
    import Stackable from "$lib/ui/structure/Stackable.svelte";
    import Option from "$lib/ui/option/Option.svelte";
    import OptionChoices from "$lib/ui/option/OptionChoices.svelte";
    import SingleChoice from "./SingleChoice.svelte";

    export let options : string[] = ["up", "down", "right", "left"];
    export let name : string = "Directions";
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
                <SingleChoice id={id} selected={selected}>
                    {option}
                </SingleChoice>
            </Stackable>
        </Option>
    {/each}
</OptionChoices>