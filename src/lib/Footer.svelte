
<script lang="ts">
    export let page;
    export let outOf;
</script>

<div class="footer">
    <div class="label-dark">
        {page} / {outOf}
    </div>
    <div 
        class="background"
        style:width={page / outOf * 100 + 'vw'}
    >
        <div class="background-inner">
            {page} / {outOf}
        </div>
    </div>
</div>

<style>
    .footer {
        position: relative;
        border-top: 0.5vh solid var(--color-dark);
        height: 5vh;
        line-height: 5vh;
        padding: 0;
        margin: 0;
    }
    
    .label-dark {
        height: 5vh;
        color: var(--color-dark);
        text-align: center;
    }

    .background {
        height: 5vh;
        background-color: var(--color-dark);
        position: relative;
        top: -5vh;
        overflow: hidden;
        transition: width 0.3s ease-out;
    }

    .background-inner {
        width: 100vw;
        color: var(--color-light);
        text-align: center;
    }
</style>