# prd-writer — Raw Run
Date: 2026-05-23
SKILL.md path: /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/prd-writer/SKILL.md
Cases: 40 (PRD-001…PRD-040)

## Summary
- PASS: 32
- PARTIAL: 8
- FAIL: 0
- Overall verdict: Yellow (80% pass — at threshold boundary, defect cluster around Main user / Main problem / Success sub-segment bank gaps + Phase A conflict-resolution silence + cross-skill contract gap)

## Cases

## TRACE: PRD-001
### Preconditions
user_input: "Draft a PRD for a new Smartico-powered VIP onboarding flow"; jira_context: null; confluence_context: null; active_memory: null; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred (no maturity signal)
- **Main user:** Inferred to "VIP player" — citation: "VIP onboarding"
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 (header: Maturity): "How mature is this feature idea?"
  options: 1) Initial idea 2) Clear direction 3) Existing feature
  (simulated PM answer: Clear direction)
Q2 (header: Main problem): "What is the main problem this should solve?"
  options: 1) Blocked / confused 2) Drop-off 3) Internal workflow
  (simulated PM answer: Drop-off)
Q3 (header: Success): "What is the main success signal?"
  options: 1) Conversion 2) Reduced friction 3) Engagement
  (simulated PM answer: Conversion)

### Phase C — Follow-ups
Q1 (header: Scope): "What's the MVP scope?"
  options: 1) VIP tier 3+ Curacao only 2) All VIP tiers global 3) VIP tier 2+ MGA + Curacao
  rationale: scope edges priority; concrete tiers + markets
Q2 (header: Ownership): "Who owns the journey logic?"
  options: 1) Smartico campaign console 2) Sidekick engine 3) PS Admin Panel
  rationale: system/data ownership

### Phase D — Artifact
```markdown-artifact
# PRD: Smartico-powered VIP Onboarding Flow
> **Inferred (not asked):**
> - Main user: VIP player — from "VIP onboarding"

## 1. Overview ... ## 12. Suggested Jira Breakdown
**Sub-epic:** Smartico VIP Onboarding
| # | Title | Type | Component | Notes |
|---|---|---|---|---|
| 1 | Define Smartico onboarding campaign | New feature | crm | Smartico console |
| 2 | Sidekick welcome modal UI | New feature | sidekick | Welcome step |
```

### Handoff
1. File save: `~/Downloads/prds/smartico-powered-vip-onboarding-flow.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip / Double down
3. Simulated user choice: Hold the chip (no MCP)
4. Tool calls: none
5. Final message: "Saved at /Users/talshani/Downloads/prds/smartico-powered-vip-onboarding-flow.md. No Confluence page created."

## VERDICT: PRD-001
**Title:** SKILL.md frontmatter parses as valid YAML with name and description
**SKILL.md ref:** prd-writer:L1-L5
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-yaml-valid | PASS | "name: prd-writer" + "description: Use when..." parse as valid YAML between --- markers | — |

### Notes
SKILL.md L1-L5 shows valid YAML frontmatter with both required keys.

---

## TRACE: PRD-002
### Preconditions
user_input: "Need a PRD for a new deposit limits screen targeted at MGA market"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Not inferred (player implicit)
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 (header: Maturity): "How mature is this feature idea?" options: Initial idea / Clear direction / Existing feature (sim: Clear direction)
Q2 (header: Main user): "Who is the main user affected?" options: End user / Admin / internal / Support / ops (sim: End user)
Q3 (header: Main problem): "What is the main problem this should solve?" options: Blocked / confused / Drop-off / Internal workflow (sim: Internal workflow)
Q4 (header: Success): options: Conversion / Reduced friction / Engagement (sim: Reduced friction)

### Phase C — Follow-ups
Q1 (header: Compliance): "Which MGA limit type is mandatory?" options: daily / weekly / monthly  rationale: scope edge for MGA compliance
Q2 (header: Rollout): "MGA only or also Curacao at launch?" options: MGA only / MGA + Curacao parallel / MGA first then Curacao follow-up

### Phase D — Artifact
```markdown-artifact
# PRD: Deposit Limits Screen — MGA Market
## 1. Overview ... ## 12. Suggested Jira Breakdown
**Sub-epic:** Deposit Limits MGA
```

### Handoff
1. File save: `~/Downloads/prds/deposit-limits-screen-mga-market.md`
2. Gamble question with header Gamble?, 3 options
3. Simulated user choice: Hold the chip
4. Final message: "Saved at ... No Confluence page created."

## VERDICT: PRD-002
**Title:** Description starts with 'Use when' and names 'maturity-adapted PRD' output
**SKILL.md ref:** prd-writer:L3-L5
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-trigger | PASS | L3 description begins "Use when a PM wants to turn an idea..." | — |
| 2 | frontmatter-description-names-output | PASS | L3 contains "returns a maturity-adapted PRD" | — |

### Notes
Both phrases present verbatim in SKILL.md frontmatter description.

---

## TRACE: PRD-003
### Preconditions
user_input: "We need a PRD for a new free-spin abuse detection feature on the Sidekick engine"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "End user" / players (abuse on player accounts) — soft signal; alternately CRM operator who detects abuse. Treated as not-confidently-inferred → defer to Phase B.
- **Main problem:** Inferred "Internal workflow" — citation: "abuse detection" (ops-style)
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 (header: Maturity), Q2 (header: Main user), Q3 (header: Success)

### Phase C — Follow-ups
Q1 (header: Ownership): "Where does detection logic live?" options: Sidekick engine rules / Smartico segment / dedicated fraud service
Q2 (header: Scope): "Detect at issuance or at redemption?" options: issuance only / redemption only / both
Q3 (header: Action): "Auto-block, flag-only, or both?" options: auto-block tier-1 only / flag for CRM ops / both behind tier-based gate

### Phase D — Artifact
PRD output with Inferred block citing "abuse detection" for Main problem.

### Handoff
1. File: `~/Downloads/prds/free-spin-abuse-detection.md`
2. Gamble?, 3 options
3. Sim choice: Hold the chip
4. Final: standard

## VERDICT: PRD-003
**Title:** Description mentions the 'Double down' chain behavior
**SKILL.md ref:** prd-writer:L3-L5
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-names-chain-behavior | PASS | L3 includes "...optionally chain the ticket-builder skill to create the Jira epic + child tickets" and ends with the Double down summary in handoff — the description references the chain behavior explicitly | — |

### Notes
The frontmatter description uses the phrase "chain the ticket-builder skill to create the Jira epic + child tickets". Although the exact word "Double down" is not in the description (it's only used later in §Handoff at L185), the description does name the chain behavior. PARTIAL risk on strict expected_phrase match: criterion expected_phrase "Double down" is NOT in the description verbatim. Marking PARTIAL on exact-phrase check.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P2
Location: skills/prd-writer/SKILL.md:L3
Symptom: Description names the chain behavior but does not include the literal handoff option name "Double down", so a literal phrase match fails.
Proposed edit:
```
description: Use when a PM wants to turn an idea, initiative, or discovery outcome into a full PRD. Scans Jira/Confluence for related context, adaptively asks only the questions input doesn't already answer, adds up to 3 context-derived follow-ups for real unknowns, and returns a maturity-adapted PRD. Ends with a "Ready To Gamble On It?" handoff that can push to Confluence (Product Knowledge Base space) and optionally "Double down" to chain the ticket-builder skill to create the Jira epic + child tickets, or save markdown only.
```

Actually re-reading L3: "and optionally chain the ticket-builder skill". The expected_phrase is exactly "Double down" — not present. So this is a real PARTIAL.

**Overall (revised):** PARTIAL

---

## TRACE: PRD-004
### Preconditions
user_input: "We're thinking about a cashback-on-loss feature for VIP tier 3+ — early days, not sure yet"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Inferred "Initial idea" — citation: "thinking about" (also "early days", "not sure")
- **Main user:** Inferred "VIP player" — citation: "VIP tier 3+"
- **Main problem:** Not inferred (no churn/drop-off/blocked signal)
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 (header: Main problem); Q2 (header: Success)

### Phase C — Follow-ups
Q1 (header: Scope): "Cashback cadence?" options: weekly / monthly / per-session  rationale: scope edges
Q2 (header: Ownership): "Where does ledger live?" options: Smartico / Sidekick wallet / dedicated promotions service

### Phase D — Artifact
```markdown-artifact
# PRD: Cashback-on-Loss for VIP Tier 3+
> **Inferred (not asked):**
> - Maturity: Initial idea — from "thinking about"
> - Main user: VIP player — from "VIP tier 3+"
## 1. Overview ... ## 12. Suggested Jira Breakdown
```

### Handoff
1. File save: `~/Downloads/prds/cashback-on-loss-for-vip-tier-3.md`
2. Gamble?
3. Sim: Hold the chip

## VERDICT: PRD-004
**Title:** Maturity inferred as 'Initial idea' from 'we're thinking about'
**SKILL.md ref:** prd-writer:L53-L58
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Maturity=Initial idea, cite "thinking about") | PASS | L54 row maps "thinking about" → Initial idea | — |
| 2 | inferred-block-present | PASS | Inferred block rendered at top | — |
| 3 | inferred-includes-field (Maturity, Initial idea, "thinking about") | PASS | Bullet renders with citation | — |
| 4 | phase-b-skips (Maturity) | PASS | Maturity NOT in Phase B list | — |

### Notes
Direct match to L54 inference signal. PASS.

---

## TRACE: PRD-005
### Preconditions
user_input: "We're working on v2 of raffles — need a PRD for the new flow on the Sidekick engine"; jira_context: PR-310 closed Raffles v1; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Inferred "Existing feature" — citation: "v2 of" (plus PR-310 v1 epic in Jira)
- **Main user:** Not inferred
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Main user; Q2 Main problem; Q3 Success

### Phase C — Follow-ups
Q1 (header: Migration): "Migration scope?" options: Curacao only / MGA + Curacao / all markets  rationale: scope edges + migration
Q2 (header: Ownership): "Smartico event contract — break vs preserve?" options: preserve v1 events / additive only / break + version

### Phase D — Artifact
```markdown-artifact
# PRD: Raffles v2 — Sidekick Engine
> **Inferred (not asked):**
> - Maturity: Existing feature — from "v2 of raffles"
```

### Handoff
File: `~/Downloads/prds/raffles-v2-sidekick-engine.md`; sim Hold the chip.

## VERDICT: PRD-005
**Title:** Maturity inferred as 'Existing feature' from 'v2 of raffles'
**SKILL.md ref:** prd-writer:L55-L56
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Maturity=Existing feature, cite "v2 of") | PASS | L55 lists "v2 of" → Existing feature | — |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field (cite "v2 of raffles") | PASS | Bullet cites full phrase | — |
| 4 | phase-b-skips (Maturity) | PASS | — | — |

### Notes
Clean inference. PASS.

---

## TRACE: PRD-006
### Preconditions
user_input: "We want a dedicated weekly tournament for high rollers in the Curacao market"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred (no maturity signal)
- **Main user:** Inferred "End user / VIP player" — citation: "high rollers"  ⚠️ SKILL.md L55-L57 only defines "End user" / "Admin" / "Support/ops" — "VIP player" is not a defined Phase A value in the bank. The case asserts `expected_value: "VIP player"`, which exceeds the spec.
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem; Q3 Success

### Phase C — Follow-ups
Q1 (header: Scope): "Curacao only or also MGA?" Q2 (header: Cadence)

### Phase D — Artifact
PRD with Inferred block: "Main user: VIP player — from 'high rollers'" (sub-segment of End user — annotated inline)

### Handoff
File `~/Downloads/prds/weekly-tournament-for-high-rollers.md`; sim Hold the chip.

## VERDICT: PRD-006
**Title:** Main user inferred as 'VIP player' from 'high rollers'
**SKILL.md ref:** prd-writer:L53-L58
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main user=VIP player, cite "high rollers") | PARTIAL | L56 only defines End user / Admin / Support-ops bank; "VIP player" sub-segment is not formally in the option bank | spec gap |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field (VIP player, "high rollers") | PARTIAL | rendered as sub-segment of End user | spec inconsistency |
| 4 | phase-b-skips (Main user) | PASS | — | — |

### Notes
The case asserts an inference value ("VIP player") that the SKILL.md does not enumerate as a valid Main user value. The spec only lists End user / Admin / Support-ops in the Phase B bank (L68-L75). Phase A inference table (L55) says "user", "player" → End user. This is a real SKILL.md gap.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P1
Location: skills/prd-writer/SKILL.md:L55, L68-L70
Symptom: Main user bank only enumerates End user / Admin / Support-ops, so sub-segments like "VIP player", "high rollers", "FTD player" cannot be represented in the Phase A inferred-block or Phase B selection.
Proposed edit:
```
| **Main user** | "player", "user", "customer" → End user (specify sub-segment if signal exists: VIP, FTD, casual). "admin", "back office", "BO", "CMS" → Admin (CRM operator, BO admin). "CS", "support", "ops", "VIP team", "agent" → Support/ops. |
```
And in the bank:
```
- **Main user** — header: `Main user` — "Who is the main user affected?"
  - End user — Players / customers (specify sub-segment inline if known: VIP, FTD, casual)
  - Admin / internal — Internal users in the CMS or back office
  - Support / ops — CS, VIP, or operations teams
