<script lang="ts">
  import FeedBackList from './components/FeedBackList.svelte';

  import type {FeedBack} from './IFeedBack';
 
  let feedback : FeedBack[] = [
	
	{
    id: 1,
    rating: 10,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  },
  {
    id: 2,
    rating: 9,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  },
  {
    id: 3,
    rating: 8,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  },
  ]

</script>

<main>
  <FeedBackList {feedback}/>

</main>

<style>
 
</style>
