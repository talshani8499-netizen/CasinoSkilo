# ticket-builder Test Catalog — Coverage Map

Single-table view of all 40 cases, the rule each covers, and the SKILL.md lines that anchor that rule. The judge sub-agent uses `skill_md_lines` as ground-truth lookup; this table is the human-readable index of the same data.

| ID | Category | Title | SKILL.md lines |
|---|---|---|---|
| TB-001 | frontmatter | SKILL.md frontmatter parses as valid YAML with name and description | 1–5 |
| TB-002 | frontmatter | Frontmatter description begins with the literal trigger 'Use when' | 1–5 |
| TB-003 | frontmatter | Frontmatter description names the output type as a Jira-ready ticket | 1–5 |
| TB-004 | phase-a-inference | Bug ticket-type inferred from 'broken' in input | 56–60 |
| TB-005 | phase-a-inference | Feature ticket-type inferred from 'add' in input | 56–60 |
| TB-006 | phase-a-inference | Improvement ticket-type inferred from 'redesign' in input | 56–60 |
| TB-007 | phase-a-inference | Main user 'Admin' inferred from 'CMS' in input | 56–60 |
| TB-008 | phase-a-inference | Main goal 'Business need' inferred from 'drive deposits' | 56–60 |
| TB-009 | phase-a-inference | Connection 'Extends' inferred from explicit file/component reference | 56–60 |
| TB-010 | phase-a-inference | Ambiguous input falls through — Phase A infers nothing, Phase B asks all 4 | 56–64 |
| TB-011 | phase-a-inference | Conflicting signals 'fix the new feature' resolve cleanly or fall through | 56–64 |
| TB-012 | phase-b-core-questions | Phase B asks only the questions Phase A could not infer | 65–67 |
| TB-013 | phase-b-core-questions | Each Phase B question has exactly 3 spec'd options verbatim | 67–87 |
| TB-014 | phase-b-core-questions | Phase B Main goal and Connection question headers + options match spec | 67–87 |
| TB-015 | phase-b-core-questions | All Phase B questions emit via AskUserQuestion, not free-form prompts | 50–53 |
| TB-016 | phase-b-core-questions | When Phase A infers zero fields, Phase B asks all 4 core questions | 65–87 |
| TB-017 | phase-c-followups | Phase C emits at most 3 follow-up questions (rule 1) | 92 |
| TB-018 | phase-c-followups | Phase C rejects banned generic placeholder option labels (rule 2) | 94 |
| TB-019 | phase-c-followups | Phase C skips a question that Jira context already answers (rule 3) | 95 |
| TB-020 | phase-c-followups | Phase C does not ask about styling, color, copy, or exact event names (rule 4) | 96 |
| TB-021 | phase-c-followups | Phase C respects priority order — data source ambiguity first | 97–102 |
| TB-022 | phase-c-followups | Phase C falls back to assume + flag when 3 concrete options can't be written (rule 6) | 103 |
| TB-023 | phase-c-followups | Total questions across Phase B + Phase C never exceed 7 | 53 |
| TB-024 | phase-c-followups | Smartico VIP progress bar — Phase C generates the spec'd worked-example follow-ups | 105–108 |
| TB-025 | output-structure | Artifact contains all 4 required sections in order | 119–161 |
| TB-026 | output-structure | Artifact omits all banned sections (Background, Context, Problem, Scope, FRs, etc.) | 119–162 |
| TB-027 | output-structure | User Story line follows the canonical 'As a / I want / so that' shape | 136–137 |
| TB-028 | output-structure | ASCII flow uses box-drawing chars and arrows inside a fenced code block | 143–145 |
| TB-029 | output-structure | Inferred (not asked) block appears at top when Phase A inferred ≥1 field | 129–134 |
| TB-030 | output-structure | Inferred block is OMITTED when Phase A inferred zero fields | 129–134 |
| TB-031 | output-structure | No meta-commentary, builder notes, or reflections after Definition of Done | 168 |
| TB-032 | handoff | 'Ready To Gamble On It?' is presented exactly once with header 'Gamble?' | 149–156 |
| TB-033 | handoff | Handoff options are exactly 'Bet on it' and 'Hold the chip' — no 'Double down' | 152–156 |
| TB-034 | handoff | 'Bet on it' + Atlassian MCP connected → calls jira-create-issue via correct tool regex | 157–159 |
| TB-035 | handoff | 'Bet on it' + no MCP → exact fallback 'Atlassian MCP not connected — saved markdown only at <path>' | 160 |
| TB-036 | handoff | 'Hold the chip' confirms save and prints absolute path with kebab-case slug | 149–162 |
| TB-037 | quality | Artifact uses Jira component names and file paths verbatim (not generic placeholders) | 163–164 |
| TB-038 | quality | Facts cite source inline; assumptions are marked inline (not in a separate section) | 165 |
| TB-039 | edge-case | Vague input → sharper title applied directly, no separate 'suggested title' note | 166 |
| TB-040 | edge-case | Too-large request → one-sentence split proposal ABOVE the artifact, not buried in notes | 167 |

## Category totals

| Category | Count | ID range |
|---|---|---|
| frontmatter | 3 | TB-001 – TB-003 |
| phase-a-inference | 8 | TB-004 – TB-011 |
| phase-b-core-questions | 5 | TB-012 – TB-016 |
| phase-c-followups | 8 | TB-017 – TB-024 |
| output-structure | 7 | TB-025 – TB-031 |
| handoff | 5 | TB-032 – TB-036 |
| quality | 2 | TB-037 – TB-038 |
| edge-case | 2 | TB-039 – TB-040 |
| **Total** | **40** | |

## Assertion ID usage

All `pass_criteria` entries use IDs from [`../rubric/pass-criteria-vocabulary.md`](../rubric/pass-criteria-vocabulary.md). No new assertion IDs were added — the existing vocabulary covered every rule in scope for this skill.

## Known coverage gaps

- **Multiple-atlassian disambiguation** is mentioned in SKILL.md line 158 ("if multiple Jira MCPs are connected, ask the user which one to use") but no dedicated case was budgeted in the 40 — the generic `multiple-atlassian-asks-which` assertion is available in the vocabulary if the catalog is later extended. The user's category distribution gave the `multiple-atlassian` mcp_state to handoff cases only as a variant, but the per-category quota didn't leave a slot for a standalone case.
- **MCP create failure** (SKILL.md line 159: "If the create fails, report the error and confirm the markdown file is still saved") is covered by the vocabulary's `mcp-create-failure-confirms-markdown-saved` but not in a dedicated case here — the 5-handoff-case budget was spent on the higher-frequency branches (single MCP, no MCP, hold-the-chip).
- **Quality category is intentionally thin** (2 cases) per the distribution; rules around "copy-pasteable markdown" (line 167) are touched by TB-037 (`output-copy-pasteable`) but not isolated to their own case.
