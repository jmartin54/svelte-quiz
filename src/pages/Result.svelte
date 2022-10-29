<script>
  import HStack from "../lib/HStack.svelte";
  import { best_colors } from "../assets/theme/best_colors";
  import Swatch from "../lib/Swatch.svelte";
  import PageLayout from "./PageLayout.svelte";
  import VStack from "../lib/VStack.svelte";
  import NextButton from "../lib/NextButton.svelte";
  import Space from "../lib/Space.svelte";

    export let colorGroup;

    function enterEmail(){
    }
    function openToBooklet(){
        window.open('https://mycolorcode.com/collections/red-orange-clothing/products/blue-purple-color-booklet')
    }

    function openToClothes(){
        window.open(`https://mycolorcode.com/collections/${colorGroup.replace("_","-")}-clothing`)
    }
</script>
<PageLayout on:click disableNext={true}>
    <h1>Your color group is {colorGroup.replace('_', ' ')}!</h1>
    <VStack>
        <HStack>
            {#each best_colors[colorGroup] as color}
                <Swatch {color} />
            {/each}
        </HStack>

        <p>Some of your best colors are shown above</p>
        <!-- <NextButton on:click={enterEmail}>Email me the results</NextButton> -->
        <Space />
        <NextButton on:click={openToBooklet}>Get a booklet with all your best colors</NextButton>
        <Space />
        <NextButton on:click={openToClothes}>Shop clothes in your colors</NextButton>
    </VStack>
</PageLayout>