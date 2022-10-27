<script lang="ts">
	import VStack from '../lib/VStack.svelte';
    import NextButton from './../lib/NextButton.svelte';

    export let disableNext = false;
</script>

<div class="page">
    <VStack class="container">
        <slot></slot>
        <div class="button-container">
            {#if !disableNext}
                <NextButton on:click>
                    <slot name="buttonTitle">
                        <slot name="missing">Next</slot>
                    </slot>
                </NextButton>
            {/if}
        </div>
    </VStack>
</div>


<style>

    .page {
        display: flex;
        flex-direction: column;
        flex-grow: 1;
        padding: 5vh;
    }

    .page :global(.container) {
        justify-content: space-between;
    }

    .button-container {
        align-self: flex-end;
    }

</style>