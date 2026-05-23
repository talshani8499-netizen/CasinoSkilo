# prd-writer — Test Report

**Skill:** [`prd-writer/SKILL.md`](/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/prd-writer/SKILL.md) (205 lines)
**Catalog:** [`tests/prd-writer/cases/`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/prd-writer/cases/) — 40 cases
**Run date:** 2026-05-23
**Raw run:** [`reports/raw/prd-writer/full-run.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/prd-writer/full-run.md)

## Executive Summary

| Verdict | Count | % |
|---|---|---|
| PASS | 32 | 80.0% |
| PARTIAL | 8 | 20.0% |
| FAIL | 0 | 0.0% |
| **Total** | 40 | 100% |

**Overall verdict:** 🟡 Yellow (80% PASS — sitting exactly on the green/yellow boundary). The skill is structurally sound — every behavioral assertion (Phase B/C mechanics, output structure, maturity adaptation, handoff) passed — but a tight cluster of Phase-A sub-segment bank gaps and a single cross-skill contract gap dragged the score down to threshold.

**Double-down chain (PRD-037):** PARTIAL. The chain works end-to-end on the happy path — 1 Confluence page + 1 Jira sub-epic + 6 child tickets created from a single click with zero user questions and every child citing the PRD — but the "PRD-driven mode" contract that governs ticket-builder's child-ticket behavior lives only in `prd-writer/SKILL.md:L198/L204` and is not mirrored in `ticket-builder/SKILL.md`. An independent edit to ticket-builder can silently break the chain.

## Per-Category Breakdown

| Category | Cases | PASS | PARTIAL | FAIL | % PASS |
|---|---|---|---|---|---|
| A. Frontmatter & metadata | 3 | 2 | 1 | 0 | 66.7% |
| B. Phase A inference | 8 | 3 | 5 | 0 | 37.5% |
| C. Phase B core questions | 5 | 5 | 0 | 0 | 100% |
| D. Phase C follow-ups | 8 | 8 | 0 | 0 | 100% |
| E. Output structure | 7 | 6 | 1 | 0 | 85.7% |
| F. Maturity adaptation | 3 | 3 | 0 | 0 | 100% |
| G. Handoff & MCP integration | 4 | 3 | 1 | 0 | 75.0% |
| H. Quality & specificity | 1 | 1 | 0 | 0 | 100% |
| I. Edge cases & failure modes | 1 | 1 | 0 | 0 | 100% |
| **Total** | **40** | **32** | **8** | **0** | **80.0%** |

The defect distribution is highly concentrated: **5 of 8 PARTIALs** sit in **Category B (Phase A inference)**, all symptoms of the same root cause — the Main user / Main problem / Success option banks (SKILL.md L55–L58, L68–L85) don't enumerate the sub-segments and named values the test catalog (and real PMs) routinely use ("VIP player", "CRM operator", "Retention / re-engagement", "GGR lift").

## Detailed Results

### A. Frontmatter & metadata

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-001 | SKILL.md frontmatter parses as valid YAML with name and description | PASS | L1–L5 | — |
| PRD-002 | Description starts with 'Use when' and names 'maturity-adapted PRD' output | PASS | L3–L5 | — |
| PRD-003 | Description mentions the 'Double down' chain behavior | PARTIAL | L3–L5 | Description names the chain ("chain the ticket-builder skill") but does not contain the literal phrase "Double down". |

### B. Phase A inference

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-004 | Maturity inferred as 'Initial idea' from 'we're thinking about' | PASS | L54 | — |
| PRD-005 | Maturity inferred as 'Existing feature' from 'v2 of raffles' | PASS | L55–L56 | — |
| PRD-006 | Main user inferred as 'VIP player' from 'high rollers' | PARTIAL | L55, L68–L70 | "VIP player" sub-segment is not a first-class value in the Main user bank; only End user / Admin / Support-ops are enumerated. |
| PRD-007 | Main user inferred as 'CRM operator' from 'PS Admin Panel' | PARTIAL | L55 | "PS Admin Panel" is not enumerated as an inference trigger; "CRM operator" is not a first-class bank value. |
| PRD-008 | Main problem inferred as retention from 'churn after first deposit' | PARTIAL | L57, L73 | Spec maps "churn" → "Drop-off"; "Retention / re-engagement" is not a distinct Main problem value. |
| PRD-009 | Success signal inferred as GGR-lift from 'increase GGR by 5%' | PARTIAL | L58, L77 | Spec subsumes "GGR" under "Conversion"; "GGR / revenue lift" is not a distinct Success value. |
| PRD-010 | Ambiguous input — Phase A infers nothing, Phase B asks all 4 | PASS | L53–L64 | — |
| PRD-011 | Conflicting signals (Maturity 'new' vs 'v2 of') — Phase A resolves or defers | PARTIAL | L51–L58 | Spec has no documented conflict-resolution rule when opposing signals fire. Output is correct by luck, not by rule. |

### C. Phase B core questions

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-012 | Phase B asks only the 2 questions Phase A didn't infer | PASS | L62–L85 | — |
| PRD-013 | Each Phase B question emits exactly 3 spec'd options (Maturity bank) | PASS | L65–L75 | — |
| PRD-014 | Phase B question headers match the spec exactly | PASS | L65–L85 | — |
| PRD-015 | Phase B uses AskUserQuestion only — no free-form prompts | PASS | L62–L85 | — |
| PRD-016 | When Phase A infers zero fields, Phase B asks all 4 core questions | PASS | L62–L85 | — |

### D. Phase C follow-ups

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-017 | Phase C emits at most 3 follow-up questions | PASS | L93 | — |
| PRD-018 | Phase C rejects banned generic placeholders | PASS | L94 | — |
| PRD-019 | Phase C skips a topic already answered by Jira/Confluence context | PASS | L95 | — |
| PRD-020 | Phase C skips styling/copy/event-name questions | PASS | L96, L108–L110 | — |
| PRD-021 | Phase C priority order respected — scope edges over rollout | PASS | L97–L101 | — |
| PRD-022 | Phase C falls back to assume+flag when 3 concrete options aren't writeable | PASS | L101 | — |
| PRD-023 | Total user-facing questions across Phase B + Phase C does not exceed 7 | PASS | L48, L93 | — |
| PRD-024 | Good Phase C follow-ups for Community Chat MVP cut (worked example) | PASS | L103–L111 | — |

### E. Output structure

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-025 | PRD contains all 12 numbered sections in order | PASS | L131–L174 | — |
| PRD-026 | §6 User Stories embeds Edge Cases as a table — not Gherkin | PASS | L141 | — |
| PRD-027 | §7 User Flow uses box-drawing characters and arrows in a fenced code block | PASS | L144 | — |
| PRD-028 | §8 Requirements has Functional and Non-Functional subsections | PASS | L147–L148 | — |
| PRD-029 | §10 Analytics has Primary, Secondary, and Tracking subsections | PASS | L150–L152 | — |
| PRD-030 | Inferred (not asked) block at top when Phase A inferred ≥1 field | PARTIAL | L53–L60 | Block format is correct, but the "VIP player" sub-segment naming gap (PRD-006 duplicate) re-surfaces. |
| PRD-031 | §12 Suggested Jira Breakdown includes a sub-epic title plus child ticket rows | PASS | L170–L178 | — |

### F. Maturity adaptation

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-032 | Initial idea — emphasizes Problem/Assumptions/Validation/MVP, no Open Questions section | PASS | L116–L122 | — |
| PRD-033 | Clear direction — emphasizes Requirements/Flows/Breakdown, no Dependencies section | PASS | L116–L122 | — |
| PRD-034 | Existing feature — emphasizes Current/Proposed/Migration, no Risks section | PASS | L116–L122 | — |

### G. Handoff & MCP integration

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-035 | Ready To Gamble On It? handoff has header 'Gamble?' and 3 spec'd options | PASS | L181–L204 | — |
| PRD-036 | Bet on it + atlassian MCP → Confluence create call with PKB params | PASS | L181–L190 | — |
| PRD-037 | Double down chain — Confluence page + Jira sub-epic + 6 child tickets, no questions, cite PRD | PARTIAL | L191–L204 | Core behavior works, but the PRD-driven mode contract is not mirrored in ticket-builder's SKILL.md; chain length is also uncapped. |
| PRD-038 | Double down + no MCP → same fallback message as Bet on it | PASS | L200–L201 | — |

### H. Quality & specificity

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-039 | PRD uses company terminology from context (PR-266, PR-280, Smartico, PS Admin Panel) | PASS | L90–L178 | — |

### I. Edge cases & failure modes

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| PRD-040 | Thin §12 row ('Misc — TBD') → chained ticket defaults to Task with Open flag | PASS | L204 | — |

## Actionable Items

### P0 — Cross-skill contract: mirror "PRD-driven mode" in ticket-builder/SKILL.md

**Affected tests:** PRD-037, PRD-040
**Location:** `skills/prd-writer/SKILL.md:L191–L204` (canonical) + new mirror clause in `skills/ticket-builder/SKILL.md` (Phase A section)
**Symptom:** The "PRD-driven mode" contract that governs how ticket-builder behaves when called from prd-writer's Double down chain (skip Phase B + Phase C, cite PRD sections in the Inferred block, default thin rows to Task with Open flag) exists *only* in prd-writer's SKILL.md (L198, L204). ticket-builder is unaware of this mode; an independent edit to ticket-builder removing inline assume+flag handling or AskUserQuestion-skip logic will silently break the entire Double down chain without any test in ticket-builder's own catalog catching it.
**Proposed edit:**

In `skills/prd-writer/SKILL.md` near L204, append:

```
**Cross-skill contract:** This "PRD-driven mode" must also be acknowledged in `ticket-builder/SKILL.md` (its Phase A section). If ticket-builder is updated to remove inline assume+flag handling or its AskUserQuestion-skip behavior, also update this section and re-run the Double down test (PRD-037).
```

And in `skills/ticket-builder/SKILL.md` (Phase A or top of skill body), add the mirror clause:

```
### PRD-driven mode (invoked by prd-writer Double down)
When this skill is invoked as part of a prd-writer Double down chain, run in PRD-driven mode:
- Skip Phase B (no core questions) and Phase C (no adaptive follow-ups).
- Do NOT call AskUserQuestion.
- Source every Phase A inference from the parent PRD; surface them in the ticket's `Inferred (not asked)` block citing the PRD section (e.g. `from PRD §10 FR-2`).
- If the PRD §12 row is too thin to infer a ticket type (e.g. just "Misc — TBD"), default to type=Task with an inline `Open: ticket type not inferable from PRD §12 — confirm with owner` line in the ticket body, and proceed.
- Auto-Bet on it at handoff (no Gamble question).
Authoritative source: `prd-writer/SKILL.md:L191–L204`.
```

### P1 — Expand Main user option bank to include sub-segments

**Affected tests:** PRD-006, PRD-007, PRD-030
**Location:** `skills/prd-writer/SKILL.md:L55, L68–L70`
**Symptom:** The Main user bank only enumerates End user / Admin / Support-ops, so common product-relevant sub-segments ("VIP player", "FTD player", "CRM operator", "BO admin") cannot be cleanly represented in the Phase A inferred-block. Phase A inference table also omits company-specific admin terms like "PS Admin Panel".
**Proposed edit:**

L55 (Phase A inference table row):

```
| **Main user** | "player", "user", "customer" → End user (specify sub-segment if signal exists: VIP, FTD, casual). "admin", "back office", "BO", "CMS", "PS Admin Panel", "Admin Panel" → Admin (CRM operator / BO admin). "CS", "support", "ops", "VIP team", "agent" → Support/ops. |
```

L68–L70 (Phase B bank):

```
- **Main user** — header: `Main user` — "Who is the main user affected?"
  - End user — Players / customers (specify sub-segment inline if known: VIP, FTD, casual)
  - Admin / internal — Internal users in the CMS or back office (CRM operator, BO admin, PS Admin Panel)
  - Support / ops — CS, VIP, or operations teams
```

### P1 — Add Retention / re-engagement as a Main problem value

**Affected tests:** PRD-008
**Location:** `skills/prd-writer/SKILL.md:L57, L73`
**Symptom:** Main problem bank lacks an explicit Retention / re-engagement value; "churn" is mapped to Drop-off, which conflates pre-deposit drop-off with post-FTD retention — two materially different problem framings in casino product work.
**Proposed edit:**

L57 (Phase A inference table row):

```
| **Main problem** | ... "drop", "abandon", "not converting" → Drop-off. "churn", "retention", "re-engagement", "winback", "dormant" → Retention / re-engagement. "manual", "slow", "tedious", "spreadsheets" → Internal workflow. |
```

L73 (Phase B bank — add new option):

```
  - Retention / re-engagement — Users churning or going dormant
```

Note: this brings the Main problem bank to 4 options. If the 3-option-per-question rule (L66, L93) is hard, either split into "Drop-off (pre-conversion)" / "Retention (post-conversion)" as a single contextual choice, or relax the bank to allow up to 4 for Main problem specifically.

### P1 — Document Phase A conflict-resolution rule

**Affected tests:** PRD-011
**Location:** `skills/prd-writer/SKILL.md:L51–L58`
**Symptom:** Phase A lists inference signals but never tells the runner what to do when two opposing signals fire for the same field (e.g. "brand-new" + "v2 of"). Behavior is undefined; PRD-011 passed only because the runner guessed correctly.
**Proposed edit:**

Append a paragraph after the Phase A inference table:

```
**Conflict resolution:** When two signals fire for the same field with different values, prefer the more specific signal (e.g. "v2 of X" beats "new"; "PS Admin Panel" beats "admin"; an existing Jira epic beats an "exploring" verb in user_input). If neither signal is more specific, defer to Phase B and ask.
```

### P2 — Add "Double down" verbatim to frontmatter description

**Affected tests:** PRD-003
**Location:** `skills/prd-writer/SKILL.md:L3`
**Symptom:** The description names the chain behavior ("chain the ticket-builder skill") but does not contain the literal handoff option label "Double down", so a strict expected-phrase match fails.
**Proposed edit:**

```
description: Use when a PM wants to turn an idea, initiative, or discovery outcome into a full PRD. Scans Jira/Confluence for related context, adaptively asks only the questions input doesn't already answer, adds up to 3 context-derived follow-ups for real unknowns, and returns a maturity-adapted PRD. Ends with a "Ready To Gamble On It?" handoff that can push to Confluence (Product Knowledge Base space) and optionally "Double down" to chain the ticket-builder skill to create the Jira epic + child tickets, or save markdown only.
```

### P2 — Promote GGR / revenue lift to a first-class Success signal

**Affected tests:** PRD-009
**Location:** `skills/prd-writer/SKILL.md:L58, L77`
**Symptom:** GGR / revenue lift is conflated with Conversion despite being a distinct, business-critical success signal in casino product work.
**Proposed edit:**

L58:

```
| **Success signal** | "convert", "activate", "sign up", "deposit" → Conversion. "GGR", "+X%", "revenue", "monetization", "ARPU" → GGR / revenue lift. "fewer tickets", "support load" → Reduced friction. "DAU", "retention", "sessions", "engagement" → Engagement. |
```

L77 (Phase B bank): add "GGR / revenue lift — Top-line revenue or monetization" as a 4th option (same 3-vs-4 caveat as Main problem above).

### P2 — Document Confluence parentId fallback

**Affected tests:** PRD-036
**Location:** `skills/prd-writer/SKILL.md:L188–L190`
**Symptom:** parentId=772571521 is hardcoded. If the PKB overview page is moved/deleted, every Bet on it / Double down publish fails with no documented recovery path.
**Proposed edit:**

```
      - `parentId` = `772571521` (the PKB overview homepage — required; PKB rejects top-level creates with 404). **If the create call returns "parent not found" or 404, retry by fetching the PKB space's homepage via the Atlassian MCP's space-get tool and using that page id as parentId. Report the new parentId in the final message so the SKILL.md can be updated.**
```

### P2 — Add upper bound on Double down chain length

**Affected tests:** PRD-037
**Location:** `skills/prd-writer/SKILL.md:L204`
**Symptom:** L204 advertises "A PRD with 14 child tickets produces 14 Jira tickets" with no upper cap. A pathological 50-row §12 fans out unchecked, creating 50+ Jira issues from a single click.
**Proposed edit:**

Insert in the L204 paragraph:

```
**Maximum chain length: 25 child tickets.** If §12 has more rows than that, the chain creates the first 25 children and emits a single warning line at the end of the final message listing the unbuilt rows so the PM can re-run for the remainder.
```

### P2 — Clarify 7-question cap scope for chained calls

**Affected tests:** PRD-037
**Location:** `skills/prd-writer/SKILL.md:L48`
**Symptom:** L48 says "Total questions asked across all phases must never exceed 7" — ambiguous about whether chained ticket-builder questions count. (Moot for happy path because PRD-driven mode emits 0, but the spec should still be explicit.)
**Proposed edit:**

```
Total questions asked across all phases must never exceed 7. The Gamble handoff at the end is the 8th and final question. Chained ticket-builder calls running in PRD-driven mode emit 0 questions and do not contribute to this cap.
```

## Catalog Quality Notes

The 40-case catalog is well-balanced for behavioral coverage but slightly imbalanced for defect surfacing. **Strong-signal cases**: PRD-006 through PRD-011 stress-tested the Phase A option bank and exposed the entire Category-B sub-segment cluster — these were the highest-value tests in the catalog. PRD-037 (Double down chain) and PRD-040 (thin §12 row) exposed the cross-skill contract gap that no single-skill assertion could have caught. **Weak-signal cases**: PRD-013 through PRD-016 are near-duplicates that all verify Phase B mechanics — three of these could have been collapsed into one. PRD-039 (quality/terminology) is broad enough that it can't fail unless something is structurally wrong elsewhere.

**Underweighted:** edge cases & failure modes (only PRD-040). Missing: what happens when AskUserQuestion is unavailable, what happens on MCP tool-name regex miss, what happens when the user answers a Phase B question with "I don't know", what happens on Confluence 409 conflict (duplicate title). **Overweighted:** Phase B mechanics (5 cases for what is essentially one rule).

**Next-iteration suggestions:** (1) Add an explicit cross-skill contract test that mutates ticket-builder's SKILL.md and re-runs PRD-037 to prove the chain breaks — this would force the P0 mirror clause to land. (2) Add a "thin context + many unknowns" stress case to verify the L101 rule 6 fallback at scale. (3) Add an AskUserQuestion-unavailable degradation test.

## Cross-Skill Notes (Double-Down Chain)

**Does the chain work end-to-end?** Yes, on the happy path. PRD-037 demonstrates one Confluence page + one Jira sub-epic + six child tickets created from a single Double-down click with zero user questions, every child citing the PRD section it came from, and PRD-038 confirms the no-MCP fallback path.

**Documented vs. undocumented contract surfaces:**

| Contract surface | Where it lives today | Status |
|---|---|---|
| 3 Gamble options (Bet on it / Hold the chip / Double down) | `prd-writer/SKILL.md:L184–L186` | Documented |
| Confluence create-page params (spaceId, parentId, contentFormat) | `prd-writer/SKILL.md:L186–L188` | Documented |
| MCP tool-name regex (`mcp__.*atlassian.*` etc.) | `prd-writer/SKILL.md:L184` | Documented |
| Markdown save path (`~/Downloads/prds/<slug>.md`) | `prd-writer/SKILL.md:L182` | Documented |
| **ticket-builder runs in "PRD-driven mode": skip Phase B + Phase C, 0 questions** | `prd-writer/SKILL.md:L198` only | **Undocumented in ticket-builder** |
| **ticket-builder cites PRD sections in its Inferred block** | `prd-writer/SKILL.md:L198` only | **Undocumented in ticket-builder** |
| **Thin §12 row → type=Task with inline Open flag** | `prd-writer/SKILL.md:L204` only | **Undocumented in ticket-builder** |
| Upper bound on chain length | — | Not documented anywhere |

**What happens if ticket-builder's SKILL.md is edited without coordination?** Any of the following changes would silently break the chain:
- If ticket-builder's spec removes its ability to skip AskUserQuestion in any mode, every chained child call will pause for user input — defeating the "single click" promise.
- If ticket-builder's spec stops accepting cited-from-PRD context as valid Phase A inference signal, children will defer to Phase B (questions) instead of inferring from the PRD body.
- If ticket-builder's spec removes the inline assume+flag fallback, thin §12 rows like "Misc — TBD" will fail outright instead of degrading to Task + Open flag.

**Recommended mirror clauses** (full text under P0 above):
1. In `prd-writer/SKILL.md` near L204: add a Cross-skill contract callout pointing to ticket-builder.
2. In `ticket-builder/SKILL.md` (Phase A section): add a dedicated `### PRD-driven mode` subsection documenting the 5 behaviors (skip Phase B, skip Phase C, no AskUserQuestion, cite PRD sections in Inferred block, thin-row → Task + Open flag, auto-Bet on it at handoff) and naming `prd-writer/SKILL.md:L191–L204` as the authoritative source.

## Out of Scope for This Report

- Real Confluence/Jira MCP calls — stubbed in preconditions.
- Modifying any SKILL.md.
- Verifying actual PKB space/parent IDs (772571142, 772571521) are still valid — left for the user to check.
