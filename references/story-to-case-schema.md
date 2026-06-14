# Story To Case Schema

Use this reference when converting a story, script, or scenario into game-ready case data.

## Extraction Order

1. Identify the immutable truth.
   - culprit
   - victim or missing object
   - crime method
   - motive
   - opportunity window
   - decisive evidence chain

2. Build the timeline.
   - Use absolute times when present.
   - Mark unknown windows, blackouts, camera gaps, movement gaps, and testimony conflicts.
   - Keep author-only truth separate from player-facing clues.

3. Build suspects.
   - `id`
   - `name`
   - `role`
   - `surface suspicion`
   - `actual relation to the case`
   - `motive appearance`
   - `alibi`
   - `questions`
   - `present-evidence reactions`
   - `elimination evidence`

4. Build evidence cards.
   - `id`: stable code, usually `E01`, `E02`, etc.
   - `title`
   - `source`: briefing, location, interview, object, document, CCTV, photo, trace
   - `tags`: type labels such as time, route, object, witness, trace, motive, alibi, status, relation, document
   - `body`: player-facing text
   - `visualization`: timeline, route map, object diagram, witness card, CCTV strip, inventory delta, receipt, photo contact sheet
   - `unlocks`: locations, questions, board rules, final decision

5. Build locations.
   - `id`, `name`, `round`, `short scene state`
   - `available evidence`
   - `locked/unlocked conditions`
   - `visual role`: map node, scene panel, evidence cluster

6. Build contradiction-board rules.
   - `id`
   - `required`: exact evidence IDs, author-only
   - `title`
   - `result`
   - `kind`: insight, contradiction, core, elimination
   - `suspect`: only when relevant
   - `typeHints`: non-spoiling clue/reasoning types only
   - `unlocks`

7. Build final accusation.
   - culprit answer
   - motive answer
   - method answer
   - decisive evidence requirements
   - acceptable partial failure copy
   - success epilogue

## Non-Spoiling Boundaries

Keep these separate:

- Player-facing card text may include evidence IDs because cards are visible.
- Wrong-link feedback must not include exact card IDs, exact suspect-answer combinations, or candidate bundles.
- Hints may escalate from broad category to reasoning question, but should not become an auto-solver unless the user asks.

## Case Bible Output

Before coding, produce or maintain an internal case bible with:

```text
Truth:
Timeline:
Suspects:
Locations:
Evidence Cards:
Board Rules:
Unlock Rules:
Final Accusation:
Open Ambiguities:
```

If an ambiguity would change the culprit or final deduction, ask the user. If it only affects wording, choose conservatively and proceed.