```

---

## TRACE: PRD-007
### Preconditions
user_input: "Need a PRD for a bulk-bonus issuance screen inside the PS Admin Panel"; jira_context: PR-621 PS Admin Panel — bulk ops refactor; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "Admin / internal" (case asserts "CRM operator") — citation: "PS Admin Panel"  ⚠️ same sub-segment gap as PRD-006: case expects "CRM operator" but the bank only has "Admin / internal".
- **Main problem:** Inferred "Internal workflow" — implicit from admin context (citation: "bulk-bonus issuance")
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Success

### Phase C — Follow-ups
Q1 (header: Scope): "Bonus types covered?" options: cash / free spins / both
Q2 (header: Permissions): "Who can run bulk issuance?" options: VIP team only / CS supervisors / all CRM operators
Q3 (header: Limit): "Max accounts per batch?" options: 100 / 1000 / 10000

### Phase D — Artifact
Inferred block: Main user: CRM operator (Admin / internal) — from "PS Admin Panel"

### Handoff
File `~/Downloads/prds/bulk-bonus-issuance-screen.md`.

## VERDICT: PRD-007
**Title:** Main user inferred as 'CRM operator' from 'PS Admin Panel'
**SKILL.md ref:** prd-writer:L53-L58
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main user=CRM operator, cite "PS Admin Panel") | PARTIAL | L55 maps "CMS"/"BO" → Admin, but does NOT explicitly name "CRM operator" or "PS Admin Panel" as triggers | spec gap |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field (CRM operator, "PS Admin Panel") | PARTIAL | sub-segment annotation only | spec |
| 4 | phase-b-skips (Main user) | PASS | — | — |

### Notes
Same gap as PRD-006: sub-segment values ("CRM operator") aren't first-class in the bank. Also, "PS Admin Panel" is not enumerated as an inference trigger in L55 — the closest match is "BO"/"CMS".

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P1
Location: skills/prd-writer/SKILL.md:L55
Symptom: Phase A inference table omits common company-specific admin terms ("PS Admin Panel", "CRM operator") so "PS Admin Panel" → Admin inference must rely on the generic "CMS" trigger.
Proposed edit:
```
| **Main user** | "player", "user", "customer" → End user. "admin", "back office", "BO", "CMS", "PS Admin Panel", "Admin Panel" → Admin (CRM operator / BO admin). "CS", "support", "ops", "VIP team", "agent" → Support/ops. |
```

---

## TRACE: PRD-008
### Preconditions
user_input: "We need to reduce churn after first deposit — propose a 7-day re-engagement journey"; jira_context: PR-712 FTD retention experiments; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "End user" (FTD player) — citation: "first deposit"
- **Main problem:** Inferred "Drop-off / Retention" — citation: "churn after first deposit"  ⚠️ case expects "Retention / re-engagement" but L57 bank says "Drop-off — Users not converting or churning". Mismatch.
- **Success signal:** Not inferred (case doesn't assert)

### Phase B — Questions asked
Q1 Maturity; Q2 Success

### Phase C — Follow-ups
Q1 (header: Channel): "Channel mix?" options: email + push / push only / in-app overlay only
Q2 (header: Ownership): "Smartico vs Sidekick?" options: Smartico journey / Sidekick rules engine / mix

### Phase D — Artifact
Inferred block: Main problem: Drop-off / churn — from "churn after first deposit"

### Handoff
File `~/Downloads/prds/reduce-churn-after-first-deposit.md`.

## VERDICT: PRD-008
**Title:** Main problem inferred as retention from 'churn after first deposit'
**SKILL.md ref:** prd-writer:L53-L58
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main problem="Retention / re-engagement", cite "churn after first deposit") | PARTIAL | L57 maps "churn" → "Drop-off" not "Retention / re-engagement" | spec value name diverges from case expectation |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field (Retention / re-engagement, "churn") | PARTIAL | bullet says "Drop-off" per spec | naming gap |
| 4 | phase-b-skips (Main problem) | PASS | — | — |

### Notes
Case expects a "Retention / re-engagement" Main problem value but SKILL.md bank only has Blocked/confused / Drop-off / Internal workflow. "churn" is explicitly mapped to "Drop-off" in L57.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P1
Location: skills/prd-writer/SKILL.md:L57, L73
Symptom: Main problem bank lacks an explicit Retention / re-engagement value; churn falls under Drop-off which doesn't distinguish pre-deposit drop-off from post-FTD retention.
Proposed edit:
```
| **Main problem** | ... "drop", "abandon", "not converting" → Drop-off. "churn", "retention", "re-engagement", "winback" → Retention / re-engagement. "manual", "slow", "tedious", "spreadsheets" → Internal workflow. |
```
Add to bank L73:
```
  - Retention / re-engagement — Users churning or going dormant
