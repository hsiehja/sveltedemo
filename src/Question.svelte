<!--
  Question.svelte

  A reusable component that displays a single trivia question and a list of answer buttons. 
  It calls `onAnswer()` when a choice is selected.
-->

<script>
  export let question;
  export let choices;
  export let onAnswer;
</script>

<h2>{question}</h2>
{#each choices as choice}
  <button on:click={() => onAnswer(choice)}>
    {choice}
  </button>
{/each}
