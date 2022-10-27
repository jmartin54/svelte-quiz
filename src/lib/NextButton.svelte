<button on:click>
    <slot></slot>
</button>

<style>
    button {
        display: inline-block;
        border: none;
        padding: 1rem 2rem;
        margin: 0;
        text-decoration: none;
        background: var(--color-dark);
        color: var(--color-light);
        font-family: sans-serif;
        font-size: 1rem;
        cursor: pointer;
        text-align: center;
        transition: background 250ms ease-in-out, 
                    transform 150ms ease;
        -webkit-appearance: none;
        -moz-appearance: none;
    }

    button:hover,
    button:focus {
        background: var(--color-dark-200);
    }

    button:focus {
        outline: 1px solid var(--color-light);
        outline-offset: -4px;
    }

    button:active {
        transform: scale(0.99);
    }
</style>