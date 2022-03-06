<script>
    import {createEventDispatcher} from 'svelte';
    import Card from './Card.svelte';

    export let feedback = {};

    const dispatch = createEventDispatcher()

    const handleDelete = (feedbackId) => {
        dispatch('delete-feedback', feedbackId);
    }
</script>

<Card>
    <div class="num-display">
        {feedback.rating}
    </div>
    <button class="close" on:click={() => handleDelete(feedback.id)}>X</button>
    <div class="text-display">
        {feedback.text}
    </div>
</Card>

<style>
    .num-display {
        position: absolute;
        top: -10px;
        left: -10px;
        width: 30px;
        height: 30px;
        background: #FF6A95;
        color: #FFFFFF;
        border: 1px #EEEEEE solid;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 19px;
    }

    .close {
        position: absolute;
        top: 10px;
        right: 20px;
        cursor: pointer;
        background: none;
        border: none;
    }
</style>