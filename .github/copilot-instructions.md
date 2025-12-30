# React BuzzFeed Quiz - AI Coding Guidelines

## Project Overview
This is a React TypeScript library for creating BuzzFeed-style personality quizzes. The main `BuzzFeedQuiz` component renders a sequence of questions, collects answers, and displays results based on the most frequent `resultID`.

## Architecture
- **Main Component**: `BuzzFeedQuiz.tsx` - Orchestrates the quiz flow using React Context for state management.
- **Data Flow**: Props-driven; questions and results arrays define quiz structure. Answers map to `resultID`s, with majority vote determining final result.
- **Components**: Modular structure in `src/components/` - `Question`, `Answers`, `Result`, `Byline`, `ShareButtons`.
- **Styling**: SCSS-based with BEM-like class naming (e.g., `rbq_question_overlap_text`).
- **Performance**: Components use `memo` to prevent unnecessary re-renders; `react-scroll` handles auto-scrolling.

## Key Patterns
- **Props Interfaces**: Strictly typed via TypeScript interfaces in `src/interfaces/`. All component props extend base interfaces.
- **Context Usage**: `QuizContext` provides `selectedAnswers` state and `scrollFunction` across components.
- **Result Calculation**: Frequency count of `resultID`s from selected answers determines outcome.
- **Image Handling**: Background images on questions/answers with optional attributions; text overlays use custom `TextFit` component.
- **Share Functionality**: Built-in Facebook/Twitter/Copy buttons in `Result` component.

## Development Workflow
- **Build**: `npm run build` runs webpack bundling + TypeScript declarations to `lib/`.
- **Example App**: `cd example && npm start` for local development/demo.
- **Dependencies**: Peer deps on React/React-DOM; bundles SCSS to `lib/styles.css`.
- **Testing**: No explicit test scripts; validate via example app.

## Conventions
- **File Structure**: Components in `src/components/`, interfaces in `src/interfaces/`, partials in `src/partials/`.
- **Naming**: PascalCase for components, camelCase for props/functions, kebab-case for SCSS classes.
- **Imports**: Absolute paths from `src/`, external libs first.
- **State Management**: Local `useState` for component state, Context for cross-component data.
- **Event Handling**: Callback props like `onAnswerSelection` for extensibility.

## Examples
- Add a question: `{ question: "What's your favorite color?", answers: [{ answer: "Blue", resultID: 0 }, { answer: "Red", resultID: 1 }] }`
- Customize styling: Pass `backgroundColor` and `fontColor` to questions/answers.
- Handle events: Use `onResult` to trigger actions when quiz completes.

Reference `src/BuzzFeedQuiz.tsx` for prop structure, `example/src/App.js` for usage patterns.