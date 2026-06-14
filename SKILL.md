---
name: crimescene-game-builder
description: Build a polished browser-based crimescene investigation game from a supplied mystery story, scenario, case file, script, or clue document. Use when the user wants Codex to turn narrative material into a playable crime-scene game with suspects, evidence cards, investigation locations, interviews, contradiction-board logic, final accusation flow, premium dossier-style UI, and browser verification.
---

# Crimescene Game Builder

## Purpose

Turn a story file into a complete playable mystery web game. Preserve the story's culprit logic, evidence facts, and deduction chain while building the actual interactive experience: briefing, investigation hub, evidence notebook, suspect questioning, contradiction board, hints, and final accusation.

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

3. **Design the game loop**
   - Use `gameplay-blueprint.md`.
   - Default loop: setup screen -> briefing -> investigation hub -> evidence notebook -> suspect questioning -> contradiction board -> final accusation.
   - Make the first screen the game, not a marketing page.
   - Preserve deduction: hints should guide categories, not reveal exact answers unless the user asks for an easier mode.

4. **Implement the web game**
   - Follow the current repository's framework and patterns.
   - Prefer data-driven case structures: evidence cards, locations, suspects, questions, board rules, unlock rules, final answer rules.
   - Use real UI controls and responsive layouts; avoid placeholder screens.
   - If there is an existing app, upgrade it in place without broad unrelated rewrites.

5. **Upgrade presentation quality**
   - Use `premium-investigation-ui.md`.
   - Aim for a premium investigation file: dossier surfaces, maps, timelines, CCTV/event cards, evidence tags, suspect files, subtle motion, and strong visual hierarchy.
   - Add visualizations for timeline, route, object state, witness contradictions, and clue relationships whenever evidence is text-heavy.

6. **Add anti-stuck guidance**
   - Add low-intervention guidance for wrong contradiction-board attempts.
   - Default to type-only hints: time, route, object, witness, trace, motive, alibi, status, relation, document.
   - Do not show exact card IDs, exact suspect-answer combinations, or candidate bundles unless explicitly requested.

7. **Verify**
   - Use `verification-contract.md`.
   - Run build/type checks available in the repo.
   - Use the in-app Browser for local app smoke tests.
   - Verify desktop and mobile viewports, no horizontal overflow, no blank screens, correct and incorrect board paths, and final accusation behavior.

## Completion Report

Report:

- Changed files.
- The playable flow implemented.
- The main deduction chain and non-spoiling guidance behavior.
- Verification evidence: build/typecheck, browser smoke, mobile layout, and any known gaps.

Keep final responses concise and user-facing.
