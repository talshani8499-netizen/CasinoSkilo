# competitor-research Test Coverage Map

40 YAML cases under `cases/`. Each row links one case to its SKILL.md anchor.

| Case ID | Category | Title | SKILL.md lines |
|---|---|---|---|
| CR-001 | frontmatter | SKILL.md frontmatter parses as valid YAML with name and description | 1–5 |
| CR-002 | frontmatter | Description begins with 'Use when' trigger phrase | 3–5 |
| CR-003 | frontmatter | Description names output type and clarifies research-only (no Jira tickets) | 3–5 |
| CR-004 | phase-a-inference | Focus inferred as 'Onboarding' from 'compare our signup to competitors' | 67–73 |
| CR-005 | phase-a-inference | Focus inferred as 'Pricing/Bonuses' from 'how do they price welcome bonuses?' | 67–73 |
| CR-006 | phase-a-inference | Output emphasis inferred as 'UX flow + screenshots' from 'walk me through their flow' | 67–73 |
| CR-007 | phase-a-inference | Depth inferred as 'Deep UX flow' from 'every screen, frame by frame' | 67–73 |
| CR-008 | phase-a-inference | Depth inferred as 'Quick scan' from '30-minute scan' | 67–73 |
| CR-009 | phase-a-inference | Competitors NOT inferred when memory has no list and input is generic | 67–73 |
| CR-010 | phase-a-inference | Ambiguous fall-through: vague 'check what others are doing' infers nothing | 67–73 |
| CR-011 | phase-a-inference | Multi-signal conflict: 'quick deep dive' resolves to one Depth or stays uninferred | 67–73 |
| CR-012 | phase-b-core-questions | Phase B asks only the questions Phase A didn't infer | 78–98 |
| CR-013 | phase-b-core-questions | Each Phase B question has exactly 3 concrete options matching the spec verbatim | 80–98 |
| CR-014 | phase-b-core-questions | Phase B headers match spec verbatim: Focus / Targets / Output / Depth | 80–98 |
| CR-015 | phase-b-core-questions | When Phase A infers zero fields, Phase B asks all 4 core questions | 78–98 |
| CR-016 | phase-b-core-questions | Competitors question label substitutes real names from memory at runtime | 85–88 |
| CR-017 | phase-c-followups | Phase C emits at most 3 follow-up questions | 103–113 |
| CR-018 | phase-c-followups | Phase C rejects banned placeholder options | 106–108 |
| CR-019 | phase-c-followups | Phase C skips region question when input already names a market | 109–110 |
| CR-020 | phase-c-followups | Phase C does NOT ask about screenshot filenames | 111–120 |
| CR-021 | phase-c-followups | Phase C does NOT re-ask 'use existing competitors or different ones?' | 111–122 |
| CR-022 | phase-c-followups | Phase C respects CR-specific priority order (region > source mix > time horizon > auth) | 111–113 |
| CR-023 | phase-c-followups | Phase C falls back to assume+flag when no 3 concrete options exist | 112–113 |
| CR-024 | phase-c-followups | Good follow-ups: 21.com region + third-party source-mix scenario asks both with concrete options | 115–122 |
| CR-025 | output-structure | Output contains all 7 numbered sections in order | 155–200 |
| CR-026 | output-structure | Metadata table at top has Status / Author / Date / Depth / Region scope rows | 159–165 |
| CR-027 | output-structure | §4 Comparison Table has at least 4 rows from canonical labels | 175–185 |
| CR-028 | output-structure | §5 UX Flow Notes references screenshots inline — no separate Screenshots section | 185–195 |
| CR-029 | output-structure | §6 Key Patterns distinguishes table-stakes vs. differentiation | 195–200 |
| CR-030 | output-structure | Output ends at §7 — no Jira tickets generated, no meta-commentary | 200–244 |
| CR-031 | output-structure | Inferred (not asked) block appears at top when Phase A inferred at least one field | 165–175 |
| CR-032 | depth-adaptation | Quick scan depth → 3–5 opportunities, screenshots optional | 143–145 |
| CR-033 | depth-adaptation | Detailed comparison → full matrix + key-surface screenshots + prioritized recs | 145–147 |
| CR-034 | depth-adaptation | Deep UX flow → per-competitor step-by-step + friction + every-screen screenshots + side-by-side + experiments | 147–148 |
| CR-035 | handoff | Ready To Gamble On It? presented with exactly 2 options: Bet on it + Hold the chip | 226–230 |
| CR-036 | handoff | Bet on it + atlassian MCP → Confluence create with PKB spaceId/parentId and markdown format | 234–238 |
| CR-037 | handoff | After Confluence publish, surfaces one-line note: screenshots are local-only | 239 |
| CR-038 | handoff | Markdown saved to ~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md with co-located screenshots subdir | 224 |
| CR-039 | quality | Findings are specific, cite source, and call out missing/inaccessible pages | 205–220 |
| CR-040 | edge-case | Memory edge cases: differs (confirm inline) / empty (cache after Phase B) / Playwright off / robots.txt | 247 |
