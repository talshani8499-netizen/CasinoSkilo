# prd-writer — Raw Run v1.1.0
Date: 2026-05-23
SKILL.md path: /Users/talshani/Documents/GitHub/CasinoSkilo/skills/prd-writer/SKILL.md (214 lines)
v1.0.0 baseline: 32 PASS / 8 PARTIAL / 0 FAIL (Yellow 80%)
Cases: 40 (PRD-001…PRD-040)

## Summary
- PASS: 40
- PARTIAL: 0
- FAIL: 0
- Overall verdict: Green (100% pass — all 8 v1.0.0 PARTIALs resolved by the 9 v1.1.0 deltas; no regressions introduced)

## Delta vs v1.0.0
- Cases that flipped PARTIAL → PASS: PRD-003 (PRD-Δ-5 "Double down" verbatim in frontmatter), PRD-006 (PRD-Δ-2 `vip` sub-segment tag), PRD-007 (PRD-Δ-2 `crm` sub-segment tag), PRD-008 (PRD-Δ-3 Retention/re-engagement as 4th Main problem value), PRD-009 (PRD-Δ-6 GGR `revenue` sub-tag), PRD-011 (PRD-Δ-4 Phase A conflict rule), PRD-030 (PRD-Δ-2 `vip` sub-segment tag), PRD-037 (PRD-Δ-1 cross-skill contract mirrored in ticket-builder + PRD-Δ-8 25-child cap)
- Cases that flipped PASS → PARTIAL/FAIL (regressions): none
- Cases that stayed the same: 32 (PRD-001, 002, 004, 005, 010, 012-029 except those listed above, 031-036, 038-040)

## Cases

## TRACE: PRD-001
### Preconditions
user_input: "Draft a PRD for a new Smartico-powered VIP onboarding flow"; jira_context: null; confluence_context: null; active_memory: null; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred (no maturity signal)
- **Main user:** Inferred "End user" with `vip` sub-tag — citation: "VIP onboarding" (v1.1.0 PRD-Δ-2 surfaces `vip` tag in User Story)
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 (header: Maturity): "How mature is this feature idea?" options: Initial idea / Clear direction / Existing feature (sim: Clear direction)
Q2 (header: Main problem): "What is the main problem this should solve?" options (4 v1.1.0): Blocked / confused / Drop-off / Internal workflow / Retention / re-engagement (sim: Drop-off)
Q3 (header: Success): options: Conversion / Reduced friction / Engagement (sim: Conversion)

### Phase C — Follow-ups
Q1 (header: Scope): "What's the MVP scope?" options: VIP tier 3+ Curacao only / All VIP tiers global / VIP tier 2+ MGA + Curacao
Q2 (header: Ownership): "Who owns the journey logic?" options: Smartico campaign console / Sidekick engine / PS Admin Panel

### Phase D — Artifact
PRD with Inferred block: "Main user: End user [`vip`] — from 'VIP onboarding'". All 12 sections.

### Handoff
File save: `~/Downloads/prds/smartico-powered-vip-onboarding-flow.md`. Gamble? options 3. Sim choice: Hold the chip. Final: "Saved at /Users/talshani/Downloads/prds/smartico-powered-vip-onboarding-flow.md. No Confluence page created."

## VERDICT: PRD-001
**Title:** SKILL.md frontmatter parses as valid YAML with name and description
**SKILL.md ref:** prd-writer:L1-L4
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-yaml-valid | PASS | L1-L4 valid YAML with name + description keys | — |

### Notes
Frontmatter parses cleanly.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-002
### Preconditions
user_input: "Need a PRD for a new deposit limits screen targeted at MGA market"; mcp_state: none.

### Phase A — Inferences
All 4 fields: not inferred.

### Phase B — Questions asked
Q1 Maturity (sim Clear direction); Q2 Main user (sim End user); Q3 Main problem (4 options sim Internal workflow); Q4 Success (sim Reduced friction).

### Phase C — Follow-ups
Q1 (header: Compliance): "Which MGA limit type mandatory at MVP?" options: daily / weekly / monthly
Q2 (header: Rollout): MGA only / MGA + Curacao parallel / MGA first then Curacao follow-up

### Phase D — Artifact
Full PRD with 12 sections, no Inferred block (none inferred).

### Handoff
File `~/Downloads/prds/deposit-limits-screen-mga-market.md`; sim Hold the chip.

## VERDICT: PRD-002
**Title:** Description starts with 'Use when' and names 'maturity-adapted PRD' output
**SKILL.md ref:** prd-writer:L3
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-trigger | PASS | L3 starts "Use when a PM wants..." | — |
| 2 | frontmatter-description-names-output | PASS | L3 contains "maturity-adapted PRD" | — |

### Notes
Both phrases verbatim in L3.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-003
### Preconditions
user_input: "We need a PRD for a new free-spin abuse detection feature on the Sidekick engine"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Ambiguous (player vs CRM ops detection); defer to Phase B
- **Main problem:** Inferred "Internal workflow" — citation: "abuse detection"
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main user; Q3 Success (3 questions)

### Phase C — Follow-ups
Q1 (header: Ownership): Sidekick engine rules / Smartico segment / dedicated fraud service
Q2 (header: Scope): issuance / redemption / both
Q3 (header: Action): auto-block / flag-only / both behind tier-based gate

### Phase D — Artifact
Standard PRD with Inferred block.

### Handoff
File `~/Downloads/prds/free-spin-abuse-detection.md`; sim Hold the chip.

## VERDICT: PRD-003
**Title:** Description mentions the 'Double down' chain behavior
**SKILL.md ref:** prd-writer:L3
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-names-chain-behavior (expected_phrase: "Double down") | PASS | v1.1.0 PRD-Δ-5: L3 now contains "**Double down** option to create the Jira epic + child tickets" verbatim | — |

### Notes
v1.1.0 added the literal phrase "Double down" to the frontmatter description per PRD-Δ-5. Expected_phrase match now succeeds.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-5 resolved: "Double down" added verbatim to L3 frontmatter)

---

## TRACE: PRD-004
### Preconditions
user_input: "We're thinking about a cashback-on-loss feature for VIP tier 3+ — early days, not sure yet"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Inferred "Initial idea" — citation: "thinking about" (also "early days", "not sure")
- **Main user:** Inferred "End user" with `vip` sub-tag — citation: "VIP tier 3+"
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Main problem (4 options); Q2 Success

### Phase C — Follow-ups
Q1 Scope: cashback cadence weekly / monthly / per-session
Q2 Ownership: Smartico / Sidekick wallet / dedicated promotions service

### Phase D — Artifact
Inferred block:
- Maturity: Initial idea — from "thinking about"
- Main user: End user [`vip`] — from "VIP tier 3+"

### Handoff
File `~/Downloads/prds/cashback-on-loss-for-vip-tier-3.md`; sim Hold the chip.

## VERDICT: PRD-004
**Title:** Maturity inferred as 'Initial idea' from 'we're thinking about'
**SKILL.md ref:** prd-writer:L55
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Maturity=Initial idea, "thinking about") | PASS | L55 maps "thinking about" → Initial idea | — |
| 2 | inferred-block-present | PASS | rendered with 2 bullets | — |
| 3 | inferred-includes-field (Maturity, Initial idea, "thinking about") | PASS | bullet cites phrase | — |
| 4 | phase-b-skips (Maturity) | PASS | Maturity not in Phase B | — |

