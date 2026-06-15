# Prompt Template

Use this reference to write the final copy-paste prompt. Adapt labels to the user's language.

## Prompt Skeleton

```markdown
# Build Prompt: [Game Title]

You are building a polished browser-based mystery investigation game.

## 1. Core Goal
[Explain the playable experience, target players, device context, and session length.]

## 2. Non-Negotiable Constraints
- [Framework / file target]
- [No backend / storage / network constraints]
- [Language, tone, accessibility]
- [Preserve canon facts]

## 3. Game Canon
- Apparent incident:
- True incident:
- Culprit:
- Motive:
- Method:
- Opportunity:
- Staging/concealment:
- Decisive proof:
- Final lesson or epilogue:

## 4. Player Flow
1. Team setup
2. Briefing
3. Investigation hub
4. Location search
5. Evidence notebook
6. Suspect questioning
7. Contradiction board
8. Final accusation
9. Reveal sequence
10. Result screen

## 5. Suspects
[Table with id, name, role, surface suspicion, real secret, claimed alibi, real alibi, clearing evidence, key reactions.]

## 6. Locations
[Table with id, name, round, scene state, available evidence, unlock condition, visual role.]

## 7. Evidence Cards
[Table or structured list. Include all IDs, title, source, tags, player text, true meaning, supports, implicates, clears, dependencies, reveal phase.]

## 8. Timeline and Movement
[Time-slot table showing claimed and real movement, object transfers, witnesses, blind spots, and key contradictions.]

## 9. Contradiction Board Rules
[List rules with required IDs, insight title, result copy, kind, unlocks, and non-spoiling type hints.]

## 10. Suspect Questioning
[Question budget, base statements, question options, evidence-presentation reactions.]

## 11. Hints and Anti-Stuck Design
[Hint ladder and forbidden hint leakage.]

## 12. Scoring
[Point table and result tiers.]

## 13. Reveal Sequence
[6-10 reveal steps with exact truth explanation.]

## 14. Visual and UX Direction
[Mood, palette, typography feel, layout, icon use, evidence visualization requirements, mobile/tablet behavior.]

## 15. Technical Implementation Requirements
- Use structured constants near the top.
- Use data-driven rendering for suspects, evidence, locations, board rules, and reveal steps.
- Add helper functions for card lookup, rule matching, unlocks, score calculation, and final validation.
- Include responsive layout and accessible controls.
- Avoid placeholder screens and unused data.

## 16. Suggested Components
[Component list appropriate to the target framework.]

## 17. Acceptance Checklist
- [ ] Game starts at the playable experience.
- [ ] Every evidence card is visible through normal play.
- [ ] The culprit can be proven before the reveal.
- [ ] At least two proof paths converge.
- [ ] Every innocent suspect has a suspicious path and clearing path.
- [ ] Wrong board feedback does not reveal exact answer bundles.
- [ ] Final accusation validates culprit, motive/method, and evidence.
- [ ] Reveal explains timeline, motive, method, and red herrings.
- [ ] Mobile/tablet layout has no horizontal overflow.
- [ ] No backend, network, or persistent storage if constrained.
```

## Writing Rules

- Make the prompt direct and executable: tell the builder exactly what to build.
- Put canon truth inside the prompt; it is an author-facing build artifact.
- Include enough data that the builder does not need to invent the mystery logic.
- Keep implementation advice concrete but not over-prescriptive unless the user has named a stack.
- If the user asks for a Claude-style artifact prompt, explicitly say "single React default export" and list allowed libraries.
- If the user asks for Codex/repo implementation, describe the desired app behavior and tell the builder to follow the existing repo framework.

## Default React Artifact Constraints

Use when no target platform is given:

- single React component file
- default export
- no server
- no external fetch
- no localStorage/sessionStorage
- Tailwind utility classes allowed if available
- lucide-react icons allowed if available
- SVG/CSS avatars and diagrams are acceptable
- all data constants in the file
- large tap targets for shared-device play
