# Premium Investigation UI

Use this reference before implementing or redesigning screens.

## Direction

Aim for a premium case-file interface, not a generic template.

Good signals:

- dossier folders
- stamped evidence labels
- annotated maps
- CCTV/event strips
- timeline modules
- object-state diagrams
- witness cards
- corkboard links
- restrained dark investigation shell with warm paper/evidence surfaces
- theme-matched location imagery
- clear locked/unlocked/newly-available states
- derived progress rail with current phase, next action, and percent meters
- map pins or location cards with per-location progress and `NEXT` cue
- readable clue details and comparison cues

Avoid:

- oversized irrelevant mascot or object art
- old-fashioned default buttons
- generic card grids with no hierarchy
- text-only clue walls
- decorative gradients or blobs
- visual elements that hide actual evidence
- relying on text-only cards when the case has distinctive places or objects
- vague locked states that only say "locked" or "more clues needed"
- decorative motion that moves constantly without reflecting player progress

## First Screen

The first viewport must immediately feel like the case.

- Show case title, setting, status, and primary action.
- Include theme-matched case imagery or a dossier scene.
- Keep controls modern and compact.
- Do not build a marketing landing page.

## Evidence Visualization Patterns

Use visual modules based on clue type:

- Schedule -> timeline grid by time.
- CCTV -> recording strip with signal gaps and status labels.
- Route clue -> small map or path diagram.
- Object clue -> labeled object-state panel.
- Inventory clue -> before/after count delta.
- Photo clue -> contact sheet.
- Statement -> witness card with role, quote, and contradiction tags.
- Motive clue -> relationship or history capsule.

## Asset Pass

Create or source visual assets when the story does not provide them:

- one hero/case image for the entry screen
- one image per major investigation location
- optional evidence-cluster images for repeated cards
- visual treatment for final/decisive evidence when it becomes available

Images must support the actual investigation setting. Avoid generic dark atmosphere if players need to understand the room, object, route, or evidence state.

## Clue State UI

Every clue card should make its state obvious:

- `available`: generic title, clear investigation action
- `newly available`: highlighted border, "new" label, and action text
- `found`: evidence ID, real title, source, player-facing text
- `locked`: generic title/source/body plus a non-spoiling opening-condition panel

Locked condition panels should be compact and scan-friendly:

- prerequisite evidence progress
- board connection progress
- final-gate progress
- next useful location or clue type for undiscovered items

Do not show hidden evidence titles or final text inside locked placeholders.

## Progress Feedback UI

Make players feel progress without turning the mystery into a checklist.

- Derive every progress indicator from existing game state: collected clues, completed or visited locations, solved board rules, cleared suspects, current view/phase, and available uncollected clues.
- Do not maintain a parallel `progress` object unless persistence or network sync requires it.
- Show a compact investigation rail near the top of the play shell: current phase, overall progress, evidence percent, location percent, deduction percent, suspect-clear percent, and one next-action signal.
- Use phase chips or a spine for `briefing -> scene -> notebook -> interview -> board -> final`; highlight the current phase and mark earned phases.
- On maps, show per-location counts (`1/5`) and state styling: active, next, available, in progress, complete, locked.
- Use a `NEXT` badge only for the strongest recommended action. Preserve player choice by keeping other available actions visible.
- After evidence collection or board success, update the rail, location counts, newly available state, and unlock notice in the same render pass.

## Motion Rules

Use motion as state-change feedback, not as ambient decoration.

- Good motion: a short sweep on a progress bar after percentage changes, a pulse on the current phase or next location, a lift/fade on newly unlocked cards or notices.
- Avoid constant background animation, large decorative stamps, spinning objects, or layout movement that makes controls feel unstable.
- Respect `prefers-reduced-motion: reduce`; keep all information visible and reduce animation/transition duration to near-zero.

## Layout Rules

- Keep card radius at 8px or less unless the existing design system differs.
- Korean body copy should generally be 14px or larger.
- Text must wrap cleanly on mobile and never overflow buttons.
- Hover states may lift or glow, but must not move targets enough to dodge the cursor.
- Use stable widths/heights for board cards, map nodes, toolbars, and counters.
- Use icons for actions when a familiar symbol exists.
- Avoid nested cards inside cards.

## Visual QA Targets

Check at desktop and mobile widths:

- no horizontal overflow
- no overlapping text
- clickable targets remain stable on hover
- evidence visuals remain readable
- locked-clue condition panels remain readable
- newly-unlocked notices are visible without covering primary actions
- progress rail and percent meters are visible after start and update after collection/deduction
- map pins or location cards show per-location counts and a single readable next-action cue
- board cards and side panels do not collapse into unreadable blocks
- first screen feels case-specific and polished

## Tone

Copy should sound like an investigation file:

- precise
- restrained
- slightly official
- mystery-forward
- never jokey during evidence review

Prefer labels such as:

- `CASE FILE`
- `CONFIDENTIAL`
- `FIELD NOTE`
- `EVIDENCE`
- `WITNESS`
- `WRONG LINK REVIEW`
- `FINAL ACCUSATION`