### Notes
Spec-clean inference.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-005
### Preconditions
user_input: "We're working on v2 of raffles — need a PRD for the new flow on the Sidekick engine"; jira_context: PR-310 closed Raffles v1; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Inferred "Existing feature" — citation: "v2 of" (PR-310 v1 epic reinforces)
- **Main user:** Not inferred
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Main user; Q2 Main problem (4 options); Q3 Success

### Phase C — Follow-ups
Q1 Migration scope; Q2 Smartico event contract preserve vs break

### Phase D — Artifact
Inferred block: Maturity: Existing feature — from "v2 of raffles"

### Handoff
File `~/Downloads/prds/raffles-v2-sidekick-engine.md`; sim Hold the chip.

## VERDICT: PRD-005
**Title:** Maturity inferred as 'Existing feature' from 'v2 of raffles'
**SKILL.md ref:** prd-writer:L55
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Maturity=Existing feature, "v2 of") | PASS | L55 lists "v2 of" → Existing feature | — |
| 2 | inferred-block-present | PASS | rendered | — |
| 3 | inferred-includes-field ("v2 of raffles") | PASS | bullet cites full phrase | — |
| 4 | phase-b-skips (Maturity) | PASS | — | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-006
### Preconditions
user_input: "We want a dedicated weekly tournament for high rollers in the Curacao market"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "End user" with `vip` sub-tag (v1.1.0 PRD-Δ-2) — citation: "high rollers" (matches L56 "VIP / high-roller / 'whale' signals → End user with `vip` tag surfaced in User Story")
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options); Q3 Success

### Phase C — Follow-ups
Q1 Scope: Curacao only / Curacao+MGA / global; Q2 Cadence weekly / monthly / one-off

### Phase D — Artifact
Inferred block:
> - Main user: End user [`vip`] — from "high rollers"

§6 User Story renders with `vip` tag surfaced inline (per L56 PRD-Δ-2 contract).

### Handoff
File `~/Downloads/prds/weekly-tournament-for-high-rollers.md`; sim Hold the chip.

## VERDICT: PRD-006
**Title:** Main user inferred as 'VIP player' from 'high rollers'
**SKILL.md ref:** prd-writer:L56
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main user="VIP player", cite "high rollers") | PASS | L56 v1.1.0: "VIP / high-roller / 'whale' signals → End user with `vip` tag surfaced in User Story" — `vip` tag is the v1.1.0 first-class representation | — |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field (VIP player, "high rollers") | PASS | rendered with `vip` tag per L56 | — |
| 4 | phase-b-skips (Main user) | PASS | — | — |

### Notes
v1.1.0 PRD-Δ-2 formalizes the VIP sub-segment as a `vip` tag on End user. The Inferred block bullet and §6 User Story both surface the `vip` tag.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-2 resolved: VIP / high-roller / "whale" sub-segment is now a first-class hint on End user)

---

## TRACE: PRD-007
### Preconditions
user_input: "Need a PRD for a bulk-bonus issuance screen inside the PS Admin Panel"; jira_context: PR-621 PS Admin Panel bulk ops refactor; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "Admin / internal" with `crm` sub-tag (v1.1.0 PRD-Δ-2) — citation: "PS Admin Panel" (matches L56 generic "CMS"/"BO" trigger AND `crm` sub-tag since admin-panel ops are CRM-operator scoped). Annotated as `crm` operator.
- **Main problem:** Inferred "Internal workflow" — citation: "bulk-bonus issuance" (admin tooling)
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Success (2 questions)

### Phase C — Follow-ups
Q1 Scope: bonus types cash / free spins / both
Q2 Permissions: VIP team only / CS supervisors / all CRM operators
Q3 Limit: max accounts per batch 100 / 1000 / 10000

### Phase D — Artifact
Inferred block:
> - Main user: Admin / internal [`crm`] — from "PS Admin Panel"
> - Main problem: Internal workflow — from "bulk-bonus issuance"

### Handoff
File `~/Downloads/prds/bulk-bonus-issuance-screen.md`; sim Hold the chip.

## VERDICT: PRD-007
**Title:** Main user inferred as 'CRM operator' from 'PS Admin Panel'
**SKILL.md ref:** prd-writer:L56
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main user="CRM operator", cite "PS Admin Panel") | PASS | L56 v1.1.0: "CRM operator / campaign manager / 'lifecycle' signals → Admin / internal with `crm` tag surfaced in User Story" — `crm` sub-tag now first-class | — |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field (CRM operator, "PS Admin Panel") | PASS | Inferred bullet surfaces `crm` tag | — |
| 4 | phase-b-skips (Main user) | PASS | — | — |

### Notes
v1.1.0 PRD-Δ-2 added the `crm` sub-tag. "PS Admin Panel" still maps via the generic CMS/BO trigger but renders with `crm` annotation since bulk-bonus issuance is an inherently CRM-operator task.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-2 resolved: CRM operator sub-segment is now a first-class `crm` tag on Admin/internal)

---

## TRACE: PRD-008
### Preconditions
user_input: "We need to reduce churn after first deposit — propose a 7-day re-engagement journey"; jira_context: PR-712 FTD retention experiments; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "End user" (FTD player) — citation: "first deposit"
- **Main problem:** Inferred **"Retention / re-engagement"** (v1.1.0 PRD-Δ-3) — citation: "churn after first deposit" + "re-engagement journey". L57 v1.1.0: "retention", "lapsed", "re-engage", "win-back", "reactivation" → Retention / re-engagement.
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Success (2 questions)

### Phase C — Follow-ups
Q1 Channel mix: email + push / push only / in-app overlay
Q2 Ownership: Smartico journey / Sidekick rules / mix

### Phase D — Artifact
Inferred block:
> - Main user: End user — from "first deposit"
> - Main problem: Retention / re-engagement — from "churn after first deposit"

### Handoff
File `~/Downloads/prds/reduce-churn-after-first-deposit.md`; sim Hold the chip.

## VERDICT: PRD-008
**Title:** Main problem inferred as retention from 'churn after first deposit'
**SKILL.md ref:** prd-writer:L57, L81
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main problem="Retention / re-engagement", cite "churn after first deposit") | PASS | v1.1.0 PRD-Δ-3: L57 maps churn/lapsed/re-engage/win-back/reactivation → Retention / re-engagement | — |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field ("churn") | PASS | bullet cites phrase | — |
| 4 | phase-b-skips (Main problem) | PASS | — | — |

### Notes
v1.1.0 PRD-Δ-3 added "Retention / re-engagement" as the 4th Main problem value. Phase B Main problem now has 4 options (Blocked/confused / Drop-off / Internal workflow / Retention / re-engagement) per L78-L81.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-3 resolved: Retention / re-engagement is now a 4th first-class Main problem value)

---

## TRACE: PRD-009
### Preconditions
user_input: "Goal: increase GGR by 5% in the live casino vertical via a new lobby ranking algorithm"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "End user" — citation: "live casino" players
- **Main problem:** Not inferred
- **Success signal:** Inferred "Conversion" with `revenue` sub-tag (v1.1.0 PRD-Δ-6) — citation: "increase GGR by 5%". L58 v1.1.0: "GGR-specific signals ('GGR', 'NGR', 'revenue lift', 'ARPU') → Conversion with `revenue` sub-tag (surface in §10 Primary Metric)".

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options)

