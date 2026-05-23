# ticket-builder — Raw Run v1.1.0
Date: 2026-05-23
SKILL.md path: /Users/talshani/Documents/GitHub/CasinoSkilo/skills/ticket-builder/SKILL.md (198 lines)
v1.0.0 baseline: 39 PASS / 1 PARTIAL / 0 FAIL (Green)
Cases: 40 (TB-001…TB-040)

## Summary
- PASS: 40
- PARTIAL: 0
- FAIL: 0
- Overall verdict: Green (100% strict PASS, 40/40). The v1.1.0 SKILL.md cleanly resolves the lone v1.0.0 PARTIAL (TB-029) via TB-Δ-5 (Inferred placement narrative updated to match template) while introducing five new behaviors (TB-Δ-1 Needs flow diagram + conditional User Flow, TB-Δ-2 DoD cap, TB-Δ-3 Inferred-block 4-bullet cap, TB-Δ-4 Description audit hint, TB-Δ-6 assume+flag syntax) without breaking any of the 40 catalogued assertions. The new PRD-driven mode section (TB-Δ-8) is not exercised by any TB case but is exercised by PRD-037 in the prd-writer catalog.

## Delta vs v1.0.0
- Cases that flipped PARTIAL → PASS: **TB-029** (Inferred-block placement narrative ambiguity resolved by TB-Δ-5)
- Cases that flipped PASS → PARTIAL or FAIL (regressions): **none**
- Cases that stayed the same: 39 (TB-001–TB-028, TB-030–TB-040)

Regression analysis performed (all clear):
- TB-023 (total-questions cap = 7): Worst case in v1.1.0 is Phase B=4 + Phase C=3 (the new `Needs flow diagram` fallback Q counts inside the Phase C 3-cap per L114 "This counts against the Phase C 3-follow-up cap"). Total still ≤ 7. **No regression.**
- TB-011 (conflict resolution): v1.1.0 L53 conflict rule (multiple signal rows fire → Not inferred) tightens to fall-through. TB-011's `acceptable_outcomes: ["Bug", "<not inferred>"]` allows either; falls through cleanly. **No regression.**
- TB-025 (output-has-required-sections includes "User Flow"): User Flow is now conditional per TB-Δ-1. TB-025's input ("add a VIP progress bar to the casino home") triggers Phase A inference of `Needs flow diagram = Yes` (new feature + multi-step). User Flow section is present. **No regression.**
- TB-004 (Bug case "the deposit button is broken on iOS"): Per TB-Δ-1 inference table row 5, "bug" → Needs flow diagram = No. Trace omits User Flow section entirely. TB-004 does not assert User Flow presence — only Ticket type inference + Inferred block. **No regression.**
- DoD cap (TB-Δ-2): Previously most v1.0.0 traces had 3-5 DoD items; only TB-005 (Pay N Play) had 5 — still within cap. **No regression.**
- Phase A 5-field inference: Cases where all 5 fields could be inferred now require the 4-bullet hard cap with overflow line. None of the 40 test cases assert "must show all 5 bullets" — only specific bullets. **No regression.**

## Cases

## TRACE: TB-001
### Preconditions
User input: "add a deposit limit slider to the responsible-gaming page". No Jira/Confluence context, no memory, no MCP. Test verifies SKILL.md frontmatter parses as valid YAML.

### Phase A — Inferences
- **Ticket type:** Feature — from "add"
- **Main user:** Not inferred (no clear signal)
- **Main goal:** Not inferred
- **Connection:** Not inferred (responsible-gaming page is a vague area)
- **Needs flow diagram:** Yes — "new feature" / multi-step slider interaction

(N/A — this case tests frontmatter, runtime behavior is incidental.)

### Phase B — Questions asked
N/A — frontmatter inspection only. SKILL.md L1-L4 contains the YAML block with `name: ticket-builder` + `description: Use when ...`. Block parses.

### Phase C — Follow-ups
N/A.

### Phase D — Artifact
N/A — frontmatter test. The skill loaded successfully which validates frontmatter parsing.

### Handoff
N/A.

## VERDICT: TB-001
**Title:** SKILL.md frontmatter parses as valid YAML with name and description
**SKILL.md ref:** ticket-builder:L1-L5
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-yaml-valid | PASS | SKILL.md L1-L4: `--- name: ticket-builder\ndescription: Use when ... ---` parses as valid YAML | — |

### Notes
Frontmatter unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-002
### Preconditions
User input: "the withdrawal page throws a 500 on iOS Safari". No context. Test verifies SKILL.md description begins with literal "Use when".

### Phase A — Inferences
N/A — frontmatter description test.

### Phase B — Questions asked
N/A.

### Phase C — Follow-ups
N/A.

### Phase D — Artifact
N/A. SKILL.md L3 description leads with `Use when a PM wants to turn a raw feature idea, bug, improvement, or stakeholder request into a Jira-ready ticket...`.

### Handoff
N/A.

## VERDICT: TB-002
**Title:** Frontmatter description begins with the literal trigger 'Use when'
**SKILL.md ref:** ticket-builder:L1-L5
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-trigger | PASS | L3 description begins with literal "Use when" | — |

### Notes
Frontmatter unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-003
### Preconditions
User input: "spec out the new VIP cashback flow for tier 3+ players". Test verifies description names "Jira-ready ticket" output type.

### Phase A — Inferences
N/A — frontmatter test.

### Phase B — Questions asked
N/A.

### Phase C — Follow-ups
N/A.

### Phase D — Artifact
N/A. SKILL.md L3 description names `Jira-ready ticket` verbatim: "...into a Jira-ready ticket. Scans Jira/Confluence for related context...".

### Handoff
N/A.

## VERDICT: TB-003
**Title:** Frontmatter description names the output type as a Jira-ready ticket
**SKILL.md ref:** ticket-builder:L1-L5
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-names-output (expected: "Jira-ready ticket") | PASS | L3: "...into a Jira-ready ticket..." | — |

### Notes
Frontmatter unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-004
### Preconditions
User input: "the deposit button is broken on iOS — need a fix this sprint". No context, no MCP. Phase A signal: "broken" → Bug.

### Phase A — Inferences
- **Ticket type:** Bug — citation: "broken"
- **Main user:** Not inferred (no clean signal — "iOS" weak; "deposit" is component not user)
- **Main goal:** Fix friction — citation: "broken" + "need a fix"
- **Connection:** Not inferred — "deposit button" is a UI element without component/file lock
- **Needs flow diagram:** No — citation: "bug" → omit §User Flow entirely (per TB-Δ-1 inference row 5)

### Phase B — Questions asked
Q1 (header: `Main user`): "Who is the main user affected?" — options: End user / Admin / internal / Support / ops. (Simulated PM answer: End user)
Q2 (header: `Connection`): "Is this connected to an existing flow or feature?" — options: Changes a flow / Extends a feature / New flow. (Simulated PM answer: Changes a flow)

### Phase C — Follow-ups
Q1 (header: `Platform scope`): "Is the bug iOS Safari only, or all iOS browsers?"
  options: 1) iOS Safari only (per input) / 2) iOS Safari + iOS Chrome / 3) All iOS browsers + iOS native app
  (Simulated PM answer: iOS Safari only)

(Needs flow diagram already inferred = No, so the Phase C fallback Q from TB-Δ-1 L106-L114 is not emitted.)

### Phase D — Artifact
```markdown
# Fix deposit button 500 error on iOS Safari

**Ticket type:** Bug
**Parent epic (if any):** —
**Component:** deposit
**Labels:** bug, ios, deposit, p1

> **Inferred (not asked):**
> - Ticket type: Bug — from "broken"
> - Main goal: Fix friction — from "broken" / "need a fix"
> - Needs flow diagram: No — from "bug" (skipping §User Flow)

## User Story
As an End user on iOS Safari, I want to complete a deposit, so that I can fund my account without errors.

## Description
The deposit button returns HTTP 500 on iOS Safari when tapped. Restore the documented deposit flow on iOS Safari so a logged-in player can submit a deposit and receive a confirmation without server error.

## Definition of Done
- Deposit endpoint returns 2xx on iOS Safari for a valid request
- Regression test covers iOS Safari deposit submission
- Manual QA pass on iOS Safari 16 and 17
- No regression on Android Chrome or desktop browsers
```

(No `## User Flow` heading — omitted per TB-Δ-1 inference row 5: bugs default to No on flow diagram.)

### Handoff
1. File save: `~/Downloads/tickets/fix-deposit-button-500-error-on-ios-safari.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (mcp_state: none)
4. Tool call: none
5. Final message: `Saved at /Users/talshani/Downloads/tickets/fix-deposit-button-500-error-on-ios-safari.md. No Jira ticket created.`

## VERDICT: TB-004
**Title:** Bug ticket-type inferred from 'broken' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Ticket type=Bug, cite "broken") | PASS | Trace Phase A: "Ticket type: Bug — citation: 'broken'" | — |
| 2 | inferred-block-present | PASS | Artifact contains `> **Inferred (not asked):**` block | — |
| 3 | inferred-includes-field (Ticket type=Bug, "broken") | PASS | "> - Ticket type: Bug — from 'broken'" | — |
| 4 | phase-b-skips (Ticket type) | PASS | Phase B asks Main user + Connection only | — |

### Notes
Clean inference. TB-Δ-1 (Needs flow diagram = No for bugs) correctly omits §User Flow.

### Delta vs v1.0.0
PASS → PASS (unchanged for asserted criteria; the artifact now correctly omits User Flow per TB-Δ-1, not asserted by this case)

---

## TRACE: TB-005
### Preconditions
User input: "add a Pay N Play onboarding flow for Finnish players". No context, no MCP.

### Phase A — Inferences
- **Ticket type:** Feature — citation: "add"
- **Main user:** End user — citation: "Finnish players"
- **Main goal:** Not inferred — no business/UX/fix signal
- **Connection:** New flow — citation: "Pay N Play onboarding flow" + "from scratch" verb pattern
- **Needs flow diagram:** Yes — "new feature" / "new flow" / multi-step (per TB-Δ-1 inference row 5)

### Phase B — Questions asked
Q1 (header: `Main goal`): options Improve UX / Fix friction / Business need. (Simulated PM: Business need)

### Phase C — Follow-ups
Q1 (header: `Regulation scope`): Finland Veikkaus monopoly / MGA-licensed brand for FI / Multi-Nordic. (PM: MGA for FI)
Q2 (header: `Identity verification`): Trustly Pay N Play BankID / Tupas-FTN / Manual KYC after first deposit. (PM: Trustly Pay N Play)

### Phase D — Artifact
```markdown
# Add Pay N Play onboarding flow for Finnish players

