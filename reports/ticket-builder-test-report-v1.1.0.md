# ticket-builder — Test Report (v1.1.0)

**Skill:** [`skills/ticket-builder/SKILL.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/skills/ticket-builder/SKILL.md) (198 lines)
**Catalog:** [`tests/ticket-builder/cases/`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/cases/) — 40 cases
**Run date:** 2026-05-23
**Raw run:** [`reports/raw/ticket-builder/full-run-v1.1.0.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/ticket-builder/full-run-v1.1.0.md)
**v1.0.0 baseline:** [`reports/ticket-builder-test-report.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/ticket-builder-test-report.md) (39/1/0 Green, 97.5%)

## Executive Summary

| Verdict | Count | % |
|---|---|---|
| PASS | 40 | 100% |
| PARTIAL | 0 | 0% |
| FAIL | 0 | 0% |
| **Total** | 40 | 100% |

**Overall verdict:** 🟢 Green (100%) — 40/40 strict PASS, 40/40 not-FAIL. Up from v1.0.0's 39/1/0 Green (97.5%). The v1.1.0 SKILL.md cleanly resolves the lone v1.0.0 PARTIAL (TB-029) via the TB-Δ-5 spec update and addresses both v1.0.0 P2 actionable items (Inferred-block placement and assume+flag flag syntax) without introducing any regressions across the 40 catalogued assertions.

## Per-Category Breakdown

| Category | Cases | PASS | PARTIAL | FAIL | % PASS |
|---|---|---|---|---|---|
| A. Frontmatter & metadata | 3 | 3 | 0 | 0 | 100% |
| B. Phase A inference | 8 | 8 | 0 | 0 | 100% |
| C. Phase B core questions | 5 | 5 | 0 | 0 | 100% |
| D. Phase C follow-ups | 8 | 8 | 0 | 0 | 100% |
| E. Output structure | 7 | 7 | 0 | 0 | 100% |
| G. Handoff & MCP integration | 5 | 5 | 0 | 0 | 100% |
| H. Quality & specificity | 2 | 2 | 0 | 0 | 100% |
| I. Edge cases & failure modes | 2 | 2 | 0 | 0 | 100% |
| **Total** | 40 | 40 | 0 | 0 | 100% |

## Detailed Results

### A. Frontmatter & metadata

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-001 | SKILL.md frontmatter parses as valid YAML with name and description | PASS → PASS | L1-L5 | Frontmatter unchanged in v1.1.0. |
| TB-002 | Frontmatter description begins with the literal trigger 'Use when' | PASS → PASS | L1-L5 | — |
| TB-003 | Frontmatter description names the output type as a Jira-ready ticket | PASS → PASS | L1-L5 | — |

### B. Phase A inference

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-004 | Bug ticket-type inferred from 'broken' in input | PASS → PASS | L56-L60 | Artifact now correctly omits User Flow per TB-Δ-1 (bug class → flow diagram No). Not asserted by this case. |
| TB-005 | Feature ticket-type inferred from 'add' in input | PASS → PASS | L56-L60 | v1.1.0 improvements (TB-Δ-2 DoD cap, TB-Δ-3 4-bullet cap) applied as bonus quality. |
| TB-006 | Improvement ticket-type inferred from 'redesign' in input | PASS → PASS | L56-L60 | First case to exercise TB-Δ-3 5+ inference overflow handling — 4 priority bullets + italic overflow line. |
| TB-007 | Main user 'Admin' inferred from 'CMS' in input | PASS → PASS | L56-L60 | — |
| TB-008 | Main goal 'Business need' inferred from 'drive deposits' | PASS → PASS | L56-L60 | — |
| TB-009 | Connection 'Extends' inferred from explicit file/component reference | PASS → PASS | L56-L60 | — |
| TB-010 | Ambiguous input falls through — Phase A infers nothing, Phase B asks all 4 | PASS → PASS | L56-L64 | v1.1.0 adds Phase C `Flow?` fallback Q (TB-Δ-1); counted against 3-cap, total still ≤ 7. |
| TB-011 | Conflicting signals 'fix the new feature' resolve cleanly or fall through | PASS → PASS | L56-L64 | TB-Δ-7 conflict rule (L53) now formalizes: when multiple signal rows fire on the same field → Not inferred. Resolves v1.0.0 ambiguity. |

### C. Phase B core questions

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-012 | Phase B asks only the questions Phase A could not infer | PASS → PASS | L65-L67 | — |
| TB-013 | Each Phase B question has exactly 3 spec'd options verbatim | PASS → PASS | L67-L87 | — |
| TB-014 | Phase B Main goal and Connection question headers + options match spec | PASS → PASS | L67-L87 | — |
| TB-015 | All Phase B questions emit via AskUserQuestion, not free-form prompts | PASS → PASS | L50-L53 | — |
| TB-016 | When Phase A infers zero fields, Phase B asks all 4 core questions | PASS → PASS | L65-L87 | — |

### D. Phase C follow-ups

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-017 | Phase C emits at most 3 follow-up questions (rule 1) | PASS → PASS | L92 | 3-cap honored even under pressure. `Flow?` fallback (TB-Δ-1) suppressed when already inferred. |
| TB-018 | Phase C rejects banned generic placeholder option labels (rule 2) | PASS → PASS | L94 | — |
| TB-019 | Phase C skips a question that Jira context already answers (rule 3) | PASS → PASS | L95 | Skipped Q now converts to inline assumption using TB-Δ-6 syntax (`> **Assumption:** … **Flag:** …`). |
| TB-020 | Phase C does not ask about styling, color, copy, or exact event names (rule 4) | PASS → PASS | L96 | TB-Δ-6 assume+flag syntax now formalized — v1.0.0 P2 ambiguity gone. |
| TB-021 | Phase C respects priority order — data source ambiguity first | PASS → PASS | L97-L102 | — |
| TB-022 | Phase C falls back to assume + flag when 3 concrete options can't be written (rule 6) | PASS → PASS | L103 | v1.0.0 P2 ("define concrete flag syntax") resolved by TB-Δ-6. |
| TB-023 | Total questions across Phase B + Phase C never exceed 7 | PASS → PASS | L53, L114 | Verified regression-safe: `Flow?` fallback counts inside Phase C 3-cap (per L114), so worst case 4+3 = 7. |
| TB-024 | Smartico VIP progress bar — Phase C generates the spec'd worked-example follow-ups | PASS → PASS | L105-L108 | — |

### E. Output structure

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-025 | Artifact contains all 4 required sections in order | PASS → PASS | L119-L161 | Verified regression-safe — feature input ("VIP progress bar") triggers `Needs flow diagram = Yes`, so User Flow remains present. |
| TB-026 | Artifact omits all banned sections | PASS → PASS | L119-L162 | Lean output even with rich tempting context. DoD = 5 (cap respected, TB-Δ-2). |
| TB-027 | User Story line follows the canonical 'As a / I want / so that' shape | PASS → PASS | L136-L137 | — |
| TB-028 | ASCII flow uses box-drawing chars and arrows inside a fenced code block | PASS → PASS | L143-L145 | — |
| TB-029 | Inferred (not asked) block appears at top when Phase A inferred ≥1 field | **PARTIAL → PASS (TB-Δ-5)** | L127, L139 | v1.0.0 PARTIAL resolved. L127 updated to: "immediately after the 4 metadata header lines (Ticket type / Parent epic / Component / Labels), before `## User Story`" — now matches template exactly. |
| TB-030 | Inferred block is OMITTED when Phase A inferred zero fields | PASS → PASS | L129-L134 | — |
| TB-031 | No meta-commentary, builder notes, or reflections after Definition of Done | PASS → PASS | L168 | — |

### G. Handoff & MCP integration

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-032 | 'Ready To Gamble On It?' is presented exactly once with header 'Gamble?' | PASS → PASS | L149-L156 | — |
| TB-033 | Handoff options are exactly 'Bet on it' and 'Hold the chip' — no 'Double down' | PASS → PASS | L152-L156 | TB-Δ-8 PRD-driven mode auto-chooses `Bet on it` (L195); does NOT introduce a third option. Double down concept lives in prd-writer's upstream contract. |
| TB-034 | 'Bet on it' + Atlassian MCP connected → calls jira-create-issue via correct tool regex | PASS → PASS | L157-L159 | — |
| TB-035 | 'Bet on it' + no MCP → exact fallback 'Atlassian MCP not connected — saved markdown only at <path>' | PASS → PASS | L160 | — |
| TB-036 | 'Hold the chip' confirms save and prints absolute path with kebab-case slug | PASS → PASS | L149-L162 | — |

### H. Quality & specificity

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-037 | Artifact uses Jira component names and file paths verbatim | PASS → PASS | L163-L164 | Company terminology used verbatim. TB-Δ-3 4-bullet cap + overflow line applied (5 fields inferred). |
| TB-038 | Facts cite source inline; assumptions are marked inline (not in a separate section) | PASS → PASS | L165 | TB-Δ-6 now defines exact syntax — `> **Assumption:** … **Flag:** …` inline blockquote within Description or DoD. |

### I. Edge cases & failure modes

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| TB-039 | Vague input → sharper title applied directly, no separate 'suggested title' note | PASS → PASS | L166 | — |
| TB-040 | Too-large request → one-sentence split proposal ABOVE the artifact, not buried in notes | PASS → PASS | L167 | — |

## Delta vs v1.0.0

### Verdict flips

| ID | v1.0.0 | v1.1.0 | Driver |
|---|---|---|---|
| TB-029 | PARTIAL | PASS | **TB-Δ-5** — L127 narrative updated to match template ("immediately after the 4 metadata header lines, before `## User Story`"). The v1.0.0 narrative/template placement conflict is gone. |

### Regressions
**0 regressions.** All 39 v1.0.0 PASS cases remain PASS. Five regression-candidate cases were explicitly verified safe in the raw run:

- **TB-023** (7-cap): `Flow?` fallback Q (TB-Δ-1) is explicitly inside the Phase C 3-cap per L114, so worst case stays at 4+3 = 7.
- **TB-011** (conflict resolution): TB-Δ-7 tightens conflict handling to fall-through, but the case YAML lists `["Bug", "<not inferred>"]` as acceptable — both branches PASS.
- **TB-025** (required sections include User Flow): User Flow is now conditional per TB-Δ-1, but the case input ("VIP progress bar") infers `Needs flow diagram = Yes` → User Flow present.
- **TB-004** (Bug case): TB-Δ-1 row 5 omits User Flow for bugs; TB-004 does not assert User Flow presence — only Ticket type + Inferred block.
- **DoD cap** (TB-Δ-2): No v1.0.0 trace exceeded the new cap; TB-005 hit 5 items (at cap, within bounds).

### TB-Δ behaviors observed in v1.1.0 traces

All 8 v1.1.0 SKILL.md additions were exercised at least once across the 40 traces:

| ΔID | Behavior | Where observed |
|---|---|---|
| TB-Δ-1 | `Needs flow diagram` 5th Phase A field + conditional `## User Flow` + Phase C `Flow?` fallback Q | TB-004 (bug → No, omitted), TB-010/TB-013/TB-023 (Phase C fallback Q fires), TB-025 (Yes → present), TB-005 |
| TB-Δ-2 | DoD cap (max 5 items) | TB-005, TB-008, TB-026 (DoD = 5, at cap) |
| TB-Δ-3 | Inferred-block 4-bullet hard cap + italic overflow line for 5+ inferences | TB-006 (first case to exercise overflow), TB-037 (5 fields → 4 bullets + overflow) |
| TB-Δ-4 | Description audit hint | Implicit across all artifacts; no case explicitly asserts. |
| TB-Δ-5 | Inferred-block placement narrative rewrite (resolves v1.0.0 P2 #1) | TB-029 (flipped PARTIAL → PASS) |
| TB-Δ-6 | `> **Assumption:** … **Flag:** …` inline blockquote syntax (resolves v1.0.0 P2 #2) | TB-019, TB-020, TB-022, TB-038 (syntax used verbatim) |
| TB-Δ-7 | L53 conflict-resolution rule (multiple signal rows fire on same field → Not inferred) | TB-011 (TB-029 of v1.0.0 ambiguity tightened) |
| TB-Δ-8 | PRD-driven mode (L195: auto-choose `Bet on it`, do NOT call AskUserQuestion) | Not exercised by any TB case; exercised by PRD-037 in the prd-writer catalog. TB-033 confirms it does not add a third handoff option. |

## Actionable Items

**No actionable items at v1.1.0.** All v1.0.0 P2 items resolved by TB-Δ-5 and TB-Δ-6.

- v1.0.0 P2 #1 (Inferred-block placement narrative vs template) → resolved by TB-Δ-5.
- v1.0.0 P2 #2 (concrete syntax for assume + flag fallback) → resolved by TB-Δ-6.

Coverage gaps from the v1.0.0 report (multiple-Atlassian disambiguation L158, MCP create failure L159, isolated `output-copy-pasteable`, vague-input trigger threshold) carry over as catalog-extension suggestions, not actionable items against the skill itself.

## Catalog Quality Notes

The 40-case catalog continues to give strong, isolated signal on the high-traffic surfaces. v1.1.0 strengthens the spec at exactly the two ambiguities the catalog correctly flagged in v1.0.0 (TB-022 / TB-029) — the catalog's "PARTIAL surfaced spec ambiguity, not implementation bug" diagnosis at v1.0.0 was directly validated by the v1.1.0 SKILL.md edits.

The new TB-Δ-1 conditional `## User Flow` behavior was a meaningful spec change but is not asserted by any case — TB-025's `output-has-required-sections` was the regression-candidate, and the input happens to infer `flow = Yes`. A future catalog iteration should add an isolated case asserting "bug input omits User Flow" to lock in TB-Δ-1.

Next-iteration improvements (carried over from v1.0.0):
- Add multiple-Atlassian disambiguation case (L158).
- Add MCP create failure case (L159).
- Add isolated `output-copy-pasteable` case (L167).
- Add a case probing the "vague input" trigger threshold (TB-039 noted this as a spec gap).
- **New for v1.1.0:** add a case asserting User Flow is omitted for bug class inputs (locks in TB-Δ-1 row 5).
- **New for v1.1.0:** add a case asserting DoD ≤ 5 items hard cap (locks in TB-Δ-2).

## Out of Scope for This Report

- Real Jira MCP calls — all MCP behavior was stubbed in case preconditions.
- The 3 deferred skills (`skills-deferred/`) — those are not loaded today.
- The PRD-driven mode (TB-Δ-8) — exercised in the prd-writer catalog (PRD-037), not in any TB case.
- Modifying any SKILL.md — this report documents the v1.1.0 state; no further edits are recommended at this verdict level.
