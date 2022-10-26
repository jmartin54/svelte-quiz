<script lang="ts">
  import PageLayout from "./PageLayout.svelte";
  
  export let selected;

  function select(ev: MouseEvent) {
    selected = ev.target.getAttribute('data-value');
  }

  function selectKeyboard(){} // TODO: this

  let options = ['warm', 'cool', 'turkoise ± bc u always need more koolaid'];

</script>

<PageLayout on:click>
    <h1>Warm or cool</h1>

    {#each options as option}
      <div on:click={select} on:keypress={selectKeyboard} data-value={option}>
        {option}
      </div>
    {/each}

</PageLayout>