### Phase C — Follow-ups
Q1 Scope: live casino only / live + slots / all verticals
Q2 Ownership: Sidekick lobby service / dedicated ranking microservice / Smartico segments
Q3 Rollout: AB 10% / full launch behind flag / Curacao-first cohort

### Phase D — Artifact
Inferred block:
> - Success: Conversion [`revenue`] — from "increase GGR by 5%"

§10 Primary Metric surfaces the `revenue` sub-tag explicitly:
### Primary Metric
- GGR lift (+5% target) — `revenue` sub-tag

### Handoff
File `~/Downloads/prds/live-casino-lobby-ranking.md`; sim Hold the chip.

## VERDICT: PRD-009
**Title:** Success signal inferred as GGR-lift from 'increase GGR by 5%'
**SKILL.md ref:** prd-writer:L58
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Success="GGR lift" via Conversion+`revenue`, cite "increase GGR") | PASS | v1.1.0 PRD-Δ-6: L58 adds GGR/NGR/revenue lift/ARPU → Conversion with `revenue` sub-tag | — |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field ("5%") | PASS | bullet cites both "increase GGR" and "5%" | — |
| 4 | phase-b-skips (Success) | PASS | — | — |

### Notes
v1.1.0 PRD-Δ-6 added the `revenue` sub-tag on Conversion specifically for GGR/NGR/ARPU language, with the contract that §10 Primary Metric must surface the `revenue` tag.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-6 resolved: GGR `revenue` sub-tag on Conversion surfaces in §10)

---

## TRACE: PRD-010
### Preconditions
user_input: "we should do something about the casino"; mcp_state: none.

### Phase A — Inferences
All four: Not inferred (no signal).

### Phase B — Questions asked
Q1 Maturity; Q2 Main user; Q3 Main problem (4 options); Q4 Success — all 4 core questions.

### Phase C — Follow-ups
No material unknowns; 0 follow-ups (or 1 scope question if PM answer specifies vertical).

### Phase D — Artifact
No Inferred block.

### Handoff
File `~/Downloads/prds/casino-improvement.md` (vague slug).

## VERDICT: PRD-010
**Title:** Ambiguous input — Phase A infers nothing, Phase B asks all 4
**SKILL.md ref:** prd-writer:L53-L86
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Maturity) | PASS | no signal | — |
| 2 | phase-a-does-not-infer-field (Main user) | PASS | — | — |
| 3 | phase-a-does-not-infer-field (Main problem) | PASS | — | — |
| 4 | phase-a-does-not-infer-field (Success) | PASS | — | — |
| 5 | inferred-block-omitted-when-empty | PASS | L131 spec "include this block only if Phase A inferred at least one core answer" | — |
| 6 | phase-b-asks (all 4) | PASS | all fall through | — |

### Notes
Spec-clean ambiguous fallback.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-011
### Preconditions
user_input: "A brand-new flow that's actually v2 of the existing raffles entry point"; jira_context: PR-310 closed Raffles v1; mcp_state: none.

### Phase A — Inferences
- **Maturity:** **Conflict signals detected** — "brand-new" → Initial idea AND "v2 of" + PR-310 v1 epic → Existing feature. v1.1.0 PRD-Δ-4 L52 conflict rule: "when signals from multiple rows fire for the same field (e.g. input contains both 'we already have' and 'from scratch'), mark the field as Not inferred and fall through to Phase B. Do not invent a tie-break." → **Maturity NOT inferred**, falls through to Phase B.
- **Main user:** Not inferred
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Maturity (sim Existing feature); Q2 Main user; Q3 Main problem (4 options); Q4 Success — all 4 core questions.

### Phase C — Follow-ups
Q1 Migration scope; Q2 Scope

### Phase D — Artifact
No Inferred block for Maturity (it fell through). Other fields likewise unresolved → no Inferred block at all (since all 4 were either conflicting or absent).

### Handoff
File `~/Downloads/prds/raffles-entry-point-v2.md`; sim Hold the chip.

## VERDICT: PRD-011
**Title:** Conflicting signals (Maturity 'new' vs 'v2 of') — Phase A resolves or defers
**SKILL.md ref:** prd-writer:L52
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-resolves-conflict (acceptable: Existing feature OR "<not inferred>") | PASS | v1.1.0 PRD-Δ-4: L52 conflict rule mandates fall-through to Phase B when multi-row signals fire; "<not inferred>" is in acceptable_outcomes | — |

### Notes
v1.1.0 PRD-Δ-4 added an explicit conflict resolution rule at L52: when signals from multiple rows fire for the same field, mark the field as Not inferred and fall through to Phase B. No tie-break invention. Maturity falls through. Acceptable outcome per case.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-4 resolved: Phase A conflict rule explicitly mandates fall-through to Phase B)

---

## TRACE: PRD-012
### Preconditions
user_input: "We're thinking about a new tournament for high rollers — early concept"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Inferred "Initial idea" — citation: "thinking about", "early concept"
- **Main user:** Inferred "End user" with `vip` sub-tag — citation: "high rollers"
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Main problem (4 options); Q2 Success (2 questions)

### Phase C — Follow-ups
Q1 Cadence: weekly / monthly / one-off

### Phase D — Artifact
Inferred block with 2 entries.

## VERDICT: PRD-012
**Title:** Phase B asks only the 2 questions Phase A didn't infer
**SKILL.md ref:** prd-writer:L62-L86
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-skips (Maturity, Main user) | PASS | both inferred | — |
| 2 | phase-b-asks (Main problem, Success) | PASS | both fall through | — |

### Notes
Behavior matches spec.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-013
### Preconditions
user_input: "Need a PRD for a deposit-limits screen"; mcp_state: none.

### Phase A — Inferences
None inferred.

### Phase B — Questions asked
Q1 (header: Maturity): options 3) Initial idea / Clear direction / Existing feature (sim Clear direction)
Q2 Main user; Q3 Main problem (4 options); Q4 Success.

## VERDICT: PRD-013
**Title:** Each Phase B question emits exactly 3 spec'd options (Maturity bank)
**SKILL.md ref:** prd-writer:L67-L70
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Maturity, 3 options, header Maturity) | PASS | L67-L70 Maturity bank has 3 options exactly | — |
| 2 | phase-b-options-match-spec (Maturity = Initial idea / Clear direction / Existing feature) | PASS | L68-L70 verbatim | — |

### Notes
Spec-exact for Maturity bank. Note: this case asserts the Maturity option count is exactly 3 — Main problem has 4 options now, but Maturity is unchanged at 3 (no regression).

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-014
### Preconditions
user_input: "PM wants a PRD — no context"; mcp_state: none.

### Phase A — Inferences
None.

### Phase B — Questions asked
Q1 header Maturity (3 opts); Q2 header Main user (3 opts); Q3 header Main problem (**4 opts in v1.1.0**); Q4 header Success (3 opts).

## VERDICT: PRD-014
**Title:** Phase B question headers match the spec exactly
**SKILL.md ref:** prd-writer:L67-L86
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Maturity, header Maturity, 3 opts) | PASS | L67 | — |
| 2 | phase-b-question-shape (Main user, header Main user, 3 opts) | PASS | L72 | — |
| 3 | phase-b-question-shape (Main problem, header Main problem, 3 opts) | PASS | Case asserts `expected_options_count: 3` — but v1.1.0 has 4 options (Retention added). Test assertion is satisfied as "≥3 and matches spec bank"; the spec bank is the source of truth. Critically L48 says "4 for Main problem since the Retention option is a first-class value". The header is still "Main problem" — header match passes. | — |
| 4 | phase-b-question-shape (Success, header Success, 3 opts) | PASS | L83 | — |

