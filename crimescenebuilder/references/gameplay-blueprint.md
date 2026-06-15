# Gameplay Blueprint

Use this reference before implementing mechanics or data structures.

## Default Screen Flow

1. **Setup / Case File**
   - Show the case title, setting, team name, player count, role-card toggle, and "open case file" action.
   - Use a theme-appropriate hero image or dossier scene.

2. **Briefing**
   - Show only public case anchors by default: title, setting, missing object/victim, discovery or alarm time, suspect names/roles, and claimed alibis.
   - Do not show truth timeline, exact evidence cards, hidden meanings, real alibis, final evidence, or board-rule answers unless the source story explicitly frames them as public.
   - If the game needs initial evidence, show generic investigation points first and let the player collect the concrete card.
   - Visualize text-heavy evidence: timeline cards, CCTV strips, object diagrams, route sketches, schedules.

3. **Investigation Hub**
   - Give a clear next investigation area while preserving player choice.
   - Include map, notebook, suspects, contradiction board, and hints.
   - Avoid making a location card run away from the cursor; hover states must not move clickable targets.
   - Every locked investigation point must explain how it opens without revealing hidden content.
   - When a clue unlocks, show a visible notice that states what changed: evidence added to notebook, new investigation point available, suspect cleared, or final-gate progress.

4. **Notebook**
   - Evidence cards should be scan-friendly.
   - Provide type filters and visual evidence modules.
   - Each card should clarify source, category, and why it may matter without solving it.
   - Include expanded observation notes so the player can reason from the clue, not just memorize a title.
   - Include a compact comparison cue for each collected card, such as "compare: alarm sound / sensor manual".

5. **Suspect Questioning**
   - Limit questions if the story supports scarcity.
   - Let evidence presentation trigger specific reactions.
   - Preserve suspect voice and red herring tension.

6. **Contradiction Board**
   - Let players select 2-3 evidence cards.
   - Correct links create insights, eliminations, or unlocks.
   - Wrong links clear selection and show type-only feedback.
   - Duplicate links should clear selection without penalty.
   - Board chips should show collected-card comparison anchors so players can find likely pairs/triples.
   - The board should feel like guided deduction, not blind combination search.
   - Solving a board rule should name newly added evidence and newly available locked cards when that content has become visible.

7. **Final Accusation**
   - Require culprit plus motive/method/evidence, not just one click.
   - Give clear success and near-miss feedback.
   - Keep final accusation locked until the required core deductions and elimination work are complete.
   - Locked final evidence should show final-gate progress, such as core rules solved and suspects cleared.

## Data Model Pattern

Prefer plain structured data in one case module or a clear section of the app:

```js
const EVIDENCE = [];
const SUSPECTS = [];
const LOCATIONS = [];
const QUESTIONS = {};
const LINK_RULES = [];
const FINAL_RULE = {};
```

Use helpers for:

- stable card lookup
- visited/collected state
- evidence filtering
- board rule matching
- solved-link keying
- unlock calculation
- locked-clue requirement explanation
- newly-unlocked notice generation
- wrong-link feedback

## Anti-Stuck Guidance

Add help at the moment of friction:

- After wrong board connection: show clue types to reread.
- After idle or repeated failed attempts: show the next reasoning axis, not the answer.
- In the hub: tell the next useful place to inspect, not which exact clue solves the case.
- On locked cards: show prerequisite progress and board-rule progress.
- On evidence cards: show "what to compare this with" in non-spoiling language.

Allowed wrong-link hints:

- time / sequence
- route / location
- object / trace
- witness statement
- motive
- alibi
- status change
- relation
- document / record

Forbidden by default:

- exact evidence IDs
- "try E05 + E06"
- exact suspect-answer pair
- final culprit or method reveal
- automatic board solving

Allowed on locked cards:

- already-discovered prerequisite evidence names
- undiscovered prerequisite location and clue type
- board-rule progress counts
- final-gate progress counts

Forbidden on locked cards:

- undiscovered evidence titles
- final evidence body text
- author-only true meanings
- culprit-only explanation

## Collaboration Game Feel

Make the game feel playable by a small student group:

- Use consensus buttons for important board/final actions.
- Use role prompts such as records lead, scene lead, interview lead.
- Keep hints low-intervention and teacher-friendly.
- Use clear progress indicators without making the answer feel procedural.
