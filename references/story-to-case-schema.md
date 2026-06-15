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
   - Normalize every briefing alibi into a comparable time window. If the source gives a time for one suspect but not another, add an explicit "time unspecified / needs confirmation" gap rather than leaving the alibi as action-only prose.
   - Track which clue proves, weakens, or reframes each time window so the UI can later highlight the contradiction on a timeline.
   - Keep author-only truth separate from player-facing clues.

4. Build suspects.
   - `id`
   - `name`
   - `role`
   - `surface suspicion`
   - `actual relation to the case`
   - `motive appearance`
   - `alibi`
   - `alibiWindow`: start/end time, approximate range, or explicit unknown gap
   - `conflicts`: relationship tensions with other suspects, including cause, visible symptom, hidden pressure, and evidence that can surface it
   - `questions`
   - `present-evidence reactions`
   - `reactionMap`: multiple evidence-triggered responses per suspect, including denial, deflection, partial admission, contradiction, emotional pressure, and relation-specific remarks
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
   - `flowPlacement`: optional timeline time, route node, object state, or witness-conflict slot where this clue should appear after collection
   - `playerText`: concise clue content safe to show inside timeline/route visualizations after the clue is acquired
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
   - `preSolveNudge`: soft clue-category hint that a board connection can open new material, without naming the required evidence set
   - `postSolveNotice`: specific newly opened clue/location to inspect after the rule is solved

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
- Board-unlock hints must not list exact prerequisite bundles before success. Say that a relevant deduction-board connection may open the clue; after success, name the newly available clue or location.
- Board chips may show comparison cues for collected cards. This is allowed because the player already owns those cards.
- Timeline/route visualizations may show acquired clue content, but must not show hidden `trueMeaning`, final answers, or undiscovered clue bodies.

## Case Bible Output

Before coding, produce or maintain an internal case bible with:

```text
Truth:
Public Opening Record:
Timeline:
Suspects:
Conflict Graph:
Locations:
Evidence Cards:
Board Rules:
Unlock Rules:
Clue Flow Visuals:
Final Accusation:
Asset Inventory:
Open Ambiguities:
```

If an ambiguity would change the culprit or final deduction, ask the user. If it only affects wording, choose conservatively and proceed.
