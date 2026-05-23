# prd-writer — Test Report v1.2.0

**Skill:** [`prd-writer/SKILL.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/skills/prd-writer/SKILL.md) (214 lines, **unchanged from v1.1.0**)
**Catalog:** [`tests/prd-writer/cases/`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/prd-writer/cases/) — 47 cases
**Run date:** 2026-05-23
**Raw run:** [`reports/raw/prd-writer/full-run-v1.2.0.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/prd-writer/full-run-v1.2.0.md)
**v1.1.0 baseline report:** [`reports/prd-writer-test-report-v1.1.0.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/prd-writer-test-report-v1.1.0.md)

## Executive Summary

| Verdict | Count | % |
|---|---|---|
| PASS | 47 | 100% |
| PARTIAL | 0 | 0% |
| FAIL | 0 | 0% |
| **Total** | 47 | 100% |

**Overall verdict:** 🟢 Green (**47/0/0**, 100% PASS). Up from v1.1.0's **40/0/0** — same Green percentage, **+7 cases of coverage**. **No SKILL.md changes** between v1.1.0 and v1.2.0 (214 lines, identical). All 7 new v1.1.0-backfill cases (PRD-041…PRD-047) PASS on first run against the unchanged spec, confirming that the v1.1.0 deltas (PRD-Δ-1…PRD-Δ-9) are now structurally enforceable through dedicated test cases.

**Double-down chain:** end-to-end PASS at the new 25-row cap boundary (PRD-046) and the Confluence parentId 404-retry path (PRD-047). The chain remains the strongest cross-skill contract surface in the suite.

## Per-Category Breakdown

| Category | Cases | PASS | PARTIAL | FAIL | % PASS | v1.1.0 → v1.2.0 |
|---|---|---|---|---|---|---|
| A. Frontmatter & metadata | 3 | 3 | 0 | 0 | 100% | 100% → 100% |
| B. Phase A inference | 13 | 13 | 0 | 0 | 100% | 100% → 100% (+5 cases) |
| C. Phase B core questions | 5 | 5 | 0 | 0 | 100% | 100% → 100% |
| D. Phase C follow-ups | 8 | 8 | 0 | 0 | 100% | 100% → 100% |
| E. Output structure | 7 | 7 | 0 | 0 | 100% | 100% → 100% |
| F. Maturity adaptation | 3 | 3 | 0 | 0 | 100% | 100% → 100% |
| G. Handoff & MCP integration | 6 | 6 | 0 | 0 | 100% | 100% → 100% (+2 cases) |
| H. Quality & specificity | 1 | 1 | 0 | 0 | 100% | 100% → 100% |
| I. Edge cases & failure modes | 1 | 1 | 0 | 0 | 100% | 100% → 100% |
| **Total** | **47** | **47** | **0** | **0** | **100%** | **100% → 100%** |

The +7 new cases distribute as **+5 in Phase A inference** (PRD-041…PRD-045 — Retention/re-engagement signal, `vip` and `crm` sub-tag rendering, `revenue` sub-tag in §10, conflict-rule fall-through) and **+2 in Handoff** (PRD-046 25-row chain cap, PRD-047 Confluence parentId 404 retry). Both clusters target previously under-tested v1.1.0 contract surfaces.

## Detailed Results

### A. Frontmatter & metadata

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-001 | SKILL.md frontmatter parses as valid YAML with name and description | PASS | PASS → PASS | L1–L4 | — |
| PRD-002 | Description starts with 'Use when' and names 'maturity-adapted PRD' output | PASS | PASS → PASS | L3 | — |
| PRD-003 | Description mentions the 'Double down' chain behavior | PASS | PASS → PASS | L3 | — |

### B. Phase A inference

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-004 | Maturity inferred as 'Initial idea' from 'we're thinking about' | PASS | PASS → PASS | L55 | — |
| PRD-005 | Maturity inferred as 'Existing feature' from 'v2 of raffles' | PASS | PASS → PASS | L55 | — |
| PRD-006 | Main user inferred as 'VIP player' from 'high rollers' | PASS | PASS → PASS | L56 | — |
| PRD-007 | Main user inferred as 'CRM operator' from 'PS Admin Panel' | PASS | PASS → PASS | L56 | — |
| PRD-008 | Main problem inferred as retention from 'churn after first deposit' | PASS | PASS → PASS | L57, L81 | — |
| PRD-009 | Success signal inferred as GGR-lift from 'increase GGR by 5%' | PASS | PASS → PASS | L58 | — |
| PRD-010 | Ambiguous input — Phase A infers nothing, Phase B asks all 4 | PASS | PASS → PASS | L53–L86 | — |
| PRD-011 | Conflicting signals (Maturity 'new' vs 'v2 of') — Phase A resolves or defers | PASS | PASS → PASS | L52 | — |
| PRD-041 | Main problem inferred as Retention / re-engagement from 're-engage lapsed' signal | PASS | **NEW → PASS** | L57, L81 | First-run PASS. "re-engage lapsed" → Retention / re-engagement per L57; Phase B Main problem skipped. |
| PRD-042 | Main user surfaces `vip` sub-tag in User Story when input names VIP players | PASS | **NEW → PASS** | L56 | First-run PASS. `vip` tag rendered in §6 User Story line ("As a VIP player (vip-tier ≥ 2), I want…"), not only in Inferred block. |
| PRD-043 | Main user surfaces `crm` sub-tag in User Story when input names CRM operator + lifecycle | PASS | **NEW → PASS** | L56 | First-run PASS. `crm` tag rendered in §6 User Story ("As a CRM operator, I want…"). |
| PRD-044 | GGR `revenue` sub-tag surfaces in §10 Primary Metric when input mentions NGR / ARPU | PASS | **NEW → PASS** | L58 | First-run PASS. §10 Primary Metric bullet contains "**NGR lift [revenue]**" verbatim — `[revenue]` marker surfaced in rendered §10, not only in Inferred block. |
| PRD-045 | Conflict rule — 'v2 of raffles from scratch' leaves Maturity Not inferred | PASS | **NEW → PASS** | L52 | First-run PASS. Per L52 (PRD-Δ-4) "v2 of" + "from scratch" both fire on Maturity → fall-through to Phase B; no tie-break invented. |

### C. Phase B core questions

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-012 | Phase B asks only the 2 questions Phase A didn't infer | PASS | PASS → PASS | L62–L86 | — |
| PRD-013 | Each Phase B question emits exactly 3 spec'd options (Maturity bank) | PASS | PASS → PASS | L67–L70 | — |
| PRD-014 | Phase B question headers match the spec exactly | PASS | PASS → PASS | L67–L86 | — |
| PRD-015 | Phase B uses AskUserQuestion only — no free-form prompts | PASS | PASS → PASS | L48 | — |
| PRD-016 | When Phase A infers zero fields, Phase B asks all 4 core questions | PASS | PASS → PASS | L62–L86 | — |

### D. Phase C follow-ups

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-017 | Phase C emits at most 3 follow-up questions | PASS | PASS → PASS | L93 | — |
| PRD-018 | Phase C rejects banned generic placeholders | PASS | PASS → PASS | L94 | — |
| PRD-019 | Phase C skips a topic already answered by Jira/Confluence context | PASS | PASS → PASS | L95 | — |
| PRD-020 | Phase C skips styling/copy/event-name questions | PASS | PASS → PASS | L96, L110–L112 | — |
| PRD-021 | Phase C priority order respected — scope edges over rollout | PASS | PASS → PASS | L97–L102 | — |
| PRD-022 | Phase C falls back to assume+flag when 3 concrete options aren't writeable | PASS | PASS → PASS | L102 | — |
| PRD-023 | Total user-facing questions across Phase B + Phase C does not exceed 7 | PASS | PASS → PASS | L48 | — |
| PRD-024 | Good Phase C follow-ups for Community Chat MVP cut (worked example) | PASS | PASS → PASS | L105–L112 | — |

### E. Output structure

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-025 | PRD contains all 12 numbered sections in order | PASS | PASS → PASS | L130–L153 | — |
| PRD-026 | §6 User Stories embeds Edge Cases as a table — not Gherkin | PASS | PASS → PASS | L142 | — |
| PRD-027 | §7 User Flow uses box-drawing characters and arrows in a fenced code block | PASS | PASS → PASS | L144 | — |
| PRD-028 | §8 Requirements has Functional and Non-Functional subsections | PASS | PASS → PASS | L146–L148 | — |
| PRD-029 | §10 Analytics has Primary, Secondary, and Tracking subsections | PASS | PASS → PASS | L150 | — |
| PRD-030 | Inferred (not asked) block at top when Phase A inferred ≥1 field | PASS | PASS → PASS | L131–L134, L56 | — |
| PRD-031 | §12 Suggested Jira Breakdown includes a sub-epic title plus child ticket rows | PASS | PASS → PASS | L152 | — |

### F. Maturity adaptation

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-032 | Initial idea — emphasizes Problem/Assumptions/Validation/MVP, no Open Questions section | PASS | PASS → PASS | L120 | — |
| PRD-033 | Clear direction — emphasizes Requirements/Flows/Breakdown, no Dependencies section | PASS | PASS → PASS | L121 | — |
| PRD-034 | Existing feature — emphasizes Current/Proposed/Migration, no Risks section | PASS | PASS → PASS | L122 | — |

### G. Handoff & MCP integration

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-035 | Ready To Gamble On It? handoff has header 'Gamble?' and 3 spec'd options | PASS | PASS → PASS | L175–L181 | — |
| PRD-036 | Bet on it + atlassian MCP → Confluence create call with PKB params | PASS | PASS → PASS | L182–L189 | — |
| PRD-037 | Double down chain — Confluence page + Jira sub-epic + 6 child tickets, no questions, cite PRD | PASS | PASS → PASS | L195–L201 (+ ticket-builder L186–L194) | 6 ≤ 25 cap; 5-field Phase A in chained children (incl. `Needs flow diagram`) holds. |
| PRD-038 | Double down + no MCP → same fallback message as Bet on it | PASS | PASS → PASS | L202 | — |
| PRD-046 | Double-down chain with 26+ §12 rows triggers chain-too-long question BEFORE any Jira call | PASS | **NEW → PASS** | L208–L214 | First-run PASS. **Trace-order audit:** zero `mcp__*` create-issue / create-page calls precede the `Chain too long?` AskUserQuestion. Header verbatim; 3 options verbatim (Split the PRD / Bet on it instead / Cancel); question text contains "exceeds the Double-down chain cap of 25". |
| PRD-047 | Confluence parentId 404 → retry without parentId, report which space-root the page landed at | PASS | **NEW → PASS** | L189 | First-run PASS. Two create calls visible in order: (1) WITH parentId=772571521 → 404, (2) WITHOUT parentId → 200. User-facing report includes "PKB space root", "without parentId", and "/spaces/PKB/" substrings per L189. |

### H. Quality & specificity

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-039 | PRD uses company terminology from context (PR-266, PR-280, Smartico, PS Admin Panel) | PASS | PASS → PASS | L156–L162 | — |

### I. Edge cases & failure modes

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| PRD-040 | Thin §12 row ('Misc — TBD') → chained ticket defaults to Task with Open flag | PASS | PASS → PASS | L206 (+ ticket-builder L194) | — |

## Delta vs v1.1.0

**Zero regressions.** Every v1.1.0 PASS (40 cases) remained PASS in v1.2.0. All **7 new PRD-041…PRD-047 cases PASS first time** against the unchanged v1.1.0 SKILL.md, confirming that the v1.1.0 deltas (PRD-Δ-1…PRD-Δ-9) are now empirically anchored by dedicated test coverage.

| Case ID | v1.1.0 | v1.2.0 | Targeted v1.1.0 delta | Mechanism verified |
|---|---|---|---|---|
| PRD-041 | NEW | **PASS** | PRD-Δ-3 | L57 maps "re-engage", "lapsed", "win-back" → Retention / re-engagement; Phase B Main problem correctly skipped. |
| PRD-042 | NEW | **PASS** | PRD-Δ-2 | L56 `vip` sub-tag surfaces in §6 User Story line ("As a VIP player…"), not only in Inferred block. |
| PRD-043 | NEW | **PASS** | PRD-Δ-2 | L56 `crm` sub-tag surfaces in §6 User Story line ("As a CRM operator…"). |
| PRD-044 | NEW | **PASS** | PRD-Δ-6 | L58 `revenue` sub-tag rendered in §10 Primary Metric as "**NGR lift [revenue]**", not only in Inferred block. |
| PRD-045 | NEW | **PASS** | PRD-Δ-4 | L52 conflict rule: "v2 of" + "from scratch" both fire on Maturity → Not inferred → Phase B Q1 fires with the 3 core-bank options verbatim. |
| PRD-046 | NEW | **PASS** | PRD-Δ-8 | L208–L214 25-child hard cap. **See special call-out below.** |
| PRD-047 | NEW | **PASS** | PRD-Δ-7 | L189 404-retry path: first call with parentId → 404, second call without parentId → 200, user-facing report names the space-root the page landed at. |

### Special call-out — PRD-046 (Double-down 25-row cap, trace-order verified)

PRD-046 is the most operationally load-bearing of the seven new cases because its acceptance criterion turns on **call-ordering**, not just outcome. The criterion `double-down-chain-cap-question-fires` requires that the `Chain too long?` AskUserQuestion fires **BEFORE any `mcp__*` create call** — i.e. Confluence-createPage, Jira-createIssue (sub-epic), and Jira-createIssue (any child) must all be uncalled at the moment the question is presented.

The trace explicitly audits this at step 4: with §12 containing exactly 26 rows (= 25 + 1, the first count over cap), the order is (1) save markdown → (2) AskUserQuestion `Gamble?` → user picks Double down → (3) chain-length pre-check fires `Chain too long?` AskUserQuestion. **Zero `mcp__*` create-issue / create-page calls precede the question.** Header verbatim ("Chain too long?"), three options verbatim ("Split the PRD" / "Bet on it instead" / "Cancel"), question text contains "exceeds the Double-down chain cap of 25". L208's "abort the chain BEFORE making any Jira call" instruction is honored to the letter — the v1.1.0 contract is not only documented but verifiably enforced in trace order.

## Actionable Items

**No actionable items at v1.2.0.**

The SKILL.md is unchanged from v1.1.0 and the v1.1.0 actionable list (already empty) remains empty. The v1.2.0 work added test coverage without finding new defects.

## Cross-Skill Notes (Double-Down Chain)

**Does the chain work end-to-end at v1.1.0 contracts?** **Yes — confirmed across both happy-path and cap-boundary cases.**

- **PRD-037** (happy path, 6 rows): Confluence page + Jira sub-epic + 6 child tickets created from a single Double-down click with zero user questions in the children, every child citing the PRD section it came from. 5-field Phase A in chained children (incl. `Needs flow diagram`) holds. PASS → PASS.
- **PRD-038** (no-MCP fallback): "Atlassian MCP not connected — saved markdown only…" emitted; no chain executed. PASS → PASS.
- **PRD-046** (cap boundary, 26 rows): chain aborts BEFORE any MCP create call; `Chain too long?` AskUserQuestion fires with the 3 spec'd options. **New 25-cap behavior is testable and PASSes on first run.**
- **PRD-047** (Confluence parentId 404 retry): first create call WITH `parentId=772571521` returns 404; retry WITHOUT `parentId` returns 200; user-facing report names the PKB space root. PRD-Δ-7's 404-retry path is now empirically anchored.
- **PRD-040** (thin §12 row): "Misc — TBD" row defaults to `type=Task` with inline Open flag, per L206 + ticket-builder L194 mirror. PASS → PASS.

**Cross-skill contract with ticket-builder PRD-driven mode remains in sync.** **TB-048** in the v1.2.0 ticket-builder run also PASSes (the corresponding ticket-builder backfill case for PRD-driven chained-call behavior), confirming the bidirectional mirror landed via PRD-Δ-1 + TB-Δ-8 holds under expanded coverage on both sides. An independent edit to either skill that breaks the chain would surface in at least one of {PRD-037, PRD-038, PRD-040, PRD-046, PRD-047, TB-048}; today all six are Green.

## Note on Section N (vocabulary additions)

The v1.2.0 raw run introduces **4 new criterion IDs** to support the 7 backfill cases. None of these required SKILL.md text changes — they are testable surfaces on existing v1.1.0 contracts. They should be added to the shared criterion vocabulary used by the coverage map / Section N glossary:

| Criterion ID | Used by | What it verifies |
|---|---|---|
| `phase-a-sub-segment-tag-applied` | PRD-042, PRD-043 | A Phase A `vip` or `crm` sub-tag is rendered in the §6 User Story line (e.g. "As a VIP player", "As a CRM operator"), not only inside the Inferred block. |
| `analytics-primary-metric-has-revenue-tag` | PRD-044 | A Phase A `revenue` sub-tag (from GGR/NGR/ARPU signals) is rendered in §10 Primary Metric — e.g. "**NGR lift [revenue]**" — not only inside the Inferred block. |
| `double-down-chain-cap-question-fires` | PRD-046 | When §12 has > 25 rows, the `Chain too long?` AskUserQuestion fires with the expected header, expected question substring, and 3 verbatim options, AND **no `mcp__*` create-issue / create-page calls precede the question** in trace order. |
| `confluence-parentid-404-retry-fallback` | PRD-047 | First Confluence create call includes `parentId=772571521`; on HTTP 404, exactly one retry without `parentId` follows; the user-facing report names the space root the page landed at (e.g. "PKB space root", "without parentId", "/spaces/PKB/"). |

## Out of Scope for This Report

- Real Confluence/Jira MCP calls — stubbed in preconditions (PRD-036, PRD-037, PRD-046, PRD-047 simulate MCP responses).
- Modifying any SKILL.md.
- Verifying actual PKB space/parent IDs (772571142, 772571521) are still valid against the live Atlassian instance — left for the user to check.
- The "if second Confluence attempt also fails" sub-branch in PRD-047 (markdown-only fallback) — not exercised in this run because the simulated retry returns 200.
