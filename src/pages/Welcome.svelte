<script lang="ts">
	import PageLayout from './PageLayout.svelte';
	import NextButton from './../lib/NextButton.svelte';
</script>

<PageLayout on:click>
    <h1>Let's Begin!</h1>
    <p>
        Let your instincts guide you. If you have used any other color system, don’t let that influence your answers.
    </p>
    <span slot="buttonTitle">Start Quiz</span>
</PageLayout>