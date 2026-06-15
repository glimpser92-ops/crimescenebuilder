---
name: crime-scene-webgame-prompt
description: "Create AI-ready web game build prompts for crime-scene, mystery, clue investigation, or classroom deduction games. Use when the user wants to turn a premise, PPT scenario, story bible, clue list, or rough mystery idea into a detailed prompt for building a playable browser game, especially when the source needs repair of story logic, clue relationships, alibis, movement paths, contradiction-board rules, hint/scoring systems, UI flow, or implementation constraints before handing off to a web-game builder."
---

# Crime Scene Webgame Prompt

## Purpose

Turn mystery material into a copy-paste-ready web game build prompt. Strengthen only the case logic needed for playability, then specify the browser-game experience: screens, data model, evidence graph, contradiction rules, collaboration gates, hints, scoring, reveal, visual direction, and acceptance checks.

This skill outputs a prompt-only handoff for `$crimescene-game-builder`; it does not implement the game.

## Load References

Load only what the task needs:

- Read `references/intake-repair.md` when the source scenario is incomplete, inconsistent, or needs clue/alibi/movement repair before prompt writing.
- Read `references/mechanics-data.md` when designing the web game loop, data model, contradiction board, collaboration, hints, scoring, or reveal sequence.
- Read `references/prompt-template.md` when composing the final build prompt.
- Read `references/qa-checklist.md` before finalizing any prompt package.

If the source already comes from `$crime-scene-blueprint`, preserve that scenario bible as canon and repair only gaps that would make the web game unfair or unplayable. If the user asks to build the actual playable game after the prompt is ready, hand off to `$crimescene-game-builder`.

## Default Assumptions

Use these defaults unless the user states otherwise:

- Korean output for Korean source material.
- Single browser game for small-group play on one shared device.
- Single-file React/JSX target with data constants near the top, no backend, no network calls, and no persistent storage.
- 4 suspects, 3-5 locations, 18-30 evidence cards, 5-8 contradiction-board rules, 3 hint levels, one final accusation, and a staged reveal.
- Classroom-safe tone unless the source explicitly asks for adult, horror, gore, or dark material.
- Evidence-first deduction: players should prove culprit, motive, opportunity or movement, and why each innocent suspect is cleared.

Ask one concise question only when a missing answer would change the core game, such as target age/tone, whether to preserve an existing culprit, or whether the final prompt must target a specific framework. Otherwise choose conservatively and label author decisions.

## Workflow

1. **Read the source fully**
   - Ingest every provided story, PPT summary, scenario bible, clue list, or example prompt.
   - Extract title, setting, incident, culprit, motive, method, opportunity, suspects, locations, timeline, alibis, relationships, clues, red herrings, and reveal facts.
   - Separate canon facts from inferred repairs.

2. **Repair the case enough for playability**
   - Use `intake-repair.md`.
   - Lock the truth spine and final answer.
   - Build or repair suspect matrix, timeline, movement paths, relationship conflicts, evidence graph, and clearing paths for innocents.
   - Ensure at least two independent proof paths converge on the culprit.

3. **Convert the case into playable systems**
   - Use `mechanics-data.md`.
   - Define screen flow, investigation locations, evidence card schema, suspect questioning, contradiction-board rules, unlocks, hints, scoring, final accusation, and reveal.
   - Make clue interaction group-friendly: consensus gates for major decisions, non-spoiling feedback for wrong links, and visible progress without making the solution procedural.

4. **Write the build prompt**
   - Use `prompt-template.md`.
   - Produce one complete prompt that another AI or developer can use to build the web game.
   - Include all canonical case data needed by the builder, even if it reveals the culprit; the build prompt is an author-facing document.
   - State technical constraints, component expectations, UX/visual direction, data constants, and acceptance checklist.

5. **QA the prompt**
   - Use `qa-checklist.md`.
   - Check that the prompt contains enough detail to implement without inventing the mystery logic again.
   - Fix missing proof links, dead clues, unfair final answers, exact-answer hint leakage, and unclear unlock rules before presenting the result.

## Output Shape

Default to this package:

1. **Scenario Repair Notes**: brief list of canon facts preserved, gaps filled, and author decisions.
2. **Web Game Build Prompt**: the final copy-paste prompt.
3. **QA Checklist**: concise pass/fail notes and any remaining risk.

If the user asks for "prompt only", output only the build prompt.

## Rules

- Preserve explicit user canon unless the user asks for a rewrite.
- Do not create a full scenario bible when the user only needs a build prompt; repair only what the prompt must know.
- Do not implement UI code, create assets, run a dev server, or verify a playable game inside this skill.
- Do not make the decisive clue the only real proof.
- Do not let red herrings be random; every false suspicion needs a later explanation or clearing clue.
- Do not expose exact answer bundles in wrong-link feedback or hints unless the user explicitly wants an easy mode.
- Do not require outside knowledge unless the game is explicitly designed as an expert puzzle.
- Mark invented or repaired facts as author decisions when they are not present in the source.
