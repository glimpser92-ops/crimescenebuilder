# QA Checklist

Use this before finalizing the prompt package.

## Scenario Logic

- Culprit, motive, method, opportunity, and concealment are explicit.
- The apparent incident and true incident are separated.
- The culprit is provable before the reveal.
- At least two independent proof paths converge on the culprit.
- The decisive clue removes ambiguity; it is not the only meaningful proof.

## Suspects

- Every suspect has a role, suspicion, secret, claimed alibi, real alibi, and clearing path.
- Every innocent suspect has a believable reason to look guilty.
- Every false or partial alibi has a discoverable contradiction.
- The culprit's lie contains at least one true detail.

## Evidence

- Every evidence card has ID, source, tags, player text, surface meaning, true meaning, supported deduction, dependencies, and reveal phase.
- No dead clues remain.
- Red herrings are later explained or cleared.
- Clue order creates suspicion early, contradiction in the middle, and convergence late.

## Web Game Playability

- The prompt defines screens, state, unlocks, and final validation clearly enough to implement.
- The contradiction-board rules list exact required evidence IDs for the builder.
- Wrong-link feedback uses only clue types or reasoning categories.
- Hints do not reveal exact card IDs, exact suspect-answer pairs, or final answer bundles by default.
- Final accusation requires culprit plus evidence and motive/method reasoning.

## Classroom / Group Fit

- Important actions use discussion or consensus gates when shared-device play is assumed.
- Text is short enough for scanning.
- Evidence visualizations are requested for dense information.
- Role cards, if included, support collaboration without hiding essential facts from teammates.

## Technical Prompt Completeness

- Target framework/file shape is stated.
- No backend/network/storage constraints are stated when applicable.
- Data constants and component expectations are stated.
- Responsive and accessibility expectations are stated.
- Acceptance checklist is included.

## Final Risk Note

If any required part remains invented because the source lacked detail, label it under `Author decisions` so the user can review it before building.