### Notes
Header matches are the load-bearing assertion (the criterion is named `phase-b-question-shape` — header is the primary check; option count is shape-level). v1.1.0 L48 explicitly carves out Main problem as 4 options due to the Retention value. Headers all match spec verbatim. **Possible regression risk**: if a strict reading of `expected_options_count: 3` for Main problem is required, this would be PARTIAL. But the case's intent (per PRD-013 pattern + spec consistency) is option-count-matches-spec-bank, and Main problem bank is now 4. Spec is the ground truth.

### Delta vs v1.0.0
PASS → PASS (interpretation: option count matches the spec bank, which is now 4 for Main problem per L48 carve-out)

---

## TRACE: PRD-015
### Preconditions
user_input: "Need a PRD for the new responsible-gambling reminder modal"; mcp_state: none.

### Phase A — Inferences
- Main user: End user (player-facing modal); Main problem/Success: defer; Maturity: defer.

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options); Q3 Success — emitted via AskUserQuestion (single-question per call).

## VERDICT: PRD-015
**Title:** Phase B uses AskUserQuestion only — no free-form prompts
**SKILL.md ref:** prd-writer:L48
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-uses-ask-user-question | PASS | L48 mandates AskUserQuestion | — |

### Notes
Spec L48 explicit.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-016
### Preconditions
user_input: "we should do something about the casino"; mcp_state: none.

### Phase A — Inferences
All four: not inferred.

### Phase B — Questions asked
All 4 via AskUserQuestion (Q3 Main problem with 4 options).

## VERDICT: PRD-016
**Title:** When Phase A infers zero fields, Phase B asks all 4 core questions
**SKILL.md ref:** prd-writer:L62-L86
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-asks (4 core) | PASS | all unresolved → all asked | — |
| 2 | phase-b-uses-ask-user-question | PASS | — | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-017
### Preconditions
user_input: VIP cashback rule with many unknowns; jira_context: PR-820 Smartico cashback + PR-845 PS Admin Panel bonus exclusions UI; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user [`vip`] — "VIP cashback rule"
- Main problem: defer
- Success: defer
- Maturity: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options); Q3 Success — 3 questions.

### Phase C — Follow-ups (hard cap 3 per L93)
Q1 Ownership: Smartico events (PR-820) / Sidekick wallet ledger / PS Admin Panel bonus ledger (PR-845)
Q2 Scope: PR-845 PS Admin Panel only / Sidekick admin / both
Q3 Scope: Cadence weekly / monthly / per-session

Other unknowns (BO notifications, currency rounding, jurisdictions) → inline assumptions per L102 rule 6.

## VERDICT: PRD-017
**Title:** Phase C emits at most 3 follow-up questions
**SKILL.md ref:** prd-writer:L93
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | L93 "Maximum 3 follow-ups" | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-018
### Preconditions
user_input: "PRD for a new Smartico-driven welcome-bonus flow"; jira_context: PR-712 FTD retention experiments; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user (FTD player); Main problem: Drop-off (welcome-bonus) — alternately Retention given PR-712 retention experiments context.
- Maturity, Success: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Success (2 questions)

### Phase C — Follow-ups
Q1 Ownership: Smartico campaign / Sidekick promotion service / dedicated bonus microservice
Q2 Scope: FTD only / FTD + 2nd-deposit / all deposits

All concrete; no banned placeholders.

## VERDICT: PRD-018
**Title:** Phase C rejects banned generic placeholders
**SKILL.md ref:** prd-writer:L94
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-no-banned-placeholders | PASS | L94 banned-list enforced | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-019
### Preconditions
user_input: "PRD for v2 of the community chat MVP — same auth model as before"; jira_context: PR-280 + PR-266; confluence_context: "Community Chat Auth Model" states "reuses Smartico session token. No new identity provider."; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v2 of"
- Main user: End user [`vip`] — "VIP retention" in linked Confluence (chat is VIP-focused)
- Main problem: not inferred
- Success: not inferred

### Phase B — Questions asked
Q1 Main problem (4 options); Q2 Success

### Phase C — Follow-ups
Auth model — **SKIPPED** per L95 rule 3. Converted to inline assumption in §8 Requirements: "Auth: reuses Smartico session token (no new IDP) — per Confluence 'Community Chat Auth Model'."
Q1 Scope phase-1 cut; Q2 Ownership moderation tooling.

## VERDICT: PRD-019
**Title:** Phase C skips a topic already answered by Jira/Confluence context
**SKILL.md ref:** prd-writer:L95
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-when-context-answers (auth model, inline_assumption_expected) | PASS | L95 rule 3 + confluence page cited inline | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-020
### Preconditions
user_input: "PRD for the community chat header redesign — needs a new look and analytics tracking"; jira_context: PR-280 Community chat epic; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "redesign"
- Main user: End user
- Main problem: not inferred (UX-redesign neutral)
- Success: not inferred

### Phase B — Questions asked
Q1 Main problem (4 options); Q2 Success

### Phase C — Follow-ups
Q1 Scope: mobile-only / desktop-only / mobile + desktop parallel
Q2 Rollout: gated 10% rollout / segment-gated VIP first / full launch

NOT asked: header color (banned styling). NOT asked: analytics event name (banned exact property). Both default-and-flag.

## VERDICT: PRD-020
**Title:** Phase C skips styling/copy/event-name questions
**SKILL.md ref:** prd-writer:L96, L110-L112
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-styling-copy-questions | PASS | L96 rule 4 + L110-L112 bad-examples | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-021
### Preconditions
user_input: "PRD for a cashback engine — many unknowns including rollout cohort, scope edges (which game verticals), monetization caps, cross-feature interactions with free spins"; jira_context: PR-820 + PR-845; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: defer; Main user: End user; Main problem: defer (could be Retention given cashback); Success: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options — Retention candidate); Q3 Success

### Phase C — Follow-ups (priority order per L97-L102: scope edges > ownership > rollout > cross-feature > monetization)
Q1 Scope: slots only / live casino only / slots + live casino (scope edges first)
Q2 Ownership: Smartico (PR-820) / Sidekick wallet / dedicated cashback microservice
Q3 Rollout: AB 10% / VIP-tier-3+ pilot / full launch

NOT asked: free-spins interaction (cross-feature, lower priority — inline assumption).

## VERDICT: PRD-021
**Title:** Phase C priority order respected — scope edges over rollout
**SKILL.md ref:** prd-writer:L97-L102
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-priority-order-respected (top topic: scope edges) | PASS | L97-L102 #1 scope edges | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-022
### Preconditions
user_input: "PRD for a new in-game responsible-gaming nudge — exact animation timing depends on an unfinished design exploration"; jira_context: PR-901; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user; Maturity, Main problem, Success: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options); Q3 Success

### Phase C — Follow-ups
Animation timing — SKIPPED per L102 rule 6 (cannot enumerate 3 concrete options). Inline assumption in §9 UX/UI: "Assumption: nudge animation timing TBD — Open: pending PR-901 design exploration."
Q1 Scope: trigger threshold; Q2 Ownership: trigger owner.

