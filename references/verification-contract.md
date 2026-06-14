# Verification Contract

Use this reference before claiming a crimescene game is complete.

## Required Local Checks

Run the repo's available checks:

- build command, usually `npm run build`
- typecheck or lint when available
- any contract tests added for clue logic or hint boundaries

If no test command exists, add a narrow verification script when a behavior is fragile, such as wrong-link feedback or final-answer validation.

## Required Browser Smoke

Use the in-app Browser for local web apps.

Smoke path:

1. Open the local app URL.
2. Start the case from the first screen.
3. Reach briefing.
4. Reach investigation hub.
5. Open notebook or evidence list.
6. Open contradiction board.
7. Try one wrong connection and verify feedback.
8. Try one known correct connection and verify insight/unlock behavior.
9. Reach final accusation when feasible.
10. Check mobile viewport for no horizontal overflow.

## Wrong-Link Feedback Contract

Verify:

- feedback appears only after an incorrect board connection
- feedback names only clue/reasoning types
- feedback does not include exact evidence IDs
- feedback does not include exact suspect-answer combinations
- feedback does not include candidate card bundles
- success and duplicate paths clear feedback

Recommended guard script checks:

- wrong branch creates feedback
- success branch clears feedback
- duplicate branch clears feedback
- feedback panel renders only allowed fields
- type hint data contains no exact IDs
- feedback text contains no exact IDs, suspect names, or bundle wording

## Visual QA

Check:

- desktop and mobile readability
- no horizontal overflow
- no blank canvas or missing image
- no overlapping buttons/text
- hover targets remain stable
- evidence visualizations are visible without excessive scrolling

## Final Report

Include:

- changed files
- playable flow
- major mechanics
- verification commands and results
- browser smoke evidence
- known gaps, if any
