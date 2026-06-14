# Gameplay Blueprint

Use this reference before implementing mechanics or data structures.

## Default Screen Flow

1. **Setup / Case File**
   - Show the case title, setting, team name, player count, role-card toggle, and "open case file" action.
   - Use a theme-appropriate hero image or dossier scene.

2. **Briefing**
   - Show initial evidence and first statements.
   - Visualize text-heavy evidence: timeline cards, CCTV strips, object diagrams, route sketches, schedules.

3. **Investigation Hub**
   - Give a clear next investigation area while preserving player choice.
   - Include map, notebook, suspects, contradiction board, and hints.
   - Avoid making a location card run away from the cursor; hover states must not move clickable targets.

4. **Notebook**
   - Evidence cards should be scan-friendly.
   - Provide type filters and visual evidence modules.
   - Each card should clarify source, category, and why it may matter without solving it.

5. **Suspect Questioning**
   - Limit questions if the story supports scarcity.
   - Let evidence presentation trigger specific reactions.
   - Preserve suspect voice and red herring tension.

6. **Contradiction Board**
   - Let players select 2-3 evidence cards.
   - Correct links create insights, eliminations, or unlocks.
   - Wrong links clear selection and show type-only feedback.
   - Duplicate links should clear selection without penalty.

7. **Final Accusation**
   - Require culprit plus motive/method/evidence, not just one click.
   - Give clear success and near-miss feedback.

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
- wrong-link feedback

## Anti-Stuck Guidance

Add help at the moment of friction:

- After wrong board connection: show clue types to reread.
- After idle or repeated failed attempts: show the next reasoning axis, not the answer.
- In the hub: tell the next useful place to inspect, not which exact clue solves the case.

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

## Collaboration Game Feel

Make the game feel playable by a small student group:

- Use consensus buttons for important board/final actions.
- Use role prompts such as records lead, scene lead, interview lead.
- Keep hints low-intervention and teacher-friendly.
- Use clear progress indicators without making the answer feel procedural.