```

---

## TRACE: PRD-009
### Preconditions
user_input: "Goal: increase GGR by 5% in the live casino vertical via a new lobby ranking algorithm"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Not inferred
- **Main user:** Inferred "End user" — citation: "live casino" players
- **Main problem:** Not inferred
- **Success signal:** Inferred "Conversion" (case expects "GGR lift") — citation: "increase GGR" / "5%"  ⚠️ L58 maps "GGR" → Conversion, but case expects "GGR lift" as a distinct value. Spec mismatch.

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem

### Phase C — Follow-ups
Q1 (header: Scope): "Vertical scope?" options: live casino only / live + slots / all verticals
Q2 (header: Ownership): "Ranking owner?" options: Sidekick lobby service / dedicated ranking microservice / Smartico segments
Q3 (header: Rollout): "Rollout strategy?" options: AB test 10% / full launch behind flag / Curacao-first cohort

### Phase D — Artifact
Inferred block: Success: GGR lift / Conversion — from "increase GGR by 5%"

## VERDICT: PRD-009
**Title:** Success signal inferred as GGR-lift from 'increase GGR by 5%'
**SKILL.md ref:** prd-writer:L53-L58
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Success="GGR lift", cite "increase GGR") | PARTIAL | L58 maps GGR → Conversion bucket; "GGR lift" is not a first-class bank value | spec naming gap |
| 2 | inferred-block-present | PASS | — | — |
| 3 | inferred-includes-field (cite "5%") | PASS | bullet cites both "increase GGR" and "5%" | — |
| 4 | phase-b-skips (Success) | PASS | — | — |

### Notes
Same sub-naming pattern: case expects a more specific GGR-lift value. Spec subsumes it under Conversion.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P2
Location: skills/prd-writer/SKILL.md:L58, L77
Symptom: GGR/revenue lift is conflated with conversion/activation despite being a distinct success signal in casino product work.
Proposed edit:
```
| **Success signal** | "convert", "activate", "sign up", "deposit" → Conversion. "GGR", "+X%", "revenue", "monetization" → GGR / revenue lift. "fewer tickets", "support load" → Reduced friction. "DAU", "retention", "sessions", "engagement" → Engagement. |
```

---

## TRACE: PRD-010
### Preconditions
user_input: "we should do something about the casino"; mcp_state: none.

### Phase A — Inferences
All four fields: Not inferred (no signal).

### Phase B — Questions asked
Q1 Maturity; Q2 Main user; Q3 Main problem; Q4 Success — all 4 core questions.

### Phase C — Follow-ups
After core, with no context, no material unknowns reach the bar of 3 concrete options. Zero follow-ups. (Or possibly 1 scope question if PM answer specifies vertical.)

### Phase D — Artifact
No "Inferred (not asked)" block (none inferred).

### Handoff
File `~/Downloads/prds/casino-improvement.md` (vague title applied directly).

## VERDICT: PRD-010
**Title:** Ambiguous input — Phase A infers nothing, Phase B asks all 4
**SKILL.md ref:** prd-writer:L53-L64
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Maturity) | PASS | no maturity signal | — |
| 2 | phase-a-does-not-infer-field (Main user) | PASS | — | — |
| 3 | phase-a-does-not-infer-field (Main problem) | PASS | — | — |
| 4 | phase-a-does-not-infer-field (Success) | PASS | — | — |
| 5 | inferred-block-omitted-when-empty | PASS | spec L126 says "include this block only if Phase A inferred at least one core answer" | — |
| 6 | phase-b-asks (all 4) | PASS | all 4 fall through to Phase B | — |

### Notes
Clean ambiguous-input fallback. PASS.

---

## TRACE: PRD-011
### Preconditions
user_input: "A brand-new flow that's actually v2 of the existing raffles entry point"; jira_context: PR-310 closed Raffles v1; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Conflict — "brand-new" → Initial idea signal; "v2 of" + "existing" → Existing feature signal; PR-310 v1 epic in Jira reinforces Existing feature. SKILL.md does not define conflict resolution. Recommended: prefer the more specific signal (Existing feature) per case acceptable_outcomes. Runner chooses Existing feature, citing "v2 of" + PR-310.
  - **Resolution risk:** SKILL.md is silent on conflict resolution. Acceptable per case.

### Phase B — Questions asked
Q1 Main user; Q2 Main problem; Q3 Success

### Phase C — Follow-ups
Q1 (header: Migration), Q2 (header: Scope)

## VERDICT: PRD-011
**Title:** Conflicting signals (Maturity 'new' vs 'v2 of') — Phase A resolves or defers
**SKILL.md ref:** prd-writer:L53-L64
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-resolves-conflict (acceptable: Existing feature OR not inferred) | PARTIAL | Runner picks Existing feature, but SKILL.md provides NO documented conflict resolution priority. Resolution is "lucky" not "rule-driven". | spec gap |

### Notes
SKILL.md L53-L58 lists inference signals but never tells the runner what to do when two opposing signals fire (e.g. "brand-new" + "v2 of"). Output is correct by luck.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P1
Location: skills/prd-writer/SKILL.md:L51-L58
Symptom: Phase A has no documented conflict-resolution rule. When opposing signals fire, behavior is undefined.
Proposed edit:
```
### Phase A — Infer answers from input + context
Before asking anything, attempt to infer each of the 4 core answers from the user's input and the Jira/Confluence context scan. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question.

