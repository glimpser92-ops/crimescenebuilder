# Intake and Repair

Use this reference to turn a rough mystery into a fair, playable case before writing the web game prompt.

## Source Hierarchy

Treat facts in this order:

1. User-stated canon facts.
2. Scenario bible or existing blueprint facts.
3. Source PPT/story/prompt facts.
4. Reasonable repairs invented to make the game solvable.

Never change a higher-priority fact silently. If a repair conflicts with canon, either choose a different repair or ask one question.

## Extraction Table

| Field | Need |
| --- | --- |
| Title and premise | Game identity and opening briefing |
| Apparent incident | What players initially think happened |
| True incident | What actually happened |
| Culprit | Final answer |
| Motive | Emotional and practical reason |
| Method | Tool, access, action, or deception |
| Opportunity | Time window and route |
| Staging/concealment | What was hidden, altered, faked, or omitted |
| Suspects | Role, secret, conflict, alibi, suspicion, clearing path |
| Locations | Search areas, evidence clusters, unlock order |
| Evidence | ID, source, player-facing text, true meaning, dependency |
| Reveal | Step-by-step truth explanation |

## Repair Pass

If the source is weak, fill gaps in this order:

1. **Truth spine**
   - Write one sentence: culprit, motive, method, time/place, concealment, and false impression.
   - Decide whether the apparent incident is the true incident or a cover.

2. **Suspect matrix**
   - Give each suspect a surface suspicion, real secret, claimed alibi, real alibi, and clearing evidence.
   - Give every innocent suspect a reason to lie that is not the main crime.
   - Give the culprit a lie that is partly true, not cartoonishly false.

3. **Timeline and movement**
   - Use fixed time slots.
   - Track claimed movement and real movement.
   - Assign every key, camera, witness, object transfer, blind spot, and route to a time slot.
   - Make the culprit route possible but not obvious.

4. **Evidence graph**
   - Every clue needs a surface meaning, true meaning, supported deduction, implicated suspect, cleared suspect, dependency, and reveal phase.
   - Add at least two proof paths:
     - motive plus opportunity plus alibi contradiction
     - method plus movement trace plus concealment failure
   - Delete or repurpose dead clues.

5. **Relationship conflicts**
   - Make conflict relational: jealousy, protection, rivalry, debt, shame, fear, loyalty, credit, exposure, or obligation.
   - Connect suspect-to-victim/object and suspect-to-suspect edges.

## Ask vs Decide

Ask the user if:

- Culprit identity is missing and the user clearly wants to preserve a canon answer.
- Target age/tone would materially change the case.
- A repair would reverse a user-stated fact.
- The requested platform is incompatible with the assumed single-file browser game.

Decide and label the choice if:

- Only clue wording, ordering, UI theme, score values, hint copy, or location names are missing.
- More evidence is needed to make a known culprit provable.
- A suspect needs a stronger but non-canon secret to support a red herring.

## Repair Output

Before the final build prompt, summarize repairs briefly:

- `Preserved canon`
- `Filled gaps`
- `Author decisions`
- `Fair-play fixes`

Keep this section short; the final build prompt is the main deliverable.
