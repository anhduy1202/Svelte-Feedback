<script lang="ts">
  import { v4 as uuidv4 } from "uuid";
  import {FeedBackStore} from "../stores";
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  import RatingSelect from "./RatingSelect.svelte";
 
 
  let text = "";
  let btnDisabled: boolean = true;
  let rating: number | string = 10;
  let message: string;

  const handleSelect = (e) => (rating = e.detail);

  const handleInput = () => {
    if (text.trim().length <= 10) {
      message = "Text must be at least 10 characters";
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };
  const handleSubmit = () => {
    if (text.trim().length > 10) {
      const newFeedBack = {
        id: uuidv4(), //random ID
        text,
        rating: +rating, //turn string into number
      };
        FeedBackStore.update((currentFeedback)=> {
            return [newFeedBack, ...currentFeedback];
        })

        text = '';
    }
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <Card>
    <header>
      <h2>How was your experience?</h2>
    </header>
    <RatingSelect on:rating-select={handleSelect} />
    <div class="input-group">
      <input
        on:input={handleInput}
        type="text"
        bind:value={text}
        placeholder="Provide us some feedbacks"
      />
      <Button disabled={btnDisabled} type="submit">Submit</Button>
    </div>
  </Card>
</form>

{#if message}
  <div class="message">
    {message}
  </div>
{/if}

<style>
  header {
    max-width: 400px;
    margin: auto;
  }
  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }
  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }
  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }
  input:focus {
    outline: none;
  }
  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