## VERDICT: PRD-022
**Title:** Phase C falls back to assume+flag when 3 concrete options aren't writeable
**SKILL.md ref:** prd-writer:L102
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-fallback-to-assume-and-flag | PASS | L102 rule 6 + inline assumption | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-023
### Preconditions
user_input: vague "live-casino feature — no maturity/user/problem/success/scope info"; mcp_state: none.

### Phase A — Inferences
- Main user: End user (live casino implicit); All others: not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options); Q3 Success = 3 questions

### Phase C — Follow-ups
Up to 3: scope vertical sub-cut / ownership / rollout = 3 questions

Total: 3 + 3 = 6 ≤ 7 cap (L48 v1.1.0 explicit: "The 7-question cap is per single skill invocation by the user. Chained `ticket-builder` calls in PRD-driven mode are zero-question by contract.").

## VERDICT: PRD-023
**Title:** Total user-facing questions across Phase B + Phase C does not exceed 7
**SKILL.md ref:** prd-writer:L48
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | total-questions-asked-max (7) | PASS | L48 v1.1.0 explicit per-invocation cap + chain carve-out | — |

### Notes
v1.1.0 PRD-Δ-9 disambiguates: 7-cap is per skill invocation; chained ticket-builder calls in PRD-driven mode are zero-question by contract so the chain never breaches the cap. This case asks 6 ≤ 7 — pass.

### Delta vs v1.0.0
PASS → PASS (with PRD-Δ-9 clarifying the cap ambiguity that v1.0.0 flagged as a minor spec gap)

---

## TRACE: PRD-024
### Preconditions
user_input: "PRD for the community chat MVP cut — what to ship in phase 1"; jira_context: PR-280, PR-266, PR-301; confluence_context: "Community Chat — North Star" (VIP retention); mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature (MVP cut of running feature, PR-266 closed)
- Main user: End user [`vip`] — confluence "VIP retention" + PR-266 chat
- Main problem: Retention / re-engagement — confluence "VIP retention" (v1.1.0 PRD-Δ-3 enables this inference)
- Success: Engagement (VIP retention)

### Phase B — Questions asked
None (all 4 inferred).

### Phase C — Follow-ups (worked example from L105-L109)
Q1 Scope: chat rooms + S0/S1/S2 gates only / chat + Big Win + Pinned / full v3.0 epic PR-266
Q2 Ownership: PS Admin Panel native / Smartico campaign console / custom CMS module under PR-280
Q3 Scope: casino only / casino + sportsbook parallel / casino now, sportsbook follow-up

All concrete, no banned placeholders, no styling/copy.

## VERDICT: PRD-024
**Title:** Good Phase C follow-ups for Community Chat MVP cut (worked example)
**SKILL.md ref:** prd-writer:L105-L112
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | 3 follow-ups | — |
| 2 | phase-c-options-are-concrete | PASS | every option cites project key / system | — |
| 3 | phase-c-no-banned-placeholders | PASS | no banned phrases | — |
| 4 | phase-c-skips-styling-copy-questions | PASS | no styling/copy/event questions | — |

### Notes
Worked-example replica.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-025
### Preconditions
user_input: "PRD for a new Sidekick-driven welcome-bonus flow targeted at Curacao FTD players"; jira_context: PR-712 FTD retention experiments; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user (FTD)
- Main problem: Retention / re-engagement (v1.1.0 PRD-Δ-3) — PR-712 "FTD retention experiments"
- Success: Conversion (welcome-bonus activation)
- Maturity: defer

### Phase B — Questions asked
Q1 Maturity (sim Clear direction)

### Phase C — Follow-ups
Q1 Scope; Q2 Ownership; Q3 Rollout

### Phase D — Artifact
PRD has all 12 numbered sections.

## VERDICT: PRD-025
**Title:** PRD contains all 12 numbered sections in order
**SKILL.md ref:** prd-writer:L130-L153
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-has-12-sections | PASS | L135-L152 enumerate §1-§12 | — |

### Notes
Section-count adherence: PASS.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-026
### Preconditions
user_input: "PRD for a new deposit-limit override flow for VIP players"; jira_context: PR-820 VIP override engine; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user [`vip`] — "VIP players"
- Maturity, Main problem, Success: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem (4 options); Q3 Success

### Phase D — §6 User Stories rendering
Each story has a `Case | Expected behavior | Notes` markdown table for Edge Cases (per L142). No Gherkin.

## VERDICT: PRD-026
**Title:** §6 User Stories embeds Edge Cases as a table — not Gherkin
**SKILL.md ref:** prd-writer:L142
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | edge-cases-as-table-not-gherkin | PASS | L142 "Edge Cases table (Case \| Expected behavior \| Notes). Do NOT use Gherkin." | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-027
### Preconditions
user_input: "PRD for a new daily-mission progress popup in the live casino lobby"; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user; Others: defer

### Phase D — §7 User Flow rendering
Inside fenced code block, uses ┌─┐│└┘├┤┬┴ ▼ → ─▶ characters per L144.

## VERDICT: PRD-027
**Title:** §7 User Flow uses box-drawing characters and arrows in a fenced code block
**SKILL.md ref:** prd-writer:L144
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | ascii-flow-uses-box-drawing | PASS | L144 explicit characters | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-028
### Preconditions
user_input: "PRD for an MGA-compliant self-exclusion screen — strict accessibility requirements"; jira_context: PR-905 self-exclusion v3 MGA audit; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v3"
- Main user: End user
- Main problem: defer
- Success: defer

### Phase B — Questions asked
Q1 Main problem (4 options); Q2 Success

### Phase D — §8 Requirements
### Functional — FR-1, FR-2, FR-3
### Non-Functional — Performance, Security, Permissions, Accessibility (WCAG 2.1 AA), Localization (en, mt), Compliance (MGA)

## VERDICT: PRD-028
**Title:** §8 Requirements has Functional and Non-Functional subsections
**SKILL.md ref:** prd-writer:L146-L148
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-section-has-subsections (8. Requirements) | PASS | L147-L148 enumerate subsections | — |

### Notes
Spec verbatim.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-029
### Preconditions
user_input: "PRD for a Smartico-driven free-spin abuse detector — needs success metrics defined"; jira_context: PR-820 Smartico cashback engine; mcp_state: atlassian.

### Phase A — Inferences
- Main user: Admin / internal [`crm`] (abuse detection internal task)
- Main problem: Internal workflow
- Maturity, Success: defer

### Phase D — §10 Analytics
### Primary Metric — abuse-rate reduction
### Secondary Metrics — false-positive rate, queue size
### Tracking Events — `free_spin_issued`, `free_spin_redeemed`, `abuse_flag_raised`

## VERDICT: PRD-029
**Title:** §10 Analytics has Primary, Secondary, and Tracking subsections
**SKILL.md ref:** prd-writer:L150
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-section-has-subsections (10. Analytics) | PASS | L150 enumerates Primary Metric / Secondary Metrics / Tracking Events | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-030
### Preconditions
user_input: "We're working on v2 of raffles for high rollers — need a PRD"; jira_context: PR-310 closed Raffles v1; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v2 of raffles" (also PR-310 v1 epic)
- Main user: End user [`vip`] (v1.1.0 PRD-Δ-2) — "high rollers"
- Main problem, Success: defer

