# ticket-builder — Test Report (v1.2.0)

**Skill:** [`skills/ticket-builder/SKILL.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/skills/ticket-builder/SKILL.md) (198 lines, **unchanged from v1.1.0** — v1.2.0 is a catalog-only release)
**Catalog:** [`tests/ticket-builder/cases/`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/cases/) — 49 cases (40 original + 9 v1.1.0-backfill)
**Run date:** 2026-05-23
**Raw run:** [`reports/raw/ticket-builder/full-run-v1.2.0.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/ticket-builder/full-run-v1.2.0.md)
**v1.1.0 baseline:** [`reports/ticket-builder-test-report-v1.1.0.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/ticket-builder-test-report-v1.1.0.md) (40/0/0 Green, 100%)

## Executive Summary

| Verdict | Count | % |
|---|---|---|
| PASS | 49 | 100% |
| PARTIAL | 0 | 0% |
| FAIL | 0 | 0% |
| **Total** | 49 | 100% |

**Overall verdict:** 🟢 Green (100%) — 49/49 strict PASS, 49/49 not-FAIL. Up from v1.1.0's 40/0/0 — same Green percentage, +9 cases of coverage. No SKILL.md changes (byte-identical at 198 lines). The 9 new v1.1.0-backfill cases (TB-041…TB-049) all PASS on first scoring, locking in the eight TB-Δ behaviors that v1.1.0 introduced but the original 40-case catalog did not isolate. Zero regressions across TB-001…TB-040.

## Per-Category Breakdown

| Category | Cases | PASS | PARTIAL | FAIL | % PASS |
|---|---|---|---|---|---|
| A. Frontmatter & metadata | 3 | 3 | 0 | 0 | 100% |
| B. Phase A inference | 11 | 11 | 0 | 0 | 100% |
| C. Phase B core questions | 5 | 5 | 0 | 0 | 100% |
| D. Phase C follow-ups | 10 | 10 | 0 | 0 | 100% |
| E. Output structure | 9 | 9 | 0 | 0 | 100% |
| G. Handoff & MCP integration | 7 | 7 | 0 | 0 | 100% |
| H. Quality & specificity | 2 | 2 | 0 | 0 | 100% |
| I. Edge cases & failure modes | 2 | 2 | 0 | 0 | 100% |
| **Total** | 49 | 49 | 0 | 0 | 100% |

Cell-count expansions vs v1.1.0: Phase A inference 8 → 11 (TB-041, TB-042, TB-047), Phase C follow-ups 8 → 10 (TB-043, TB-046), Output structure 7 → 9 (TB-044, TB-045), Handoff 5 → 7 (TB-048, TB-049). No new categories.

## Detailed Results

### A. Frontmatter & metadata

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-001 | SKILL.md frontmatter parses as valid YAML with name and description | PASS → PASS (unchanged) | L1-L5 | Frontmatter unchanged in v1.2.0. |
| TB-002 | Frontmatter description begins with the literal trigger 'Use when' | PASS → PASS (unchanged) | L1-L5 | — |
| TB-003 | Frontmatter description names the output type as a Jira-ready ticket | PASS → PASS (unchanged) | L1-L5 | — |

### B. Phase A inference

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-004 | Bug ticket-type inferred from 'broken' in input | PASS → PASS (unchanged) | L56-L60 | — |
| TB-005 | Feature ticket-type inferred from 'add' in input | PASS → PASS (unchanged) | L56-L60 | — |
| TB-006 | Improvement ticket-type inferred from 'redesign' in input | PASS → PASS (unchanged) | L56-L60 | — |
| TB-007 | Main user 'Admin' inferred from 'CMS' in input | PASS → PASS (unchanged) | L56-L60 | — |
| TB-008 | Main goal 'Business need' inferred from 'drive deposits' | PASS → PASS (unchanged) | L56-L60 | — |
| TB-009 | Connection 'Extends' inferred from explicit file/component reference | PASS → PASS (unchanged) | L56-L60 | — |
| TB-010 | Ambiguous input falls through — Phase A infers nothing, Phase B asks all 4 | PASS → PASS (unchanged) | L56-L64 | — |
| TB-011 | Conflicting signals 'fix the new feature' resolve cleanly or fall through | PASS → PASS (unchanged) | L56-L64 | — |
| TB-041 | Phase A infers 'Needs flow diagram = Yes' from 'new feature' signal | **NEW → PASS** | L61, L150 | Locks in TB-Δ-1 positive path. "new feature" signal fires cleanly; §User Flow rendered. Needs flow diagram drops into the L139 overflow line when all 5 fields infer. |
| TB-042 | Phase A infers 'Needs flow diagram = No' from 'bug' + 'config'; §User Flow omitted entirely | **NEW → PASS** | L61, L150 | Locks in TB-Δ-1 negative path. Both "bug" AND "config" signals agree on No (no L53 conflict). §User Flow heading and code block are both absent — not rendered as "N/A" or as an empty section. |
| TB-047 | Conflict rule — 'fix the new feature on iOS' leaves Ticket type Not inferred | **NEW → PASS** | L53 | Locks in TB-Δ-7 conflict rule. Both "fix" (→ Bug) and "new feature" (→ Feature) fire on the same Ticket type field; field marked Not inferred; no invented tie-break; Phase B asks the canonical Ticket type question. |

### C. Phase B core questions

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-012 | Phase B asks only the questions Phase A could not infer | PASS → PASS (unchanged) | L65-L67 | — |
| TB-013 | Each Phase B question has exactly 3 spec'd options verbatim | PASS → PASS (unchanged) | L67-L87 | — |
| TB-014 | Phase B Main goal and Connection question headers + options match spec | PASS → PASS (unchanged) | L67-L87 | — |
| TB-015 | All Phase B questions emit via AskUserQuestion, not free-form prompts | PASS → PASS (unchanged) | L50-L53 | — |
| TB-016 | When Phase A infers zero fields, Phase B asks all 4 core questions | PASS → PASS (unchanged) | L65-L87 | — |

### D. Phase C follow-ups

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-017 | Phase C emits at most 3 follow-up questions (rule 1) | PASS → PASS (unchanged) | L92 | — |
| TB-018 | Phase C rejects banned generic placeholder option labels (rule 2) | PASS → PASS (unchanged) | L94 | — |
| TB-019 | Phase C skips a question that Jira context already answers (rule 3) | PASS → PASS (unchanged) | L95 | — |
| TB-020 | Phase C does not ask about styling, color, copy, or exact event names (rule 4) | PASS → PASS (unchanged) | L96 | — |
| TB-021 | Phase C respects priority order — data source ambiguity first | PASS → PASS (unchanged) | L97-L102 | — |
| TB-022 | Phase C falls back to assume + flag when 3 concrete options can't be written (rule 6) | PASS → PASS (unchanged) | L103 | — |
| TB-023 | Total questions across Phase B + Phase C never exceed 7 | PASS → PASS (unchanged) | L53, L114 | — |
| TB-024 | Smartico VIP progress bar — Phase C generates the spec'd worked-example follow-ups | PASS → PASS (unchanged) | L105-L108 | — |
| TB-043 | Ambiguous input → Phase C 'Flow?' fallback fires with 3 spec'd options | **NEW → PASS** | L106-L114 | Locks in TB-Δ-1 Phase C fallback. Header `Flow?` and the 3 options match L107-L112 verbatim; counted inside the Phase C 3-cap per L114. Total Phase C = 3, total questions = 3, well within 7-cap. |
| TB-046 | 'Assume + flag' inline syntax matches the spec'd '> **Assumption:** … **Flag:** …' format | **NEW → PASS** | L104 | Locks in TB-Δ-6 syntax. Rendered line matches the regex `> \*\*Assumption:\*\* .+ \*\*Flag:\*\* .+` exactly; placed inside the Description (not in a separate section). |

### E. Output structure

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-025 | Artifact contains all 4 required sections in order | PASS → PASS (unchanged) | L119-L161 | — |
| TB-026 | Artifact omits all banned sections | PASS → PASS (unchanged) | L119-L162 | — |
| TB-027 | User Story line follows the canonical 'As a / I want / so that' shape | PASS → PASS (unchanged) | L136-L137 | — |
| TB-028 | ASCII flow uses box-drawing chars and arrows inside a fenced code block | PASS → PASS (unchanged) | L143-L145 | — |
| TB-029 | Inferred (not asked) block appears at top when Phase A inferred ≥1 field | PASS → PASS (unchanged) | L127, L139 | Placement narrative resolved in v1.1.0 (TB-Δ-5); stable in v1.2.0. |
| TB-030 | Inferred block is OMITTED when Phase A inferred zero fields | PASS → PASS (unchanged) | L129-L134 | — |
| TB-031 | No meta-commentary, builder notes, or reflections after Definition of Done | PASS → PASS (unchanged) | L168 | — |
| TB-044 | DoD hard cap enforced — multi-component bug naïvely yielding 8 items trimmed to ≤5 | **NEW → PASS** | L155 | Locks in TB-Δ-2 DoD cap. Naïve 8-item list trimmed to exactly 5; MGA reconciliation thread collapsed into a single follow-up-ticket bullet rather than expanded inline. |
| TB-045 | Inferred block 4-bullet cap + overflow marker when Phase A infers all 5 fields | **NEW → PASS** | L139 | Locks in TB-Δ-3 4-bullet cap + overflow. Inferred block renders exactly 4 bullets in the L139 priority order (Ticket type > Connection > Main user > Main goal > Needs flow diagram); 5th field surfaces via the italic `_(+1 more inferred — see context for full set)_` line. |

### G. Handoff & MCP integration

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-032 | 'Ready To Gamble On It?' is presented exactly once with header 'Gamble?' | PASS → PASS (unchanged) | L149-L156 | — |
| TB-033 | Handoff options are exactly 'Bet on it' and 'Hold the chip' — no 'Double down' | PASS → PASS (unchanged) | L152-L156 | — |
| TB-034 | 'Bet on it' + Atlassian MCP connected → calls jira-create-issue via correct tool regex | PASS → PASS (unchanged) | L157-L159 | — |
| TB-035 | 'Bet on it' + no MCP → exact fallback 'Atlassian MCP not connected — saved markdown only at <path>' | PASS → PASS (unchanged) | L160 | — |
| TB-036 | 'Hold the chip' confirms save and prints absolute path with kebab-case slug | PASS → PASS (unchanged) | L149-L162 | — |
| TB-048 | PRD-driven mode — zero questions, all 5 inferences cite PRD section, auto Bet on it | **NEW → PASS** | L186-L198 | **Marquee case for v1.2.0.** Locks in TB-Δ-8 PRD-driven mode end-to-end: Phase B = 0 questions (L189), Phase C = 0 questions including the Needs flow diagram fallback (L190), all 5 inferences cite a specific PRD section (L191), Inferred block rendered with PRD citations (L192), auto Bet on it without AskUserQuestion (L195), `parentEpicKey: PR-484` supplied on the create call (L195), per-chain question count = 0 (L196). |
| TB-049 | PRD-driven mode — thin §12 row 'Misc — TBD' defaults to type Task with inline Open flag | **NEW → PASS** | L194 | Locks in TB-Δ-8 thin-row default. `**Ticket type:** Task` in metadata; Description contains the spec'd inline `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` blockquote verbatim; `issueType: Task` on the Jira create call. |

### H. Quality & specificity

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-037 | Artifact uses Jira component names and file paths verbatim | PASS → PASS (unchanged) | L163-L164 | — |
| TB-038 | Facts cite source inline; assumptions are marked inline (not in a separate section) | PASS → PASS (unchanged) | L165 | — |

### I. Edge cases & failure modes

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-039 | Vague input → sharper title applied directly, no separate 'suggested title' note | PASS → PASS (unchanged) | L166 | — |
| TB-040 | Too-large request → one-sentence split proposal ABOVE the artifact, not buried in notes | PASS → PASS (unchanged) | L167 | — |

## Delta vs v1.1.0

### Verdict flips
**None.** All 40 v1.1.0 PASS cases (TB-001…TB-040) remain PASS in v1.2.0. SKILL.md is byte-identical to v1.1.0 (198 lines, same frontmatter, same Phase A signal table including row 5 `Needs flow diagram`, same Phase C 3-cap with Flow? fallback counted, same DoD 3–5 cap, same 4-bullet Inferred cap, same `> **Assumption:** … **Flag:** …` syntax, same PRD-driven mode block at L186–L198), so no spec-driven drift is possible and none was observed.

### Regressions
**0 regressions** among TB-001…TB-040. The 9 new TB-041…TB-049 backfill cases all PASS first time. The TB-048 PRD-driven mode marquee case is verified end-to-end against L186-L198.

### v1.1.0-backfill cases — all PASS first time

| ΔID locked in | Case(s) | Outcome |
|---|---|---|
| TB-Δ-1 (Needs flow diagram + §User Flow conditional + Phase C `Flow?` fallback) | TB-041 (Yes path), TB-042 (No path, §User Flow omitted), TB-043 (Phase C fallback) | PASS, PASS, PASS |
| TB-Δ-2 (DoD 3–5 hard cap) | TB-044 (8 naïve items trimmed to 5) | PASS |
| TB-Δ-3 (Inferred block 4-bullet cap + overflow marker) | TB-045 (all 5 fields → 4 bullets + italic overflow) | PASS |
| TB-Δ-6 (`> **Assumption:** … **Flag:** …` inline syntax) | TB-046 (regex match verbatim) | PASS |
| TB-Δ-7 (L53 conflict rule — multiple signal rows fire on same field → Not inferred) | TB-047 ("fix the new feature" → Ticket type Not inferred) | PASS |
| TB-Δ-8 (PRD-driven mode — zero questions, auto Bet on it, parent epic key, thin-row default) | TB-048 (full chain), TB-049 (thin §12 row → Task) | PASS, PASS |

Of the eight TB-Δ behaviors introduced in v1.1.0, six are now directly asserted by a backfill case. TB-Δ-4 (Description audit hint) and TB-Δ-5 (Inferred-block placement narrative) remain implicitly exercised by the broader output-structure cases — no dedicated case was budgeted because TB-029 already locked in the placement narrative in v1.1.0.

## Actionable Items

**No actionable items at v1.2.0.** The 9 new backfill cases all PASS, and no v1.1.0 case regressed. SKILL.md is unchanged and stable at 198 lines.

## Note on Section M vocabulary additions

The 9 v1.1.0-backfill cases (TB-041…TB-049) introduced 6 new assertion IDs under section M ("ticket-builder v1.1.0 additions") of [`tests/ticket-builder/rubric/pass-criteria-vocabulary.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/rubric/pass-criteria-vocabulary.md):

