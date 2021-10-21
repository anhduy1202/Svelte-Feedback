<script lang="ts">
    import {FeedBackStore} from '../stores';
import FeedBackForm from './FeedBackForm.svelte';
  
    $: count = $FeedBackStore.length;
    $: average = $FeedBackStore.reduce((a,{rating}) => a + rating, 0) / count;
    $FeedBackStore.length
</script>

<div class="feedback-stats">
    <h4> {count} Reviews </h4>
    <h4> Rating Average: {average}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>