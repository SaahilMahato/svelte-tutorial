<script>
    export let style = 'primary';
    export let type = 'button';
    export let disabled = false;
</script>

<button {type} {disabled} class={style}>
    <slot></slot>
</button>

<style>
    button {
        color: #FFFFFF;
        border: 0;
        border-radius: 8px;
        color: #FFFFFF;
        width: 100px;
        height: 40px;
        cursor: pointer;
    }

    .primary {
        background-color: #202142;
    }

    .secondary {
        background-color: #FF6A95;
    }

    button:hover {
        transform: scale(0.98);
        opacity: 0.9;
    }

    button:disabled {
        background-color: #CCCCCC;
        color: #333333;
        cursor: auto;
    }

    button:disabled:hover {
        transform: scale(1);
        opacity: 1;
    }
</style>