| Assertion ID | Used by | Locks in |
|---|---|---|
| `dod-item-count-within-cap` | TB-044 | TB-Δ-2 DoD 3–5 hard cap |
| `inferred-block-cap-respected` | TB-045 | TB-Δ-3 Inferred block 4-bullet cap + overflow marker + priority order |
| `assume-flag-syntax-format` | TB-046 | TB-Δ-6 inline `> **Assumption:** … **Flag:** …` regex |
| `prd-driven-mode-zero-questions` | TB-048, TB-049 | TB-Δ-8 L189/L190/L196 (zero Phase B + zero Phase C + zero per-chain) |
| `prd-driven-mode-auto-bet-on-it` | TB-048, TB-049 | TB-Δ-8 L195 (auto Bet on it, no AskUserQuestion, parent epic key supplied) |
| `prd-driven-mode-thin-row-default` | TB-049 | TB-Δ-8 L194 (thin §12 row defaults to Task + inline Open flag) |

TB-042 additionally exercises the existing `output-omits-banned-sections` assertion with `User Flow` as the banned section — a new context for that existing ID (User Flow is conditionally banned IFF `Needs flow diagram = No`).

## Out of Scope for This Report

- Real Jira MCP calls — all MCP behavior was stubbed in case preconditions.
- The 3 deferred skills (`skills-deferred/`) — those are not loaded today.
- Modifying any SKILL.md — this report documents the v1.2.0 state; SKILL.md is byte-identical to v1.1.0 and no edits are recommended at this verdict level.
- The carryover v1.0.0 coverage gaps (multiple-Atlassian disambiguation L158, MCP create failure L159, isolated `output-copy-pasteable`, vague-input trigger threshold) remain catalog-extension suggestions, not actionable items against the skill itself.