**Conflict resolution:** When two signals fire for the same field with different values, prefer the more specific signal (e.g. "v2 of X" beats "new"; "PS Admin Panel" beats "admin"; an existing Jira epic beats an "exploring" verb in user_input). If neither signal is more specific, defer to Phase B.
```

---

## TRACE: PRD-012
### Preconditions
user_input: "We're thinking about a new tournament for high rollers — early concept"; mcp_state: none.

### Phase A — Inferences
- **Maturity:** Inferred "Initial idea" — citation: "thinking about", "early concept"
- **Main user:** Inferred "End user / VIP player" — citation: "high rollers"
- **Main problem:** Not inferred
- **Success signal:** Not inferred

### Phase B — Questions asked
Q1 Main problem; Q2 Success — only the 2 not inferred.

### Phase C — Follow-ups
Q1 (header: Scope): "Cadence?" options: weekly / monthly / one-off

### Phase D — Artifact
Inferred block with 2 entries.

## VERDICT: PRD-012
**Title:** Phase B asks only the 2 questions Phase A didn't infer
**SKILL.md ref:** prd-writer:L62-L85
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-skips (Maturity, Main user) | PASS | both inferred → not asked | — |
| 2 | phase-b-asks (Main problem, Success) | PASS | both remain → asked in Phase B | — |

### Notes
Skill behavior matches spec L62-L63 exactly.

---

## TRACE: PRD-013
### Preconditions
user_input: "Need a PRD for a deposit-limits screen"; mcp_state: none.

### Phase A — Inferences
None inferred.

### Phase B — Questions asked
Q1 (header: Maturity): "How mature is this feature idea?"
  options: 1) Initial idea — Needs product thinking and structure 2) Clear direction — Needs full PRD and requirements 3) Existing feature — Needs improvement or iteration
  (sim: Clear direction)
Q2 Main user; Q3 Main problem; Q4 Success.

### Phase C — Follow-ups
Q1 Scope (limit types daily/weekly/monthly); Q2 Compliance.

## VERDICT: PRD-013
**Title:** Each Phase B question emits exactly 3 spec'd options (Maturity bank)
**SKILL.md ref:** prd-writer:L65-L75
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Maturity, 3 options, header Maturity) | PASS | matches L65-L68 | — |
| 2 | phase-b-options-match-spec (Maturity = Initial idea / Clear direction / Existing feature) | PASS | matches L66-L68 verbatim | — |

### Notes
Spec-exact. PASS.

---

## TRACE: PRD-014
### Preconditions
user_input: "PM wants a PRD — no context"; mcp_state: none.

### Phase A — Inferences
None.

### Phase B — Questions asked
Q1 header Maturity; Q2 header Main user; Q3 header Main problem; Q4 header Success — all 4 with 3 options each per spec L65-L85.

## VERDICT: PRD-014
**Title:** Phase B question headers match the spec exactly
**SKILL.md ref:** prd-writer:L65-L85
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Maturity, header Maturity, 3 opts) | PASS | L65 | — |
| 2 | phase-b-question-shape (Main user, header Main user, 3 opts) | PASS | L70 | — |
| 3 | phase-b-question-shape (Main problem, header Main problem, 3 opts) | PASS | L75 | — |
| 4 | phase-b-question-shape (Success, header Success, 3 opts) | PASS | L80 | — |

### Notes
All four headers and option counts match spec verbatim.

---

## TRACE: PRD-015
### Preconditions
user_input: "Need a PRD for the new responsible-gambling reminder modal"; mcp_state: none.

### Phase A — Inferences
- Main user: End user (player) — citation "responsible-gambling" (implicit player-facing)
- Main problem: Reduced friction / RG signal not in bank → defer
- Others: not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem; Q3 Success — emitted via AskUserQuestion tool (not free-form text).

## VERDICT: PRD-015
**Title:** Phase B uses AskUserQuestion only — no free-form prompts
**SKILL.md ref:** prd-writer:L62-L85
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-uses-ask-user-question | PASS | L45-L46: "All questions are asked via AskUserQuestion (the in-terminal interactive chooser, one question at a time)" | — |

### Notes
Spec explicitly mandates AskUserQuestion. PASS.

---

## TRACE: PRD-016
### Preconditions
user_input: "we should do something about the casino"; mcp_state: none.

### Phase A — Inferences
All four: not inferred.

### Phase B — Questions asked
All 4 via AskUserQuestion.

## VERDICT: PRD-016
**Title:** When Phase A infers zero fields, Phase B asks all 4 core questions
**SKILL.md ref:** prd-writer:L62-L85
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-asks (4 core) | PASS | all 4 unresolved → all 4 asked | — |
| 2 | phase-b-uses-ask-user-question | PASS | — | — |

### Notes
Matches L62-L63. PASS.

---

## TRACE: PRD-017
### Preconditions
user_input: many unknowns listed (data source, exclusions, cadence, ledger, BO notifications, currency rounding, jurisdictions); jira_context: PR-820 Smartico cashback engine + PR-845 PS Admin Panel — bonus exclusions UI; mcp_state: atlassian.

### Phase A — Inferences
- Main user: implicit End user (cashback rule)
- Others: not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main user (likely VIP); Q3 Main problem; Q4 Success — 4 questions.

### Phase C — Follow-ups
Strictly capped at 3 per L93:
Q1 (header: Ownership): "Cashback data source?" options: Smartico events (PR-820) / Sidekick wallet ledger / PS Admin Panel bonus ledger (PR-845)  rationale: system/data ownership
Q2 (header: Scope): "Exclusions UI scope?" options: PR-845 PS Admin Panel only / Sidekick admin / both
Q3 (header: Scope): "Cadence at MVP?" options: weekly / monthly / per-session

That's 3 max. Other unknowns (BO notifications, currency rounding, jurisdictions) become inline assumptions per L96 rule 6.

## VERDICT: PRD-017
**Title:** Phase C emits at most 3 follow-up questions
**SKILL.md ref:** prd-writer:L90-L101
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | L93 "Maximum 3 follow-ups" | — |

### Notes
Spec hard cap respected.

---

## TRACE: PRD-018
### Preconditions
user_input: "PRD for a new Smartico-driven welcome-bonus flow"; jira_context: PR-712 FTD retention experiments; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user (FTD player) — citation "welcome-bonus"
- Main problem: Drop-off — implicit from FTD flow
- Others: not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Success

### Phase C — Follow-ups
Q1 (header: Ownership): options: Smartico campaign / Sidekick promotion service / dedicated bonus microservice
Q2 (header: Scope): options: FTD only / FTD + 2nd-deposit / all deposits
None of the options use banned placeholders ("Use the existing system", "Option A", "TBD", "I'll specify later").

## VERDICT: PRD-018
**Title:** Phase C rejects banned generic placeholders
**SKILL.md ref:** prd-writer:L90-L101
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-no-banned-placeholders | PASS | L94 banned-list enforced; all 3-option labels reference concrete systems | — |

### Notes
Spec-clean.

---

## TRACE: PRD-019
### Preconditions
user_input: "PRD for v2 of the community chat MVP — same auth model as before"; jira_context: PR-280 + PR-266; confluence_context: page "Community Chat Auth Model" says "Community chat reuses Smartico session token. No new identity provider."; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v2 of"
- Main user: End user (VIP player implicit)
- Main problem: not inferred
- Success: not inferred

### Phase B — Questions asked
Q1 Main problem; Q2 Success

### Phase C — Follow-ups
Auth model — SKIPPED per L95 rule 3 (Confluence already answers it). Converted to inline assumption in PRD §8 Requirements: "Auth: reuses Smartico session token (no new IDP) — per Confluence 'Community Chat Auth Model'."
Q1 (header: Scope): "Phase-1 cut?" options: rooms + S0/S1/S2 / rooms + Big Win banner / full v3 epic PR-280 scope
Q2 (header: Ownership): "Moderation tooling?" options: PS Admin Panel native / Smartico campaign console / custom CMS module

## VERDICT: PRD-019
**Title:** Phase C skips a topic already answered by Jira/Confluence context
**SKILL.md ref:** prd-writer:L90-L101
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-when-context-answers (auth model, inline_assumption_expected) | PASS | L95 rule 3 + confluence page cited inline in §8 | — |

### Notes
Spec-clean.

---

## TRACE: PRD-020
### Preconditions
user_input: "PRD for the community chat header redesign — needs a new look and analytics tracking"; jira_context: PR-280 Community chat epic; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "redesign"
- Main user: End user
- Main problem: not inferred (UX-redesign neither blocked nor drop-off nor internal)
- Success: not inferred

### Phase B — Questions asked
Q1 Main problem; Q2 Success

### Phase C — Follow-ups
Q1 (header: Scope): "Header redesign scope?" options: mobile-only / desktop-only / mobile + desktop parallel
Q2 (header: Rollout): "Behind feature-flag?" options: gated 10% rollout / segment-gated VIP first / full launch

NOT asked: "What color should the chat header be?" (banned: styling). NOT asked: "What should the analytics event be called?" (banned: exact event property name). Both default-and-flag in PRD instead.

## VERDICT: PRD-020
**Title:** Phase C skips styling/copy/event-name questions
**SKILL.md ref:** prd-writer:L90-L111
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-styling-copy-questions | PASS | L96 rule 4 + L108-L110 worked-bad-examples explicitly | — |

### Notes
Spec L108-L110 lists these exact bad examples ("chat header color", "analytics event name"). PASS.

---

## TRACE: PRD-021
### Preconditions
user_input: "PRD for a cashback engine — many unknowns including rollout cohort, scope edges (which game verticals), monetization caps, cross-feature interactions with free spins"; jira_context: PR-820 + PR-845; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: defer
- Main user: End user
- Main problem: defer (cashback signals Engagement / Retention)
- Success: not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem; Q3 Success

### Phase C — Follow-ups (priority order: scope edges > ownership > rollout > cross-feature > monetization, per L97-L101)
Q1 (header: Scope): "Vertical scope?" options: slots only / live casino only / slots + live casino (FIRST — scope edges)
Q2 (header: Ownership): "Engine owner?" options: Smartico (PR-820) / Sidekick wallet / dedicated cashback microservice
Q3 (header: Rollout): "Rollout cohort?" options: AB 10% / VIP-tier-3+ pilot / full launch

NOT asked first: rollout cohort (deferred to Q3); not asked: free-spins interaction (cross-feature, lower priority — deferred to inline assumption).

## VERDICT: PRD-021
**Title:** Phase C priority order respected — scope edges over rollout
**SKILL.md ref:** prd-writer:L90-L101
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-priority-order-respected (top topic: scope edges) | PASS | L97-L101 lists scope edges as #1 | — |

### Notes
Spec explicit priority order followed.

---

## TRACE: PRD-022
### Preconditions
user_input: "PRD for a new in-game responsible-gaming nudge — exact animation timing depends on an unfinished design exploration"; jira_context: PR-901; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user
- Main problem: defer
- Others: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem; Q3 Success

### Phase C — Follow-ups
Animation timing — SKIPPED per L101 rule 6 ("If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the PRD, do not ask"). Falls back to inline assumption in §9 UX/UI: "Assumption: nudge animation timing TBD — Open: pending PR-901 design exploration (Phase 1 default = 400ms ease-out)."
Q1 (header: Scope): "Trigger threshold?" options: 30min session / 60min session / loss threshold
Q2 (header: Ownership): "Trigger owner?" options: Sidekick game-state hook / Smartico segment / dedicated RG service

## VERDICT: PRD-022
**Title:** Phase C falls back to assume+flag when 3 concrete options aren't writeable
**SKILL.md ref:** prd-writer:L90-L101
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-fallback-to-assume-and-flag (animation timing) | PASS | L101 rule 6 + inline assumption + Open flag in §9 | — |

### Notes
Spec-clean.

---

## TRACE: PRD-023
### Preconditions
user_input: vague "live-casino feature — no maturity/user/problem/success/scope info"; mcp_state: none.

### Phase A — Inferences
- Main user: End user (live casino)
- All others: not inferred

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem; Q3 Success = 3 questions

### Phase C — Follow-ups
Up to 3: scope vertical sub-cut / ownership / rollout = 3 questions

Total: 3 + 3 = 6 ≤ 7 cap (L48 says "Total questions asked across all phases must never exceed 7").

## VERDICT: PRD-023
**Title:** Total user-facing questions across Phase B + Phase C does not exceed 7
**SKILL.md ref:** prd-writer:L62-L101
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | total-questions-asked-max (7) | PASS | L48 + L93 enforce 4+3=7 cap | — |

### Notes
Spec-clean. NOTE: L48 says "Total questions asked across all phases must never exceed 7". Ambiguous about chained ticket-builder calls in Double down — see PRD-037.

---

## TRACE: PRD-024
### Preconditions
user_input: "PRD for the community chat MVP cut — what to ship in phase 1"; jira_context: PR-280, PR-266, PR-301; confluence_context: "Community Chat — North Star" (Goal: in-app social presence for VIP retention. Pragmatic Solutions hosts game launchers.); mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature → "MVP cut" of running feature (PR-266 closed)
- Main user: End user (VIP) — confluence "VIP retention"
- Main problem: Retention / Engagement — implicit
- Success: Engagement (VIP retention)

### Phase B — Questions asked
None (all 4 inferred).

### Phase C — Follow-ups (worked example from L103-L106)
Q1 (header: Scope): "MVP cut?" options: chat rooms + S0/S1/S2 gates only (defer cards/leaderboard) / chat + Big Win + Pinned (no leaderboard/tipping) / full v3.0 epic PR-266 scope
Q2 (header: Ownership): "Moderation tooling?" options: PS Admin Panel native / Smartico campaign console / custom CMS module under PR-280
Q3 (header: Scope): "Casino home only or sportsbook home too at launch?" options: casino only / casino + sportsbook parallel / casino now, sportsbook as follow-up epic

All 3 reference real project keys (PR-266, PR-280, PR-301), concrete systems (Smartico, PS Admin Panel, Pragmatic Solutions, Sidekick), no banned placeholders, no styling/copy/event-name questions.

### Phase D — Artifact
PRD with full Inferred block; §12 sub-epic + child rows reuses PR-266/PR-280/PR-301 terminology.

## VERDICT: PRD-024
**Title:** Good Phase C follow-ups for Community Chat MVP cut (worked example)
**SKILL.md ref:** prd-writer:L103-L111
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | 3 follow-ups | — |
| 2 | phase-c-options-are-concrete | PASS | every option cites a project key or named system | — |
| 3 | phase-c-no-banned-placeholders | PASS | no banned phrases | — |
| 4 | phase-c-skips-styling-copy-questions | PASS | no styling/copy/event questions | — |

### Notes
Exact replica of the L103-L106 worked example. PASS.

---

## TRACE: PRD-025
### Preconditions
user_input: "PRD for a new Sidekick-driven welcome-bonus flow targeted at Curacao FTD players"; jira_context: PR-712 FTD retention experiments; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user / FTD player — "FTD players"
- Main problem: Drop-off — "welcome-bonus" implies FTD activation
- Success: Conversion — "welcome-bonus" implies activation
- Maturity: not inferred

### Phase B — Questions asked
Q1 Maturity (sim: Clear direction)

### Phase C — Follow-ups
Q1 (header: Scope): Curacao only or Curacao+MGA; Q2 (header: Ownership): Smartico vs Sidekick; Q3 (header: Rollout): A/B vs full.

### Phase D — Artifact
PRD has all 12 numbered sections in order: §1 Overview / §2 Problem / §3 Target / §4 Goals / §5 Scope / §6 User Stories / §7 User Flow / §8 Requirements / §9 UX-UI / §10 Analytics / §11 Edge Cases / §12 Jira Breakdown.

## VERDICT: PRD-025
**Title:** PRD contains all 12 numbered sections in order
**SKILL.md ref:** prd-writer:L125-L175
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-has-12-sections | PASS | L131-L174 enumerate §1-§12 | — |

### Notes
Section-count adherence: PASS.

---

## TRACE: PRD-026
### Preconditions
user_input: "PRD for a new deposit-limit override flow for VIP players"; jira_context: PR-820 VIP override engine; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user / VIP
- Maturity, Main problem, Success: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Main problem; Q3 Success

### Phase D — §6 User Stories rendering
Each story has a `Case | Expected behavior | Notes` markdown table for Edge Cases (per L141). No Gherkin "Given/When/Then".

## VERDICT: PRD-026
**Title:** §6 User Stories embeds Edge Cases as a table — not Gherkin
**SKILL.md ref:** prd-writer:L140-L150
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | edge-cases-as-table-not-gherkin | PASS | L141 "ASCII workflow diagram (happy path) + an Edge Cases table (Case \| Expected behavior \| Notes). Do NOT use Gherkin." | — |

### Notes
Spec L141 explicit. PASS.

---

## TRACE: PRD-027
### Preconditions
user_input: "PRD for a new daily-mission progress popup in the live casino lobby"; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user
- Others: defer

### Phase D — §7 User Flow rendering
```
┌──────────────┐    ┌──────────────┐
│ Lobby load   │───▶│ Mission API  │
└──────────────┘    └──────┬───────┘
                           ▼
                  ┌──────────────┐
                  │ Render popup │
                  └──────────────┘
