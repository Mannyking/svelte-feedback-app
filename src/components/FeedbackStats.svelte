<script>
  import {FeedbackStore} from '../stores'

  const handleNaN = function(value) {
    if(Number.isNaN(value)) {
      return 0
    }
    else {
      return value;
    }
  }
  
  $: count = $FeedbackStore.length
  $: average = handleNaN($FeedbackStore.reduce((a, {rating}) => a + rating, 0) / $FeedbackStore.length)
</script>

<div class="feedback-stats">
  <h4>{count} Reviews</h4>
  <h4>Ratings Average: {average}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>