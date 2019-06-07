<style>
    button {
        font: inherit;
        padding: 0.15rem 0.5rem;
        background: rgb(184, 15, 128);
        border: 1px solid rgb(184, 15, 128);
        color: white;
    }
    button:hover,
    button:active {
        box-shadow: 1px 1px 6px rgba(0,0,0,0.26)
    }
</style>

<button on:click>
<slot />
</button>