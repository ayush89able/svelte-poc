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

  function addFeedback(e) {
    feedback.push({
      id: feedback.length + 1,
      text: e.detail.text,
      rating: e.detail.rating
    })
    feedback = feedback
  }

  function editFeedback(e) {
    console.log(e.detail)
    let currentItem = feedback.find((fb) => fb.id === e.detail)
    console.log(currentItem)
  }
</script>
<FeedbackForm on:add-feedback={addFeedback}/>
<FeedbackStats {count} {average} />
<FeedbackList {feedback} on:delete-feedback={deleteFeedback} on:edit-feedback={editFeedback} />