<script lang="ts">
    import Option from "$lib/ui/option/Option.svelte";
    import OptionChoices from "$lib/ui/option/OptionChoices.svelte";
    import Stackable from "$lib/ui/structure/Stackable.svelte";
    import SingleChoice from "$lib/ui/option/SingleChoice.svelte"
    import CatlystCarousel from "$lib/carousel/CatlystCarousel.svelte";
</script>

<CatlystCarousel speed={2}>
    <div style="min-width:100vw;max-width:100vw;height:100vw">
        <OptionChoices let:selected let:select>
            {#each ["up", "down", "right", "left"] as option, id}
                <Option id={id} handleClick={select}>
                    <Stackable stack={id != 0}>
                        <SingleChoice id={id} selected={selected}>
                            {option}
                        </SingleChoice>
                    </Stackable>
                </Option>
            {/each}
        </OptionChoices>
    </div>
    <div style="min-width:100vw;max-width:100vw;height:100vw">
        <OptionChoices let:selected let:select>
            {#each ["one", "two", "three", "four"] as option, id}
                <Option id={id} handleClick={select}>
                    <Stackable stack={id != 0}>
                        <SingleChoice id={id} selected={selected}>
                            {option}
                        </SingleChoice>
                    </Stackable>
                </Option>
            {/each}
        </OptionChoices>
    </div>
</CatlystCarousel>