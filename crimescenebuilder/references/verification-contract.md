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
9. Verify newly-unlocked notices name what became available.
10. Verify locked evidence explains how it opens.
11. Verify progress UI updates after collecting evidence or solving a board rule.
12. Verify map/location progress counts and next-action cue are visible.
13. Reach final accusation when feasible.
14. Check mobile viewport for no horizontal overflow.

## Early Spoiler Contract

Verify before claiming completion:

- start screen and opening briefing show only public case anchors
- public global data does not expose private runtime data
- hidden runtime loader or author-only data is not left publicly inspectable after boot
- uncollected scene cards use generic placeholders
- locked cards do not show hidden titles, hidden sources, truth meanings, final evidence text, or real alibis
- suspect screens hide secrets, real alibis, and author-only profile facts until earned
- notebook starts empty unless initial evidence was explicitly requested
- hint panels do not pre-answer the case before the player asks

Recommended guard script checks:

- scan initial DOM text for forbidden truth terms
- inspect public data shape for private fields
- assert initial evidence count and notebook card count
- assert final tab/evidence is locked until required deductions
- collect one clue and assert concrete text appears only after collection

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

## Unlock Explainability Contract

Verify:

- every locked investigation card renders an opening-condition panel
- prerequisite progress counts update after evidence collection
- already-discovered prerequisite evidence can be named
- undiscovered prerequisite evidence remains generic by location/type
- board-rule progress counts update after solving links
- final locked evidence shows final-gate progress
- newly available cards are visually marked
- collecting or solving produces a visible unlock notice
- collection or solving updates derived progress indicators without needing a separate progress state

Recommended guard script checks:

- initial locked cards all contain a requirements panel
- a dependency-unlocked card becomes "newly available"
- a board-rule-unlocked card is named after the rule is solved
- a final locked card shows prerequisite, board, and final-gate progress
- no locked-card panel contains hidden `trueMeaning` text

## Progress Feedback Contract

Verify:

- progress indicators are derived from actual game state such as collected evidence, solved board rules, cleared suspects, current phase/view, and available clues
- the progress rail appears after the case starts
- collecting one clue changes at least the evidence count or evidence percent
- solving one board rule changes deduction progress and any newly opened clue/location signal
- maps or location lists show per-location counts such as `1/5`
- exactly one strongest next-action cue is visually emphasized when a next clue cluster exists
- progress UI does not reveal hidden evidence titles, exact board bundles, culprit-only facts, or final answers
- `prefers-reduced-motion: reduce` preserves progress information while removing nonessential motion

Recommended guard script checks:

- snapshot progress before and after collecting a clue
- assert the after snapshot changed in the expected meter text or width
- assert one `next` marker exists when available uncollected clues exist
- assert locked/final spoilers remain absent from progress text
- emulate reduced motion or inspect CSS for a reduced-motion override

## Visual QA

Check:

- desktop and mobile readability
- no horizontal overflow
- no blank canvas or missing image
- no overlapping buttons/text
- hover targets remain stable
- evidence visualizations are visible without excessive scrolling
- board comparison cues are visible on evidence chips
- notebook expanded details are readable
- progress rail, next-action cue, and per-location counters remain readable on desktop and mobile

## Source Handoff Contract

When the user wants GitHub or reuse guidance, identify:

Commit for editing the current game:

- app source, usually `public/`
- generated/curated assets used by the app
- case data module
- server entry point
- package files
- tests or smoke scripts
- `.gitignore`

Commit additionally for recreating a new game from the same process:

- story blueprint or case bible
- webgame build prompt
- reusable design notes or scenario documents

Exclude by default:

- `node_modules/`
- generated verification screenshots
- local runtime state such as `.omx/`
- logs
- temporary browser artifacts
- large source decks or slide exports unless the user asks for archival material

## Final Report

Include:

- changed files
- playable flow
- major mechanics
- verification commands and results
- browser smoke evidence
- known gaps, if any