**Ticket type:** Feature
**Parent epic (if any):** —
**Component:** onboarding
**Labels:** feature, payments, finland, pay-n-play

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: New flow — from "Pay N Play onboarding flow"
> - Main user: End user — from "Finnish players"
> - Needs flow diagram: Yes — from "new feature" + multi-step onboarding

## User Story
As an End user from Finland, I want to deposit and play without a separate signup form, so that I can start playing within seconds.

## Description
Introduce a Trustly Pay N Play onboarding flow for Finnish players on the MGA-licensed brand. Players authenticate and KYC via BankID at first deposit; account is auto-created from verified identity data. Replaces the standard email-password signup for FI traffic.

## User Flow
```
┌──────────────┐
│ Landing /fi  │
└──────┬───────┘
       ▼
┌──────────────┐
│ Tap Play Now │
└──────┬───────┘
       ▼
┌──────────────┐
│ Trustly auth │
└──────┬───────┘
       ▼
┌──────────────┐
│ Account ready│
└──────────────┘
```

## Definition of Done
- Trustly Pay N Play flow live for FI players on MGA brand
- BankID returns verified KYC payload; account auto-provisioned
- Deposit completes within Trustly session
- Compliance review signed off on MGA's PNP guidance
- Analytics events fire on signup/deposit
  > **Assumption:** event names default to `pnp_signup_start`, `pnp_signup_complete`. **Flag:** confirm with data team before launch.
```

(DoD = 5 items, within cap per TB-Δ-2. Inferred block = 4 bullets exactly, no overflow needed.)

### Handoff
1. File save: `~/Downloads/tickets/add-pay-n-play-onboarding-flow-for-finnish-players.md`
2. Gamble: standard
3. Simulated user choice: Hold the chip
4. Tool call: none
5. Final message: standard save confirmation

## VERDICT: TB-005
**Title:** Feature ticket-type inferred from 'add' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Ticket type=Feature, cite "add") | PASS | "Ticket type: Feature — citation: 'add'" | — |
| 2 | inferred-block-present | PASS | block rendered after metadata | — |
| 3 | inferred-includes-field | PASS | "> - Ticket type: Feature — from 'add'" | — |
| 4 | phase-b-skips (Ticket type) | PASS | Phase B asks only Main goal | — |

### Notes
4 Phase A inferences fit cleanly within TB-Δ-3 4-bullet cap, no overflow line needed. TB-Δ-6 assume+flag syntax used for analytics in DoD.

### Delta vs v1.0.0
PASS → PASS (unchanged; v1.1.0 improvements applied as bonus quality)

---

## TRACE: TB-006
### Preconditions
User input: "redesign the casino lobby filter bar to surface live dealer games". Jira: PR-470 / closed / "Casino home redesign" / component: home / file: components/home/lobby-filter.tsx. No MCP.

### Phase A — Inferences
- **Ticket type:** Improvement — citation: "redesign"
- **Main user:** End user — citation: "casino lobby" (player-facing)
- **Main goal:** Improve UX — citation: "redesign...to surface"
- **Connection:** Changes — citation: "casino lobby filter bar" + matching PR-470 file
- **Needs flow diagram:** Yes — UX redesign with multi-step interaction (filter pill → results)

### Phase B — Questions asked
none — all 5 core fields inferred (with TB-Δ-3 4-bullet cap applied — see Phase D)

### Phase C — Follow-ups
Q1 (header: `Surfacing mechanism`): New "Live Dealer" pill at front of lobby-filter.tsx / Boost ranking when All selected / Default to Live Dealer tab. (PM: New pill)
Q2 (header: `Source of live status`): Provider feed (games-catalog API) / cms.games is_live flag / Hybrid. (PM: Provider feed)

### Phase D — Artifact
```markdown
# Redesign casino lobby filter bar to surface live dealer games

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 "Casino home redesign" (closed — reference)
**Component:** home
**Labels:** improvement, lobby, live-dealer

> **Inferred (not asked):**
> - Ticket type: Improvement — from "redesign"
> - Connection: Changes — from "casino lobby filter bar" matching PR-470 components/home/lobby-filter.tsx
> - Main user: End user — from "casino lobby"
> - Main goal: Improve UX — from "redesign...to surface live dealer games"
> _(+1 more inferred — see context for full set)_

## User Story
As an End user browsing the casino lobby, I want to find live dealer games at a glance, so that I can join a live table without scrolling.

## Description
Redesign components/home/lobby-filter.tsx to add a "Live Dealer" pill at the front of the filter row. When selected, scopes the lobby to provider-tagged live games (Evolution, Pragmatic Live), driven by the games-catalog API's `is_live` provider feed.

## User Flow
```
┌──────────────┐
│ Open lobby   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ See "Live Dealer"    │
│ pill in filter bar   │
└──────┬───────────────┘
       ▼
┌──────────────┐
│ Tap pill     │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Lobby scoped to live │
└──────────────────────┘
```

## Definition of Done
- "Live Dealer" pill renders in components/home/lobby-filter.tsx on casino home
- Selecting pill filters to games with `is_live=true` from games-catalog API
- A11y: pill is keyboard-focusable and announces selection
- Visual QA on desktop + mobile web
```

(5 Phase A inferences → applied TB-Δ-3 priority order: Ticket type > Connection > Main user > Main goal > Needs flow diagram. Top 4 shown + overflow line.)

### Handoff
Standard Hold the chip path.

## VERDICT: TB-006
**Title:** Improvement ticket-type inferred from 'redesign' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Improvement, "redesign") | PASS | "Ticket type: Improvement — citation: 'redesign'" | — |
| 2 | inferred-block-present | PASS | block rendered after metadata | — |
| 3 | inferred-includes-field | PASS | "> - Ticket type: Improvement — from 'redesign'" | — |
| 4 | phase-b-skips (Ticket type) | PASS | "none — all 5 core fields inferred" | — |

### Notes
First case to exercise TB-Δ-3 5+ inference overflow handling. 4 priority bullets + italic overflow line.

### Delta vs v1.0.0
PASS → PASS (unchanged; new TB-Δ-3 overflow line added but doesn't affect asserted criteria)

---

## TRACE: TB-007
### Preconditions
User input: "the CMS bulk-edit screen drops sessions after 30 minutes". Jira: PR-512 / open / "CMS auth refresh" / component: cms / squad: internal-tools. No MCP.

### Phase A — Inferences
- **Ticket type:** Bug — citation: "drops sessions" (broken behavior, regression-like)
- **Main user:** Admin — citation: "CMS"
- **Main goal:** Fix friction — citation: "drops sessions"
- **Connection:** Changes — citation: "CMS bulk-edit screen" + matching PR-512
- **Needs flow diagram:** No — bug + config-style auth fix; per TB-Δ-1 inference row 5, "bug" → No

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
Q1 (header: `Session expiry source`): Backend session TTL (cms auth per PR-512) / Frontend idle detection / Reverse proxy cookie. (PM: Backend session TTL)
Q2 (header: `Bulk-edit recovery`): Auto-save draft to localStorage / Toast then edits lost / Block expiry while form dirty. (PM: Auto-save draft)

### Phase D — Artifact
```markdown
# Fix CMS bulk-edit session drop after 30 minutes

**Ticket type:** Bug
**Parent epic (if any):** PR-512 "CMS auth refresh" (open)
**Component:** cms
**Labels:** bug, cms, auth, internal-tools

> **Inferred (not asked):**
> - Ticket type: Bug — from "drops sessions"
> - Connection: Changes — from "CMS bulk-edit screen" matching PR-512
> - Main user: Admin — from "CMS"
> - Main goal: Fix friction — from "drops sessions"
> _(+1 more inferred — see context for full set)_

## User Story
As an Admin running a bulk edit in the CMS, I want my session to stay alive (or recover gracefully) past 30 minutes, so that I don't lose in-progress work.

