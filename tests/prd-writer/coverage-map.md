# prd-writer Test Coverage Map

47 cases under `tests/prd-writer/cases/`, mapped to SKILL.md line ranges they exercise.

| Case ID  | Category               | Title                                                                                              | SKILL.md lines |
|----------|------------------------|----------------------------------------------------------------------------------------------------|----------------|
| PRD-001  | frontmatter            | SKILL.md frontmatter parses as valid YAML with name and description                                | 1–5            |
| PRD-002  | frontmatter            | Description starts with 'Use when' and names 'maturity-adapted PRD' output                         | 3–5            |
| PRD-003  | frontmatter            | Description mentions the 'Double down' chain behavior                                              | 3–5            |
| PRD-004  | phase-a-inference      | Maturity inferred as 'Initial idea' from 'we're thinking about'                                    | 53–58          |
| PRD-005  | phase-a-inference      | Maturity inferred as 'Existing feature' from 'v2 of raffles'                                       | 55–56          |
| PRD-006  | phase-a-inference      | Main user inferred as 'VIP player' from 'high rollers'                                             | 53–58          |
| PRD-007  | phase-a-inference      | Main user inferred as 'CRM operator' from 'PS Admin Panel'                                         | 53–58          |
| PRD-008  | phase-a-inference      | Main problem inferred as retention from 'churn after first deposit'                                | 53–58          |
| PRD-009  | phase-a-inference      | Success signal inferred as GGR-lift from 'increase GGR by 5%'                                      | 53–58          |
| PRD-010  | phase-a-inference      | Ambiguous input — Phase A infers nothing, Phase B asks all 4                                       | 53–64          |
| PRD-011  | phase-a-inference      | Conflicting signals (Maturity 'new' vs 'v2 of') — Phase A resolves or defers                       | 53–64          |
| PRD-012  | phase-b-core-questions | Phase B asks only the 2 questions Phase A didn't infer                                             | 62–85          |
| PRD-013  | phase-b-core-questions | Each Phase B question emits exactly 3 spec'd options (Maturity bank)                               | 65–75          |
| PRD-014  | phase-b-core-questions | Phase B question headers match the spec exactly                                                    | 65–85          |
| PRD-015  | phase-b-core-questions | Phase B uses AskUserQuestion only — no free-form prompts                                           | 62–85          |
| PRD-016  | phase-b-core-questions | When Phase A infers zero fields, Phase B asks all 4 core questions                                 | 62–85          |
| PRD-017  | phase-c-followups      | Phase C emits at most 3 follow-up questions                                                        | 90–101         |
| PRD-018  | phase-c-followups      | Phase C rejects banned generic placeholders                                                        | 90–101         |
| PRD-019  | phase-c-followups      | Phase C skips a topic already answered by Jira/Confluence context                                  | 90–101         |
| PRD-020  | phase-c-followups      | Phase C skips styling/copy/event-name questions (worked example)                                   | 90–111         |
| PRD-021  | phase-c-followups      | Phase C priority order respected — scope edges over rollout                                        | 90–101         |
| PRD-022  | phase-c-followups      | Phase C falls back to assume+flag when 3 concrete options aren't writeable                         | 90–101         |
| PRD-023  | phase-c-followups      | Total user-facing questions across Phase B + Phase C does not exceed 7                             | 62–101         |
| PRD-024  | phase-c-followups      | Good Phase C follow-ups for Community Chat MVP cut (worked example)                                | 103–111        |
| PRD-025  | output-structure       | PRD contains all 12 numbered sections in order                                                     | 125–175        |
| PRD-026  | output-structure       | §6 User Stories embeds Edge Cases as a table — not Gherkin                                         | 140–150        |
| PRD-027  | output-structure       | §7 User Flow uses box-drawing characters and arrows in a fenced code block                         | 150–160        |
| PRD-028  | output-structure       | §8 Requirements has Functional and Non-Functional subsections                                      | 155–167        |
| PRD-029  | output-structure       | §10 Analytics has Primary, Secondary, and Tracking subsections                                     | 165–175        |
| PRD-030  | output-structure       | Inferred (not asked) block at top when Phase A inferred ≥1 field                                   | 53–60          |
| PRD-031  | output-structure       | §12 Suggested Jira Breakdown includes a sub-epic title plus child ticket rows                      | 170–178        |
| PRD-032  | maturity-adaptation    | Initial idea — emphasizes Problem/Assumptions/Validation/MVP, no Open Questions section            | 116–122        |
| PRD-033  | maturity-adaptation    | Clear direction — emphasizes Requirements/Flows/Breakdown, no Dependencies section                 | 116–122        |
| PRD-034  | maturity-adaptation    | Existing feature — emphasizes Current/Proposed/Migration, no Risks section                         | 116–122        |
| PRD-035  | handoff                | Ready To Gamble On It? handoff has header 'Gamble?' and 3 spec'd options                           | 181–204        |
| PRD-036  | handoff                | Bet on it + atlassian MCP → Confluence create call with PKB params                                 | 181–190        |
| PRD-037  | handoff                | Double down chain — Confluence page + Jira sub-epic + 6 child tickets, no questions, cite PRD     | 191–204        |
| PRD-038  | handoff                | Double down + no MCP → same fallback message as Bet on it                                          | 200            |
| PRD-039  | quality                | PRD uses company terminology from context (PR-266, PR-280, Smartico, PS Admin Panel)               | 90–178         |
| PRD-040  | edge-case              | Thin §12 row ('Misc — TBD') → chained ticket defaults to Task with Open flag                       | 204            |
| PRD-041  | phase-a-inference      | Main problem inferred as Retention / re-engagement from 're-engage lapsed' signal (v1.1.0)         | 57, 80         |
| PRD-042  | phase-a-inference      | Main user surfaces `vip` sub-tag in User Story when input names VIP players (v1.1.0)               | 56             |
| PRD-043  | phase-a-inference      | Main user surfaces `crm` sub-tag in User Story when input names CRM operator + lifecycle (v1.1.0)  | 56             |
| PRD-044  | phase-a-inference      | GGR `revenue` sub-tag surfaces in §10 Primary Metric when input mentions NGR / ARPU (v1.1.0)       | 58             |
| PRD-045  | phase-a-inference      | Conflict rule — 'v2 of raffles from scratch' leaves Maturity Not inferred (v1.1.0)                 | 52             |
| PRD-046  | handoff                | Double-down chain with 26+ §12 rows triggers chain-too-long question BEFORE any Jira call (v1.1.0) | 208–214        |
| PRD-047  | handoff                | Confluence parentId 404 → retry without parentId, report space-root the page landed at (v1.1.0)    | 189            |
