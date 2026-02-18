# Specification: NJAIO Pilot Interactive Quiz

## 1. Overview
The goal is to create an interactive MCQ quiz for the NJAIO Pilot program. The source content is a text file containing 100 questions. We need to process this content, enrich it with metadata (correct answers, explanations, topics), and present it in a user-friendly web interface.

## 2. Input Data
- **Questions Source**: `pilot/ijaio26pilot.txt`
  - Format: 5 lines per question (Line 1: Question, Lines 2-5: Options).
  - Total: 100 questions.
- **Topics Source**: `pilot/topics.txt`
  - Hierarchical list of Topics and Subtopics (e.g., Mathematics > Calculus).

## 3. Data Processing Requirements
We need to convert the raw text into a structured JSON file (`pilot/ijaio26pilot.json`).
For each of the 100 questions, the following processing steps are required:
1.  **Parsing**: Extract the question text and the 4 options.
2.  **Solution Identification**: Determine which of the 4 options is the correct answer.
3.  **Feedback Generation**:
    -   Generate a concise explanation for why the correct answer is correct.
    -   Generate a concise explanation for why the incorrect options are incorrect (or a general explanation of the concept).
    -   *Target Audience*: High school students.
4.  **Classification**: Assign the most appropriate Topic and Subtopic from `topics.txt`.

## 4. Output Data Format (`ijaio26pilot.json`)
```json
[
  {
    "id": 1,
    "question": "Question text...",
    "options": ["Option A", "Option B", "Option C", "Option D"],
    "correctAnswerIndex": 0, // 0-3
    "explanation": "Concise explanation...",
    "topic": "Mathematics",
    "subtopic": "Linear Algebra"
  },
  ...
]
```

## 5. Frontend Application (`pilot/quiz.html`)
An interactive HTML page to administer the quiz.

### Functional Requirements
1.  **Loading**: Load questions from `ijaio26pilot.json`.
2.  **Display**: Show one question at a time.
3.  **Interaction**:
    -   User clicks an option.
    -   **Visual Feedback**:
        -   Correct selection: Highlight option with a Green bounding box.
        -   Incorrect selection: Highlight selected option with a Red bounding box AND highlight the correct option with Green.
    -   **Text Feedback**: Display the explanation text below the options after selection.
4.  **Navigation**:
    -   "Previous" and "Next" buttons to traverse questions.
    -   Disable "Previous" on first question, "Next" on last.
5.  **Reset**: A button to reset the current quiz state (clear selection) or restart the whole quiz (user choice, simple reset of current question is minimum). *Clarification: Requirement says "have a reset button have the user try again". likely means reset the specific question or the whole quiz. We will implement "Reset Quiz" and maybe "Try Again" for a question is not standard if answer is revealed. Let's assume "Reset Quiz" clears all progress, or just a "Restart" button.*
    -   *Refinement*: "try again" usually implies re-attempting. But if we show the answer immediately, re-attempting is trivial. We will implement a "Reset Quiz" to clear all answers.

### UI/UX Requirements
-   Clean, modern interface suitable for students.
-   Clear distinction between question, options, and controls.
-   Responsive design.
