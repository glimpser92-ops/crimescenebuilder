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

Visualization modules are interactive case surfaces, not decoration:

- Fill them with acquired clue content, not only generic dots or labels.
- Highlight newly acquired or newly unlocked clues in their timeline, route, object-state, or conflict position.
- Keep undiscovered clue bodies, hidden meanings, final answers, and exact board prerequisites out of the visualization.
- When a board connection unlocks a clue, show the new clue's visual position and a short instruction to review that clue.

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
- soft board-connection nudges, without listing the exact evidence bundle

Do not show hidden evidence titles or final text inside locked placeholders.

## Suspect Relationship UI

Suspect files should support richer story play:

- show public relation tags and visible tensions
- distinguish claimed alibi, alibi time window, and unconfirmed gaps
- surface evidence-presentation reactions as authored beats, not generic "no comment" copy
- reveal conflict texture gradually when evidence is earned
- avoid showing hidden motive truth or real alibi until the game has unlocked it

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
- acquired clue content appears in timeline, route, object-state, or conflict visualizations
- locked-clue condition panels remain readable
- newly-unlocked notices are visible without covering primary actions
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