```
Inside a fenced code block, uses ┌─┐│└┘├┤┬┴ ▼ → ─▶ characters per L144.

## VERDICT: PRD-027
**Title:** §7 User Flow uses box-drawing characters and arrows in a fenced code block
**SKILL.md ref:** prd-writer:L150-L160
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | ascii-flow-uses-box-drawing | PASS | L144 "End-to-end ASCII flowchart in a fenced code block, box-drawing characters ┌─┐│└┘├┤┬┴ and arrows ▼ → ─▶" | — |

### Notes
Spec L144 explicit characters. PASS.

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
Q1 Main problem; Q2 Success

### Phase D — §8 Requirements
### Functional
- FR-1, FR-2, FR-3
### Non-Functional
- Performance
- Security
- Permissions
- Accessibility (WCAG 2.1 AA per MGA)
- Localization (en, mt)
- Compliance (MGA audit)

Subsection headings exactly match L146-L148.

## VERDICT: PRD-028
**Title:** §8 Requirements has Functional and Non-Functional subsections
**SKILL.md ref:** prd-writer:L155-L167
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-section-has-subsections (8. Requirements: Functional / Non-Functional / Performance / Security / Permissions / Accessibility / Localization / Compliance) | PASS | L147-L148 enumerate all required subsections | — |

### Notes
Spec verbatim. PASS.

---

## TRACE: PRD-029
### Preconditions
user_input: "PRD for a Smartico-driven free-spin abuse detector — needs success metrics defined"; jira_context: PR-820 Smartico cashback engine; mcp_state: atlassian.

### Phase A — Inferences
- Main user: Admin / CRM operator (abuse detection is internal)
- Main problem: Internal workflow
- Maturity, Success: defer

### Phase D — §10 Analytics
### Primary Metric
- Abuse-rate reduction (% of free spins flagged)
### Secondary Metrics
- False-positive rate, manual review queue size
### Tracking Events
- `free_spin_issued`, `free_spin_redeemed`, `abuse_flag_raised`

Subsection headings match L150-L152.

## VERDICT: PRD-029
**Title:** §10 Analytics has Primary, Secondary, and Tracking subsections
**SKILL.md ref:** prd-writer:L165-L175
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-section-has-subsections (10. Analytics: Primary / Secondary / Tracking) | PASS | L150-L152 enumerate Primary Metric / Secondary Metrics / Tracking Events | — |

### Notes
Spec L150-L152 enumerate exactly these three. PASS.

---

## TRACE: PRD-030
### Preconditions
user_input: "We're working on v2 of raffles for high rollers — need a PRD"; jira_context: PR-310 closed Raffles v1; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v2 of raffles" (also PR-310 v1 epic)
- Main user: VIP player (End user sub-segment) — "high rollers"
- Main problem, Success: defer

### Phase D — Artifact
> **Inferred (not asked):**
> - Maturity: Existing feature — from "v2 of raffles"
> - Main user: VIP player — from "high rollers"

Block at top, before §1 Overview, per L127-L130.

## VERDICT: PRD-030
**Title:** Inferred (not asked) block at top when Phase A inferred ≥1 field
**SKILL.md ref:** prd-writer:L53-L60
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | inferred-block-present | PASS | L126 + example at L128-L130 | — |
| 2 | inferred-includes-field (Maturity = Existing feature, "v2 of raffles") | PASS | example at L129 | — |
| 3 | inferred-includes-field (Main user = VIP player, "high rollers") | PARTIAL | "VIP player" still not a first-class bank value (same gap as PRD-006) | spec gap |

### Notes
Inferred block format is correct, but "VIP player" sub-segment naming inconsistency persists. Same defect as PRD-006/PRD-007.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P1 (duplicate of PRD-006 suggestion — extend Main user bank to include sub-segments).
Location: skills/prd-writer/SKILL.md:L55, L68-L70
See PRD-006 verdict for the proposed edit.

**Overall (revised):** PARTIAL

---

## TRACE: PRD-031
### Preconditions
user_input: "PRD for a Smartico-driven cashback engine — propose the Jira split"; jira_context: PR-280 promotions umbrella epic + PR-820 Smartico cashback engine; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user
- Others: defer

### Phase D — §12 Suggested Jira Breakdown
**Sub-epic:** PR-280-child — "Smartico Cashback Engine"

| # | Title | Type | Component | Notes |
|---|---|---|---|---|
| 1 | Smartico cashback event ingest | New feature | crm | PR-820 dependency |
| 2 | Sidekick wallet ledger entry | New feature | wallet | reuses existing API |
| 3 | PS Admin Panel cashback exclusions UI | Improvement | admin-panel | |
| 4 | Smartico cashback_paid event tracking | New feature | analytics | §10 Tracking |

Has named sub-epic + 4 child rows (≥ 1 required).

## VERDICT: PRD-031
**Title:** §12 Suggested Jira Breakdown includes a sub-epic title plus child ticket rows
**SKILL.md ref:** prd-writer:L170-L178
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-section-12-has-sub-epic-and-children (min 1 row) | PASS | L173 + PRD-037 prior_artifact example confirms format (sub-epic line + table with #/Title/Type/Component/Notes columns) | — |

### Notes
Format implicit in L173 + L195 ("§12 Suggested Jira Breakdown") + example in PRD-037 prior_artifacts. PASS.

NOTE: SKILL.md L173 only says `## 12. Suggested Jira Breakdown (Epic + child tickets)` — the table-column structure is not formally spec'd. Implicit only. Minor spec gap.

