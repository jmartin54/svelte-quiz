<script lang="ts">
    import HStack from "../lib/HStack.svelte";
    import Swatch from "../lib/Swatch.svelte";
    import VStack from "../lib/VStack.svelte";
    import PageLayout from "./PageLayout.svelte";
  import Space from "../lib/Space.svelte";

    export let selected = []
    export let colors;

    function select(colorGroup: string) {
        const wasSelected = selected.find(s => s == colorGroup);
        if(wasSelected) selected = selected.filter(s => s != colorGroup);
        if(selected.length >= 2) selected = [selected[1]];
        if(!wasSelected) selected = [...selected, colorGroup]
    }

</script>
<PageLayout on:click disableNext={selected.length < 2}>
    <h1>Pick Two</h1>
    <VStack>
        <HStack>
            <Swatch 
                color={colors.red_orange} 
                on:click={()=> select('red_orange')} 
                circle={selected.find(s=> s== 'red_orange')}
            />
            <Swatch 
                color={colors.red_purple} 
                on:click={()=> select('red_purple')} 
                circle={selected.find(s=> s== 'red_purple')}
            />
        </HStack>
        <HStack>
            <Swatch 
                color={colors.blue_green} 
                on:click={()=> select('blue_green')} 
                circle={selected.find(s=> s== 'blue_green')}
            />
            <Swatch 
                color={colors.blue_purple} 
                on:click={()=> select('blue_purple')} 
                circle={selected.find(s=> s== 'blue_purple')}
            />
        </HStack>
        <HStack>
            <Swatch 
                color={colors.yellow_orange} 
                on:click={()=> select('yellow_orange')} 
                circle={selected.find(s=> s== 'yellow_orange')}
            />
            <Swatch 
                color={colors.yellow_green} 
                on:click={()=> select('yellow_green')} 
                circle={selected.find(s=> s== 'yellow_green')}
            />
        </HStack>
    </VStack>
    <Space />
</PageLayout>