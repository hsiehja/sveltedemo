<!--
  App.svelte

  This is the main component of the trivia game.
  It manages the game state (question index, score, player name, etc.)
  and renders either the next question or a final score screen.
-->

<script>
  import { questions } from './questions.js';
  import Question from './Question.svelte';

  let current = 0;
  let showScore = false;

  // TODO 🍌 (Step 2): Add a new variable to track score
  // TODO 🍌 (Step 3): Add a variable for the player's name
  // TODO 🍌 (Step 5): Add a variable to track time remaining
  // TODO 🍌 (Step 5): Add logic to start and update a countdown timer

  function handleAnswer(choice) {
    // TODO 🍌 (Step 2): Track score by comparing selected answer
    // TODO 🍌 (Step 5): Stop the timer when an answer is given

    current++;
    if (current >= questions.length) {
      showScore = true;
    } else {
      // TODO 🍌 (Step 5): Restart timer for next question
    }
  }

  // TODO 🍌 (Step 4): Create a function to reset the game state for "Play Again"
  // TODO 🍌 (Step 3): Create a function to start the game once name is entered
</script>

<h1>Trivia!</h1>

<!-- TODO 🍌 (Step 3): Show an input field for player name before the game starts -->
<!-- TODO 🍌 (Step 3): When the user presses Enter, start the game and hide the input -->

{#if showScore}
  <!-- TODO 🍌 (Step 2): Show final score here -->
  <!-- TODO 🍌 (Step 3): Personalize message with player name -->
  <p>You've completed the game!</p>

  <!-- TODO 🍌 (Step 4): Add a “Play Again” button here -->
{:else}
  <!-- TODO 🍌 (Step 5): Show countdown timer here -->
  <Question
    question={questions[current].question}
    choices={questions[current].choices}
    onAnswer={handleAnswer}
  />
{/if}

<!-- TODO 🍌 (Step 6): Add styles/animations to highlight correct/incorrect answers -->
