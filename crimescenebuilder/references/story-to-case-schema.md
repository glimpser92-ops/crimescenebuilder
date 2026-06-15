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

2. Identify the public opening record.
   - case title
   - setting
   - victim or missing object
   - discovery/alarm time
   - suspect names and roles
   - claimed alibis only
   - publicly observable scene state

   This is the only content allowed on the start screen and opening briefing by default.

3. Build the timeline.
   - Use absolute times when present.
   - Mark unknown windows, blackouts, camera gaps, movement gaps, and testimony conflicts.
   - Keep author-only truth separate from player-facing clues.

4. Build suspects.
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
   - `public profile`: name, role, badge/label, claimed alibi
   - `hidden profile`: secrets, real alibi, motive truth, and author-only interpretation

5. Build evidence cards.
   - `id`: stable code, usually `E01`, `E02`, etc.
   - `title`
   - `source`: briefing, location, interview, object, document, CCTV, photo, trace
   - `tags`: type labels such as time, route, object, witness, trace, motive, alibi, status, relation, document
   - `body`: player-facing text
   - `detail`: expanded observation note explaining what the player should notice
   - `boardHint`: compact comparison cue, such as "compare: time gap / card log"
   - `surfaceMeaning`: plausible non-final reading
   - `trueMeaning`: author-only interpretation, never shown in the notebook by default
   - `dependsOn`: evidence IDs needed before this card can be investigated
   - `visualization`: timeline, route map, object diagram, witness card, CCTV strip, inventory delta, receipt, photo contact sheet
   - `unlocks`: locations, questions, board rules, final decision
   - `lockedExplanation`: non-spoiling opening condition shown while locked

6. Build locations.
   - `id`, `name`, `round`, `short scene state`
   - `available evidence`
   - `locked/unlocked conditions`
   - `visual role`: map node, scene panel, evidence cluster
   - `public scene state`: safe before investigation
   - `private scene notes`: author-only clues, staging truths, or culprit path

7. Build contradiction-board rules.
   - `id`
   - `required`: exact evidence IDs, author-only
   - `title`
   - `result`
   - `kind`: insight, contradiction, core, elimination
   - `suspect`: only when relevant
   - `typeHints`: non-spoiling clue/reasoning types only
   - `unlocks`
   - `visibleProgress`: how much of the required set is already collected, without showing unavailable card titles

8. Build final accusation.
   - culprit answer
   - motive answer
   - method answer
   - decisive evidence requirements
   - acceptable partial failure copy
   - success epilogue

## Non-Spoiling Boundaries

Keep these separate:

- Player-facing card text may include evidence IDs because cards are visible.
- Start screen, briefing, public globals, and locked placeholders must not include evidence titles, hidden interpretations, real alibis, exact board-rule results, final evidence text, or culprit-only facts.
- Wrong-link feedback must not include exact card IDs, exact suspect-answer combinations, or candidate bundles.
- Hints may escalate from broad category to reasoning question, but should not become an auto-solver unless the user asks.
- Locked clue explanations may name already-discovered prerequisite cards, but for undiscovered cards they should name only location, status, and clue type.
- Board chips may show comparison cues for collected cards. This is allowed because the player already owns those cards.

## Case Bible Output

Before coding, produce or maintain an internal case bible with:

```text
Truth:
Public Opening Record:
Timeline:
Suspects:
Locations:
Evidence Cards:
Board Rules:
Unlock Rules:
Final Accusation:
Asset Inventory:
Open Ambiguities:
```

If an ambiguity would change the culprit or final deduction, ask the user. If it only affects wording, choose conservatively and proceed.
