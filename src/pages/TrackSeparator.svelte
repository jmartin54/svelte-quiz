<script>
  import Swatch from "../lib/Swatch.svelte";
  import { best_colors } from "../assets/theme/best_colors";
  import PageLayout from "./PageLayout.svelte";
  import HStack from "../lib/HStack.svelte";
  import VStack from "../lib/VStack.svelte";
  import Space from "../lib/Space.svelte";

    export let topTwo;

    let trackOne = best_colors[topTwo[0]];
    let trackTwo = best_colors[topTwo[1]];
    let selections = [null, null, null, null, null];

    function select(choice, track) {
        if(selections[choice] == track) selections[choice] = null
        else selections[choice] = track;
        selections = selections;
    }

    export let topGroup;
    $: topGroup =  selections.some(v => v==null) ? null : (()=> {
        let counts = [0, 0]
        for(var selection of selections) {
            counts[selection] = counts[selection] + 1;
        }
        if(counts[0] > counts[1]) return topTwo[0];
        return topTwo[1]
    })()
    
</script>
<PageLayout on:click disableNext={topGroup == null}>

    <h1> Pick one of each</h1>

    <VStack>

        <HStack>
            <Swatch color={trackOne[0]} circle={selections[0] == 0} on:click={() => select(0, 0)} />
            <Space />
            <Swatch color={trackTwo[0]} circle={selections[0] == 1} on:click={() => select(0, 1)} />
        </HStack>

        <Space />

        <HStack>
            <Swatch color={trackTwo[1]} circle={selections[1] == 1} on:click={() => select(1, 1)} /> <Space /> <!-- these are reversed to debias answers -->
            <Swatch color={trackOne[1]} circle={selections[1] == 0} on:click={() => select(1, 0)} />
        </HStack>

        <Space />

        <HStack>
            <Swatch color={trackTwo[2]} circle={selections[2] == 1} on:click={() => select(2, 1)} /> <Space />
            <Swatch color={trackOne[2]} circle={selections[2] == 0} on:click={() => select(2, 0)} />
        </HStack>

        <Space />

        <HStack>
            <Swatch color={trackOne[3]} circle={selections[3] == 0} on:click={()=> select(3, 0)} />
            <Space />
            <Swatch color={trackTwo[3]} circle={selections[3] == 1} on:click={()=> select(3, 1)} />
        </HStack>

        <Space />

        <HStack>
            <Swatch color={trackTwo[4]} circle={selections[4] == 2} on:click={()=> select(4, 1)} /> <Space />
            <Swatch color={trackOne[4]} circle={selections[4] == 0} on:click={()=> select(4, 0)} />
        </HStack>
    
        <Space />

    </VStack>

</PageLayout>