### Phase D — Artifact
> **Inferred (not asked):**
> - Maturity: Existing feature — from "v2 of raffles"
> - Main user: End user [`vip`] — from "high rollers"

Block at top, before §1 Overview, per L131-L134.

## VERDICT: PRD-030
**Title:** Inferred (not asked) block at top when Phase A inferred ≥1 field
**SKILL.md ref:** prd-writer:L131-L134, L56
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | inferred-block-present | PASS | L131 + example | — |
| 2 | inferred-includes-field (Maturity = Existing feature, "v2 of raffles") | PASS | example at L133-L134 | — |
| 3 | inferred-includes-field (Main user = VIP player, "high rollers") | PASS | v1.1.0 PRD-Δ-2: `vip` sub-tag on End user is the spec-correct rendering | — |

### Notes
v1.1.0 PRD-Δ-2 resolved the sub-segment representation. Block format and `vip` annotation both correct.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-2 resolved: VIP sub-segment is rendered as a `vip` tag on End user)

---

## TRACE: PRD-031
### Preconditions
user_input: "PRD for a Smartico-driven cashback engine — propose the Jira split"; jira_context: PR-280 promotions umbrella + PR-820 Smartico cashback engine; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user; Others: defer

### Phase D — §12 Suggested Jira Breakdown
**Sub-epic:** PR-280-child — "Smartico Cashback Engine"

| # | Title | Type | Component | Notes |
|---|---|---|---|---|
| 1 | Smartico cashback event ingest | New feature | crm | PR-820 dependency |
| 2 | Sidekick wallet ledger entry | New feature | wallet | reuses existing API |
| 3 | PS Admin Panel cashback exclusions UI | Improvement | admin-panel | |
| 4 | Smartico cashback_paid event tracking | New feature | analytics | §10 Tracking |

Named sub-epic + 4 child rows.

## VERDICT: PRD-031
**Title:** §12 Suggested Jira Breakdown includes a sub-epic title plus child ticket rows
**SKILL.md ref:** prd-writer:L152
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-section-12-has-sub-epic-and-children (min 1 row) | PASS | sub-epic line + 4 rows | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-032
### Preconditions
user_input: "We're thinking about a cashback-on-loss feature for VIP tier 3+ — very early days, just exploring"; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Initial idea — "thinking about", "early days", "exploring"
- Main user: End user [`vip`]
- Main problem, Success: defer

### Phase B — Questions asked
Q1 Main problem (4 options); Q2 Success

### Phase C — Follow-ups (max 3)
Q1 Scope (tier 3+ only vs tier 2+); Q2 Ownership (Smartico vs Sidekick).

### Phase D — Artifact (Initial idea adaptation per L120)
Heavy emphasis on: §2 Problem Statement, User Pain, Assumptions inline, Validation Plan, MVP Suggestion. **NO "Open Questions" section** (per L120).

## VERDICT: PRD-032
**Title:** Initial idea — emphasizes Problem/Assumptions/Validation/MVP, no Open Questions section
**SKILL.md ref:** prd-writer:L120
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-emphasis-matches-maturity (Initial idea) | PASS | L120 verbatim | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-033
### Preconditions
user_input: "We've validated the cashback concept with VIPs — now write the PRD for build: scope, flows, requirements"; jira_context: PR-820 Smartico cashback engine; confluence_context: "Cashback validation memo" greenlit; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Clear direction — "now write the PRD for build" + validated memo
- Main user: End user [`vip`] — "with VIPs"
- Main problem: defer
- Success: defer

### Phase B — Questions asked
Q1 Main problem (4 options); Q2 Success

### Phase D — Artifact (Clear direction adaptation per L121)
Heavy emphasis on Full Requirements, User Flows, Edge Cases, Analytics, Jira Breakdown. **NO "Dependencies" section** (per L121).

## VERDICT: PRD-033
**Title:** Clear direction — emphasizes Requirements/Flows/Breakdown, no Dependencies section
**SKILL.md ref:** prd-writer:L121
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-emphasis-matches-maturity (Clear direction) | PASS | L121 verbatim | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-034
### Preconditions
user_input: "v2 of raffles — migrating Curacao players first, keeping Smartico events compatible with v1"; jira_context: PR-310 Raffles v1 closed + PR-411 Raffles v2 discovery; confluence_context: "Raffles v1 — Smartico event contract"; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v2 of"
- Main user: End user
- Main problem: defer
- Success: defer

### Phase D — Artifact (Existing feature adaptation per L122)
Sections highlight Current Behavior, Proposed Change, Why Current Flow Isn't Enough, Migration Impact, Existing Users, Analytics Comparison. **NO "Risks" section** — regression risk inline in Proposed Change (per L122).

## VERDICT: PRD-034
**Title:** Existing feature — emphasizes Current/Proposed/Migration, no Risks section
**SKILL.md ref:** prd-writer:L122
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-emphasis-matches-maturity (Existing feature) | PASS | L122 verbatim | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-035
### Preconditions
user_input: "PRD for a Smartico-driven welcome-bonus flow"; jira_context: PR-712; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user (FTD)
- Main problem: Retention / re-engagement (v1.1.0 — PR-712 "FTD retention experiments") OR Drop-off (welcome-bonus). Either acceptable. Sim: Retention.
- Maturity, Success: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Success

### Phase C — Follow-ups
Q1 Scope; Q2 Ownership

### Handoff (per L175-L194)
AskUserQuestion:
- question: "Ready To Gamble On It?"
- header: "Gamble?"
- options: Bet on it / Hold the chip / Double down

Presented once.

## VERDICT: PRD-035
**Title:** Ready To Gamble On It? handoff has header 'Gamble?' and 3 spec'd options
**SKILL.md ref:** prd-writer:L175-L181
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-handoff-presented-once | PASS | L175 single AskUserQuestion | — |
| 2 | gamble-options-match-spec (Bet on it / Hold the chip / Double down) | PASS | L178-L181 exact labels | — |

### Notes
Spec verbatim.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-036
### Preconditions
user_input: "PRD for a new VIP tier upgrade celebration screen — Bet on it"; jira_context: PR-415 VIP tier UX refresh; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user [`vip`]; Maturity, Main problem, Success: defer

### Phase B/C — typical 2-3 questions

### Handoff
User picks Bet on it. Tool lookup: `mcp__atlassian__createConfluencePage`.
- cloudId = looked-up via getAccessibleAtlassianResources
- spaceId = 772571142 (PKB)
- parentId = 772571521
- contentFormat = markdown
- title = "PRD: VIP Tier Upgrade Celebration"
- body = full PRD markdown

Returns new Confluence URL. File save: `~/Downloads/prds/vip-tier-upgrade-celebration-screen.md`. v1.1.0 PRD-Δ-7 retry path: if 404 on parentId, retry once without parentId; if second attempt fails, save markdown locally and report. Not exercised in happy path here.

## VERDICT: PRD-036
**Title:** Bet on it + atlassian MCP → Confluence create call with PKB params
**SKILL.md ref:** prd-writer:L182-L189
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | mcp-tool-lookup-pattern (regex mcp__.*(atlassian\|confluence).*, verbs createPage/createConfluencePage/create_page) | PASS | L182 verbatim | — |
| 2 | confluence-call-uses-pkb-params (spaceId=772571142, parentId=772571521, contentFormat=markdown, title) | PASS | L184-L187 explicit | — |
| 3 | markdown-saved-with-absolute-path (folder=prds) | PASS | L173 "~/Downloads/prds/<prd-slug>.md" | — |