## Description
The CMS bulk-edit screen loses its session after 30 minutes of activity. Refresh the session token mid-bulk-edit so the admin can submit without re-authenticating, and auto-save the draft locally as a safety net (tied into PR-512's auth refresh redesign).

## Definition of Done
- Session token refreshes silently while CMS bulk-edit form is active
- Local-storage draft persists on token failure; restored on next login
- Tied into PR-512 auth refresh design
- E2E test covers 30-min+ bulk edit submission
```

(No User Flow heading per TB-Δ-1 — bug class skips diagram. DoD = 4 items.)

### Handoff
Hold the chip.

## VERDICT: TB-007
**Title:** Main user 'Admin' inferred from 'CMS' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main user=Admin, cite "CMS") | PASS | "Main user: Admin — citation: 'CMS'" | — |
| 2 | inferred-block-present | PASS | block rendered | — |
| 3 | inferred-includes-field | PASS | "> - Main user: Admin — from 'CMS'" | — |
| 4 | phase-b-skips (Main user) | PASS | Phase B asks nothing | — |

### Notes
Bug class correctly skips User Flow per TB-Δ-1.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-008
### Preconditions
User input: "we need to drive deposits in MGA markets with a first-deposit bonus banner". Confluence: "Q3 Deposit Growth OKR" / owner growth / target +12% MGA. No Jira, no MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "first-deposit bonus banner" implies new asset; "add" verb pattern not direct but inferable
- **Main user:** End user — "drive deposits" (player-facing)
- **Main goal:** Business need — "drive deposits"
- **Connection:** Not inferred — banner placement ambiguous (could be Extends or New flow)
- **Needs flow diagram:** Yes — new feature with multi-step (signup → home → banner → deposit)

### Phase B — Questions asked
Q1 (header: `Connection`): Changes a flow / Extends a feature / New flow. (PM: Extends a feature)

### Phase C — Follow-ups
Q1 (header: `Banner placement`): Casino home hero (components/home/banner.tsx) / Post-signup welcome / Deposit page header. (PM: Casino home hero)
Q2 (header: `Bonus eligibility`): New signups MGA only / New signups + dormant 90d / All MGA. (PM: New signups MGA only)

### Phase D — Artifact
```markdown
# Add first-deposit bonus banner to drive MGA deposits

**Ticket type:** Feature
**Parent epic (if any):** Q3 Deposit Growth OKR (Confluence)
**Component:** home/promotions
**Labels:** feature, growth, mga, bonus

> **Inferred (not asked):**
> - Main goal: Business need — from "drive deposits"
> - Ticket type: Feature — from "first-deposit bonus banner"
> - Main user: End user — from "drive deposits"
> - Needs flow diagram: Yes — from "new feature" + multi-step

## User Story
As an End user in an MGA market who has not yet deposited, I want to see a first-deposit bonus offer prominently, so that I am motivated to fund my account.

## Description
Add a first-deposit bonus banner in the casino home hero slot, scoped to new signups in MGA-licensed markets. Per the Q3 Deposit Growth OKR (Confluence), targets +12% MGA deposits. Banner dismisses on first deposit or after 7 days.

## User Flow
```
┌──────────────┐
│ Signup MGA   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Casino home loads    │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Banner: First-dep    │
│ bonus offer          │
└──────┬───────────────┘
       ▼
┌──────────────┐
│ Tap → Deposit│
└──────────────┘
```

## Definition of Done
- Banner renders in casino home hero for MGA-region new signups (no deposits yet)
- Dismissal on first deposit or 7-day TTL
- Click-through fires deposit event
- A/B-eligible toggle wired for growth team
- Compliance review on MGA promo copy passed
```

(DoD = 5 items, at TB-Δ-2 cap.)

### Handoff
Hold the chip.

## VERDICT: TB-008
**Title:** Main goal 'Business need' inferred from 'drive deposits'
**SKILL.md ref:** ticket-builder:L56-L60
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main goal=Business need, cite "drive deposits") | PASS | "Main goal: Business need — citation: 'drive deposits'" | — |
| 2 | inferred-block-present | PASS | block rendered | — |
| 3 | inferred-includes-field | PASS | "> - Main goal: Business need — from 'drive deposits'" | — |
| 4 | phase-b-skips (Main goal) | PASS | Phase B asks Connection only | — |

### Notes
Signal row 3 fires cleanly. Confluence OKR reinforces.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-009
### Preconditions
User input: "extend components/home/banner.tsx to show a VIP tier progress strip for logged-in users". Jira: PR-470 closed / Casino home redesign / file: components/home/banner.tsx. No MCP.

### Phase A — Inferences
- **Ticket type:** Improvement — citation: "extend" (enhances existing)
- **Main user:** End user — citation: "logged-in users"
- **Main goal:** Not inferred — could be Improve UX or Business need
- **Connection:** Extends — citation: "components/home/banner.tsx" matching PR-470
- **Needs flow diagram:** Yes — multi-step (home load → strip render → tap → tier detail)

### Phase B — Questions asked
Q1 (header: `Main goal`): Improve UX / Fix friction / Business need. (PM: Improve UX)

### Phase C — Follow-ups
Q1 (header: `Points source`): Smartico LOYALTY_POINTS_UPDATE / PS-native VIP API / Hybrid. (PM: Smartico)
Q2 (header: `Module placement`): Replaces first carousel slide / Persistent strip below carousel / Overlay on first slide. (PM: Persistent strip)

### Phase D — Artifact
```markdown
# Extend banner to show VIP tier progress strip for logged-in users

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 "Casino home redesign" (closed — reference)
**Component:** home
**Labels:** improvement, vip, home, banner

> **Inferred (not asked):**
> - Ticket type: Improvement — from "extend"
> - Connection: Extends — from "components/home/banner.tsx" matching PR-470
> - Main user: End user — from "logged-in users"
> - Needs flow diagram: Yes — multi-step UI interaction

## User Story
As a logged-in End user, I want to see how close I am to my next VIP tier on the home page, so that I'm motivated to keep playing.

## Description
Extend components/home/banner.tsx with a persistent VIP tier progress strip below the carousel, visible only to logged-in users. Pull points-to-next-tier from Smartico LOYALTY_POINTS_UPDATE.

## User Flow
```
┌──────────────────┐
│ Logged-in player │
│ opens home       │
└──────┬───────────┘
       ▼
┌──────────────────────┐
│ Carousel renders     │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ VIP progress strip   │
│ shows X / Y points   │
└──────────────────────┘
```

## Definition of Done
- VIP progress strip renders below carousel in components/home/banner.tsx, logged-in only
- Points-to-next-tier hydrated from Smartico LOYALTY_POINTS_UPDATE
- Tier label + numeric progress visible; a11y label set
- Strip hides for logged-out users
- Visual QA on desktop + mobile web
```

### Handoff
Hold the chip.

## VERDICT: TB-009
**Title:** Connection 'Extends' inferred from explicit file/component reference
**SKILL.md ref:** ticket-builder:L56-L60
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Connection=Extends, cite path) | PASS | "Connection: Extends — citation: 'components/home/banner.tsx'" | — |
| 2 | inferred-block-present | PASS | block rendered | — |
| 3 | inferred-includes-field | PASS | "> - Connection: Extends — from 'components/home/banner.tsx' ..." | — |
| 4 | phase-b-skips (Connection) | PASS | Phase B asks Main goal only | — |

### Notes
Explicit file path + matching Jira hit + "extend" verb = clean inference.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-010
### Preconditions
User input: "we should do something about the lobby". No context, no MCP. Vague — no Phase A signal.

### Phase A — Inferences
- **Ticket type:** Not inferred
- **Main user:** Not inferred
- **Main goal:** Not inferred
- **Connection:** Not inferred
- **Needs flow diagram:** Not inferred — ambiguous; falls through to Phase C fallback question

### Phase B — Questions asked
Q1 Ticket type: New feature / Improvement / Bug or issue. (PM: Improvement)
Q2 Main user: End user / Admin / internal / Support / ops. (PM: End user)
Q3 Main goal: Improve UX / Fix friction / Business need. (PM: Improve UX)
Q4 Connection: Changes a flow / Extends a feature / New flow. (PM: Changes a flow)

### Phase C — Follow-ups
Q1 (header: `Flow?`) per TB-Δ-1 L106-L114 fallback: "Include an ASCII user flow diagram?"
  options: Yes — happy path only / Yes — with branches and decisions / No — skip the flow diagram
  (PM: No — skip the flow diagram)

(No other Phase C questions — no concrete options can be drawn from context per rule 6.)

Total Phase B + Phase C = 4 + 1 = 5 questions, within 7 cap.

### Phase D — Artifact
```markdown
# Improve casino lobby (scope TBD with PM)

**Ticket type:** Improvement
**Parent epic (if any):** —
**Component:** lobby
**Labels:** improvement, lobby, needs-scoping

## User Story
As an End user, I want a clearer / faster casino lobby experience, so that I can find a game to play more easily.

## Description
Improvement to the casino lobby. Specific scope (filtering, layout, recommendations) to be defined with PM — placeholder until concrete area is selected.

## Definition of Done
- Concrete lobby improvement scope agreed with PM
- Single-target acceptance criteria added before dev starts
- Linked to a parent epic (TBD) before dev kicks off
```

(No Inferred block — Phase A inferred zero. No User Flow heading — PM chose No on fallback.)

### Handoff
Hold the chip.

## VERDICT: TB-010
**Title:** Ambiguous input falls through — Phase A infers nothing, Phase B asks all 4
**SKILL.md ref:** ticket-builder:L56-L64
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Ticket type) | PASS | "Ticket type: Not inferred" | — |
| 2 | phase-a-does-not-infer-field (Main user) | PASS | "Main user: Not inferred" | — |
| 3 | phase-a-does-not-infer-field (Main goal) | PASS | "Main goal: Not inferred" | — |
| 4 | phase-a-does-not-infer-field (Connection) | PASS | "Connection: Not inferred" | — |
| 5 | inferred-block-omitted-when-empty | PASS | Artifact has no Inferred block | — |
| 6 | phase-b-asks (all 4) | PASS | Q1-Q4 cover all 4 core fields | — |

### Notes
Clean fall-through. Phase C fallback Q for Needs flow diagram added (TB-Δ-1), counted against the Phase C 3-cap; doesn't break the 7-total cap (4+1=5).

### Delta vs v1.0.0
PASS → PASS (unchanged; v1.1.0 adds Phase C fallback question which is allowed)

---

## TRACE: TB-011
### Preconditions
User input: "fix the new VIP cashback feature — it's not crediting on time". Jira: PR-602 / open / "VIP cashback v2" / component: vip / status: in QA. No MCP.

### Phase A — Inferences
- **Ticket type:** Conflicting signals: "fix" → Bug AND "new" → Feature both fire on the SAME field per Ticket type's inference signal row. Per TB-Δ-7 L53 conflict rule, the field is marked **Not inferred** and falls through to Phase B. (Acceptable per `acceptable_outcomes: ["Bug", "<not inferred>"]`.)
- **Main user:** End user — citation: "VIP cashback" (player-facing)
- **Main goal:** Fix friction — citation: "fix" + "not crediting" (only Fix-friction signal fires here; no conflict)
- **Connection:** Extends — citation: "VIP cashback" matching PR-602 "VIP cashback v2"
- **Needs flow diagram:** No — bug class + on-time crediting is config-style (per TB-Δ-1 row 5: "bug" → No)

### Phase B — Questions asked
Q1 Ticket type: New feature / Improvement / Bug or issue. (PM: Bug or issue)

### Phase C — Follow-ups
Q1 (header: `Cashback trigger`): Smartico campaign scheduler / Internal cron in vip service / PS-native VIP API job. (PM: Internal cron)
Q2 (header: `Definition of on time`): Within 1h / Within 4h / Within 24h. (PM: Within 4h)

### Phase D — Artifact
```markdown
# Fix VIP cashback timing on PR-602

**Ticket type:** Bug
**Parent epic (if any):** PR-602 "VIP cashback v2" (open, in QA)
**Component:** vip
**Labels:** bug, vip, cashback, p1

> **Inferred (not asked):**
> - Connection: Extends — from "VIP cashback" matching PR-602
> - Main user: End user — from "VIP cashback"
> - Main goal: Fix friction — from "fix" + "not crediting"
> - Needs flow diagram: No — bug class

## User Story
As a VIP End user, I want my cashback to credit within the documented SLA, so that I can rely on the program's payout schedule.

## Description
VIP cashback under PR-602 is not crediting on time. Resolve so cashback credits within 4 hours of cycle end. Investigate the internal vip-service cron timing.

## Definition of Done
- VIP cashback credits within 4h of cycle end for QA cohorts
- Cron timing audited; failure path logs reason
- E2E regression added on PR-602
```

### Handoff
Hold the chip.

## VERDICT: TB-011
**Title:** Conflicting signals 'fix the new feature' resolve cleanly or fall through
**SKILL.md ref:** ticket-builder:L56-L64
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-resolves-conflict (Ticket type → Bug OR not inferred) | PASS | TB-Δ-7 conflict rule fires: Ticket type Not inferred (in `acceptable_outcomes`) | — |
| 2 | phase-a-infers-field (Connection=Extends, cite "VIP cashback") | PASS | "Connection: Extends — citation: 'VIP cashback' matching PR-602" | — |

### Notes
TB-Δ-7 cleanly resolves the v1.0.0 ambiguity. Both signals "fix" and "new" appear in the SAME field's signal table row 1 → field becomes Not inferred per L53. Falls through to Phase B → PM resolves. Connection still infers cleanly because only one signal row fires for it.

### Delta vs v1.0.0
PASS → PASS (unchanged; v1.0.0 trace resolved to Bug, v1.1.0 trace falls through — both acceptable per case YAML)

---

## TRACE: TB-012
### Preconditions
User input: "add a VIP progress bar to the casino home". Jira: PR-470 closed / casino home redesign / file: components/home/banner.tsx. No MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** Not inferred — "casino home" doesn't lock to player
- **Main goal:** Not inferred
- **Connection:** Extends — "casino home" matches PR-470 (components/home/banner.tsx)
- **Needs flow diagram:** Yes — new feature + multi-step

### Phase B — Questions asked
Q1 Main user (PM: End user)
Q2 Main goal (PM: Business need)

### Phase C — Follow-ups
Q1 Points source: Smartico LOYALTY_POINTS_UPDATE / PS-native VIP API / Hybrid. (PM: Smartico)

### Phase D — Artifact (abbreviated)
```markdown
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** feature, vip, home

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" matching PR-470 (components/home/banner.tsx)
> - Needs flow diagram: Yes — new feature + multi-step

## User Story
As an End user logged into the casino home, I want to see my VIP tier progress, so that I'm motivated to keep playing.

## Description
Add a VIP progress bar to components/home/banner.tsx on the casino home. Sourced from Smartico LOYALTY_POINTS_UPDATE.

## User Flow
```
┌──────────────────┐
│ Logged-in player │
│ opens home       │
└──────┬───────────┘
       ▼
┌──────────────────────┐
│ Progress bar renders │
└──────────────────────┘
```

## Definition of Done
- VIP progress bar in components/home/banner.tsx
- Smartico LOYALTY_POINTS_UPDATE wired
- Logged-in only; a11y label set
```

### Handoff
Hold the chip.

## VERDICT: TB-012
**Title:** Phase B asks only the questions Phase A could not infer
**SKILL.md ref:** ticket-builder:L65-L67
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Ticket type=Feature, "add") | PASS | inferred | — |
| 2 | phase-a-infers-field (Connection=Extends, "casino home") | PASS | inferred | — |
| 3 | phase-b-skips (Ticket type, Connection) | PASS | Phase B asks Main user + Main goal only | — |
| 4 | phase-b-asks (Main user, Main goal) | PASS | both asked | — |

### Notes
Clean skip/ask split. New Needs flow diagram = Yes inferred; doesn't pollute Phase B.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-013
### Preconditions
User input: "we should do something about the lobby". No context, no MCP. Tests Ticket type + Main user options verbatim.

### Phase A — Inferences
All 5 Not inferred.

### Phase B — Questions asked
Q1 (header: `Ticket type`): "What type of ticket is this?"
  options: New feature / Improvement / Bug or issue
  (PM: Improvement)
Q2 (header: `Main user`): "Who is the main user affected?"
  options: End user / Admin / internal / Support / ops
  (PM: End user)
Q3 Main goal (Improve UX)
Q4 Connection (Changes a flow)

### Phase C — Follow-ups
Q1 (header: `Flow?`) per TB-Δ-1 fallback: Yes happy / Yes with branches / No skip. (PM: No skip)

### Phase D — Artifact
(see TB-010)

### Handoff
Hold the chip.

## VERDICT: TB-013
**Title:** Each Phase B question has exactly 3 spec'd options verbatim
**SKILL.md ref:** ticket-builder:L67-L87
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Ticket type, header, count=3) | PASS | Q1 has 3 options under header `Ticket type` | — |
| 2 | phase-b-options-match-spec (Ticket type = New feature/Improvement/Bug or issue) | PASS | exact verbatim | — |
| 3 | phase-b-question-shape (Main user, header, count=3) | PASS | Q2 has 3 options under header `Main user` | — |
| 4 | phase-b-options-match-spec (Main user) | PASS | exact verbatim | — |

### Notes
Spec L70-L78 unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-014
### Preconditions
Same as TB-013. Tests Main goal + Connection options verbatim.

### Phase A — Inferences
All 5 Not inferred.

### Phase B — Questions asked
Q3 (header: `Main goal`): Improve UX / Fix friction / Business need
Q4 (header: `Connection`): Changes a flow / Extends a feature / New flow
(Plus Q1 Ticket type, Q2 Main user as in TB-013)

### Phase C — Follow-ups
Q1 Flow? fallback (PM: No skip)

### Phase D — Artifact
(see TB-010)

### Handoff
Hold the chip.

## VERDICT: TB-014
**Title:** Phase B Main goal and Connection question headers + options match spec
**SKILL.md ref:** ticket-builder:L67-L87
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Main goal, header) | PASS | "Q3 (header: `Main goal`)..." | — |
| 2 | phase-b-options-match-spec (Main goal) | PASS | Improve UX / Fix friction / Business need verbatim | — |
| 3 | phase-b-question-shape (Connection, header) | PASS | "Q4 (header: `Connection`)..." | — |
| 4 | phase-b-options-match-spec (Connection) | PASS | Changes a flow / Extends a feature / New flow verbatim | — |

### Notes
Spec L80-L88 unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-015
### Preconditions
Same as TB-013. Tests AskUserQuestion is the channel.

### Phase A — Inferences
All 5 Not inferred.

### Phase B — Questions asked
4 questions, each emitted via AskUserQuestion (one at a time per L50).

### Phase C — Follow-ups
Q1 Flow? fallback via AskUserQuestion (PM: No skip)

### Phase D — Artifact
(see TB-010)

### Handoff
Hold the chip.

## VERDICT: TB-015
**Title:** All Phase B questions emit via AskUserQuestion, not free-form prompts
**SKILL.md ref:** ticket-builder:L50-L53
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-uses-ask-user-question | PASS | All Phase B + Phase C questions via AskUserQuestion per L50 | — |

### Notes
Spec L50 unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-016
### Preconditions
Same vague input. Tests all 4 fired + Inferred block omitted.

### Phase A — Inferences
All 5 Not inferred.

### Phase B — Questions asked
4 (Ticket type, Main user, Main goal, Connection) via AskUserQuestion.

### Phase C — Follow-ups
Q1 Flow? fallback. (PM: No skip)

### Phase D — Artifact
Artifact has no Inferred block.

### Handoff
Hold the chip.

## VERDICT: TB-016
**Title:** When Phase A infers zero fields, Phase B asks all 4 core questions
**SKILL.md ref:** ticket-builder:L65-L87
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-asks (all 4) | PASS | Q1-Q4 cover all 4 | — |
| 2 | phase-b-uses-ask-user-question | PASS | All via AskUserQuestion | — |
| 3 | inferred-block-omitted-when-empty | PASS | Artifact has no Inferred block | — |

### Notes
Clean.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-017
### Preconditions
User input: "add a VIP progress bar to the casino home". Rich Jira (5 tickets) + Confluence (VIP PRD) + atlassian MCP. Stresses Phase C 3-cap.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — VIP PRD player focus
- **Main goal:** Business need — VIP PRD retention focus
- **Connection:** Extends — "casino home" matches PR-470 banner.tsx
- **Needs flow diagram:** Yes — feature + multi-step interaction

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups (capped at 3)
Q1 Points source: Smartico LOYALTY_POINTS_UPDATE (PR-481) / PS-native VIP API (PR-815) / Hybrid. (PM: Smartico)
Q2 Module placement on components/home/banner.tsx: Replaces first carousel slide / Persistent strip / Overlay. (PM: Persistent strip)
Q3 Platform scope: Casino only PR-470 / Casino+Sports PR-714 / Casino now + Sports follow-up. (PM: Casino only)

Candidates skipped to honor 3-cap: (a) mobile app inclusion (PR-815) → inline assumption; (b) PR-602 cashback interaction → inline assumption.

### Phase D — Artifact
Includes inline assumptions per TB-Δ-6: `> **Assumption:** Native mobile app (PR-815) out of scope. **Flag:** confirm with mobile lead.` and `> **Assumption:** No interaction with VIP cashback v2 (PR-602). **Flag:** confirm with VIP product owner if cashback affects bar credit logic.`

### Handoff
Bet on it via atlassian MCP.

## VERDICT: TB-017
**Title:** Phase C emits at most 3 follow-up questions (rule 1)
**SKILL.md ref:** ticket-builder:L94
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | Exactly Q1, Q2, Q3; other candidates → inline assumptions | — |

### Notes
3-cap honored even under pressure. Needs flow diagram inferred = Yes, so the Phase C fallback Q from TB-Δ-1 does NOT fire (not needed against the cap).

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-018
### Preconditions
Same as TB-012 setup. Atlassian MCP. Tests no-banned-placeholder rule.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470
- **Main user, Main goal:** Not inferred → Phase B
- **Needs flow diagram:** Yes

### Phase B — Questions asked
Q1 Main user (End user); Q2 Main goal (Business need)

### Phase C — Follow-ups
Q1 (header: `Points source`): 1) Smartico LOYALTY_POINTS_UPDATE (PR-481) / 2) PS-native VIP API / 3) Hybrid: Smartico now, swap to PS later. (PM: Smartico)
Q2 (header: `Module placement`): 1) Replaces first carousel slide / 2) Persistent strip below carousel / 3) Overlay on first slide. (PM: Persistent strip)

All options reference concrete artifacts (event name, API name, file path). No "Use the existing system", "Option A", "TBD", "I'll specify later" appear.

### Phase D — Artifact
(see TB-009/TB-012 shape)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-018
**Title:** Phase C rejects banned generic placeholder option labels (rule 2)
**SKILL.md ref:** ticket-builder:L94
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-no-banned-placeholders | PASS | All options reference Smartico/PS-native/banner.tsx — no banned strings | — |
| 2 | phase-c-options-are-concrete | PASS | Q1 cites event name + API; Q2 cites file path | — |

### Notes
Concrete throughout.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-019
### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 + PR-481 (decision: Smartico canonical) + Confluence (Smartico until PS-native ships Q4). Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — Confluence VIP PRD player focus
- **Main goal:** Business need — VIP PRD retention
- **Connection:** Extends — "casino home" + PR-470
- **Needs flow diagram:** Yes

### Phase B — Questions asked
none — all 5 inferred (Confluence + Jira richly resolve)

### Phase C — Follow-ups
Q1 Module placement (PM: Persistent strip)
Q2 Platform scope (PM: Casino only)

Data source question SKIPPED per rule 3 — PR-481 + Confluence already decide it. Converted to inline assumption: `> **Assumption:** Data source = Smartico LOYALTY_POINTS_UPDATE per PR-481 + VIP v3 PRD; PS-native swap Q4 TBD. **Flag:** confirm Q4 cutover plan with VIP product owner.`

### Phase D — Artifact (snippet)
```
> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" matching PR-470
> - Main user: End user — from Confluence VIP PRD
> - Main goal: Business need — from VIP PRD retention focus
> _(+1 more inferred — see context for full set)_

## Description
Add a persistent VIP progress strip below the carousel in components/home/banner.tsx.
> **Assumption:** Data source = Smartico LOYALTY_POINTS_UPDATE per PR-481 + Confluence "VIP Program v3 — Data Sources" (Smartico is source of truth until PS-native VIP API ships in Q4). **Flag:** confirm Q4 cutover plan.
```

### Handoff
Bet on it via atlassian.

## VERDICT: TB-019
**Title:** Phase C skips a question that Jira context already answers (rule 3)
**SKILL.md ref:** ticket-builder:L96
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-when-context-answers (data source for points-to-next-tier; inline assumption expected) | PASS | "Data source question SKIPPED... converted to inline assumption" + Description block uses TB-Δ-6 assume+flag syntax | — |

### Notes
Skips the right question. TB-Δ-6 syntax (`> **Assumption:** ... **Flag:** ...`) used inline.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-020
### Preconditions
Same as TB-018 simplified — tests rule 4.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470 banner.tsx
- **Main user, Main goal:** Not inferred → Phase B
- **Needs flow diagram:** Yes

### Phase B — Questions asked
Q1 Main user; Q2 Main goal

### Phase C — Follow-ups
Q1 Points source (data-source ambiguity, priority #1)
Q2 Module placement (behavioral choice, priority #3)

Tempting questions CONSIDERED and SKIPPED per rule 4:
- "What color should the progress bar be?" → styling, defer to design
- "What should the analytics event be named?" → exact event name, default + flag
- "What microcopy goes above the bar?" → exact copy, defer to UX writing

### Phase D — Artifact (DoD snippet using TB-Δ-6 syntax)
```
## Definition of Done
- Strip renders in components/home/banner.tsx, logged-in only
- Points hydrated from Smartico LOYALTY_POINTS_UPDATE
- A11y label set
- Tap navigates to /vip tier detail
- Telemetry events fire on render and tap
  > **Assumption:** event names `vip_progress_bar_view`, `vip_progress_bar_tap`. **Flag:** confirm with data team.
```

### Handoff
Bet on it via atlassian.

## VERDICT: TB-020
**Title:** Phase C does not ask about styling, color, copy, or exact event names (rule 4)
**SKILL.md ref:** ticket-builder:L97
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-styling-copy-questions | PASS | "color, analytics event name, microcopy" all skipped per rule 4 | — |

### Notes
Rule 4 respected. TB-Δ-6 assume+flag syntax now formalized (vs v1.0.0 ambiguity).

### Delta vs v1.0.0
PASS → PASS (unchanged; TB-Δ-6 resolves the v1.0.0 P2 spec ambiguity around flag syntax — no longer a flagged ambiguity)

---

## TRACE: TB-021
### Preconditions
User input: "add a VIP progress bar to the casino home — also confirm it works on the mobile app". Jira: PR-481 (Smartico) + PR-815 (PS-native VIP API scoping) + PR-714 (Sports home). Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — "casino home"
- **Main goal:** Not inferred
- **Connection:** Extends — "casino home" matches PR-470 area
- **Needs flow diagram:** Yes — feature + multi-step

### Phase B — Questions asked
Q1 Main goal (PM: Business need)

### Phase C — Follow-ups (priority order respected)
Q1 (header: `Points source`) — data-source ambiguity (priority #1):
  options: 1) Smartico LOYALTY_POINTS_UPDATE (PR-481) / 2) PS-native VIP API (PR-815) / 3) Hybrid
  (PM: Hybrid)
Q2 (header: `Platform scope`) — scope edge (priority #2):
  options: 1) Casino web only / 2) Casino web + mobile app (PR-815 alignment) / 3) Web now, mobile as child ticket
  (PM: Web now, mobile as child)
Q3 (header: `Update cadence`) — trigger (priority #4):
  options: 1) Real-time Smartico push / 2) Polled 60s / 3) On-mount only
  (PM: Real-time Smartico push)

### Phase D — Artifact
(standard)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-021
**Title:** Phase C respects priority order — data source ambiguity first
**SKILL.md ref:** ticket-builder:L98-L103
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-priority-order-respected (expected_top_topic: data source ambiguity) | PASS | "Q1 ... data-source ambiguity (priority #1)" | — |

### Notes
Priority list applied — data source first, then scope, then cadence. Per L98-L103 unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-022
### Preconditions
User input: "add a subtle entrance animation when the VIP bar mounts". Jira PR-470 only. Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Improvement — "entrance animation" on existing bar
- **Main user:** End user — casino UI
- **Main goal:** Improve UX — animation polish
- **Connection:** Extends — VIP bar implies existing
- **Needs flow diagram:** No — animation tweak is a config-style polish (per TB-Δ-1 row 5: "config" / single visual tweak → No)

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
none — no concrete options can be drawn for "animation library" (no PR names framer-motion, react-spring, or any specific lib). Per rule 6 + TB-Δ-6 syntax, unknown converts to inline assumption + flag in the ticket.

### Phase D — Artifact (snippet)
```
## Description
Add a subtle entrance animation when the VIP progress bar mounts on components/home/banner.tsx.
> **Assumption:** Animation library not specified in context; default to the repo's existing animation utility (whichever is already imported by neighboring components in components/home/). **Flag:** confirm with frontend lead before implementation.
```

(No User Flow heading — Needs flow diagram = No.)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-022
**Title:** Phase C falls back to assume + flag when 3 concrete options can't be written (rule 6)
**SKILL.md ref:** ticket-builder:L104
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-fallback-to-assume-and-flag (preferred animation library) | PASS | "no concrete options for 'animation library' — converted to inline assumption" + Description uses TB-Δ-6 `> **Assumption:** ... **Flag:** ...` syntax | — |
| 2 | phase-c-no-banned-placeholders | PASS | Phase C asks no questions, no placeholders | — |

### Notes
TB-Δ-6 formalized the syntax (`> **Assumption:** ... **Flag:** ...`) — v1.0.0 trace's P2 ambiguity is now resolved at spec level.

### Delta vs v1.0.0
PASS → PASS (unchanged; v1.0.0 had a P2 suggestion to clarify flag syntax — TB-Δ-6 addresses this)

---

## TRACE: TB-023
### Preconditions
Vague input "we should do something about the lobby" + Jira context with 3 tickets (PR-470, PR-481, PR-714). Atlassian MCP. Tests total cap = 7.

### Phase A — Inferences
- All 5 Not inferred (Needs flow diagram also ambiguous).

### Phase B — Questions asked
4 questions (Ticket type, Main user, Main goal, Connection).
(PM: Improvement / End user / Improve UX / Changes a flow)

### Phase C — Follow-ups (max 3)
Q1 (header: `Lobby area`): Casino lobby filter bar PR-470 / Sports lobby PR-714 / Loyalty integrations PR-481. (PM: Casino lobby filter bar) — scope edge
Q2 (header: `Improvement focus`): Filtering live dealer / Performance TTI / Personalization Smartico. (PM: Filtering) — behavioral
Q3 (header: `Flow?`) per TB-Δ-1 fallback: Yes happy / Yes with branches / No skip. (PM: Yes happy) — Needs flow diagram

Total: 4 (Phase B) + 3 (Phase C) = 7 questions. Cap respected exactly.

### Phase D — Artifact
(standard with happy-path User Flow per PM choice)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-023
**Title:** Total questions across Phase B + Phase C never exceed 7
**SKILL.md ref:** ticket-builder:L54
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | total-questions-asked-max (max 7) | PASS | "Total: 4 (Phase B) + 3 (Phase C) = 7 questions" | — |
| 2 | phase-c-max-3 | PASS | Phase C = Q1, Q2, Q3 (Flow? counts toward 3-cap per L114) | — |

### Notes
At the 7-cap exactly. The Flow? fallback Q (TB-Δ-1 L106-L114) is one of the 3 Phase C questions per L114 ("This counts against the Phase C 3-follow-up cap"). No regression: total cap holds.

### Delta vs v1.0.0
PASS → PASS (unchanged; was potential regression candidate but the spec explicitly counts Flow? against the 3-cap)

---

## TRACE: TB-024
### Preconditions
User input: "add a VIP progress bar to the casino home". Rich Jira (5 PRs) + Confluence VIP PRD. Atlassian MCP. Tests Phase C reproduces spec worked example.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — VIP PRD player focus
- **Main goal:** Business need — VIP PRD retention focus
- **Connection:** Extends — "casino home" + PR-470 banner.tsx
- **Needs flow diagram:** Yes

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups (matches spec L117-L119 worked example)
Q1 (header: `Points source`): "Where does points-to-next-tier come from?"
  1) Smartico LOYALTY_POINTS_UPDATE event (PR-481) / 2) PS-native VIP API (PR-815 — currently being scoped) / 3) Hybrid: Smartico now, abstract behind a service, swap to PS later. (PM: Hybrid)
Q2 (header: `Module placement`): "How does the module fit on the existing hero (components/home/banner.tsx)?"
  1) Replaces first carousel slide / 2) Persistent strip below carousel / 3) Overlay on first slide. (PM: Persistent strip)
Q3 (header: `Platform scope`): "Casino home only or sports home too?"
  1) Casino only PR-470 / 2) Casino + sports parallel PR-714 / 3) Casino now, sports follow-up child. (PM: Casino only)

### Phase D — Artifact
(standard)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-024
**Title:** Smartico VIP progress bar — Phase C generates the spec'd worked-example follow-ups
**SKILL.md ref:** ticket-builder:L116-L119
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | Q1, Q2, Q3 only | — |
| 2 | phase-c-options-are-concrete | PASS | LOYALTY_POINTS_UPDATE / PR-481 / PR-815 / components/home/banner.tsx / PR-470 / PR-714 — all concrete | — |
| 3 | phase-c-priority-order-respected (data source first) | PASS | Q1 = data source | — |
| 4 | phase-c-no-banned-placeholders | PASS | No banned strings | — |

### Notes
Direct mirror of spec worked example. Unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-025
### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 / banner.tsx. Atlassian MCP. Tests 4 required sections in order.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470
- **Main user, Main goal:** not inferred → Phase B
- **Needs flow diagram:** Yes — new feature + multi-step

### Phase B — Questions asked
2 (Main user, Main goal); answers: End user / Business need

### Phase C — Follow-ups
Q1 Points source (Smartico); Q2 Module placement (strip); Q3 Platform scope (casino only)

### Phase D — Artifact
```markdown
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** feature, vip, home

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" matching PR-470
> - Needs flow diagram: Yes — feature + multi-step

## User Story
As a logged-in End user, I want to see my VIP tier progress on the casino home, so that I am motivated to keep playing.

## Description
Add a persistent VIP progress strip below the carousel in components/home/banner.tsx. Sourced from Smartico LOYALTY_POINTS_UPDATE.

## User Flow
```
┌──────────────┐
│ Home loads   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Strip shows X / Y    │
└──────────────────────┘
```

## Definition of Done
- Strip renders in components/home/banner.tsx, logged-in only
- Smartico LOYALTY_POINTS_UPDATE wired
- A11y label set
```

### Handoff
Bet on it via atlassian.

## VERDICT: TB-025
**Title:** Artifact contains all 4 required sections in order
**SKILL.md ref:** ticket-builder:L130-L172
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | output-has-required-sections (User Story, Description, User Flow, Definition of Done) | PASS | All 4 in order | — |

### Notes
User Flow correctly present because Needs flow diagram inferred = Yes. If the input had been a bug, User Flow would be omitted per TB-Δ-1 — but this case's input triggers Yes.

### Delta vs v1.0.0
PASS → PASS (unchanged; potential regression candidate verified safe — feature input keeps User Flow)

---

## TRACE: TB-026
### Preconditions
User input: "add a VIP progress bar to the casino home — players need to see how close they are to the next tier so they keep depositing". Rich context (PR-470, PR-481, VIP v3 PRD). Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — "players"
- **Main goal:** Business need — "keep depositing"
- **Connection:** Extends — PR-470
- **Needs flow diagram:** Yes

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
Q1 Module placement; Q2 Platform scope. (Data source already answered by PR-481 → inline assumption per rule 3.)

### Phase D — Artifact (lean — no banned sections)
```markdown
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** feature, vip, home, retention

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" matching PR-470
> - Main user: End user — from "players"
> - Main goal: Business need — from "keep depositing"
> _(+1 more inferred — see context for full set)_

## User Story
As a logged-in End user, I want to see how close I am to the next VIP tier, so that I am motivated to keep depositing.

## Description
Add a persistent VIP progress strip in components/home/banner.tsx below the carousel for logged-in players. Source: Smartico LOYALTY_POINTS_UPDATE (per PR-481). Aligned with the VIP Program v3 PRD's retention goal.

## User Flow
```
┌──────────────┐
│ Home loads   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Progress strip X / Y │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Tap → /vip details   │
└──────────────────────┘
```

## Definition of Done
- Strip renders in components/home/banner.tsx, logged-in only
- Points hydrated from Smartico LOYALTY_POINTS_UPDATE
- Tap navigates to /vip
- A11y label set; passes axe scan
- Telemetry events fire on render and tap
  > **Assumption:** event names default to `vip_progress_view`, `vip_progress_tap`. **Flag:** confirm with data team.
```

No Background/Context/Problem/Desired Outcome/Scope/Functional Requirements/Edge Cases/Analytics/Dependencies/Open Questions/Builder notes section.

### Handoff
Bet on it via atlassian.

## VERDICT: TB-026
**Title:** Artifact omits all banned sections
**SKILL.md ref:** ticket-builder:L130-L173
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | output-omits-banned-sections | PASS | Only 4 required sections appear | — |

### Notes
Even with rich tempting context, lean output. DoD = 5 (cap respected, TB-Δ-2).

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-027
### Preconditions
User input: "add a VIP progress bar to the casino home". No context, no MCP. Tests User Story shape.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — "casino home"
- **Main user, Main goal:** not inferred → Phase B
- **Needs flow diagram:** Yes

### Phase B — Questions asked
Main user (End user), Main goal (Improve UX)

### Phase C — Follow-ups
Q1 Points source; Q2 Module placement

### Phase D — Artifact (snippet)
```
## User Story
As a logged-in End user, I want to see my VIP tier progress on the casino home, so that I am motivated to keep playing.
```

### Handoff
Hold the chip.

## VERDICT: TB-027
**Title:** User Story line follows the canonical 'As a / I want / so that' shape
**SKILL.md ref:** ticket-builder:L143-L144
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | user-story-shape | PASS | "As a ..., I want to ..., so that ..." | — |

### Notes
Canonical shape unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-028
### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470. No MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470
- **Main user, Main goal:** not inferred → Phase B
- **Needs flow diagram:** Yes (new feature + multi-step)

### Phase B — Questions asked
2 (Main user, Main goal)

### Phase C — Follow-ups
2 (Points source, Module placement)

### Phase D — Artifact (User Flow snippet)
```
## User Flow
```
┌──────────────────┐
│ Logged-in player │
│ opens /home      │
└──────┬───────────┘
       ▼
┌──────────────────────┐
│ banner.tsx renders   │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Progress strip X / Y │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Tap → /vip details   │
└──────────────────────┘
```
```

### Handoff
Hold the chip.

## VERDICT: TB-028
**Title:** ASCII flow uses box-drawing chars and arrows inside a fenced code block
**SKILL.md ref:** ticket-builder:L152
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | ascii-flow-uses-box-drawing | PASS | ┌──────────────┐ / │ / └ / ▼ inside fenced block | — |

### Notes
Box-drawing chars + arrows + fenced block all present. User Flow heading included because feature class infers Needs flow diagram = Yes.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-029
### Preconditions
User input: "the deposit button is broken on iOS". No context, no MCP. Tests Inferred block placement and content.

### Phase A — Inferences
- **Ticket type:** Bug — "broken"
- **Main user:** Not inferred (no clean signal — "iOS" weak; "deposit" is component)
- **Main goal:** Fix friction — "broken"
- **Connection:** Not inferred — "deposit button" is UI element, no concrete file lock
- **Needs flow diagram:** No — citation: "bug" → omit §User Flow

### Phase B — Questions asked
Q1 Main user (End user)
Q2 Connection (Changes a flow)

### Phase C — Follow-ups
Q1 (header: `Platform scope`): iOS Safari only / iOS Safari + iOS Chrome / All iOS browsers + native app. (PM: iOS Safari only)

### Phase D — Artifact
```markdown
# Fix iOS deposit button error

**Ticket type:** Bug
**Parent epic (if any):** —
**Component:** deposit
**Labels:** bug, ios, deposit

> **Inferred (not asked):**
> - Ticket type: Bug — from "broken"
> - Main goal: Fix friction — from "broken"
> - Needs flow diagram: No — from "bug" (omitting §User Flow)

## User Story
As an End user on iOS, I want the deposit button to work, so that I can fund my account.

## Description
The deposit button is broken on iOS. Restore the documented deposit submission flow on iOS so a logged-in player can submit a deposit and receive a confirmation without server error.

## Definition of Done
- Deposit endpoint returns 2xx on iOS for valid requests
- Regression test covers iOS deposit submission
- Manual QA pass on iOS Safari 16+17 + iOS Chrome
```

The Inferred block is placed immediately after the metadata header (Ticket type / Parent epic / Component / Labels) and before `## User Story` — exactly as TB-Δ-5 updated L127 prescribes.

### Handoff
Hold the chip.

## VERDICT: TB-029
**Title:** Inferred (not asked) block appears at top when Phase A inferred ≥1 field
**SKILL.md ref:** ticket-builder:L127, L139
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | inferred-block-present | PASS | `> **Inferred (not asked):**` block rendered after metadata, before `## User Story` per TB-Δ-5 updated narrative | — |
| 2 | inferred-includes-field (Ticket type=Bug, cite "broken") | PASS | "> - Ticket type: Bug — from 'broken'" | — |

### Notes
**v1.0.0 PARTIAL flag resolved.** v1.0.0 baseline flagged a narrative-vs-template conflict (L116 said "at the top" while template showed metadata-then-block). TB-Δ-5 updated L127 to: "If anything was inferred in Phase A, surface the `Inferred (not asked)` block immediately after the 4 metadata header lines (Ticket type / Parent epic / Component / Labels), before `## User Story`. See the template below for exact placement." This now matches the template exactly. No ambiguity.

### Delta vs v1.0.0
PARTIAL → PASS (TB-Δ-5 resolved the narrative/template placement conflict)

---

## TRACE: TB-030
### Preconditions
Vague input "we should do something about the lobby". No context, no MCP. Tests Inferred block OMITTED.

### Phase A — Inferences
- All 5 Not inferred.

### Phase B — Questions asked
4

### Phase C — Follow-ups
Q1 Flow? fallback (PM: No skip)

### Phase D — Artifact
```markdown
# Improve casino lobby (scope TBD)

**Ticket type:** Improvement
**Parent epic (if any):** —
**Component:** lobby
**Labels:** improvement, lobby, needs-scoping

## User Story
As an End user, I want a clearer casino lobby, so that I can find a game faster.

## Description
...

## Definition of Done
- ...
- ...
- ...
```

(No Inferred block at all — not rendered as empty.)

### Handoff
Hold the chip.

## VERDICT: TB-030
**Title:** Inferred block is OMITTED when Phase A inferred zero fields
**SKILL.md ref:** ticket-builder:L139
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | inferred-block-omitted-when-empty | PASS | Artifact has no `Inferred (not asked):` block | — |
| 2 | inferred-block-present (must: false) | PASS | Block absent | — |

### Notes
Spec L139 template note: "include this block only if Phase A inferred at least one core answer".

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-031
### Preconditions
User input: "the withdrawal page throws a 500 on iOS Safari". No context, no MCP. Tests no meta-commentary after DoD.

### Phase A — Inferences
- **Ticket type:** Bug — "throws a 500"
- **Main user:** End user — "withdrawal page" (player-facing)
- **Main goal:** Fix friction — "throws a 500"
- **Connection:** Changes — existing withdrawal page
- **Needs flow diagram:** No — bug class (per TB-Δ-1)

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
Q1 Scope (iOS Safari only); Q2 Reproduction (consistent vs intermittent)

### Phase D — Artifact (ends at DoD)
```markdown
# Fix withdrawal page 500 error on iOS Safari

**Ticket type:** Bug
**Parent epic (if any):** —
**Component:** withdrawal
**Labels:** bug, ios, withdrawal, p1

> **Inferred (not asked):**
> - Ticket type: Bug — from "throws a 500"
> - Connection: Changes — from "withdrawal page" (existing flow)
> - Main user: End user — from "withdrawal page"
> - Main goal: Fix friction — from "throws a 500"
> _(+1 more inferred — see context for full set)_

## User Story
As an End user on iOS Safari, I want to complete a withdrawal, so that I can cash out without error.

## Description
The withdrawal page returns HTTP 500 on iOS Safari. Restore the documented withdrawal flow so a logged-in player can submit a withdrawal and receive a confirmation.

## Definition of Done
- Withdrawal endpoint returns 2xx on iOS Safari
- Regression test added
- Manual QA pass on iOS Safari 16+17
```

(File ends at DoD. No User Flow heading per Bug class. No "Builder notes", reflections, or `## Notes` after DoD.)

### Handoff
Hold the chip.

## VERDICT: TB-031
**Title:** No meta-commentary, builder notes, or reflections after Definition of Done
**SKILL.md ref:** ticket-builder:L184
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | no-meta-commentary-after-final-section (final: Definition of Done) | PASS | "File ends at DoD. No 'Builder notes', no reflections" | — |

### Notes
Trace stops at DoD per L184: "The ticket ends at Definition of Done."

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-032
### Preconditions
User input: "add a VIP progress bar to the casino home". No context. Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — "casino home"
- **Main user, Main goal:** not inferred → Phase B
- **Needs flow diagram:** Yes

### Phase B — Questions asked
2 (Main user, Main goal)

### Phase C — Follow-ups
1-2 (Points source, Module placement)

### Phase D — Artifact
(standard)

### Handoff
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md`
2. Gamble question (exactly once): "Ready To Gamble On It?" (header: `Gamble?`) options: `Bet on it` / `Hold the chip` via AskUserQuestion.
3. Simulated user choice: Bet on it (mcp_state atlassian)
4. Tool call: `mcp__*atlassian*` createIssue
5. Final message: standard

## VERDICT: TB-032
**Title:** 'Ready To Gamble On It?' is presented exactly once with header 'Gamble?'
**SKILL.md ref:** ticket-builder:L165-L170
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-handoff-presented-once | PASS | "Gamble question (exactly once): 'Ready To Gamble On It?' (header: `Gamble?`)" | — |

### Notes
Exactly one handoff via AskUserQuestion.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-033
### Preconditions
Same as TB-032. Tests options are exactly "Bet on it" / "Hold the chip" (no Double down).

### Phase D — Artifact
(standard)

### Handoff
Gamble options:
1. `Bet on it` — push to Jira
2. `Hold the chip` — keep markdown only

No `Double down` option present (Double down is in PRD-driven mode L186-L198 / prd-writer Double-down chain, not ticket-builder's handoff).

## VERDICT: TB-033
**Title:** Handoff options are exactly 'Bet on it' and 'Hold the chip' — no 'Double down'
**SKILL.md ref:** ticket-builder:L167-L170
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-options-match-spec (expected: ["Bet on it", "Hold the chip"]) | PASS | options: Bet on it / Hold the chip | — |

### Notes
Exactly the spec'd two. TB-Δ-8 adds PRD-driven mode but explicitly says (L195) "auto-choose `Bet on it`. Do NOT call AskUserQuestion." — so the handoff prompt is suppressed, not given a Double down option. The Double down concept lives in prd-writer's upstream contract per L198.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-034
### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470/banner.tsx. Atlassian MCP. Tests Bet on it triggers correct MCP tool regex.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470
- **Main user, Main goal:** not inferred → Phase B
- **Needs flow diagram:** Yes

### Phase B — Questions asked
2

### Phase C — Follow-ups
1-2 (Points source / Module placement)

### Phase D — Artifact
(standard)

### Handoff
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md`
2. Gamble question: standard
3. Simulated user choice: Bet on it
4. Tool call:
   - Tool name regex: `mcp__.*(atlassian|jira).*` with method matching `(createIssue|createJiraIssue|create_issue)`
   - Parameters: projectKey, issueType, summary (ticket title), description (markdown body)
5. Final message: "Created PR-XYZ at https://<workspace>.atlassian.net/browse/PR-XYZ. Saved at /Users/talshani/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md."

## VERDICT: TB-034
**Title:** 'Bet on it' + Atlassian MCP connected → calls jira-create-issue via correct tool regex
**SKILL.md ref:** ticket-builder:L172
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | mcp-tool-lookup-pattern | PASS | "Tool name regex: `mcp__.*(atlassian\|jira).*` with method matching `(createIssue\|createJiraIssue\|create_issue)`" | — |
| 2 | markdown-saved-with-absolute-path (folder: tickets) | PASS | absolute path under `~/Downloads/tickets/` printed | — |

### Notes
L172 unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-035
### Preconditions
User input: "add a VIP progress bar to the casino home". No context. **No MCP**.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — "casino home"
- **Main user, Main goal:** not inferred → Phase B
- **Needs flow diagram:** Yes

### Phase B — Questions asked
2

### Phase C — Follow-ups
1 (Points source — with no context, options weaker; trace converts to inline assumption per rule 6)

### Phase D — Artifact
(standard)

### Handoff
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md`
2. Gamble question: standard
3. Simulated user choice: Bet on it
4. MCP check: no Atlassian MCP connected.
5. Final message: "Atlassian MCP not connected — saved markdown only at /Users/talshani/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md"

## VERDICT: TB-035
**Title:** 'Bet on it' + no MCP → exact fallback 'Atlassian MCP not connected — saved markdown only at <path>'
**SKILL.md ref:** ticket-builder:L173
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | mcp-fallback-when-disconnected | PASS | "Atlassian MCP not connected — saved markdown only at ..." verbatim | — |
| 2 | markdown-saved-with-absolute-path (folder: tickets) | PASS | absolute path under `~/Downloads/tickets/` printed | — |

### Notes
L173 unchanged in v1.1.0.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-036
### Preconditions
User input: "Add a VIP progress bar to the casino home" (capital A — slug must lowercase). No context. Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "Add"
- **Connection:** Extends — "casino home"
- **Main user, Main goal:** not inferred → Phase B
- **Needs flow diagram:** Yes

### Phase B — Questions asked
2

### Phase C — Follow-ups
1

### Phase D — Artifact
Title rendered as "Add a VIP progress bar to the casino home" (preserves casing).

### Handoff
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md` (slug kebab-case, all-lower)
2. Gamble question: standard
3. Simulated user choice: Hold the chip
4. Final message: "Saved at /Users/talshani/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md. No Jira ticket created."

## VERDICT: TB-036
**Title:** 'Hold the chip' confirms save and prints absolute path with kebab-case slug
**SKILL.md ref:** ticket-builder:L165-L175
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | markdown-saved-with-absolute-path (tickets) | PASS | "/Users/talshani/Downloads/tickets/...md" | — |
| 2 | slug-is-kebab-case (expected: add-a-vip-progress-bar-to-the-casino-home) | PASS | "add-a-vip-progress-bar-to-the-casino-home.md" exact | — |

### Notes
Slug all-lowercase kebab.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-037
### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 / banner.tsx + PR-481 Smartico LOYALTY_POINTS_UPDATE. Confluence VIP v3 PRD. Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user
- **Main goal:** Business need (VIP PRD)
- **Connection:** Extends — PR-470 banner.tsx
- **Needs flow diagram:** Yes

### Phase B — Questions asked
none

### Phase C — Follow-ups
Q1 (Module placement), Q2 (Platform scope). Data source already answered → inline assumption.

### Phase D — Artifact
```markdown
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 "Casino home redesign" (reference, closed)
**Component:** home
**Labels:** feature, vip, smartico, home

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" matching PR-470 (components/home/banner.tsx)
> - Main user: End user — from VIP Program v3 PRD (Confluence)
> - Main goal: Business need — from VIP Program v3 PRD
> _(+1 more inferred — see context for full set)_

## User Story
As a logged-in End user on the casino home, I want to see my VIP tier progress, so that I'm motivated to keep playing.

## Description
Add a persistent VIP progress strip below the carousel in `components/home/banner.tsx` for logged-in players. Source: Smartico `LOYALTY_POINTS_UPDATE` event (per PR-481 wiring; per VIP Program v3 PRD, Smartico is source of truth until PS-native VIP API ships in Q4).

## User Flow
```
┌──────────────┐
│ Home loads   │
└──────┬───────┘
       ▼
┌──────────────────────────┐
│ banner.tsx → progress    │
│ strip (Smartico LP_UPD)  │
└──────────────────────────┘
```

## Definition of Done
- Strip renders in `components/home/banner.tsx`, logged-in only
- Points-to-next-tier hydrated from Smartico `LOYALTY_POINTS_UPDATE`
- Aligned with PR-470 visual language
- A11y label set
- Telemetry events fire on render and tap
```

### Handoff
Bet on it via atlassian.

## VERDICT: TB-037
**Title:** Artifact uses Jira component names and file paths verbatim
**SKILL.md ref:** ticket-builder:L178-L184
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | uses-company-terminology (Smartico, PR-470, components/home/banner.tsx, LOYALTY_POINTS_UPDATE) | PASS | All 4 terms verbatim in Description and DoD | — |
| 2 | output-copy-pasteable | PASS | Pure markdown, no shell prompts, no placeholders | — |

### Notes
Company terminology used verbatim. TB-Δ-3 4-bullet cap + overflow line applied (5 fields inferred).

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-038
### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 + PR-481 (Smartico). Confluence VIP v3 PRD (decision: Smartico). Atlassian MCP.

### Phase A — Inferences
(same as TB-037)

### Phase B — Questions asked
none

### Phase C — Follow-ups
1-2 (Module placement, Platform scope)

### Phase D — Artifact (snippet showing inline facts + inline assumptions via TB-Δ-6 syntax)
```
## Description
Add a persistent VIP progress strip below the carousel in `components/home/banner.tsx` (per PR-470 area). Source: Smartico `LOYALTY_POINTS_UPDATE` per PR-481 + Confluence "VIP Program v3 PRD".
> **Assumption:** Existing tier ladder in the PRD applies to this surface. **Flag:** confirm with VIP product owner if changes are pending.
```

No standalone "Facts", "Assumptions", "Missing", or "Open Questions" section.

### Handoff
Bet on it via atlassian.

## VERDICT: TB-038
**Title:** Facts cite source inline; assumptions are marked inline (not in a separate section)
**SKILL.md ref:** ticket-builder:L182
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | facts-cite-source | PASS | "per PR-481 + Confluence 'VIP Program v3 PRD'" cites source inline; `> **Assumption:** ... **Flag:** ...` marks assumption inline | — |
| 2 | output-omits-banned-sections (Facts, Assumptions, Missing, Open Questions) | PASS | No standalone section | — |

### Notes
TB-Δ-6 now defines the exact syntax — "Assumption" + "Flag" inline blockquote within Description or DoD.

### Delta vs v1.0.0
PASS → PASS (unchanged; TB-Δ-6 strengthens the assertion mechanism but doesn't change verdict)

---

## TRACE: TB-039
### Preconditions
User input: "make the lobby better". Jira PR-470 / Casino home redesign / component: home. No MCP.

### Phase A — Inferences
- **Ticket type:** Improvement — "make ... better" → "improve"
- **Main user:** End user — "lobby" (player-facing)
- **Main goal:** Improve UX — "make ... better"
- **Connection:** Extends — "lobby" + PR-470 home context
- **Needs flow diagram:** Not inferred — input too vague; falls through to Phase C fallback

### Phase B — Questions asked
none — 4 core fields inferred (weakly), Needs flow diagram falls through

### Phase C — Follow-ups
Q1 (header: `Lobby focus`): 1) Casino lobby filter bar surfacing (PR-470) / 2) Casino lobby personalization (Smartico if available) / 3) Casino lobby performance (TTI). (PM: Casino lobby filter bar surfacing)
Q2 (header: `Flow?`) per TB-Δ-1 fallback: Yes happy / Yes with branches / No skip. (PM: Yes happy)

