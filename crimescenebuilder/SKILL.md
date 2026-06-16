---
name: crimescene-game-builder
description: Build a polished browser-based crimescene investigation game from a supplied mystery story, scenario, case file, script, or clue document. Use when the user wants Codex to turn narrative material into a playable crime-scene game with suspects, evidence cards, investigation locations, interviews, contradiction-board logic, final accusation flow, premium dossier-style UI, and browser verification.
---

# Crimescene Game Builder

## Purpose

Turn a story file into a complete playable mystery web game. Preserve the story's culprit logic, evidence facts, and deduction chain while building the actual interactive experience: briefing, investigation hub, evidence notebook, suspect questioning, contradiction board, hints, and final accusation.

This skill should produce a game that is playable without the builder sitting beside the player. It must pace clue disclosure, explain locked clue conditions, provide enough evidence-detail for deduction, and avoid early spoilers.

## Required References

Load only what the current task needs:

- Read `references/story-to-case-schema.md` when extracting or restructuring story material.
- Read `references/gameplay-blueprint.md` before designing mechanics or data structures.
- Read `references/premium-investigation-ui.md` before implementing screens or visual style.
- Read `references/verification-contract.md` before claiming completion.

## Workflow

1. **Ingest the story**
   - Read every user-provided story/scenario/build prompt file completely.
   - Extract culprit, motive, opportunity, timeline, suspects, alibis, locations, physical clues, witness statements, red herrings, and final deduction.
   - If culprit logic, key evidence, or the requested platform is missing, ask one concise question. Otherwise proceed.

2. **Create the case bible**
   - Convert the story into a structured case graph using `story-to-case-schema.md`.
   - Keep all case facts faithful to the source unless the user explicitly asks for rewriting.
   - Separate player-facing evidence from author-only truth.
   - Separate public start-screen facts from runtime case data. Public data must not contain the truth timeline, culprit-only facts, final evidence titles, hidden meanings, real alibis, or exact board solutions.
   - For every evidence card, write both a player-facing observation and a deduction aid: what axis it should be compared on, without giving away the final answer.

3. **Design the game loop**
   - Use `gameplay-blueprint.md`.
   - Default loop: setup screen -> briefing -> investigation hub -> evidence notebook -> suspect questioning -> contradiction board -> final accusation.
   - Make the first screen the game, not a marketing page.
   - Start with strict clue pacing. The first screen and briefing should show only public case anchors: title, location, missing object/victim, alarm/discovery time, suspect names/roles, and claimed alibis.
   - Preserve deduction: hints should guide categories, comparison axes, and next useful places, not reveal exact answers unless the user asks for an easier mode.

4. **Implement the web game**
   - Follow the current repository's framework and patterns.
   - Prefer data-driven case structures: evidence cards, locations, suspects, questions, board rules, unlock rules, final answer rules.
   - Use real UI controls and responsive layouts; avoid placeholder screens.
   - If there is an existing app, upgrade it in place without broad unrelated rewrites.
   - Locked cards must use generic placeholders for hidden titles/sources/bodies, but they must also explain how to open them: missing prerequisite evidence, required board connection progress, final-gate progress, or next location/category.
   - When evidence is collected or a board rule is solved, explicitly show what changed: newly added evidence, newly available investigation points, cleared suspects, and final unlock progress.
   - Derive progress UI from existing game state instead of storing a separate progress state. Compute progress from collected evidence, visited/cleared locations, solved board rules, cleared suspects, current phase/view, and available-but-uncollected clues.

5. **Upgrade presentation quality**
   - Use `premium-investigation-ui.md`.
   - Aim for a premium investigation file: dossier surfaces, maps, timelines, CCTV/event cards, evidence tags, suspect files, subtle motion, and strong visual hierarchy.
   - Add visualizations for timeline, route, object state, witness contradictions, and clue relationships whenever evidence is text-heavy.
   - Add a visible investigation progress spine: phase rail, progress meters, next-action signal, and map/location markers that update when the player earns new information.
   - Use theme-matched visual assets for the case, locations, and major evidence clusters. Do not ship a text-only investigation game unless the user explicitly requests one.

6. **Add anti-stuck guidance**
   - Add low-intervention guidance for wrong contradiction-board attempts.
   - Default to type-only hints: time, route, object, witness, trace, motive, alibi, status, relation, document.
   - Do not show exact card IDs, exact suspect-answer combinations, or candidate bundles unless explicitly requested.
   - Evidence notebook cards should include expanded observation notes and a non-spoiling comparison cue.
   - Contradiction-board chips should surface compact comparison anchors so players can form likely pairs or triples without guessing blindly.

7. **Verify**
   - Use `verification-contract.md`.
   - Run build/type checks available in the repo.
   - Use the in-app Browser for local app smoke tests.
   - Verify desktop and mobile viewports, no horizontal overflow, no blank screens, strict early-spoiler locks, locked-clue explainability, correct and incorrect board paths, all evidence reachability, and final accusation behavior.

8. **Prepare source handoff**
   - If the user wants to continue on GitHub, identify the source files required for modification and recreation.
   - Include app source, case data, assets, tests, server/package files, and reusable design/story prompts.
   - Exclude generated verification screenshots, local runtime state, installed dependencies, logs, and large source decks unless the user asks for archival material.

## Completion Report

Report:

- Changed files.
- The playable flow implemented.
- The main deduction chain and non-spoiling guidance behavior.
- Clue pacing: what is public at start, what is locked, and how locked clues explain their opening conditions.
- Anti-stuck aids: notebook detail, board comparison cues, unlock notices, and wrong-link feedback.
- Verification evidence: build/typecheck, browser smoke, mobile layout, and any known gaps.

Keep final responses concise and user-facing.
