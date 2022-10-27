<script lang="ts">

  import HStack from "../lib/HStack.svelte";
  import { best_colors, warm_cool } from "../assets/theme/best_colors";
  import PageLayout from "./PageLayout.svelte";
  import Swatch from "../lib/Swatch.svelte";
  import VStack from "../lib/VStack.svelte";
  import Space from "../lib/Space.svelte";
  
  export let selected = null;

  function select(temp: string) {
    selected = temp;
  }

  function selectKeyboard(){} // TODO: this

  let options = Object.entries(warm_cool);

</script>

<PageLayout on:click disableNext={selected == null}>

  <h1>Pick One</h1>
  {#each options as [temp, color_groups]}
    <div 
      on:click={()=> select(temp)} 
      on:keypress={selectKeyboard} 
      data-value={temp}
      class={ selected == temp ? 'active option' : 'option' }
    >
    <VStack>
      {temp}
      {#each color_groups as color_group}
        <HStack>
          {#each best_colors[color_group] as color}
          <Swatch {color} />
          {/each}
        </HStack>
      {/each}
      </VStack>
    </div>
    <Space />
  {/each}

</PageLayout>

<style>
  .option {
    display: flex;
    flex-grow: 1;
    align-items: center;
    justify-content: center;
    border-radius: 1.5vh;
    padding: 2vw;
  }
  .option[data-value='warm']:hover {
    background-color: var(--color-light-200);
  }
  .option[data-value='cool']:hover {
    background-color: var(--color-dark-400);
  }
  .active.option[data-value='warm'] {
    border: 0.1vh solid var(--color-light-800);
  }
  .active.option[data-value='cool'] {
    border: 0.1vh solid var(--color-dark-200);
  }
</style>