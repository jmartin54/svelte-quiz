<script lang="ts">
  import Footer from "./lib/Footer.svelte";
  import Header from "./lib/Header.svelte";
  import Welcome from "./pages/Welcome.svelte";
  import WarmOrCool from "./pages/WarmOrCool.svelte";

  let page = 0;
  let outOf = 12;

  function handleClick() {
    page = (page + 1) % (outOf + 1);
  }

</script>

<main>
  <Header />
  {#if      page == 0}  <Welcome on:click={handleClick} />
  {:else if page == 1}  <WarmOrCool on:click={handleClick} />
  {:else if page == 2}  <WarmOrCool on:click={handleClick} />
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