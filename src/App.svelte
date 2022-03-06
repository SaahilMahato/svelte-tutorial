<script>
    import FeedbackList from './components/FeedbackList.svelte';
    import FeedbackStats from './components/FeedbackStats.svelte';
    import FeedbackForm from './components/FeedbackForm.svelte';
    
    let feedbacks = [
        {
            id: 1,
            rating: 5,
            text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque tempor in lacus eu fringilla. Proin in dictum enim. Phasellus tempus lacus quis interdum ultricies. Maecenas lacinia convallis eros eget tristique. Vivamus ut tristique urna. Nullam condimentum nulla fermentum bibendum dapibus.'
        },
        {
            id: 2,
            rating: 4,
            text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque tempor in lacus eu fringilla. Proin in dictum enim. Phasellus tempus lacus quis interdum ultricies. Maecenas lacinia convallis eros eget tristique. Vivamus ut tristique urna. Nullam condimentum nulla fermentum bibendum dapibus.'
        },
        {
            id: 3,
            rating: 3,
            text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque tempor in lacus eu fringilla. Proin in dictum enim. Phasellus tempus lacus quis interdum ultricies. Maecenas lacinia convallis eros eget tristique. Vivamus ut tristique urna. Nullam condimentum nulla fermentum bibendum dapibus.'
        }
    ];

    $: numberOfFeedbacks = feedbacks.length;
    $: averageRating = feedbacks.reduce((a, {rating}) => a + rating, 0) / feedbacks.length;

    const deleteFeedback = (e) => {
        const feedbackId = e.detail;
        feedbacks = feedbacks.filter(feedback =>
            feedback.id !== feedbackId
        );
    }

    const addNewFeedback = (e) => {
        const newFeedback = e.detail;
        newFeedback['id'] = feedbacks.length + 1;
        feedbacks = [newFeedback, ...feedbacks];
    }
</script>

<main class="container">
    <FeedbackForm 
        on:add-new-feedback={addNewFeedback}
    />
    <FeedbackStats
        {numberOfFeedbacks}
        {averageRating}
    />
    <FeedbackList
        {feedbacks}
        on:delete-feedback={deleteFeedback}
    />
</main>