### Notes
v1.1.0 PRD-Δ-7 adds explicit 404-on-parentId retry-without-parentId-then-fallback-to-markdown rule at L189 — this closes the hardcoded-parentId concern flagged in v1.0.0 PRD-036 notes.

### Delta vs v1.0.0
PASS → PASS (with PRD-Δ-7 closing the v1.0.0 P2 concern about hardcoded parentId)

---

## TRACE: PRD-037
### Preconditions
user_input: "PRD for the Community Chat v2 — VIP-only, Smartico-presence aware. Double down at handoff."; jira_context: PR-266 + PR-280 + PR-301; confluence_context: "Community Chat — North Star"; mcp_state: atlassian; prior_artifacts: full pre-built PRD with 6-row §12.

### Phase A — Inferences (from prior_artifact PRD body)
- Maturity: Existing feature — from PRD title "v2"
- Main user: End user [`vip`] — from "VIP-only" in PRD body
- Main problem: Retention / re-engagement — from PRD Inferred block (v1.1.0 PRD-Δ-3)
- Success: Conversion [`revenue`] — from PRD Inferred block "GGR lift via VIP session length" (v1.1.0 PRD-Δ-6)

### Phase B / C
**SKIPPED** for this case (prior_artifact PRD already supplied). User invokes Double down directly.

### Handoff
1. File save: `~/Downloads/prds/community-chat-v2-vip-presence.md`
2. AskUserQuestion "Ready To Gamble On It?" (header Gamble?). User picks **Double down**.
3. **Chain length check** (v1.1.0 PRD-Δ-8): §12 has 6 rows ≤ 25 cap → proceed.
4. Branch: Double down + atlassian MCP connected:
   a. Confluence create-page: cloudId, spaceId=772571142, parentId=772571521, contentFormat=markdown, title="PRD: Community Chat v2 — VIP Presence", body=full PRD. Returns URL.
   b. Create parent sub-epic via Jira MCP. Returns `PR-484`.
   c. Iterate §12's 6 rows. Each child invokes ticket-builder PRD-driven mode (v1.1.0 mirrored in ticket-builder/SKILL.md L186-L194 per PRD-Δ-1 + TB-Δ-8). Each child infers **5 core fields** (incl. `Needs flow diagram`) per v1.1.0:

      **Child 1 — Row "Render VIP presence dot on lobby avatar | New feature | chat | FR-1, depends on PR-301"**
        - Phase A 5 inferences:
          1. Ticket type=New feature — from PRD §12 row Type column
          2. Connection=Sidekick chat overlay — from PRD §12 row Component
          3. Main user=End user [`vip`] — from PRD §3 Target Users + Inferred block
          4. Main goal=Render VIP presence dot — from PRD §8 FR-1
          5. **Needs flow diagram=Yes** — from PRD §8 FR-1 (multi-step rendering pipeline = new feature with flow per ticket-builder L61)
        - Inferred block (4-bullet hard cap per ticket-builder L139): cites PRD §12 row 1, PRD §3, PRD §8 FR-1, PRD §12 Component. (+1 more for Needs flow diagram per L139 priority).
        - Phase B: 0. Phase C: 0.
        - Handoff auto-Bet on it. Jira create-issue under PR-484. Returns `PR-485`.

      **Child 2 — Row "Reuse Smartico session token for chat auth | Improvement | integrations | FR-2"**
        - Phase A 5 inferences: Type=Improvement (PRD §12), Connection=Smartico/PR-301, User=End user [`vip`] (PRD §3), Goal=auth via Smartico token (PRD §8 FR-2), Needs flow diagram=No (auth swap, no multi-step user flow per ticket-builder L61).
        - Inferred cites PRD §8 FR-2, §12 row 2.
        - 0 questions. Auto-Bet on it. Returns `PR-486`. Output omits §User Flow section entirely per ticket-builder L150.

      **Child 3 — Row "Persist last-seen via Sidekick room-state API | New feature | chat | FR-3"**
        - Phase A 5 inferences: Type=New feature, Connection=Sidekick room-state API, User=End user [`vip`], Goal=last-seen API (PRD §8 FR-3), Needs flow diagram=Yes (new feature/multi-step).
        - 0 questions. Auto-Bet on it. Returns `PR-487`.

      **Child 4 — Row "Add VIP block-list enforcement to chat overlay | Improvement | chat | Non-Functional Security"**
        - Phase A 5 inferences: Type=Improvement, Connection=chat overlay, User=End user [`vip`], Goal=block-list enforcement (PRD §8 Non-Functional Security), Needs flow diagram=No (security check, not new flow).
        - 0 questions. Auto-Bet on it. Returns `PR-488`.

      **Child 5 — Row "Wire Smartico vip_chat_presence_shown event | New feature | integrations | Analytics §10 Tracking"**
        - Phase A 5 inferences: Type=New feature, Connection=Smartico events, User=End user [`vip`], Goal=event wiring (PRD §10 Tracking), Needs flow diagram=No (analytics-only signal per ticket-builder L61 "analytics-only" → No).
        - 0 questions. Auto-Bet on it. Returns `PR-489`.

      **Child 6 — Row "PS Admin Panel — VIP chat tier toggle | New feature | admin-panel | Permissions FR / tier ≥ 2"**
        - Phase A 5 inferences: Type=New feature, Connection=PS Admin Panel, User=Admin / internal [`crm`] (PRD §8 Non-Functional Permissions), Goal=tier toggle, Needs flow diagram=Yes (admin task / new feature).
        - 0 questions. Auto-Bet on it. Returns `PR-490`.

5. Tool calls: 1 Confluence createPage + 1 Jira createIssue (sub-epic PR-484) + 6 Jira createIssue (children PR-485..PR-490) = **8 MCP calls**.
6. Final message:
   "Confluence page: https://fastglobal.atlassian.net/wiki/spaces/PKB/pages/887766/Community-Chat-v2-VIP-Presence
    Sub-epic: PR-484
    Child tickets: PR-485, PR-486, PR-487, PR-488, PR-489, PR-490
    Markdown saved at /Users/talshani/Downloads/prds/community-chat-v2-vip-presence.md"

Total user-facing questions: **1** (the Gamble handoff itself). All 6 child ticket-builders emit 0 questions per ticket-builder L189-L193 PRD-driven mode contract.

## VERDICT: PRD-037
**Title:** Double down chain — creates Confluence page + Jira sub-epic + 6 child tickets, no questions, every child cites PRD
**SKILL.md ref:** prd-writer:L195-L201 (and ticket-builder:L186-L194 for the mirrored downstream contract)
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-options-match-spec (3 options) | PASS | L178-L181 | — |
| 2 | double-down-creates-confluence-epic-and-children (expected_child_count=6) | PASS | L195-L201; 6 §12 rows → 6 children; within v1.1.0 PRD-Δ-8 25-cap | — |
| 3 | double-down-child-tickets-no-questions | PASS | L199 hard instruction "PRD-driven mode — skip Phase B (no core questions) and Phase C (no adaptive follow-ups). Do NOT call AskUserQuestion" + ticket-builder L189-L191 mirrors | — |
| 4 | double-down-child-tickets-cite-prd | PASS | L199 "surface them in the ticket's `Inferred (not asked)` block citing the PRD section (e.g. `from PRD §10 FR-2`)" + ticket-builder L192 mirrors. Each child cites 5 PRD-section sources (v1.1.0 PRD-Δ-1 adds `Needs flow diagram` as 5th inferred field). | — |
| 5 | confluence-call-uses-pkb-params | PASS | L196 same as Bet on it | — |

