# Project Overview

**quiz-cli** is an interactive command-line quiz game built with Node.js. It loads quiz questions from a JSON file, lets the player choose a category and number of questions, then runs a timed-free question loop with colored terminal output and a final score summary.

It is designed as a learning tool for JavaScript and a simple example of building a structured CLI application with modular input handling, quiz logic, and terminal styling.

# Features

- **Interactive CLI experience**  
  Prompts the user in the terminal, shows a welcome banner, and guides the player through the quiz flow.

- **Category and question count selection**  
  The player chooses a quiz category and how many questions to answer.

- **Shuffled question order**  
  Questions are randomized before the quiz starts.

- **Score tracking and progress display**  
  Shows current progress, tracks correct answers, and calculates the final score percentage.

- **Results review**  
  Displays a performance message and reviews incorrect answers at the end.

- **Colored terminal output**  
  Uses reusable ANSI color helpers for success, errors, warnings, info, and highlights.

- **Replay support**  
  After finishing, the player can choose to play again or exit.

# Requirements

- **Node.js 18 or newer**
- Terminal/console environment that supports standard readline input and ANSI colors

# Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd quiz-cli
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

   > The project has no external runtime dependencies, but running `npm install` keeps the environment consistent and prepares the lockfile if needed.

# Usage

## Start the quiz
```bash
npm start
```

or run directly:

```bash
node index.js
```

## Run tests
```bash
npm test
```

# Controls / Workflow

1. Launch the app.
2. Read the welcome banner.
3. Select a **category** from the available quiz data.
4. Choose how many questions to answer.
5. Answer each question in the terminal.
6. View your score and incorrect answers review.
7. Choose whether to **play again** or exit.

### Input style
- Uses interactive prompts for selections and confirmations.
- Press **Enter** when prompted.
- Answers are entered as text in the terminal.

# Project Structure

```text
quiz-cli/
├─ index.js
├─ package.json
├─ data/
│  └─ questions.json
└─ src/
   ├─ colors.js
   ├─ input.js
   └─ quiz.js
```

## Key files

- **`index.js`** — Application entry point; loads questions, handles the main game loop, and coordinates input/output.
- **`data/questions.json`** — Quiz question source data.
- **`src/input.js`** — Centralized CLI input helpers using `readline`.
- **`src/quiz.js`** — Core quiz logic, scoring, progress, and results rendering.
- **`src/colors.js`** — ANSI color utility helpers for terminal output.

# Scripts

Defined in `package.json`:

- **`npm start`** → `node index.js`
- **`npm test`** → `node --test`

# Additional Info

- **Type:** ES Modules (`"type": "module"`)
- **Main entry:** `index.js`
- **Package name:** `quiz-cli`
- **Version:** `1.0.0`
- **Description:** Interactive command-line quiz game for learning JavaScript
- **License:** MIT
- **Keywords:** CLI, quiz, game, educational