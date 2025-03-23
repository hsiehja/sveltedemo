# Svelte Demo: Trivia Game

To run:
```bash
npm install
npm run dev
```

Go to: http://localhost:5173/

## Complete the following tasks:

### 1. Add 2 new trivia questions
**File:** `src/questions.js`  
- Add two more question objects to the existing array.

---

### 2. Show a final score when the game ends  
**File:** `src/App.svelte`  
- Add a new variable called `score`  
- Inside the `handleAnswer()` function, compare the selected choice with the correct answer  
- If it's correct, increment the score  
- When the game ends, show the final score below the message

---

### 3. Add a “Player Name” input  
**File:** `src/App.svelte`  
- Show an <input> element that asks the player to enter their name before the game begins
- Use two-way binding (bind:value) to track the name
- Start the game when the user presses Enter, and hide the input
- Use the player's name to personalize the final score screen

---

### 4. Add a “Play Again” button (optional)
**File:** `src/App.svelte`  
- Add a button that appears when the game ends  
- When clicked, reset `current`, `score`, and `showScore` to their initial values to restart the game

---

### 4. Add a timer (optional)
**File:** `src/App.svelte`  
- Add a countdown timer that resets with each new question  
- Automatically skip to the next question if time runs out

---

### 6. Add animations on correct/incorrect answers (optional)
**Files:** `src/App.svelte`, `src/Question.svelte`  
- Use Svelte's built-in `transition` or `animate` features to add visual feedback  
- For example: show a flash of green for a correct answer, or red for an incorrect one  
- You could also disable buttons briefly and show a short animation before moving to the next question
