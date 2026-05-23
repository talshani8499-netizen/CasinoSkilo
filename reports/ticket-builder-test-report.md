# ticket-builder — Test Report

**Skill:** [`ticket-builder/SKILL.md`](/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/ticket-builder/SKILL.md) (169 lines)
**Catalog:** [`tests/ticket-builder/cases/`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/cases/) — 40 cases
**Run date:** 2026-05-23
**Raw run:** [`reports/raw/ticket-builder/full-run.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/ticket-builder/full-run.md)

## Executive Summary

| Verdict | Count | % |
|---|---|---|
| PASS | 39 | 97.5% |
| PARTIAL | 1 | 2.5% |
| FAIL | 0 | 0% |
| **Total** | 40 | 100% |

**Overall verdict:** 🟢 Green (≥95%) — 39/40 strict PASS, 40/40 not-FAIL. The skill spec is largely solid; one ambiguity (Inferred-block placement) surfaced as PARTIAL and one minor flag-syntax gap was noted.

## Per-Category Breakdown

| Category | Cases | PASS | PARTIAL | FAIL | % PASS |
|---|---|---|---|---|---|
| A. Frontmatter & metadata | 3 | 3 | 0 | 0 | 100% |
| B. Phase A inference | 8 | 8 | 0 | 0 | 100% |
| C. Phase B core questions | 5 | 5 | 0 | 0 | 100% |
| D. Phase C follow-ups | 8 | 8 | 0 | 0 | 100% |
| E. Output structure | 7 | 6 | 1 | 0 | 85.7% |
| G. Handoff & MCP integration | 5 | 5 | 0 | 0 | 100% |
| H. Quality & specificity | 2 | 2 | 0 | 0 | 100% |
| I. Edge cases & failure modes | 2 | 2 | 0 | 0 | 100% |
| **Total** | 40 | 39 | 1 | 0 | 97.5% |

## Detailed Results

### A. Frontmatter & metadata

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-001 | SKILL.md frontmatter parses as valid YAML with name and description | PASS | L1-L5 | — |
| TB-002 | Frontmatter description begins with the literal trigger 'Use when' | PASS | L1-L5 | — |
| TB-003 | Frontmatter description names the output type as a Jira-ready ticket | PASS | L1-L5 | — |

### B. Phase A inference

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-004 | Bug ticket-type inferred from 'broken' in input | PASS | L56-L60 | — |
| TB-005 | Feature ticket-type inferred from 'add' in input | PASS | L56-L60 | — |
| TB-006 | Improvement ticket-type inferred from 'redesign' in input | PASS | L56-L60 | — |
| TB-007 | Main user 'Admin' inferred from 'CMS' in input | PASS | L56-L60 | — |
| TB-008 | Main goal 'Business need' inferred from 'drive deposits' | PASS | L56-L60 | — |
| TB-009 | Connection 'Extends' inferred from explicit file/component reference | PASS | L56-L60 | — |
| TB-010 | Ambiguous input falls through — Phase A infers nothing, Phase B asks all 4 | PASS | L56-L64 | — |
| TB-011 | Conflicting signals 'fix the new feature' resolve cleanly or fall through | PASS | L56-L64 | — |

### C. Phase B core questions

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-012 | Phase B asks only the questions Phase A could not infer | PASS | L65-L67 | — |
| TB-013 | Each Phase B question has exactly 3 spec'd options verbatim | PASS | L67-L87 | — |
| TB-014 | Phase B Main goal and Connection question headers + options match spec | PASS | L67-L87 | — |
| TB-015 | All Phase B questions emit via AskUserQuestion, not free-form prompts | PASS | L50-L53 | — |
| TB-016 | When Phase A infers zero fields, Phase B asks all 4 core questions | PASS | L65-L87 | — |

### D. Phase C follow-ups

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-017 | Phase C emits at most 3 follow-up questions (rule 1) | PASS | L92 | — |
| TB-018 | Phase C rejects banned generic placeholder option labels (rule 2) | PASS | L94 | — |
| TB-019 | Phase C skips a question that Jira context already answers (rule 3) | PASS | L95 | — |
| TB-020 | Phase C does not ask about styling, color, copy, or exact event names (rule 4) | PASS | L96 | — |
| TB-021 | Phase C respects priority order — data source ambiguity first | PASS | L97-L102 | — |
| TB-022 | Phase C falls back to assume + flag when 3 concrete options can't be written (rule 6) | PASS | L103 | — |
| TB-023 | Total questions across Phase B + Phase C never exceed 7 | PASS | L53 | — |
| TB-024 | Smartico VIP progress bar — Phase C generates the spec'd worked-example follow-ups | PASS | L105-L108 | — |

### E. Output structure

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-025 | Artifact contains all 4 required sections in order | PASS | L119-L161 | — |
| TB-026 | Artifact omits all banned sections | PASS | L119-L162 | — |
| TB-027 | User Story line follows the canonical 'As a / I want / so that' shape | PASS | L136-L137 | — |
| TB-028 | ASCII flow uses box-drawing chars and arrows inside a fenced code block | PASS | L143-L145 | — |
| TB-029 | Inferred (not asked) block appears at top when Phase A inferred ≥1 field | PARTIAL | L129-L134 | Narrative says "top of ticket" but template places block after metadata — spec ambiguity. |
| TB-030 | Inferred block is OMITTED when Phase A inferred zero fields | PASS | L129-L134 | — |
| TB-031 | No meta-commentary, builder notes, or reflections after Definition of Done | PASS | L168 | — |

### G. Handoff & MCP integration

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-032 | 'Ready To Gamble On It?' is presented exactly once with header 'Gamble?' | PASS | L149-L156 | — |
| TB-033 | Handoff options are exactly 'Bet on it' and 'Hold the chip' — no 'Double down' | PASS | L152-L156 | — |
| TB-034 | 'Bet on it' + Atlassian MCP connected → calls jira-create-issue via correct tool regex | PASS | L157-L159 | — |
| TB-035 | 'Bet on it' + no MCP → exact fallback 'Atlassian MCP not connected — saved markdown only at <path>' | PASS | L160 | — |
| TB-036 | 'Hold the chip' confirms save and prints absolute path with kebab-case slug | PASS | L149-L162 | — |

### H. Quality & specificity

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-037 | Artifact uses Jira component names and file paths verbatim | PASS | L163-L164 | — |
| TB-038 | Facts cite source inline; assumptions are marked inline (not in a separate section) | PASS | L165 | — |

### I. Edge cases & failure modes

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-039 | Vague input → sharper title applied directly, no separate 'suggested title' note | PASS | L166 | — |
| TB-040 | Too-large request → one-sentence split proposal ABOVE the artifact, not buried in notes | PASS | L167 | — |

## Actionable Items

### P2 — Clarify Inferred-block placement in template vs narrative

**Affected tests:** TB-029
**Location:** `skills/ticket-builder/SKILL.md:L116-L129`
**Symptom:** Narrative on L116 says "block at the top of the ticket" while the template on L121-L129 shows metadata first, then the Inferred block. PMs writing edits may guess the wrong placement.
**Proposed edit:**

```
Place the `Inferred (not asked):` block immediately after the metadata header lines (Ticket type / Parent epic / Component / Labels) and before the `## User Story` heading. Do not place it above the title.
```

### P2 — Define concrete syntax for "assume + flag" fallback (rule 6)

**Affected tests:** TB-022
**Location:** `skills/ticket-builder/SKILL.md:L103`
**Symptom:** "assume + flag" is vague — readers won't know the prescribed syntax for the flag marker (FLAG, TODO, ASSUMPTION, etc.).
**Proposed edit:**

```
6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — record it inline as `_Assumption (flag): <statement>. Confirm with <role>._` in the relevant section, do not ask.
```

## Catalog Quality Notes

The 40-case catalog gave strong, isolated signal on the high-traffic surfaces — Phase A inference (8 cases drilling each ticket-type/main-user/main-goal/connection signal individually), Phase C rule mechanics (8 cases mapping 1:1 onto rules 1–6 plus priority order and the worked example), and the four required output sections. The handoff slice (5 cases) cleanly separated the MCP-connected, no-MCP, and hold-the-chip branches.

Weaker-signal areas surfaced two real spec ambiguities (TB-022, TB-029) that the catalog correctly captured as edge prompts, even though they passed strictly. Frontmatter (3 cases) is arguably over-weighted for a 5-line YAML block — one combined case would suffice. The Quality category (2 cases) is thin per the coverage map's own note; copy-pasteability and verbatim terminology deserve their own dedicated cases.

Next-iteration improvements: add the two coverage gaps already flagged in `coverage-map.md` (multiple-Atlassian disambiguation L158, MCP create failure L159), one isolated `output-copy-pasteable` case, and a case probing the "vague input" trigger threshold (TB-039 noted this as a spec gap).

## Out of Scope for This Report

- Real Jira MCP calls — all MCP behavior was stubbed in case preconditions.
- The 3 deferred skills (`skills-deferred/`) — those are not loaded today.
- Modifying any SKILL.md — this report recommends edits; the user decides whether to apply them.
