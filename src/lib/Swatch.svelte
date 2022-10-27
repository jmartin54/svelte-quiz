<div 
    style:background={$$props.color} 
    style:height={$$props.height} 
    style:transform={$$props.circle? "rotate(-5deg) scale(0.75)" : ""}
    on:click
    on:keypress>
</div>

<style>
    div {
        display: flex;
        flex: 1;
        margin: 0.1vw;
        border-radius: 1vw;
        transition: transform 400ms ease-out;
    }
</style>