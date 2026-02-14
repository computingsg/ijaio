# Checklist: NJAIO Pilot Quiz

## Data Integrity
- [ ] `pilot/ijaio26pilot.json` exists.
- [ ] JSON contains exactly 100 question objects.
- [ ] Each object has `question`, `options` (array of 4), `correctAnswerIndex`, `explanation`, `topic`, `subtopic`.
- [ ] Topics and subtopics match those in `pilot/topics.txt`.

## Functionality
- [ ] Quiz loads without errors.
- [ ] Questions are displayed correctly.
- [ ] Clicking an option triggers feedback.
- [ ] Correct answer turns Green.
- [ ] Incorrect answer turns Red, and Correct answer turns Green.
- [ ] Explanation is shown after selection.
- [ ] "Next" button moves to the next question.
- [ ] "Previous" button moves to the previous question.
- [ ] Buttons are disabled at boundaries (First/Last).
- [ ] Reset button clears the quiz state.

## UI/UX
- [ ] Layout is responsive (works on mobile/desktop).
- [ ] Text is readable.
- [ ] Visual feedback is distinct and accessible (Green/Red).
