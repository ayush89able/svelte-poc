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
  $: currentItem = {}

  function deleteFeedback(e) {
    feedback = feedback.filter((feedback) => feedback.id!==e.detail)
  }

  function addFeedback(e) {
    if(!feedback.includes(e.detail.currentItem)) {
      feedback.push({
      id: feedback.length + 1,
      text: e.detail.text,
      rating: e.detail.rating
    })
    feedback = feedback
    } else {
      const updatedFeedback = feedback.map(obj =>
      obj.id === e.detail.currentItem.id ? { ...obj, text: e.detail.text, rating: e.detail.rating } : obj
      );
      feedback=updatedFeedback
    }
    
    
  }

  function editFeedback(e) {
    currentItem = feedback.find((fb) => fb.id === e.detail)
  }
</script>
<FeedbackForm on:add-feedback={addFeedback} {currentItem}/>
<FeedbackStats {count} {average} />
<FeedbackList {feedback} on:delete-feedback={deleteFeedback} on:edit-feedback={editFeedback} />