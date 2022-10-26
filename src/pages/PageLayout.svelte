<script lang="ts">
	import NextButton from './../lib/NextButton.svelte';
</script>

<div class="container">
    <slot></slot>
    <div class="button-container">
        <NextButton on:click>
            <slot name="buttonTitle">
                <slot name="missing">Next</slot>
            </slot>
        </NextButton>
    </div>
</div>


<style>

    .container {
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        padding: 1vh;
    }

    .button-container {
        align-self: flex-end;
    }
</style>