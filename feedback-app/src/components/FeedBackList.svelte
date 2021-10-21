<script lang="ts">
  import { FeedBackStore } from "../stores";
  import { fade, scale } from "svelte/transition";
  import type { FeedBack } from "../IFeedBack";
  import FeedBackItem from "./FeedBackItem.svelte";
  //import { onDestroy, onMount } from "svelte";
  let feedback: FeedBack[] = [];

  //Get data from stores.ts
  /*const unsub = FeedBackStore.subscribe((data) => {
    feedback = data;
  });
  //Similar to useEffect
  onMount(()=> {
    
  })
  onDestroy(()=> {
    unsub();
  })*/
</script>

{#each $FeedBackStore as fb (fb.id)}
  <div in:scale out:fade>
    <FeedBackItem item={fb}/>
  </div>
{/each}
