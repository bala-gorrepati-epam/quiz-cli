# Project Overview

**Quiz CLI** is an interactive command-line quiz game built with Node.js. It lets users pick a quiz category, choose how many questions to answer, and then play through a shuffled set of multiple-choice questions.

The app is designed to be simple to run and easy to extend. It uses only built-in Node.js modules, so there are **no external dependencies** required.

## What it does
- Displays a welcome banner in the terminal
- Loads quiz questions from `data/questions.json`
- Lets the user choose a category
- Lets the user choose how many questions to answer
- Asks multiple-choice questions one by one
- Shows immediate feedback for each answer
- Displays a final score and review of incorrect answers
- Offers the option to play again

---

# Setup instructions

## Requirements
- **Node.js 18+**  
  The project uses modern ES modules and built-in `node:` APIs.

## Steps to run locally

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd quiz-cli
   ```

2. **Verify Node.js version**
   ```bash
   node --version
   ```
   Make sure it is **18.0.0 or newer**.

3. **Install dependencies**
   ```bash
   npm install
   ```
   > There are no third-party dependencies, but running `npm install` is still a common setup step and will prepare the project if a lockfile or future dependencies are added.

4. **Run the quiz**
   ```bash
   npm start
   ```
   This runs:
   ```bash
   node index.js
   ```

## Optional
- Run tests:
  ```bash
  npm test
  ```
  > The project currently defines a test script using Node’s built-in test runner, but no tests are included in the provided codebase.

---

# Usage examples

## 1. Start the quiz
**Input:** Run the app from the terminal with `npm start`  
**Output:** A colorful welcome banner appears, followed by category selection.

```bash
npm start
```

---

## 2. Choose a category
**Input:** Enter the number corresponding to a category shown in the menu.  
**Output:** The app loads the questions for that category.

Example terminal flow:
```text
Choose a category:

  1. JavaScript Basics
  2. Node.js
  3. Programming Concepts

Your choice (enter number):
```

---

## 3. Choose the number of questions
**Input:** Select one of the available count options, such as:
- All questions
- 3 questions
- 5 questions

**Output:** The quiz uses the selected number of questions from the chosen category.

The count options are automatically filtered based on how many questions are available in the selected category.

---

## 4. Answer quiz questions
**Input:** For each question, enter the number of the option you think is correct.  
**Output:** The app immediately tells you whether the answer was correct or incorrect and may show an explanation.

Example:
```text
What does `typeof null` return?

  1. "null"
  2. "object"
  3. "undefined"

Your choice (enter number): 2

✓ Correct!
💡 In JavaScript, `typeof null` is historically "object".
```

---

## 5. Review results
**Input:** None; this happens automatically after the last question.  
**Output:** A score summary is shown, including:
- category name
- number of correct answers
- percentage score
- performance message
- list of incorrect answers with correct responses

Example:
```text
📊 QUIZ RESULTS
Category: JavaScript Basics
Score: 4/5 (80%)

🌟 Great job! Well done!
```

---

## 6. Play again
**Input:** Answer `y` or `n` when asked whether you want to play again.  
**Output:** If yes, the quiz restarts; if no, the app exits with a thank-you message.

---

# File Structure

```text
.
├── index.js
├── package.json
└── src
    ├── colors.js
    ├── input.js
    └── quiz.js
```

## Notes
- `data/questions.json` is also required at runtime, even though it was omitted from the provided listing.
- The questions file is expected to contain quiz categories and question data.

---

# Any other info

## Technologies used
- **Node.js**
- **ES Modules**
- **Built-in `readline` module**
- **Built-in `fs/promises` module**
- **ANSI escape codes** for terminal colors

## Main features and how they work

### 1. Question loading
- **Where:** `index.js`
- **Input:** Reads `data/questions.json`
- **Output:** Parsed quiz data used by the application

### 2. Interactive terminal input
- **Where:** `src/input.js`
- **Input:** User keyboard input in the terminal
- **Output:** Clean helper functions for prompts, selections, confirmations, and press-enter pauses

### 3. Quiz game logic
- **Where:** `src/quiz.js`
- **Input:** Array of question objects and a category name
- **Output:** Shuffled questions, scoring, progress tracking, and final results

### 4. Colored terminal output
- **Where:** `src/colors.js`
- **Input:** Plain text strings
- **Output:** Styled terminal text such as success, error, info, and highlight messages

---

## Expected question data format

The app expects `data/questions.json` to provide categories with a structure similar to this:

```json
{
  "categories": {
    "javascript": {
      "name": "JavaScript",
      "questions": [
        {
          "question": "What does `typeof null` return?",
          "options": ["null", "object", "undefined"],
          "answer": 1,
          "explanation": "In JavaScript, `typeof null` is historically \"object\"."
        }
      ]
    }
  }
}
```

### Required fields per question
- `question` — the question text
- `options` — array of answer choices
- `answer` — index of the correct option
- `explanation` — optional helper text shown after answering

---

## Design details
- Questions are **shuffled** before the quiz starts.
- Progress is shown using a simple **text progress bar**.
- Incorrect answers are reviewed at the end of the quiz.
- The app uses a **single interactive loop**, allowing users to replay without restarting the process.

---

## Scripts

### Start the app
```bash
npm start
```

### Run tests
```bash
npm test
```

---

## License
This project is licensed under the **MIT License**.