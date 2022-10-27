<script lang="ts">
  import { onMount } from "svelte";
import PageLayout from "./PageLayout.svelte";

export let selected = [0,0];
// https://www.researchgate.net/figure/A-range-of-results-using-our-model-with-varying-mixtures-of-eumelanin-and-pheomelanin_fig14_220506677
// https://icolorpalette.com/color/real-brown
const  browns = [
    0xfaf8f6, 0xf2ebe6,
    0xe9ded6, 0xe1d1c6,
    0xd9c4b6, 0xd0b7a6,
    0xc8a996, 0xbf9c86,
    0xb78f76, 0xaf8266,
    0xa67556, 0x956a4e,
    0x855e46, 0x75533d,
    0x654835, 0x553c2c,
    0x453124, 0x35251c,
    0x251a13, 0x0a0705,
]

function setBrown(ev) {
    const index = (ev.target as HTMLInputElement).value;
    selected = [browns[index], selected[1]];
}

// https://icolorpalette.com/color/red
const reds = [
    0xfff2f2, 0xfedada,
    0xfec1c1, 0xffa9a9,
    0xff9090, 0xff7878,
    0xff5f5f, 0xff4747,
    0xff2e2e, 0xff1616,
    0xfc0000, 0xe40000,
    0xcc0000, 0xb30000,
    0x9b0000, 0x820000,
    0x6a0000, 0x510000,
    0x390000, 0x100000,
]
function setRed(ev) {
    const index = (ev.target as HTMLInputElement).value;
    selected = [selected[0], reds[index]]
}

let hairColor;
$: {
    let mix = Math.max(selected[0] & 0xff0000, selected[1] & 0xff0000)
        + Math.max(selected[0] & 0x00ff00, selected[1] & 0x00ff00)
        + Math.max(selected[0] & 0x0000ff, selected[1] & 0x0000ff);
    hairColor = `#${mix.toString(16)}`;
}

onMount(()=>{
    const bi = Math.floor(browns.length / 2)
    const ri = reds.length - 1;
    selected = [browns[bi], reds[ri]];
})

</script>

<PageLayout on:click>
    <h1>What color is your hair?</h1>
    <div class="hairColor" style:background={hairColor}></div>
    <div>
        brown:
        <input type="range" min="0" max={browns.length - 1} value={Math.floor(reds.length/2)} on:input={setBrown} />    
        red:
        <input type="range" min="0" max={reds.length - 1} value={reds.length - 1} on:input={setRed}/>
    </div>
</PageLayout>

<style>
    .hairColor {
        flex-grow: 1;
    }
    input[type='range'] {
        width: 100%;
    }
</style>