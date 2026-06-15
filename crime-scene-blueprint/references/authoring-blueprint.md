# Authoring Blueprint

Use this reference to create or restructure a crime-scene scenario.

## Truth Spine

Fill this before writing clues.

| Field | Fill This |
| --- | --- |
| 사건 | What appears to have happened |
| 실제 사건 | What really happened |
| 범인 | Who did it |
| 피해/목표 | Victim, stolen object, missing person, or consequence |
| 동기 | Emotional and practical reason |
| 수단 | Weapon, tool, method, access |
| 기회 | Exact time window and access path |
| 은폐 | What the culprit staged, removed, altered, or lied about |
| 오해 | What players should believe at first |
| 결정적 증거 | The clue that makes the answer unavoidable |

## Suspect Matrix

Give every suspect a real secret, not just a fake motive.

| Suspect | Public Role | Conflict With Victim/Object | Secret | Real Alibi | Claimed Alibi | False Suspicion | Clearing Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Culprit | | strongest practical motive | crime-related secret | real movement | partial lie | strong but incomplete path | none until synthesis |
| Suspect B | | emotional motive | unrelated shame/secret | provable | omission | red herring | contradiction clears them |
| Suspect C | | opportunity | hidden relationship | partly witnessed | evasive | means red herring | means fails |
| Suspect D | | access/knowledge | protective lie | provable late | suspicious | motive red herring | timeline clears them |

## Timeline and Movement Matrix

Use fixed time slots. Track both claimed and real movement.

| Time | Location A | Location B | Location C | Location D | Notes |
| --- | --- | --- | --- | --- | --- |
| T-30 | | | | | setup before incident |
| T-20 | | | | | first contradiction seed |
| T-10 | | | | | last normal sighting |
| T0 | | | | | crime window |
| T+10 | | | | | staging/escape |
| T+20 | | | | | discovery |

Movement rules:
- No character can be in two places at once unless that is the trick.
- Every locked door, camera, witness, key, phone, object transfer, and blind spot must be assigned to a time slot.
- The culprit needs one possible hidden route and one visible trace.
- Each innocent suspect needs one suspicious trace and one later clearing trace.

## Evidence Graph

Tag every clue.

| Field | Meaning |
| --- | --- |
| ID | Evidence number |
| Source | Location, suspect item, witness, CCTV, message, lab, puzzle |
| Surface meaning | What players first think it means |
| True meaning | What it proves after cross-reference |
| Supports | motive / means / opportunity / alibi / movement / relationship / concealment |
| Implicates | Suspect(s) it appears to accuse |
| Clears | Suspect(s) it eventually clears |
| Depends on | Earlier clue needed to interpret it |
| Reveal phase | early / mid / late / final |

Recommended clue architecture for a 60-slide, 4-suspect game:
- 4 alibi statements.
- 4 suspect item clues.
- 9-12 location clues.
- 8-10 contradiction or relationship clues.
- 2-4 late synthesis clues.
- 1 decisive clue.

Proof paths:
- Path A: motive + opportunity + alibi contradiction.
- Path B: method + movement trace + concealment failure.

## Relationship Graph

Each suspect needs two edges:
- Edge to victim/object: motive or access.
- Edge to another suspect: jealousy, protection, debt, rivalry, fear, loyalty, blackmail, cover-up.

| From | To | Public Relationship | Hidden Relationship | Conflict Type | Revealing Evidence |
| --- | --- | --- | --- | --- | --- |
| A | Victim/Object | | | money/status/fear/love/revenge | |
| B | Victim/Object | | | | |
| C | Suspect D | | | | |
| Culprit | Suspect B | | | | |

Use varied motive pressures:
- gain something,
- prevent exposure,
- protect someone,
- revenge,
- escape obligation,
- seize credit/status.

