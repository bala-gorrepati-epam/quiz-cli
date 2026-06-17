# Quiz CLI

**Quiz CLI** is an interactive command-line quiz game built with modern Node.js.  
It lets users choose a quiz category, decide how many questions to answer, and then play through a multiple-choice quiz with colored terminal output, progress tracking, score summaries, and answer review.

The project is designed as a learning/demo app and showcases:

- ES Modules (`import` / `export`)
- `async` / `await`
- Node.js built-in APIs (`readline`, `fs/promises`)
- Object-oriented programming with a `Quiz` class
- ANSI terminal colors without external dependencies
- Array methods, destructuring, and template literals
- Basic error handling and CLI UX patterns

---

# Setup instructions

## Prerequisites

- **Node.js 18 or newer**
- A terminal that supports ANSI colors
- A quiz dataset file at `data/questions.json`

## Install

This project has **no external npm dependencies**, so there is nothing to install beyond having Node.js available.

If you want to initialize anyway:

```bash
npm install
```

> This will only create a lockfile if needed; there are no runtime packages listed in `package.json`.

## Run the quiz

From the project root:

```bash
npm start
```

Or directly:

```bash
node index.js
```

Because `index.js` includes a shebang (`#!/usr/bin/env node`), it can also be run as an executable in environments where it has execute permissions.

## Required quiz data file

The app expects this file to exist:

```text
data/questions.json
```

The file is not included in the repository structure provided, but the application will fail without it.

Expected structure:

```json
{
  "categories": {
    "javascript": {
      "name": "JavaScript Basics",
      "questions": [
        {
          "question": "Which keyword declares a block-scoped variable?",
          "options": ["var", "let", "function", "const"],
          "answer": 1,
          "explanation": "let declares a block-scoped variable."
        }
      ]
    }
  }
}
```

### Data format rules

- `categories` must be an object
- Each category key maps to:
  - `name` — display name
  - `questions` — array of question objects
- Each question object should contain:
  - `question` — the prompt text
  - `options` — array of answer choices
  - `answer` — zero-based index of the correct option
  - `explanation` — optional short explanation shown after answering

---

# Usage examples

## Feature 1: Start the quiz game

**What it does:**  
Launches the CLI app, loads quiz questions, and displays the welcome banner.

**Input:**  
No command-line arguments. User interaction happens through terminal prompts.

**Output:**  
A colored welcome screen and category selection menu.

**How it works:**

```bash
npm start
```

---

## Feature 2: Choose a quiz category

**What it does:**  
Shows a list of available categories from `data/questions.json`.

**Input:**  
The user enters the number corresponding to a category.

**Output:**  
The selected category is used to build the quiz session.

**Example flow:**

```text
Choose a category:

  1. JavaScript Basics
  2. Node.js
  3. General Programming
```

---

## Feature 3: Choose quiz length

**What it does:**  
Lets the user choose how many questions to answer.

**Input:**  
One of the available options:
- All questions
- 3 questions
- 5 questions

**Output:**  
The quiz is limited to the chosen number of questions.

**Notes:**  
The shorter quiz options only appear when the selected category has enough questions.

---

## Feature 4: Answer multiple-choice questions

**What it does:**  
Displays one question at a time with numbered options.

**Input:**  
The user selects an option by entering its number.

**Output:**  
The app tells the user whether the answer is correct and optionally shows an explanation.

**Example interaction:**

```text
Which keyword declares a block-scoped variable?

  1. var
  2. let
  3. function
  4. const

Your choice (enter number): 2

✓ Correct!
💡 let declares a block-scoped variable.
```

---

## Feature 5: Progress tracking

**What it does:**  
Shows a progress bar and question count while the quiz is running.

**Input:**  
The current quiz state maintained by the `Quiz` class.

**Output:**  
A visual progress indicator like:

```text
[██████░░░░░░░░░░░░░░░░░░░░░░] 50%
Question 2 of 4
```

---

## Feature 6: Score summary and performance feedback

**What it does:**  
After all questions are answered, the app displays the final score and a performance message.

**Input:**  
The recorded answers from the current quiz session.

**Output:**  
A results screen with:
- category name
- score
- percentage
- motivational message
- review of incorrect answers

**Example output:**

```text
📊 QUIZ RESULTS
Category: JavaScript Basics
Score: 4/5 (80%)

🌟 Great job! Well done!
```

---

## Feature 7: Review incorrect answers

**What it does:**  
Lists questions answered incorrectly and shows both the selected answer and the correct answer.

**Input:**  
Stored answer history from the quiz session.

**Output:**  
A review section to help the user learn from mistakes.

**Example output:**

```text
📝 Review these questions:

1. Which method converts JSON into an object?
   Your answer: JSON.stringify()
   Correct: JSON.parse()
```

---

## Feature 8: Play again

**What it does:**  
After results are shown, the user is asked if they want to start over.

**Input:**  
A yes/no response (`y` or `n`).

**Output:**  
- `y` → returns to category selection
- `n` → exits with a goodbye message

**Example:**

```text
Would you like to play again? (y/n):
```

---

# File Structure

```text
quiz-cli/
├─ index.js
├─ package.json
└─ src/
   ├─ colors.js
   ├─ input.js
   └─ quiz.js
```

## File descriptions

- **index.js**  
  Main entry point. Loads quiz data, handles the game loop, and coordinates category selection, question flow, and replay prompts.

- **package.json**  
  Project metadata, Node.js engine requirement, and npm scripts.

- **src/colors.js**  
  ANSI color helper utilities for formatted terminal output.

- **src/input.js**  
  Readline-based terminal input helpers for prompting, selecting options, confirming actions, and waiting for Enter.

- **src/quiz.js**  
  Core quiz logic, including shuffling questions, asking questions, tracking score, rendering progress, and displaying results.

---

# Any other info

## Technologies used

- **Node.js**
- **ES Modules**
- **Built-in `readline` module**
- **Built-in `fs/promises` module**
- **ANSI escape codes for terminal styling**

## Key implementation details

- The app uses a **Fisher-Yates shuffle** to randomize questions each session.
- Quiz progress is shown using a simple text-based progress bar.
- Incorrect answers are stored and shown again at the end for learning/review.
- The app uses only built-in Node.js modules, so it remains lightweight and dependency-free.

## Scripts

```json
{
  "start": "node index.js",
  "test": "node --test"
}
```

> Note: no test files were included in the provided repository content, so `npm test` may not do anything until tests are added.

## Environment requirement

The `package.json` file specifies:

```json
"engines": {
  "node": ">=18.0.0"
}
```

So you should use **Node.js 18+** to run the project reliably.

## Error handling

If something goes wrong while loading data or running the quiz, the app:

- prints a colored error message
- prints the stack trace
- exits with a non-zero status code

## Missing data file warning

The app references:

```text
data/questions.json
```

If that file is missing or malformed, the quiz will not start.
