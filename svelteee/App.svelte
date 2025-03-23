<!--
  App.svelte

  Solution version.
  This version includes score tracking, player name input (before game starts),
  a play again button, a timer, and basic animation hooks.
-->

<script>
  import { questions } from '../src/questions.js';
  import Question from '../src/Question.svelte';
  import { onMount } from 'svelte';

  let current = 0;
  let score = 0; // 🐵 Added: score tracking
  let showScore = false;
  let showNameInput = true; // 🐵 Added: name input
  let playerName = ""; // 🐵 Added: two-way bound player name

  let timeLeft = 10; // 🐵 Added: countdown timer
  let timer;

  function startTimer() {
    clearInterval(timer);
    timeLeft = 10;
    timer = setInterval(() => {
      timeLeft--;
      if (timeLeft === 0) {
        handleAnswer(null); // treat as skipped
      }
    }, 1000);
  }

  function handleAnswer(choice) {
    clearInterval(timer);

    // 🐵 Added: score tracking logic
    if (choice === questions[current]?.answer) {
      score++;
    }

    current++;
    if (current >= questions.length) {
      showScore = true;
    } else {
      startTimer(); // 🐵 Restart timer for next question
    }
  }

  function resetGame() {
    current = 0;
    score = 0;
    showScore = false;
    showNameInput = true; // 🐵 Reset name input display
    playerName = "";
  }

  function startGame() {
    showNameInput = false; // 🐵 Hide name input
    startTimer(); // 🐵 Start timer after name is entered
  }

  onMount(() => {
    // 🐵 Wait for name input before starting game
  });
</script>

<h1>Trivia!</h1>

{#if showNameInput}
  <!-- 🐵 Added: Player name input before game starts -->
  <label>
    Enter your name:
    <input bind:value={playerName} on:keydown={(e) => e.key === 'Enter' && startGame()} />
  </label>
{:else if showScore}
  <p>{playerName}, you scored {score} out of {questions.length}!</p>

  <!-- 🐵 Added: Play again button -->
  <button on:click={resetGame}>Play Again</button>
{:else}
  <p>Time left: {timeLeft}s</p>
  <Question
    question={questions[current].question}
    choices={questions[current].choices}
    onAnswer={handleAnswer}
  />
{/if}
