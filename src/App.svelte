<!-- https://svelte.dev/repl/79f4f3e0296a403ea988f74d332a7a4a?version=3.12.1 // Canvas Game Demo -->
<!-- https://stackoverflow.com/questions/49643248/html5-canvas-draw-lines-in-a-circle // Canvas visualization -->
<!-- https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API // canvas docs -->
<script lang="ts">
  import Footer from "./lib/Footer.svelte";
  import Header from "./lib/Header.svelte";
  import Welcome from "./pages/Welcome.svelte";
  import TestColorGroups from "./pages/TestColorGroups.svelte";
  import WarmOrCool from "./pages/WarmOrCool.svelte";
  import PickColors from "./pages/PickColors.svelte";
  import { reds, greens, blues } from "./assets/theme/best_colors";
  import HairColor from "./pages/HairColor.svelte";
  import ColorHexagon from "./pages/ColorHexagon.svelte";
  import TrackSeparator from "./pages/TrackSeparator.svelte";
  import { prevent_default } from "svelte/internal";
  import Result from "./pages/Result.svelte";

  let page = 1;
  let outOf = 8;

  function handleClick() {
    page = (page + 1) % (outOf + 1);
  }

  let warmCool;
  let red, green, blue;
  let hair;
  let colorHexagon;

  let topTwo;
  $: if(red && green && blue) topTwo = ((a) => {
    const counts = {}
    a.forEach(v => counts[v] = counts[v] == undefined ? 1 : counts[v] + 1)

    const countsArray = []
    for(let k in counts) countsArray.push({group: k, count: counts[k]})
    
    const sorted = countsArray.sort((a,b) => a.count < b.count) // TODO: typescript error
    return [sorted[0].group, sorted[1].group];
  })([...red, ...green, ...blue]);

  let result;

</script>

<main>
  <Header />
  {#if      page == 1}  <Welcome on:click={handleClick} />
  {:else if page == 2}  <WarmOrCool on:click={handleClick} bind:selected={warmCool} />
  {:else if page == 3}  <PickColors on:click={handleClick} bind:selected={red} colors={reds} />
  {:else if page == 4}  <PickColors on:click={handleClick} bind:selected={green} colors={greens} />
  {:else if page == 5}  <PickColors on:click={handleClick} bind:selected={blue} colors={blues} />
  {:else if page == 6}  <HairColor on:click={handleClick} bind:selected={hair} />
  {:else if page == 7}  <TrackSeparator on:click={handleClick} {topTwo} bind:topGroup={result}/>
  {:else if page == 8}  <Result on:click={handleClick} colorGroup={result} /> 
  {:else if page == 9}  <ColorHexagon on:click={handleClick} bind:selected={colorHexagon} />
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