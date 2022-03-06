<script>
    import Card from './Card.svelte';
    import Button from './Button.svelte';
    import RatingSelect from './RatingSelect.svelte';
    import {createEventDispatcher} from 'svelte';

    let text = '';
    let btnDisabled = true;
    let min = 10;
    let message;
    let rating = 5;

    const dispatch = createEventDispatcher();

    const handleInput = () => {
        if (text.trim().length <= min && text.trim().length >= 1) {
            message = `Text must be at least ${min} characters`;
            btnDisabled = true;
        }
        else {
            message = '';
            btnDisabled = false;
        }

    }

    const handleSelect = e => {
        rating = e.detail;
    }

    const handleSubmit = () => {
        if (text.trim().length > min) {
            const newFeedback = {
                text,
                rating: +rating
            }

            dispatch('add-new-feedback', newFeedback);
        }
    }
</script>

<Card>
    <header>
        <h2>How would you rate our service?</h2>
    </header>
    <form on:submit|preventDefault={handleSubmit}>
        <RatingSelect 
            on:rating-select={handleSelect}
        />
        <div class="input-group">
            <input 
                type="text" 
                placeholder="Tell us something that keeps you coming back"
                bind:value = {text}
                on:input={handleInput}
            />
            <Button
                type="submit"
                disabled={btnDisabled}
            >
            Send
            </Button>
        </div>
        {#if message}
                <div class="message">
                    {message}
                </div>
        {/if}
    </form>
</Card>

<style>
    header {
        max-width: 400px;
        margin: auto;
    }

    header h2 {
        font-size: 22px;
        font-weight: 600;
        text-align: center;
    }

    .input-group {
        display: flex;
        flex-direction: row;
        border: 1px solid #CCCCCC;
        padding: 8px 10px;
        border-radius: 8px;
        margin-top: 15px;
    }

    input {
        flex-grow: 2;
        border: none;
        font-size: 16px;
    }

    input:focus {
        outline: none;
    }

    .message {
        padding-top: 10px;
        text-align: center;
        color: rebeccapurple;
    }
</style>