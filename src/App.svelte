<script lang="ts">
  import Footer from "./lib/Footer.svelte";
  import Header from "./lib/Header.svelte";
  import Welcome from "./pages/Welcome.svelte";
  import TestColorGroups from "./pages/TestColorGroups.svelte";
  import WarmOrCool from "./pages/WarmOrCool.svelte";
  import PickColors from "./pages/PickColors.svelte";
  import { reds, greens, blues } from "./assets/theme/best_colors";
  import HairColor from "./pages/HairColor.svelte";

  let page = 1;
  let outOf = 12;

  function handleClick() {
    page = (page + 1) % (outOf + 1);
  }

  let warmCool;
  let red, green, blue;
  let hair;

</script>

<main>
  <Header />
  {#if      page == 1}  <Welcome on:click={handleClick} />
  {:else if page == 2}  <WarmOrCool on:click={handleClick} bind:selected={warmCool} />
  {:else if page == 3}  <PickColors on:click={handleClick} bind:selected={red} colors={reds} />
  {:else if page == 4}  <PickColors on:click={handleClick} bind:selected={green} colors={greens} />
  {:else if page == 5}  <PickColors on:click={handleClick} bind:selected={blue} colors={blues} />
  {:else if page == 6}  <HairColor on:click={handleClick} bind:selected={hair} />
  {:else if page == 7}  <TestColorGroups on:click={handleClick} x={hair} />
  {:else}               <Welcome on:click={handleClick} />
  {/if}
  <Footer {page} {outOf} />
</main>

<style>
  main {
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  } 
</style>