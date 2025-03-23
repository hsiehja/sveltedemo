<!--
  Question.svelte

  Solution version with optional animation support.
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

<style>
  /* Optional 🐵: Add animations or transitions here */
</style>
