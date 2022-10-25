<script lang="ts">
  import Footer from "./lib/Footer.svelte";
  import Header from "./lib/Header.svelte";
  import Welcome from "./pages/Welcome.svelte";

  let page = 1;
  let outOf = 12;

  function handleClick() {
    page = (page + 1) % (outOf + 1);
  }

</script>

<main>
  <Header />
  <Welcome  on:click={handleClick} />
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