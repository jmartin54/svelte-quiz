<script>
  import HStack from "../lib/HStack.svelte";
import VStack from "../lib/VStack.svelte";
import { best_colors } from "../assets/theme/best_colors";
import PageLayout from "./PageLayout.svelte";

  export let x;

</script>
<PageLayout on:click>
    <h1> Hello world </h1>

    {x[0].toString(16)}
    
    {#each Object.entries(best_colors) as [group, colors]} 
      <VStack>
        {group}   
        <HStack>
          {#each colors as color}
            <div style:background={color} height='10vh' style:flex={1}></div>
          {/each}
        </HStack>
      </VStack>
    {/each}

</PageLayout>