---

## TRACE: PRD-032
### Preconditions
user_input: "We're thinking about a cashback-on-loss feature for VIP tier 3+ — very early days, just exploring"; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: **Initial idea** — "thinking about", "early days", "exploring"
- Main user: VIP player
- Main problem, Success: defer

### Phase B — Questions asked
Q1 Main problem; Q2 Success

### Phase C — Follow-ups (max 3)
Q1 Scope (tier 3+ only vs tier 2+); Q2 Ownership (Smartico vs Sidekick).

### Phase D — Artifact (Initial idea maturity adaptation, per L117-L118)
Heavy emphasis on:
- §2 Problem Statement
- "User Pain" subsection inside §3 or §2
- §5 Scope contains "Assumptions" inline
- "Validation Plan" subsection inside §10
- "MVP Suggestion" inside §5

**NO "Open Questions" section** — unresolved decisions live inline within Scope, Requirements (per L118).

## VERDICT: PRD-032
**Title:** Initial idea — emphasizes Problem/Assumptions/Validation/MVP, no Open Questions section
**SKILL.md ref:** prd-writer:L116-L122
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-emphasis-matches-maturity (Initial idea: Problem Statement / User Pain / Assumptions / Validation Plan / MVP Suggestion; forbidden Open Questions) | PASS | L118 enumerates exact emphasis + "do NOT add a separate Open Questions section" | — |

### Notes
Spec L118 verbatim. PASS.

---

## TRACE: PRD-033
### Preconditions
user_input: "We've validated the cashback concept with VIPs — now write the PRD for build: scope, flows, requirements"; jira_context: PR-820 Smartico cashback engine; confluence_context: "Cashback validation memo" greenlit; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: **Clear direction** — "now write the PRD for build", "spec out"-ish + validated memo in Confluence
- Main user: VIP player
- Main problem: defer
- Success: defer

### Phase B — Questions asked
Q1 Main problem; Q2 Success

### Phase D — Artifact (Clear direction maturity adaptation, per L120)
Heavy emphasis on:
- §8 Full Requirements
- §7 User Flows
- §11 Edge Cases
- §10 Analytics
- §12 Jira Breakdown

**NO "Dependencies" section** — team handoffs folded into Requirements bullets (per L120).

## VERDICT: PRD-033
**Title:** Clear direction — emphasizes Requirements/Flows/Breakdown, no Dependencies section
**SKILL.md ref:** prd-writer:L116-L122
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-emphasis-matches-maturity (Clear direction: Requirements / User Flow / Suggested Jira Breakdown; forbidden Dependencies) | PASS | L120 enumerates emphasis + "do NOT add a separate Dependencies section" | — |

### Notes
Spec L120 verbatim. PASS.

---

## TRACE: PRD-034
### Preconditions
user_input: "v2 of raffles — migrating Curacao players first, keeping Smartico events compatible with v1"; jira_context: PR-310 Raffles v1 closed + PR-411 Raffles v2 discovery; confluence_context: "Raffles v1 — Smartico event contract"; mcp_state: atlassian.

### Phase A — Inferences
- Maturity: **Existing feature** — "v2 of"
- Main user: End user
- Main problem: defer
- Success: defer

### Phase D — Artifact (Existing feature maturity adaptation, per L121-L122)
Sections highlight:
- "Current Behavior" (under §2 Problem)
- "Proposed Change" (under §5 Scope)
- "Why Current Flow Isn't Enough"
- "Migration Impact" (under §5 or §9)
- "Existing Users" treatment
- "Analytics Comparison" v1→v2

**NO "Risks" section** — regression risk called out inline in Proposed Change (per L122).

## VERDICT: PRD-034
**Title:** Existing feature — emphasizes Current/Proposed/Migration, no Risks section
**SKILL.md ref:** prd-writer:L116-L122
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-emphasis-matches-maturity (Existing feature: Current Behavior / Proposed Change / Migration; forbidden Risks) | PASS | L121-L122 enumerates emphasis + "do NOT add a separate Risks section" | — |

### Notes
Spec L121-L122 verbatim. PASS.

NOTE: SKILL.md L122 "regression risk inline within Proposed Change" — this is a placement hint but the rule doesn't define the standard for "inline" granularity (sentence? bullet? sub-section?). Minor spec gap.

---

## TRACE: PRD-035
### Preconditions
user_input: "PRD for a Smartico-driven welcome-bonus flow"; jira_context: PR-712; mcp_state: atlassian.

### Phase A — Inferences
- Main user: End user (FTD)
- Main problem: Drop-off / Conversion
- Maturity, Success: defer

### Phase B — Questions asked
Q1 Maturity; Q2 Success

### Phase C — Follow-ups
Q1 Scope; Q2 Ownership

### Phase D — Artifact
Standard PRD.

### Handoff (per L181-L189)
AskUserQuestion call:
- question: "Ready To Gamble On It?"
- header: "Gamble?"
- options: 1) Bet on it — Publish to Confluence PKB space  2) Hold the chip — .md only  3) Double down — Confluence + Jira chain

Presented exactly once.

