<script lang="ts">
	import NextButton from './../lib/NextButton.svelte';
</script>

<div class="container">
    <h1>Let's Begin!</h1>
    <p>
        Let your instincts guide you. If you have used any other color system, don’t let that influence your answers.
    </p>
    <div class="button-container">
        <NextButton on:click>Start Quiz</NextButton>
    </div>
</div>


<style>

    .container {
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 1vh;
    }

    .button-container {
        align-self: flex-end;
    }
</style>