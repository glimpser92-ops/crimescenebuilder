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
   - Extract a relationship/conflict graph: debts, resentments, dependencies, secrets, alliances, past incidents, and what each suspect risks losing.
   - Normalize alibis into time windows. If one briefing alibi includes a time, every suspect's briefing alibi must include a comparable time range or an explicit "time not yet fixed" gap.
   - If culprit logic, key evidence, or the requested platform is missing, ask one concise question. Otherwise proceed.

2. **Create the case bible**
   - Convert the story into a structured case graph using `story-to-case-schema.md`.
   - Keep all case facts faithful to the source unless the user explicitly asks for rewriting.
   - Separate player-facing evidence from author-only truth.
   - Separate public start-screen facts from runtime case data. Public data must not contain the truth timeline, culprit-only facts, final evidence titles, hidden meanings, real alibis, or exact board solutions.
   - For every evidence card, write both a player-facing observation and a deduction aid: what axis it should be compared on, without giving away the final answer.
   - Give each suspect several evidence-presentation reactions, including deflection, partial admission, emotional pressure, contradiction, and relationship-specific responses when the evidence touches a conflict.
   - Give each suspect a playable conflict profile: a concrete desire, a resentment or fear, a dependency or secret, and pressure points with at least two other suspects.
   - Build an evidence-presentation matrix for pivotal clues. Important evidence should produce tailored reactions from every suspect it plausibly pressures, not only the culprit; each reaction should teach the player a small story or deduction fact.

3. **Design the game loop**
   - Use `gameplay-blueprint.md`.
   - Default loop: setup screen -> briefing -> investigation hub -> evidence notebook -> suspect questioning -> contradiction board -> final accusation.
   - Make the first screen the game, not a marketing page.
   - Start with strict clue pacing. The first screen and briefing should show only public case anchors: title, location, missing object/victim, alarm/discovery time, suspect names/roles, and claimed alibis.
   - Preserve deduction: hints should guide categories, comparison axes, and next useful places, not reveal exact answers unless the user asks for an easier mode.
   - Clue-unlock hints should be suggestive, not instructional. Say that certain deduction-board connections can open new material; do not name the exact evidence set before the player solves it. After the connection is solved, point clearly to the newly opened clue or location.

4. **Implement the web game**
   - Follow the current repository's framework and patterns.
   - Prefer data-driven case structures: evidence cards, locations, suspects, questions, board rules, unlock rules, final answer rules.
   - Use real UI controls and responsive layouts; avoid placeholder screens.
   - If there is an existing app, upgrade it in place without broad unrelated rewrites.
   - Locked cards must use generic placeholders for hidden titles/sources/bodies, but they must also explain how to open them: missing prerequisite evidence, required board connection progress, final-gate progress, or next location/category.
   - When evidence is collected or a board rule is solved, explicitly show what changed: newly added evidence, newly available investigation points, cleared suspects, and final unlock progress.
   - Whenever evidence is collected or unlocked, reflect the clue content in a visual timeline, route map, or clue-flow panel so players can see where time, movement, object state, or testimony starts to break.
   - Treat that visualization as the player's case memory, not decoration. Add the clue's short observation, affected time window/route/object/person, and visible contradiction axis to the timeline, route map, or clue-flow state.
   - Use two-stage unlock communication: before success, hint only that a deduction-board relationship may clarify a route, time, object, witness, or motive gap; after success, name the newly opened clue or location and point the player to where it can be read.

5. **Upgrade presentation quality**
   - Use `premium-investigation-ui.md`.
   - Aim for a premium investigation file: dossier surfaces, maps, timelines, CCTV/event cards, evidence tags, suspect files, subtle motion, and strong visual hierarchy.
   - Add visualizations for timeline, route, object state, witness contradictions, and clue relationships whenever evidence is text-heavy.
   - Show acquired clue content inside those visualizations, not just decorative markers. A timeline or route map should reveal the relevant observation once the player has earned it.
   - Use theme-matched visual assets for the case, locations, and major evidence clusters. Do not ship a text-only investigation game unless the user explicitly requests one.

6. **Add anti-stuck guidance**
   - Add low-intervention guidance for wrong contradiction-board attempts.
   - Default to type-only hints: time, route, object, witness, trace, motive, alibi, status, relation, document.
   - Do not show exact card IDs, exact suspect-answer combinations, or candidate bundles unless explicitly requested.
   - Do not tell players which clues to connect on the board before they solve a rule. Prefer soft prompts such as "a board connection may clarify this route gap"; after success, name the newly available clue and where to read it.
   - Evidence notebook cards should include expanded observation notes and a non-spoiling comparison cue.
   - Contradiction-board chips should surface compact comparison anchors so players can form likely pairs or triples without guessing blindly.
   - Suspect screens should make conflicts playable: show relation tags, pressure points, and evidence reactions that reveal more story texture without handing out author-only truth.
   - Briefing alibis must be comparable across suspects. If one suspect has a timestamped alibi, all suspects need a timestamped alibi, time window, or clearly marked unknown-time gap.
   - Presenting evidence should feel conversational and case-specific. Avoid one generic refusal line repeated across suspects; vary tone, reveal pressure, and let relationships color the response.

7. **Verify**
   - Use `verification-contract.md`.
   - Run build/type checks available in the repo.
   - Use the in-app Browser for local app smoke tests.
   - Verify desktop and mobile viewports, no horizontal overflow, no blank screens, strict early-spoiler locks, locked-clue explainability, correct and incorrect board paths, all evidence reachability, and final accusation behavior.
   - Add source-level checks when feasible for timed briefing alibis, visible conflict profiles, pivotal evidence reactions, clue-trace visualization, and pre-unlock hints that do not leak exact evidence IDs, titles, or board recipes.
   - Browser-test at least one complete deduction slice: read briefing, acquire a clue, confirm its content appears in the visual timeline/route/clue-flow, follow a subtle hint, solve the relevant board link, and confirm the success feedback points to the newly opened clue.

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