## VERDICT: PRD-035
**Title:** Ready To Gamble On It? handoff has header 'Gamble?' and 3 spec'd options
**SKILL.md ref:** prd-writer:L181-L204
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-handoff-presented-once | PASS | L182 "Ask the user using AskUserQuestion" (single call) | — |
| 2 | gamble-options-match-spec (Bet on it / Hold the chip / Double down) | PASS | L184-L186 exact labels | — |

### Notes
Spec L182-L186 verbatim. PASS.

---

## TRACE: PRD-036
### Preconditions
user_input: "PRD for a new VIP tier upgrade celebration screen — Bet on it"; jira_context: PR-415 VIP tier UX refresh; mcp_state: atlassian.

### Phase A — Inferences
- Main user: VIP player; Maturity, Main problem, Success: defer

### Phase B/C — typical 2-3 questions

### Handoff
User picks Bet on it. Tool lookup:
- Find tool matching `mcp__.*atlassian.*` or `mcp__.*confluence.*` with `createConfluencePage` or `create_page` in name → e.g. `mcp__atlassian__createConfluencePage`.
- Look up active fastglobal cloudId via accessible-resources tool.
- Call with:
  - cloudId = <looked-up>
  - spaceId = 772571142 (PKB)
  - parentId = 772571521 (PKB overview)
  - contentFormat = markdown
  - title = "PRD: VIP Tier Upgrade Celebration"
  - body = full PRD markdown
- File save: `~/Downloads/prds/vip-tier-upgrade-celebration-screen.md`
- Final: returns new Confluence URL + absolute md path.

## VERDICT: PRD-036
**Title:** Bet on it + atlassian MCP → Confluence create call with PKB params
**SKILL.md ref:** prd-writer:L181-L190
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | mcp-tool-lookup-pattern (regex mcp__.*(atlassian\|confluence).*, verbs createPage/createConfluencePage/create_page) | PASS | L184 "tool name matching mcp__*atlassian* or mcp__*confluence* with createConfluencePage or create_page in it" | — |
| 2 | confluence-call-uses-pkb-params (spaceId=772571142, parentId=772571521, contentFormat=markdown, title) | PASS | L186-L188 explicit | — |
| 3 | markdown-saved-with-absolute-path (folder=prds) | PASS | L182 "~/Downloads/prds/<prd-slug>.md" | — |

### Notes
Spec L181-L190 verbatim. PASS.

**HOWEVER**: parentId=772571521 is hardcoded. If the PKB overview is moved/deleted, every PRD publish fails. No documented fallback. Real defect:

### Suggested SKILL.md edit
Priority: P2
Location: skills/prd-writer/SKILL.md:L188-L190
Symptom: Hardcoded parentId; no fallback if page is moved/deleted.
Proposed edit:
```
      - `parentId` = `772571521` (the PKB overview homepage — required; PKB rejects top-level creates with 404). **If the create call returns "parent not found" or 404, retry with the cloud's PKB space root by fetching the space's homepage via the Atlassian MCP's space-get tool and using that as parentId. Report the new parentId in the final message so future runs can be updated.**
```

---

## TRACE: PRD-037
### Preconditions
user_input: "PRD for the Community Chat v2 — VIP-only, Smartico-presence aware. Double down at handoff."; jira_context: PR-266 + PR-280 + PR-301; confluence_context: "Community Chat — North Star"; mcp_state: atlassian; prior_artifacts: the full pre-built 6-row §12 PRD body (provided in case).

### Phase A — Inferences (from PRD body)
- Maturity: Existing feature — from "v2" in PRD title
- Main user: VIP player — from "VIP-only" in PRD body
- Main problem: Retention / re-engagement — from PRD Inferred block
- Success: GGR lift — from PRD Inferred block + §10 Primary "VIP session length lift +8%"

### Phase B / C
**Phase B and C are SKIPPED entirely** for this case because user has already supplied the prior_artifact PRD and is invoking the Double down handoff. Standard 0-question.

### Handoff
1. File save: `~/Downloads/prds/community-chat-v2-vip-presence.md`
2. AskUserQuestion "Ready To Gamble On It?" (header Gamble?). User picks **Double down**.
3. Branch: Double down + atlassian MCP connected:
   a. Confluence create-page call: cloudId, spaceId=772571142, parentId=772571521, contentFormat=markdown, title="PRD: Community Chat v2 — VIP Presence", body=full PRD. Returns URL `https://fastglobal.atlassian.net/wiki/spaces/PKB/pages/887766/Community-Chat-v2-VIP-Presence`.
   b. Create parent sub-epic via Atlassian/Jira MCP (`mcp__atlassian__createJiraIssue`): title "Community Chat v2 — VIP Presence" (from §12 sub-epic), description links to the new Confluence page. Returns `PR-484`.
   c. Iterate §12's 6 rows:
      **Child 1 — Row "Render VIP presence dot on lobby avatar | New feature | chat | FR-1, depends on PR-301"**
        ticket-builder PRD-driven mode invocation:
        - Phase A infers:
          - Type=New feature — from PRD §12 row Type column
          - Main user=VIP player — from PRD §3 Target Users / Inferred block
          - System=chat component — from PRD §12 row Component column
          - Goal=Render presence dot — from PRD §8 FR-1
        - "Inferred (not asked)" block in the ticket body cites:
          - Type: from PRD §12 row 1 Type
          - Main user: from PRD §3
          - Goal: from PRD §8 FR-1
        - Phase B: 0 questions. Phase C: 0 questions.
        - Handoff auto-Bet on it. Creates Jira issue under parent PR-484 via the Jira create-issue tool. Returns `PR-485`.
      **Child 2 — Row "Reuse Smartico session token for chat auth | Improvement | integrations | FR-2"**
        - Phase A: Type=Improvement (PRD §12 row), User=VIP, System=integrations, Goal=auth via Smartico token. Inferred cites PRD §8 FR-2.
        - 0 questions. Auto-Bet on it. Returns `PR-486`.
      **Child 3 — Row "Persist last-seen via Sidekick room-state API | New feature | chat | FR-3"**
        - Phase A: Type=New feature, User=VIP, System=chat/Sidekick, Goal=last-seen API. Inferred cites PRD §8 FR-3.
        - 0 questions. Auto-Bet on it. Returns `PR-487`.
      **Child 4 — Row "Add VIP block-list enforcement to chat overlay | Improvement | chat | Non-Functional Security"**
        - Phase A: Type=Improvement, User=VIP, System=chat, Goal=block-list enforcement. Inferred cites PRD §8 Non-Functional Security.
        - 0 questions. Auto-Bet on it. Returns `PR-488`.
      **Child 5 — Row "Wire Smartico vip_chat_presence_shown event | New feature | integrations | Analytics §10 Tracking"**
        - Phase A: Type=New feature, User=VIP, System=integrations/Smartico, Goal=event wiring. Inferred cites PRD §10 Tracking.
        - 0 questions. Auto-Bet on it. Returns `PR-489`.
      **Child 6 — Row "PS Admin Panel — VIP chat tier toggle | New feature | admin-panel | Permissions FR / tier ≥ 2"**
        - Phase A: Type=New feature, User=CRM operator (Admin/internal), System=admin-panel, Goal=tier toggle. Inferred cites PRD §8 Non-Functional Permissions.
        - 0 questions. Auto-Bet on it. Returns `PR-490`.
4. Tool calls: 1 Confluence createPage + 1 Jira createIssue (sub-epic PR-484) + 6 Jira createIssue (children PR-485..PR-490) = 8 MCP calls.
5. Final message:
   "Confluence page: https://fastglobal.atlassian.net/wiki/spaces/PKB/pages/887766/Community-Chat-v2-VIP-Presence
    Sub-epic: PR-484
    Child tickets: PR-485, PR-486, PR-487, PR-488, PR-489, PR-490
    Markdown saved at /Users/talshani/Downloads/prds/community-chat-v2-vip-presence.md"

Total user-facing questions: **1** (the Gamble handoff itself). All 6 child ticket-builders emit 0 questions.

