<script>
    export let numberOfFeedbacks = 0;
    export let averageRating = 0;
</script>

<div class="feedback-stats">
    <h4>{numberOfFeedbacks} reviews</h4>
    <h4>Ratings Average: {averageRating}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
    }
</style>