<script lang="ts">
  import Footer from "./lib/Footer.svelte";
  import Header from "./lib/Header.svelte";
  import Welcome from "./pages/Welcome.svelte";
  import TestColorGroups from "./pages/TestColorGroups.svelte";
  import WarmOrCool from "./pages/WarmOrCool.svelte";
  import PickRed from "./pages/PickRed.svelte";

  let page = 1;
  let outOf = 12;

  function handleClick() {
    page = (page + 1) % (outOf + 1);
  }

  let warmCool;
  let red

</script>

<main>
  <Header />
  {#if      page == 1}  <Welcome on:click={handleClick} />
  {:else if page == 2}  <WarmOrCool on:click={handleClick} bind:selected={warmCool} />
  {:else if page == 3}  <PickRed on:click={handleClick} bind:selected={red} />
  {:else if page == 4}  <TestColorGroups on:click={handleClick} {red} />
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