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
