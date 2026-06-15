# Mechanics and Data

Use this reference to convert the repaired case into web-game systems.

## Screen Flow

Default flow:

1. Team setup
2. Case briefing
3. Investigation hub
4. Location search
5. Evidence notebook
6. Suspect files and questioning
7. Contradiction board
8. Decision evidence or final unlock
9. Final accusation
10. Staged reveal and result

The first screen should be the game experience, not a marketing page.

## Case Data Contract

Ask the builder prompt to keep case data structured and readable:

```js
const CASE = {};
const SUSPECTS = [];
const LOCATIONS = [];
const EVIDENCE = [];
const QUESTIONS = {};
const BOARD_RULES = [];
const UNLOCK_RULES = [];
const FINAL_ACCUSATION = {};
const REVEAL_STEPS = [];
```

Every evidence card should include:

- `id`
- `title`
- `source`
- `location`
- `round`
- `tags`
- `playerText`
- `surfaceMeaning`
- `trueMeaning`
- `supports`
- `implicates`
- `clears`
- `dependsOn`
- `visualization`

## Investigation Rounds

Use rounds to control pacing:

- **Briefing**: 4-6 common clues and initial suspect statements.
- **Round 1**: location search and early suspicions.
- **Round 2**: deeper location/object/witness contradictions.
- **Decision evidence**: unlock after players solve enough elimination or core insight rules.
- **Final accusation**: unlock when the case is provable, not when all clues are clicked.

## Contradiction Board

Each rule should be implementable with exact evidence IDs but presented to players as reasoning:

| Field | Meaning |
| --- | --- |
| id | Stable rule code |
| required | Evidence IDs needed, author-facing |
| title | Insight name |
| result | Player-facing deduction |
| kind | insight / contradiction / elimination / core |
| suspect | Optional linked suspect |
| unlocks | Evidence, location, question, reveal, or final gate |
| typeHints | Non-spoiling hint categories |

Wrong-link feedback may name categories such as time, route, object, witness, motive, alibi, relation, trace, or document. It must not name exact card IDs, exact suspect-answer pairs, or final culprit bundles by default.

## Suspect Questioning

Use one or both:

- A limited shared question budget when scarcity supports collaboration.
- Unlimited evidence presentation when players need to test contradictions.

Every important suspect should have:

- base statement
- alibi statement
- relationship statement
- reaction to 2-4 key evidence cards
- clearing or pressure response
- final-reveal explanation

## Collaboration Gates

For classroom or shared-device play, add consensus gates before:

- using a hint
- submitting a contradiction-board link
- unlocking decision evidence
- final accusation
- reveal progression if desired

Optional role cards:

- scene lead
- evidence keeper
- interview lead
- board moderator

Roles should support discussion, not create separate hidden information unless the user asks for roleplay.

## Hints and Scoring

Default hint ladder:

1. Broad axis: which category to revisit.
2. Reasoning question: what conflict to compare.
3. Near-answer framing: what conclusion the evidence supports without giving the exact IDs.

Score can reward:

- correct culprit
- required evidence
- motive/method accuracy
- clearing innocents
- solved board links
- unused hint bonus
- efficient question usage

Penalize:

- hints
- wrong final accusation
- excessive random board attempts, if the game tracks them

## Reveal Sequence

Use 6-10 steps:

1. apparent incident
2. key hidden fact
3. timeline replay
4. movement route
5. method or object proof
6. motive reframing
7. why each innocent looked guilty
8. decisive convergence
9. consequence or lesson
10. result screen

For student-safe games, finish with a clear reflection line rather than a grim twist.