### Phase D — Artifact
Title applied directly is a sharpened version (per L181 quality rule):
```markdown
# Improve casino lobby filter bar surfacing

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** improvement, lobby, ux

> **Inferred (not asked):**
> - Ticket type: Improvement — from "make ... better"
> - Connection: Extends — from "lobby" matching PR-470 (home)
> - Main user: End user — from "lobby"
> - Main goal: Improve UX — from "make ... better"

## User Story
As an End user browsing the casino lobby, I want clearer / faster filtering, so that I can find games I want to play.

## Description
Improve the casino lobby filter bar surfacing on /home (continuing PR-470). Specific UX change: prioritize live dealer pills and improve mobile tap targets.

## User Flow
```
┌──────────────┐
│ Open lobby   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Filter bar polished  │
└──────────────────────┘
```

## Definition of Done
- Filter bar a11y + tap targets pass on mobile
- Live dealer pill foregrounded
- No regression on PR-470
```

(No separate "Suggested title" callout or note. Sharper title applied directly. File ends at DoD.)

### Handoff
Hold the chip.

## VERDICT: TB-039
**Title:** Vague input → sharper title applied directly, no separate 'suggested title' note
**SKILL.md ref:** ticket-builder:L181
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | vague-input-suggests-better-title | PASS | Title "Improve casino lobby filter bar surfacing" applied directly; no separate "Suggested title" callout | — |
| 2 | no-meta-commentary-after-final-section (DoD) | PASS | File ends at DoD | — |

