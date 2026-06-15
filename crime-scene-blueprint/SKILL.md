---
name: crime-scene-blueprint
description: Design, analyze, repair, or QA reusable crime-scene / mystery investigation game scenarios, especially PPT-style host-led deduction games with suspects, clues, alibis, relationship conflicts, timelines, movement paths, evidence cards, culprit reveal, and case-truth explanation. Use when the user asks to create a new mystery story/game, turn a premise into a clue blueprint, analyze existing crime-scene PPTs, make a reusable scenario template, check solvability/fairness, or prepare material for a later playable web game.
---

# Crime Scene Blueprint

## Purpose

Create fair, replayable host-led mystery games by designing the case backward from the truth. Keep the hidden truth, public evidence, alibis, movement, and final reveal internally consistent before making PPT slides or implementing a game.

## Load References

Load only what the task needs:

- Read `references/authoring-blueprint.md` when creating or restructuring a case.
- Read `references/ppt-deck-grammar.md` when producing a PPT-style slide outline, host flow, or evidence reveal sequence.
- Read `references/qa-checklist.md` when reviewing an existing scenario for fairness, solvability, dead clues, alibi gaps, or timeline contradictions.

If the user asks for a playable browser game, first create or verify the scenario bible with this skill, then use `$crimescene-game-builder` for implementation.

## Default Game Shape

Default to a 45-75 minute, host-led deduction game unless the user gives different constraints:

- 4 suspects.
- 3-4 searchable locations.
- 4 suspect belongings / personal evidence entry points.
- 24-30 evidence cards.
- One accusation phase.
- Culprit reveal plus case-truth explanation.
- Optional final objective such as finding a missing person, stolen object, password, or decisive evidence.

Ask one concise question only when missing information would materially change the case, such as target age, tone, playtime, or whether the user wants murder/theft/disappearance/sabotage. Otherwise make a reasonable default and proceed.

## Core Workflow

1. **Lock the truth first**
   - Write the answer sentence:
     `범인은 [X]이고, [동기] 때문에, [수단]으로, [시간/장소]에서 범행했으며, [조작/은폐]로 [거짓 인상]을 만들었다.`
   - Separate author-only truth from player-facing evidence.

2. **Build the scenario bible**
   - Fill the truth spine.
   - Create four suspects with motive, opportunity, secret, claimed alibi, real alibi, false suspicion, and clearing evidence.
   - Build the timeline and movement matrix before writing clue cards.
   - Build the relationship graph so conflict is relational, not just "everyone disliked the victim."

3. **Design the evidence graph**
   - Give every clue a source, surface meaning, true meaning, supported deduction, implicated suspect, cleared suspect, dependency, and reveal phase.
   - Ensure every clue supports motive, means, opportunity, alibi contradiction, movement, relationship, concealment, or a deliberate red herring.
   - Delete dead clues.

4. **Plan the reveal**
   - Reveal early clues to create suspicion.
   - Reveal middle clues to break alibis.
   - Reveal late clues to connect movement and method.
   - Use the final clue to remove ambiguity, not to introduce the only real proof.

5. **QA the mystery**
   - Confirm the culprit is provable before the reveal using public evidence.
   - Confirm at least two independent proof paths converge on the culprit.
   - Confirm every innocent suspect has both a suspicious path and a clearing path.
   - Confirm the final explanation replays the timeline and explains why alternatives fail.

## Output Formats

Choose the output that matches the user request:

- **Blueprint**: truth spine, suspect matrix, timeline, relationship graph, evidence graph, reveal gates, QA notes.
- **PPT outline**: slide-by-slide host flow with cover, premise, victim/object, suspects, alibi, evidence search, accusation, reveal, and case truth.
- **Repair report**: ranked issues, contradictions, missing clues, unfair leaps, and concrete fixes.
- **Scenario bible**: `case.md`, `suspects.csv`, `timeline.csv`, `relationships.csv`, `evidence.csv`, `deck-outline.md`, and `host-script.md` sections in one response or as files if requested.

## Rules

- Preserve supplied story facts unless the user explicitly asks for rewriting.
- Do not solve the case with one surprise clue that appears only after accusation.
- Do not make red herrings random; each must be explainable after the reveal.
- Do not let an alibi be merely true/false. Give it a true detail, an omission, and a distortion.
- Do not use outside knowledge as required proof unless the user explicitly designs an expert puzzle.
- Label unresolved assumptions and author decisions clearly.