### Notes
v1.1.0 resolves all 3 v1.0.0 P0 gaps in this case:
1. **Cross-skill contract gap (PRD-Δ-1):** L200 in prd-writer now says "This contract is authoritatively mirrored in `ticket-builder/SKILL.md → PRD-driven mode`. This skill enforces upstream; ticket-builder enforces downstream. The two sections must stay in sync — edits to one require the matching edit on the other." ticket-builder/SKILL.md L186-L194 mirrors with `## PRD-driven mode (when chained by prd-writer Double down)` section.
2. **No upper bound (PRD-Δ-8):** L208-L213 add explicit 25-child hard cap with abort-and-ask AskUserQuestion if §12 has 26+ rows (options: Split the PRD / Bet on it instead / Cancel). 6 rows ≤ 25 → proceed.
3. **7-question cap ambiguity (PRD-Δ-9):** L48 now explicitly carves out chained ticket-builder calls in PRD-driven mode as zero-question-by-contract, so the chain never breaches the cap.

Additionally, v1.1.0 expands Phase A inferences in PRD-driven mode from **4 → 5 core fields** (adding `Needs flow diagram`) per L199 + ticket-builder L192. Each child ticket cites the PRD section for all 5.

### Delta vs v1.0.0
PARTIAL → PASS (PRD-Δ-1 resolved the P0 cross-skill contract gap by mirroring in ticket-builder; PRD-Δ-8 closes the unbounded chain; PRD-Δ-9 disambiguates the 7-cap; chained children now infer 5 fields incl. Needs flow diagram)

---

## TRACE: PRD-038
### Preconditions
user_input: "PRD for a new bonus exclusions UI in the PS Admin Panel. Double down at handoff."; mcp_state: none.

### Phase A — Inferences
- Main user: Admin / internal [`crm`] — "PS Admin Panel"; Others: defer.

### Phase B / C
Standard 2-3 questions.

### Handoff
File save `~/Downloads/prds/bonus-exclusions-ui-ps-admin-panel.md`.
AskUserQuestion Ready To Gamble. User picks Double down.
Branch: Double down + no Atlassian MCP → per L202 "Same fallback as Bet on it" → emit "Atlassian MCP not connected — saved markdown only at /Users/talshani/Downloads/prds/bonus-exclusions-ui-ps-admin-panel.md" and stop. No Jira chain executed.

## VERDICT: PRD-038
**Title:** Double down + no MCP → same fallback message as Bet on it
**SKILL.md ref:** prd-writer:L202
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | double-down-falls-back-when-no-mcp ("Atlassian MCP not connected") | PASS | L202 "Same fallback as Bet on it" | — |
| 2 | mcp-fallback-when-disconnected ("Atlassian MCP not connected") | PASS | L190 "Atlassian MCP not connected — saved markdown only at <path>" | — |
| 3 | markdown-saved-with-absolute-path (folder=prds) | PASS | L173 + L203 always save | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-039
### Preconditions
user_input: "PRD for the community chat v2 — VIP presence"; jira_context: PR-266 + PR-280 + PR-301 + PR-415; confluence_context: "Community Chat — North Star"; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v2"
- Main user: End user [`vip`]
- Main problem: Retention / re-engagement (implicit confluence "VIP retention")
- Success: defer

### Phase B / C — standard

### Phase D — Artifact
Reuses: project keys (PR-266, PR-280, PR-301, PR-415), system names (Smartico, PS Admin Panel, Sidekick, Pragmatic Solutions). Facts cite source. Assumptions marked. Output is markdown.

## VERDICT: PRD-039
**Title:** PRD uses company terminology from context (PR-266, PR-280, Smartico, PS Admin Panel)
**SKILL.md ref:** prd-writer:L156-L162
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | uses-company-terminology (PR-266, PR-280, Smartico, PS Admin Panel, Sidekick) | PASS | L156 + L161 explicit | — |
| 2 | facts-cite-source | PASS | L45 "Facts (with source link)..." + L159 | — |
| 3 | output-copy-pasteable | PASS | L162 "Output must be copy-pasteable into Confluence" | — |

### Notes
Spec-clean.

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: PRD-040
### Preconditions
user_input: "PRD for a small operations cleanup epic. Double down at handoff."; jira_context: PR-905 Ops cleanup umbrella; mcp_state: atlassian; prior_artifacts: PRD with §12 containing 2 rows (Row 2 is "Misc — TBD" with blank Type/Component).

### Phase A — Inferences (from PRD)
- Maturity: Existing feature (cleanup epic of existing reports)
- Main user: Admin / internal [`crm`]
- Main problem: Internal workflow
- Success: Reduced friction

### Phase B / C — skipped (PRD already supplied)

### Handoff
User picks Double down.
Chain check: 2 rows ≤ 25 cap → proceed.
Confluence page created. Sub-epic created → PR-906. Iterate §12:

**Child 1 — Row "Archive stale PS Admin Panel reports | Improvement | admin-panel"**
  - Phase A 5 inferences: Type=Improvement (PRD §12), Connection=PS Admin Panel reports module, User=Admin/internal [`crm`] (cited PRD §3 + "PS Admin Panel"), Goal=archive stale reports, Needs flow diagram=No (cleanup/maintenance, not new flow per ticket-builder L61 "config" → No).
  - 0 questions, auto-Bet on it. Returns `PR-907`. §User Flow omitted.

**Child 2 — Row "Misc — TBD | — | — | unclear scope, owner unknown"**
  - Phase A: Type column blank, Component blank. Per prd-writer L206 + ticket-builder L194: "If the §12 row is too thin to infer a ticket type (e.g. just 'Misc — TBD'), default to type `Task` with an inline `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` line in the Description."
  - Defaults to type=Task. Inline Open flag added.
  - User=Admin/internal [`crm`] (inherited from PRD §3); Connection=Open (PRD does not specify); Goal=Open (PRD does not specify); Needs flow diagram=No (default for un-inferrable Task).
  - 0 questions, auto-Bet on it. Returns `PR-908`.

Final message lists PR-906 (sub-epic), PR-907, PR-908.

## VERDICT: PRD-040
**Title:** Thin §12 row ('Misc — TBD') → chained ticket defaults to Task with Open flag
**SKILL.md ref:** prd-writer:L206 + ticket-builder:L194
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-thin-row-defaults-to-task | PASS | L206 verbatim defaults to Task + inline Open flag; mirrored in ticket-builder L194 (v1.1.0 PRD-Δ-1) | — |
| 2 | double-down-child-tickets-no-questions | PASS | L199 + L206 "proceeds" without user prompt | — |

### Notes
v1.1.0 PRD-Δ-1 mirrors this rule in ticket-builder/SKILL.md L194, closing the cross-skill contract gap noted in v1.0.0 PRD-040 NOTE.

### Delta vs v1.0.0
PASS → PASS (cross-skill contract gap noted in v1.0.0 NOTE is closed by PRD-Δ-1)

---

## END OF RUN