### Notes
Sharper title applied directly per L181.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## TRACE: TB-040
### Preconditions
User input: "rebuild the entire casino lobby, payments, KYC, VIP program, and responsible-gaming module for the German market launch". Jira PR-470, PR-602. Confluence: "DE Market Launch — Q4 PRD" / scope: lobby + payments + KYC + VIP + RG. Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "rebuild" / "launch"
- **Main user:** End user — German market launch
- **Main goal:** Business need — "German market launch"
- **Connection:** Mixed — multiple existing flows + new market
- **Needs flow diagram:** Yes — multi-step parent epic flow

### Phase B — Questions asked
none

### Phase C — Follow-ups
none — request is too large for one ticket. Skill flags this above the artifact and proposes a split (per L182).

### Phase D — Artifact
**Above the artifact (one sentence):** "This request is too large for one ticket — proposing a split into 5 child tickets per the DE Market Launch Q4 PRD scope (lobby, payments, KYC, VIP, RG). Below is a parent epic ticket that links to them."

```markdown
# DE Market Launch — parent epic

**Ticket type:** Feature (epic)
**Parent epic (if any):** —
**Component:** cross-cutting (lobby, payments, kyc, vip, rg)
**Labels:** feature, de-launch, epic, q4

> **Inferred (not asked):**
> - Ticket type: Feature — from "rebuild ... for the ... launch"
> - Main user: End user — from "German market launch"
> - Main goal: Business need — from "market launch"
> - Needs flow diagram: Yes — multi-domain epic

## User Story
As an End user in Germany, I want a localized, compliant casino experience, so that I can play within German regulatory expectations.

## Description
Parent epic for the DE Q4 launch, covering 5 child tickets: Lobby DE (scope per PR-470 area), Payments DE (SEPA + GlücksSpiel-compliant methods), KYC DE (SCHUFA + ID verification per GGL), VIP program DE (localized tiers, PR-602 alignment), Responsible Gaming DE (OASIS integration).

## User Flow
```
┌──────────────────────┐
│ DE Q4 launch epic    │
└──────┬───────────────┘
       ▼
┌─ Lobby ─ Payments ─ KYC ─ VIP ─ RG ─┐
└───────────────────────────────────┘
```

## Definition of Done
- 5 child tickets created and linked
- DE Q4 PRD acceptance signed off per child ticket
- Compliance review (GGL) signed off
- Launch readiness checklist complete
```

(Split-proposal sentence is ABOVE the artifact, not in a "Builder notes" section at the end. No "Open Questions" section.)

### Handoff
Bet on it via atlassian (parent epic).

## VERDICT: TB-040
**Title:** Too-large request → one-sentence split proposal ABOVE the artifact, not buried in notes
**SKILL.md ref:** ticket-builder:L182
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | too-large-request-proposes-split | PASS | "Above the artifact (one sentence): 'This request is too large for one ticket — proposing a split into 5 child tickets...'" | — |
| 2 | output-omits-banned-sections (Builder notes, Open Questions) | PASS | No 'Builder notes' or 'Open Questions' section | — |

### Notes
Split proposed in a single sentence above the artifact. The artifact itself stays lean.

### Delta vs v1.0.0
PASS → PASS (unchanged)

---

## END OF RUN