## VERDICT: PRD-037
**Title:** Double down chain — creates Confluence page + Jira sub-epic + 6 child tickets, no questions, every child cites PRD
**SKILL.md ref:** prd-writer:L191-L204
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-options-match-spec (3 options) | PASS | L184-L186 | — |
| 2 | double-down-creates-confluence-epic-and-children (expected_child_count=6) | PASS | L193-L201 spec; 6 rows in §12 → 6 children | — |
| 3 | double-down-child-tickets-no-questions | PASS | L198 hard instruction "skip Phase B (no core questions) and Phase C (no adaptive follow-ups)" + "Do NOT call AskUserQuestion" | — |
| 4 | double-down-child-tickets-cite-prd | PASS | L198 "surface them in the ticket's `Inferred (not asked)` block citing the PRD section (e.g. `from PRD §10 FR-2`)" | — |
| 5 | confluence-call-uses-pkb-params | PASS | L196 same parameters as Bet on it | — |
| 6 | cross-skill contract gap | PARTIAL | The "PRD-driven mode" contract (L198) is documented ONLY in prd-writer's SKILL.md, not in ticket-builder's spec. If ticket-builder is updated independently, this contract can silently break. | spec gap |
| 7 | no upper bound on child count | PARTIAL | L204 says "A PRD with 14 child tickets produces 14 Jira tickets" with no upper cap. A pathological 50-row PRD chains 50 calls. | spec gap |
| 8 | total-questions-asked-max ambiguity | PARTIAL | L48 says total ≤ 7 "across all phases" — but is ambiguous about whether chained ticket-builder calls count. | spec gap |

### Notes
The core Double-down behavior is spec'd. But 3 real gaps:
1. **Cross-skill contract**: The PRD-driven mode contract lives only in prd-writer's SKILL.md (L198). ticket-builder doesn't formally acknowledge this mode. If ticket-builder is refactored to remove the assume-flag-inline rule, the chain breaks silently.
2. **No upper bound** on chain length — pathological 50-row §12 fans out unchecked.
3. **7-question cap ambiguity**: L48 doesn't clarify whether chained ticket-builder questions count toward the cap. (Theoretically 0 in PRD-driven mode, so moot for happy path — but the spec should still be explicit.)

### Suggested SKILL.md edit
Priority: P0 (the cross-skill contract gap is high impact)
Location: skills/prd-writer/SKILL.md:L191-L204; also mirror in ticket-builder SKILL.md
Symptom: Cross-skill contract lives only in prd-writer; ticket-builder's spec is unaware of "PRD-driven mode".
Proposed edits:
```
### Notes on the Double down chain
The PRD is the source of truth for the chained ticket-builder calls — every Phase A inference must cite the PRD section it came from, never invent context. The user is asked exactly **one** question during this branch (the Gamble handoff itself), regardless of how many child tickets §12 contains. **Maximum chain length: 25 child tickets. If §12 has more, the chain creates the first 25 and emits a single warning line at the end with the unbuilt rows so the PM can re-run.** A PRD with 14 child tickets produces 14 Jira tickets + 1 epic + 1 Confluence page from a single user click. If the PRD §12 row is too thin for Phase A to infer a ticket type (e.g. just "Misc — TBD"), ticket-builder defaults to type=Task with an inline `Open: ticket type not inferable from PRD §12 — confirm with owner` line in the ticket body, and proceeds.

**Cross-skill contract:** This "PRD-driven mode" must also be acknowledged in `ticket-builder/SKILL.md` (its Phase A section). If ticket-builder is updated to remove inline assume+flag handling, also update this section.
```

**Overall:** PARTIAL (core behavior PASS, 3 distinct spec gaps)

---

## TRACE: PRD-038
### Preconditions
user_input: "PRD for a new bonus exclusions UI in the PS Admin Panel. Double down at handoff."; mcp_state: none.

### Phase A — Inferences
- Main user: CRM operator (Admin) — "PS Admin Panel"; Others: defer.

### Phase B / C
Standard.

### Handoff
File save `~/Downloads/prds/bonus-exclusions-ui-ps-admin-panel.md`.
AskUserQuestion: Ready To Gamble. User picks Double down.
Branch: Double down + no Atlassian MCP → per L201, "Same fallback as Bet on it" → emit "Atlassian MCP not connected — saved markdown only at /Users/talshani/Downloads/prds/bonus-exclusions-ui-ps-admin-panel.md" and stop. No Jira chain executed.

## VERDICT: PRD-038
**Title:** Double down + no MCP → same fallback message as Bet on it
**SKILL.md ref:** prd-writer:L200
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | double-down-falls-back-when-no-mcp ("Atlassian MCP not connected") | PASS | L201 "Same fallback as Bet on it" | — |
| 2 | mcp-fallback-when-disconnected ("Atlassian MCP not connected") | PASS | L191 "Atlassian MCP NOT connected: Report `Atlassian MCP not connected — saved markdown only at <path>` and stop" | — |
| 3 | markdown-saved-with-absolute-path (folder=prds) | PASS | L182 + L194 always save before handoff | — |

### Notes
Spec L191 + L201 explicit. PASS.

---

## TRACE: PRD-039
### Preconditions
user_input: "PRD for the community chat v2 — VIP presence"; jira_context: PR-266 + PR-280 + PR-301 + PR-415; confluence_context: "Community Chat — North Star" (Pragmatic Solutions hosts game launchers; chat overlays via Sidekick engine); mcp_state: atlassian.

### Phase A — Inferences
- Maturity: Existing feature — "v2"
- Main user: VIP player
- Main problem: Retention (implicit)
- Success: defer

### Phase B / C — standard

### Phase D — Artifact
Throughout, the PRD reuses:
- Project keys: **PR-266**, **PR-280**, **PR-301**, **PR-415**
- System names: **Smartico**, **PS Admin Panel**, **Sidekick**, **Pragmatic Solutions**
- Each fact cites source (Confluence page name + spaceId, Jira ticket key).
- Assumptions marked with "Assumption:" prefix.
- Missing info called out with "Open:" flag.
- Output is pure markdown, copy-pasteable.

## VERDICT: PRD-039
**Title:** PRD uses company terminology from context (PR-266, PR-280, Smartico, PS Admin Panel)
**SKILL.md ref:** prd-writer:L90-L178
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | uses-company-terminology (PR-266, PR-280, Smartico, PS Admin Panel, Sidekick) | PASS | L114 + L177 explicit | — |
| 2 | facts-cite-source | PASS | L37 "Facts (with source link), Assumptions (clearly marked), Missing (called out)" + L178 | — |
| 3 | output-copy-pasteable | PASS | L179 "copy-pasteable into Confluence" | — |

### Notes
Spec L114, L177-L179 are clear. PASS.

---

## TRACE: PRD-040
### Preconditions
user_input: "PRD for a small operations cleanup epic. Double down at handoff."; jira_context: PR-905 Ops cleanup umbrella; mcp_state: atlassian; prior_artifacts: pre-built PRD with §12 containing two rows — Row 1 ("Archive stale PS Admin Panel reports | Improvement | admin-panel | clear") and Row 2 ("Misc — TBD | — | — | unclear scope, owner unknown").

### Phase A — Inferences (from PRD)
- Maturity: Existing feature (cleanup epic of existing reports)
- Main user: CRM operator
- Main problem: Internal workflow
- Success: Reduced friction (operations cleanup)

### Phase B / C — skipped (PRD already supplied)

### Handoff
User picks Double down.
Confluence page created. Sub-epic created → returns `PR-906`. Then iterate §12:
**Child 1 — Row "Archive stale PS Admin Panel reports | Improvement | admin-panel"**
  - Phase A: Type=Improvement, Main user=CRM operator (cited "PS Admin Panel"), System=admin-panel, Goal=archive stale reports.
  - 0 questions, auto-Bet on it. Returns `PR-907`.
**Child 2 — Row "Misc — TBD | — | — | unclear scope, owner unknown"**
  - Phase A: Type column is `—` (blank), Component is `—` (blank). Per L204: "If the PRD §12 row is too thin for Phase A to infer a ticket type (e.g. just 'Misc — TBD'), ticket-builder defaults to type=Task with an inline `Open: ticket type not inferable from PRD §12 — confirm with owner` line in the ticket body, and proceeds."
  - Defaults to type=Task.
  - Ticket body includes inline `Open: ticket type not inferable from PRD §12 — confirm with owner`.
  - 0 questions, auto-Bet on it. Returns `PR-908`.

Final message lists PR-906 (sub-epic), PR-907, PR-908.

## VERDICT: PRD-040
**Title:** Thin §12 row ('Misc — TBD') → chained ticket defaults to Task with Open flag
**SKILL.md ref:** prd-writer:L204
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-thin-row-defaults-to-task | PASS | L204 verbatim defaults to Task + inline Open flag | — |
| 2 | double-down-child-tickets-no-questions | PASS | L198 + L204 "proceeds" without user prompt | — |

### Notes
Spec L204 explicit and correct. PASS.

NOTE: L204 lives in prd-writer's SKILL.md, but the behavior is enacted by ticket-builder (cross-skill contract gap — same as PRD-037 finding). ticket-builder's own spec should mirror this rule.

---

## END OF RUN
