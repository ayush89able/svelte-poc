<script>
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from './components/FeedbackStats.svelte';
  import FeedbackForm from './components/FeedbackForm.svelte';
  let feedback = [
    {
      id: 1,
      rating: 10,
      text: 'Awsome and best'
    },
    {
      id: 2,
      rating: 8,
      text: 'Good one'
    }
  ]

  $: count = feedback.length
  $: average = feedback.reduce((acc, { rating }) => acc + rating ,0) / count

  function deleteFeedback(e) {
    feedback = feedback.filter((feedback) => feedback.id!==e.detail)
  }
</script>
<FeedbackForm />
<FeedbackStats {count} {average} />
<FeedbackList {feedback} on:delete-feedback={deleteFeedback}/>