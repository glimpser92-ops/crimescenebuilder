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

Avoid:

- oversized irrelevant mascot or object art
- old-fashioned default buttons
- generic card grids with no hierarchy
- text-only clue walls
- decorative gradients or blobs
- visual elements that hide actual evidence

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
