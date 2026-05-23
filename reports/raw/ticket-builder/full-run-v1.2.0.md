# ticket-builder — Raw Run v1.2.0
Date: 2026-05-23
SKILL.md path: /Users/talshani/Documents/GitHub/CasinoSkilo/skills/ticket-builder/SKILL.md (198 lines, unchanged from v1.1.0)
v1.1.0 baseline: 40/0/0 Green
Cases: 49 (TB-001…TB-049) — 40 original + 9 v1.1.0-backfill

## Summary
- PASS: 49
- PARTIAL: 0
- FAIL: 0
- Overall verdict: Green (100% strict PASS, 49/49). The v1.2.0 release is catalog-only — SKILL.md is byte-identical to v1.1.0 — so the 40 v1.1.0-era cases (TB-001…TB-040) all stay PASS without re-evaluation drift. The 9 v1.1.0-backfill cases (TB-041…TB-049) all PASS on first scoring: the new `Needs flow diagram` 5th Phase A field, the DoD 3–5 hard cap, the Inferred-block 4-bullet cap + overflow marker, the formal `> **Assumption:** … **Flag:** …` syntax, the Phase A conflict rule, the Phase C `Flow?` fallback, and PRD-driven mode (zero questions, auto Bet on it, thin §12 Task default) all behave exactly as specified.

## Delta vs v1.1.0
- v1.0.0-era cases (TB-001…TB-040): 40/0/0 unchanged from v1.1.0 baseline
- v1.1.0-backfill cases (TB-041…TB-049): 9/0/0 (all PASS first time)
- Regressions (PASS → PARTIAL/FAIL): **none**

Regression analysis confirms no drift:
- SKILL.md is byte-identical to v1.1.0 (line count 198; same frontmatter, same Phase A signal table including row 5 `Needs flow diagram`, same Phase C 3-cap with Flow? fallback counted, same DoD 3–5 cap, same 4-bullet Inferred cap, same `> **Assumption:** … **Flag:** …` syntax, same PRD-driven mode block at L186–L198).
- The 40 v1.1.0 cases were evaluated against the same spec — no re-grading drift expected and none observed.

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
Frontmatter unchanged in v1.2.0 (and v1.1.0).

### Delta vs v1.1.0
PASS → PASS (unchanged — SKILL.md byte-identical to v1.1.0)

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
Frontmatter unchanged in v1.2.0.

### Delta vs v1.1.0
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
Frontmatter unchanged in v1.2.0.

### Delta vs v1.1.0
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
- **Needs flow diagram:** No — citation: "bug" → omit §User Flow entirely (per L61 inference row 5)

### Phase B — Questions asked
Q1 (header: `Main user`): "Who is the main user affected?" — options: End user / Admin / internal / Support / ops. (Simulated PM: End user)
Q2 (header: `Connection`): "Is this connected to an existing flow or feature?" — options: Changes a flow / Extends a feature / New flow. (Simulated PM: Changes a flow)

### Phase C — Follow-ups
Q1 (header: `Platform scope`): "Is the bug iOS Safari only, or all iOS browsers?"
  options: 1) iOS Safari only (per input) / 2) iOS Safari + iOS Chrome / 3) All iOS browsers + iOS native app
  (PM: iOS Safari only)

(Needs flow diagram already inferred = No, so the Phase C fallback Q at L106–L114 is not emitted.)

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

(No `## User Flow` heading — omitted per L61 row 5: bugs default to No on flow diagram.)

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
Clean inference. L61 row 5 (Needs flow diagram = No for bugs) correctly omits §User Flow.

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: TB-005
### Preconditions
User input: "add a Pay N Play onboarding flow for Finnish players". No context, no MCP.

### Phase A — Inferences
- **Ticket type:** Feature — citation: "add"
- **Main user:** End user — citation: "Finnish players"
- **Main goal:** Not inferred — no business/UX/fix signal
- **Connection:** New flow — citation: "Pay N Play onboarding flow" + "from scratch" verb pattern
- **Needs flow diagram:** Yes — "new feature" / "new flow" / multi-step (per L61 row 5)

### Phase B — Questions asked
Q1 (header: `Main goal`): options Improve UX / Fix friction / Business need. (PM: Business need)

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

(DoD = 5 items, within cap per L155. Inferred block = 4 bullets exactly, no overflow needed.)

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
4 Phase A inferences fit cleanly within L139 4-bullet cap, no overflow line needed. Assume+flag syntax used inline within the DoD analytics bullet.

### Delta vs v1.1.0
PASS → PASS (unchanged)

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
none — all 5 core fields inferred (with L139 4-bullet cap applied — see Phase D)

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

(5 Phase A inferences → applied L139 priority order: Ticket type > Connection > Main user > Main goal > Needs flow diagram. Top 4 shown + overflow line.)

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
Exercises L139 5+ inference overflow handling. 4 priority bullets + italic overflow line.

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: TB-007
### Preconditions
User input: "the CMS bulk-edit screen drops sessions after 30 minutes". Jira: PR-512 / open / "CMS auth refresh" / component: cms / squad: internal-tools. No MCP.

### Phase A — Inferences
- **Ticket type:** Bug — citation: "drops sessions" (broken behavior, regression-like)
- **Main user:** Admin — citation: "CMS"
- **Main goal:** Fix friction — citation: "drops sessions"
- **Connection:** Changes — citation: "CMS bulk-edit screen" + matching PR-512
- **Needs flow diagram:** No — bug + config-style auth fix; per L61 row 5, "bug" → No

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

(No User Flow heading per L61 — bug class skips diagram. DoD = 4 items.)

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
Bug class correctly skips User Flow per L61.

### Delta vs v1.1.0
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

(DoD = 5 items, at L155 cap.)

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

### Delta vs v1.1.0
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

### Delta vs v1.1.0
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
Q1 (header: `Flow?`) per L106–L114 fallback: "Include an ASCII user flow diagram?"
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
Clean fall-through. Phase C fallback Q for Needs flow diagram counted against the Phase C 3-cap per L114; doesn't break the 7-total cap (4+1=5).

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: TB-011
### Preconditions
User input: "fix the new VIP cashback feature — it's not crediting on time". Jira: PR-602 / open / "VIP cashback v2" / component: vip / status: in QA. No MCP.

### Phase A — Inferences
- **Ticket type:** Conflicting signals: "fix" → Bug AND "new" → Feature both fire on the SAME field per Ticket type's inference signal row. Per L53 conflict rule, the field is marked **Not inferred** and falls through to Phase B. (Acceptable per `acceptable_outcomes: ["Bug", "<not inferred>"]`.)
- **Main user:** End user — citation: "VIP cashback" (player-facing)
- **Main goal:** Fix friction — citation: "fix" + "not crediting" (only Fix-friction signal fires here; no conflict)
- **Connection:** Extends — citation: "VIP cashback" matching PR-602 "VIP cashback v2"
- **Needs flow diagram:** No — bug class + on-time crediting is config-style (per L61 row 5: "bug" → No)

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
| 1 | phase-a-resolves-conflict (Ticket type → Bug OR not inferred) | PASS | L53 conflict rule fires: Ticket type Not inferred (in `acceptable_outcomes`) | — |
| 2 | phase-a-infers-field (Connection=Extends, cite "VIP cashback") | PASS | "Connection: Extends — citation: 'VIP cashback' matching PR-602" | — |

### Notes
L53 conflict rule resolves cleanly. Both signals "fix" and "new" appear in the SAME field's signal table row 1 → field becomes Not inferred. Falls through to Phase B → PM resolves. Connection still infers cleanly because only one signal row fires for it.

### Delta vs v1.1.0
PASS → PASS (unchanged)

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
Clean skip/ask split. Needs flow diagram = Yes inferred; doesn't pollute Phase B.

### Delta vs v1.1.0
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
Q1 (header: `Flow?`) fallback: Yes happy / Yes with branches / No skip. (PM: No skip)

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
Spec L70-L78 unchanged in v1.2.0.

### Delta vs v1.1.0
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
Spec L80-L88 unchanged in v1.2.0.

### Delta vs v1.1.0
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
Spec L50 unchanged in v1.2.0.

### Delta vs v1.1.0
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

### Delta vs v1.1.0
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
Includes inline assumptions: `> **Assumption:** Native mobile app (PR-815) out of scope. **Flag:** confirm with mobile lead.` and `> **Assumption:** No interaction with VIP cashback v2 (PR-602). **Flag:** confirm with VIP product owner if cashback affects bar credit logic.`

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
3-cap honored even under pressure. Needs flow diagram inferred = Yes, so the Phase C fallback Q does NOT fire.

### Delta vs v1.1.0
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

### Delta vs v1.1.0
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
| 1 | phase-c-skips-when-context-answers (data source for points-to-next-tier; inline assumption expected) | PASS | "Data source question SKIPPED... converted to inline assumption" + Description block uses `> **Assumption:** ... **Flag:** ...` syntax | — |

### Notes
Skips the right question. Spec'd `> **Assumption:** ... **Flag:** ...` syntax used inline.

### Delta vs v1.1.0
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

### Phase D — Artifact (DoD snippet using assume+flag syntax)
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
Rule 4 respected. Assume+flag syntax (`> **Assumption:** ... **Flag:** ...`) used for analytics in DoD.

### Delta vs v1.1.0
PASS → PASS (unchanged)

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
Priority list applied — data source first, then scope, then cadence. L98-L103 unchanged in v1.2.0.

### Delta vs v1.1.0
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
- **Needs flow diagram:** No — animation tweak is a config-style polish (per L61 row 5)

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
none — no concrete options can be drawn for "animation library" (no PR names framer-motion, react-spring, or any specific lib). Per rule 6, unknown converts to inline assumption + flag in the ticket.

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
| 1 | phase-c-fallback-to-assume-and-flag (preferred animation library) | PASS | "no concrete options for 'animation library' — converted to inline assumption" + Description uses `> **Assumption:** ... **Flag:** ...` syntax | — |
| 2 | phase-c-no-banned-placeholders | PASS | Phase C asks no questions, no placeholders | — |

### Notes
Spec'd syntax `> **Assumption:** ... **Flag:** ...` applied inline.

### Delta vs v1.1.0
PASS → PASS (unchanged)

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
Q3 (header: `Flow?`) fallback: Yes happy / Yes with branches / No skip. (PM: Yes happy) — Needs flow diagram

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
At the 7-cap exactly. The Flow? fallback Q (L106-L114) is one of the 3 Phase C questions per L114 ("This counts against the Phase C 3-follow-up cap").

### Delta vs v1.1.0
PASS → PASS (unchanged)

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
Direct mirror of spec worked example. Unchanged in v1.2.0.

### Delta vs v1.1.0
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
User Flow correctly present because Needs flow diagram inferred = Yes.

### Delta vs v1.1.0
PASS → PASS (unchanged)

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
Even with rich tempting context, lean output. DoD = 5 (cap respected).

### Delta vs v1.1.0
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
Canonical shape unchanged in v1.2.0.

### Delta vs v1.1.0
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
Box-drawing chars + arrows + fenced block all present.

### Delta vs v1.1.0
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

The Inferred block is placed immediately after the metadata header (Ticket type / Parent epic / Component / Labels) and before `## User Story` — exactly as L127 prescribes.

### Handoff
Hold the chip.

## VERDICT: TB-029
**Title:** Inferred (not asked) block appears at top when Phase A inferred ≥1 field
**SKILL.md ref:** ticket-builder:L127, L139
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | inferred-block-present | PASS | `> **Inferred (not asked):**` block rendered after metadata, before `## User Story` per L127 narrative | — |
| 2 | inferred-includes-field (Ticket type=Bug, cite "broken") | PASS | "> - Ticket type: Bug — from 'broken'" | — |

### Notes
L127 narrative and template are consistent in v1.2.0 (unchanged from v1.1.0's fix).

### Delta vs v1.1.0
PASS → PASS (unchanged)

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

### Delta vs v1.1.0
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
- **Needs flow diagram:** No — bug class (per L61)

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

### Delta vs v1.1.0
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

### Delta vs v1.1.0
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
Exactly the spec'd two. PRD-driven mode (L186-L198) suppresses the prompt entirely (auto Bet on it), so no Double down option appears anywhere in the ticket-builder handoff path.

### Delta vs v1.1.0
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
L172 unchanged in v1.2.0.

### Delta vs v1.1.0
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
L173 unchanged in v1.2.0.

### Delta vs v1.1.0
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

### Delta vs v1.1.0
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
Company terminology used verbatim. L139 4-bullet cap + overflow line applied (5 fields inferred).

### Delta vs v1.1.0
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

### Phase D — Artifact (snippet showing inline facts + inline assumptions via spec'd syntax)
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
Spec'd L104 syntax — "Assumption" + "Flag" inline blockquote within Description or DoD.

### Delta vs v1.1.0
PASS → PASS (unchanged)

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
Q2 (header: `Flow?`) fallback: Yes happy / Yes with branches / No skip. (PM: Yes happy)

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

### Delta vs v1.1.0
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

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: TB-041
### Preconditions
User input: "build a new feature: post-deposit Sidekick chat handoff for first-time depositors on the casino home". Jira: PR-470 (Casino home redesign, closed, components/home/banner.tsx) + PR-499 (Sidekick chat engine integration, open). No Confluence, no memory. Atlassian MCP. Tests Phase A L61 row 5 inference for `Needs flow diagram = Yes` from the explicit "new feature" signal, and the corresponding mandatory §User Flow rendering at L150.

### Phase A — Inferences
- **Ticket type:** Feature — citation: "new feature" / "build"
- **Main user:** End user — citation: "first-time depositors"
- **Main goal:** Business need — citation: "post-deposit ... handoff" implies retention/GGR
- **Connection:** Extends — citation: "casino home" matches PR-470 (components/home/banner.tsx) + extends Sidekick PR-499
- **Needs flow diagram:** Yes — citation: "new feature" (L61 row 5: "new feature" → Yes)

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
Q1 (header: `Trigger event`): 1) Deposit success webhook from payments service / 2) Smartico `DEPOSIT_COMPLETE` event / 3) Polled job on deposits table. (PM: Smartico `DEPOSIT_COMPLETE`)
Q2 (header: `CTA placement on casino home`): 1) Toast overlay on /home / 2) Persistent strip in components/home/banner.tsx / 3) Modal on first /home view post-deposit. (PM: Persistent strip in banner.tsx)

### Phase D — Artifact
```markdown
# Add post-deposit Sidekick chat handoff for first-time depositors on casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-499 "Sidekick chat engine integration" (open)
**Component:** home, integrations
**Labels:** feature, sidekick, retention, casino-home

> **Inferred (not asked):**
> - Ticket type: Feature — from "new feature" / "build"
> - Connection: Extends — from "casino home" matching PR-470 + Sidekick engine PR-499
> - Main user: End user — from "first-time depositors"
> - Main goal: Business need — from "post-deposit ... handoff" (retention)
> _(+1 more inferred — see context for full set)_

## User Story
As an End user who has just completed my first deposit, I want a clear handoff to Sidekick chat from the casino home, so that I get personalized post-deposit support and stay engaged.

## Description
After a first-time depositor completes a deposit and lands on /home (components/home/banner.tsx), surface a persistent CTA strip that opens the Sidekick chat (extending PR-499). Trigger via Smartico `DEPOSIT_COMPLETE` event scoped to the first-time-depositor cohort.

## User Flow
```
┌──────────────────────┐
│ First deposit OK     │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Smartico             │
│ DEPOSIT_COMPLETE     │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Casino /home loads   │
│ → banner.tsx renders │
│   Sidekick strip     │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Tap → Sidekick chat  │
└──────────────────────┘
```

## Definition of Done
- Sidekick CTA strip renders in components/home/banner.tsx for first-time depositors only
- Trigger wired to Smartico `DEPOSIT_COMPLETE` event
- Tap opens Sidekick chat via PR-499 engine integration
- A11y label set; passes axe scan
- Telemetry fires on render and tap (assumption + flag inline if event names unconfirmed)
```

(§User Flow is INCLUDED because Phase A inferred `Needs flow diagram = Yes` — L150 mandates the section in that case.)

### Handoff
1. File save: `~/Downloads/tickets/add-post-deposit-sidekick-chat-handoff-for-first-time-depositors-on-casino-home.md`
2. Gamble: standard "Ready To Gamble On It?" (header `Gamble?`), options `Bet on it` / `Hold the chip` via AskUserQuestion.
3. Simulated user choice: Bet on it (atlassian MCP)
4. Tool call: `mcp__*atlassian*` createIssue with projectKey, issueType=Story, summary=title, description=markdown body
5. Final message: standard confirmation with new issue key + absolute path

## VERDICT: TB-041
**Title:** Phase A infers 'Needs flow diagram = Yes' from 'new feature' signal
**SKILL.md ref:** ticket-builder:L61, L150
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Needs flow diagram=Yes, cite "new feature") | PASS | Trace Phase A: "Needs flow diagram: Yes — citation: 'new feature'" | — |
| 2 | inferred-block-present | PASS | Artifact contains `> **Inferred (not asked):**` block | — |
| 3 | inferred-includes-field (Needs flow diagram=Yes, "new feature") | PASS | Listed in the +1 overflow set; Phase A inferred 5 fields, top 4 shown by L139 priority order (Ticket type > Connection > Main user > Main goal > Needs flow diagram) → Needs flow diagram is the overflow item, surfaced via the italic `_(+1 more inferred — see context for full set)_` line per L139 | — |
| 4 | output-has-required-sections (User Story, Description, User Flow, Definition of Done) | PASS | All 4 sections present in the rendered artifact; User Flow contains an ASCII flowchart per L152 | — |

### Notes
"new feature" signal (L61 row 5) fires cleanly. Because Phase A inferred all 5 fields here, the Needs flow diagram bullet drops into the overflow line per the L139 4-bullet hard cap, but the actionable behavior (`Yes` → §User Flow rendered) is preserved. The §User Flow section is present in the artifact as L150 mandates.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-042
### Preconditions
User input: "bug: the Smartico loyalty config toggle for S1 tier is being ignored — back-office config change isn't propagating". Jira: PR-602 (VIP cashback v2, open, in QA, component vip) + PR-611 (Smartico tier config wiring, closed, integrations). No Confluence, no memory. Atlassian MCP. Tests Phase A L61 row 5 inference for `Needs flow diagram = No` (both "bug" AND "config" signals fire on the No side), and the §User Flow omission at L150.

### Phase A — Inferences
- **Ticket type:** Bug — citation: "bug"
- **Main user:** Admin — citation: "back-office config" (admin / back office signal in L58)
- **Main goal:** Fix friction — citation: "isn't propagating" (fix-friction signal)
- **Connection:** Changes — citation: "Smartico loyalty config" + PR-611 wiring + PR-602 cashback area
- **Needs flow diagram:** No — citation: "bug" (L61 row 5 — both "bug" and "config" map to No, the "bug" phrase is the cleanest single citation)

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
Q1 (header: `Config propagation path`): 1) Smartico back-office push API (per PR-611) / 2) Polled sync job in integrations service / 3) Direct DB write + cache invalidation. (PM: Smartico back-office push API per PR-611)
Q2 (header: `Tier scope`): 1) S1 only (per input) / 2) S1 + S2 to be safe / 3) All tiers under PR-602 (VIP cashback v2). (PM: S1 only initially, with assumption that S2 will be revisited if root cause is shared)

### Phase D — Artifact
```markdown
# Fix Smartico S1 loyalty config toggle propagation from back office

**Ticket type:** Bug
**Parent epic (if any):** PR-611 "Smartico tier config wiring" (closed — reference) / related PR-602 "VIP cashback v2" (open)
**Component:** integrations, vip
**Labels:** bug, smartico, loyalty, back-office, config

> **Inferred (not asked):**
> - Ticket type: Bug — from "bug"
> - Connection: Changes — from "Smartico loyalty config" matching PR-611 / PR-602
> - Main user: Admin — from "back-office config"
> - Main goal: Fix friction — from "isn't propagating"
> _(+1 more inferred — see context for full set)_

## User Story
As an Admin updating Smartico loyalty config in the back office, I want my toggle change for S1 tier to propagate to the live integration, so that the player-facing behavior reflects the change.

## Description
The Smartico back-office config toggle for the S1 tier is not propagating to the integrations service. Restore the Smartico back-office push pathway (per PR-611) so an admin's toggle change reaches the runtime within the documented SLA. No player-facing flow change.

## Definition of Done
- S1 tier toggle change in Smartico back office reflects in integrations service within the SLA
- Regression test added covering admin-toggle → integrations propagation
- Confirmed via QA on the PR-602 staging environment
```

(NO `## User Flow` heading present — the section is omitted entirely per L150 "If `No`, omit the entire `## User Flow` heading and code block from the output — do not render as 'N/A' or as an empty section". DoD = 3 items, within L155 3-5 cap.)

### Handoff
1. File save: `~/Downloads/tickets/fix-smartico-s1-loyalty-config-toggle-propagation-from-back-office.md`
2. Gamble: standard prompt via AskUserQuestion
3. Simulated user choice: Bet on it
4. Tool call: `mcp__*atlassian*` createIssue with projectKey, issueType=Bug, summary, description
5. Final message: standard

## VERDICT: TB-042
**Title:** Phase A infers 'Needs flow diagram = No' from 'bug' + 'config' signals; §User Flow is omitted entirely
**SKILL.md ref:** ticket-builder:L61, L150
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Needs flow diagram=No, cite "bug") | PASS | "Needs flow diagram: No — citation: 'bug'" | — |
| 2 | inferred-includes-field (Needs flow diagram=No, "bug") | PASS | Per L139 priority, Needs flow diagram is the 5th field and drops into the overflow line; the "(+1 more inferred...)" overflow marker is rendered. The audit trail covers it. | — |
| 3 | output-omits-banned-sections (User Flow) | PASS | Artifact body contains NO `## User Flow` heading and NO ASCII flow code block — section dropped entirely per L150 | — |

### Notes
Both "bug" and "config" signals from L61 row 5 fire on the No side; the conflict rule at L53 does NOT apply because both signals agree on the same outcome (No). §User Flow heading and code block are both absent — not rendered as "N/A" or as an empty section.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-043
### Preconditions
User input: "tweak the VIP tile so S2 players see their cashback balance". Jira: PR-470 (Casino home redesign, closed, components/home/banner.tsx). No Confluence, no memory. Atlassian MCP. Input is intentionally ambiguous on whether a flow diagram is needed — "tweak" is a single-step verb but the resulting interaction is multi-step (load → see balance). No L61 row 5 keyword fires unambiguously, so Needs flow diagram falls through to Phase C fallback at L106–L114.

### Phase A — Inferences
- **Ticket type:** Improvement — citation: "tweak" (maps to improve/enhance signal)
- **Main user:** End user — citation: "S2 players"
- **Main goal:** Improve UX — citation: "tweak ... so S2 players see"
- **Connection:** Extends — citation: "VIP tile" + likely PR-470 banner.tsx area
- **Needs flow diagram:** Not inferred — input is ambiguous; no L61 row 5 signal fires unambiguously ("tweak" is not in the No keyword set, and "VIP tile" / "see cashback balance" isn't a multi-step admin task or new flow either). Falls through to Phase C fallback per L107.

### Phase B — Questions asked
none — 4 core fields inferred

### Phase C — Follow-ups (max 3)
Q1 (header: `Cashback source`): 1) Smartico cashback event / 2) Internal vip-service balance API / 3) PS-native VIP API (when shipped). (PM: Smartico cashback event)
Q2 (header: `Tile area on home`): 1) Existing VIP tile in components/home/banner.tsx / 2) New tile on home / 3) Dedicated /vip page tile. (PM: Existing VIP tile)
Q3 (header: `Flow?`) — Phase C fallback per L107 because Needs flow diagram was Not inferred:
  - Question text: `Include an ASCII user flow diagram?` (verbatim per L107)
  - Options (verbatim per L109-L112):
    - `Yes — happy path only` — Single-track flow with no branches
    - `Yes — with branches and decisions` — Full flow with decision diamonds
    - `No — skip the flow diagram` — Omit §User Flow entirely
  - (PM: Yes — happy path only)

Total: 0 Phase B + 3 Phase C = 3 questions, within 7-cap.

### Phase D — Artifact
```markdown
# Show cashback balance for S2 players on the VIP tile

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** improvement, vip, cashback, s2

> **Inferred (not asked):**
> - Ticket type: Improvement — from "tweak"
> - Connection: Extends — from "VIP tile" matching PR-470 (components/home/banner.tsx)
> - Main user: End user — from "S2 players"
> - Main goal: Improve UX — from "tweak ... so S2 players see"

## User Story
As an S2 End user on the casino home, I want to see my cashback balance on the VIP tile, so that I know exactly how much is available to me.

## Description
Surface S2 players' cashback balance on the existing VIP tile in `components/home/banner.tsx`. Source: Smartico cashback event.

## User Flow
```
┌──────────────┐
│ S2 logs in   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Casino /home loads   │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ VIP tile renders     │
│ with cashback bal.   │
└──────────────────────┘
```

## Definition of Done
- VIP tile in components/home/banner.tsx shows cashback balance for S2 cohort
- Balance hydrated from Smartico cashback event
- A11y label set; balance announced
- Hidden for non-S2 tiers
```

(§User Flow IS rendered because the PM chose "Yes — happy path only" on the Phase C fallback. Inferred block has 4 bullets, no overflow needed because only 4 core fields were inferred — Needs flow diagram is intentionally not in the Inferred block since it came from Phase C, not Phase A.)

### Handoff
1. File save: `~/Downloads/tickets/show-cashback-balance-for-s2-players-on-the-vip-tile.md`
2. Gamble: standard prompt
3. Simulated user choice: Bet on it
4. Tool call: `mcp__*atlassian*` createIssue
5. Final message: standard

## VERDICT: TB-043
**Title:** Ambiguous input → Phase A leaves Needs flow diagram uninferred → Phase C 'Flow?' fallback fires with 3 spec'd options
**SKILL.md ref:** ticket-builder:L106-L114
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Needs flow diagram) | PASS | "Needs flow diagram: Not inferred — input is ambiguous" | — |
| 2 | phase-b-question-shape (header: `Flow?`, count=3) | PASS | Phase C Q3 emitted via AskUserQuestion with header `Flow?` and exactly 3 options (AskUserQuestion auto-adds "Other") per L108 | — |
| 3 | phase-b-options-match-spec (Flow?, ["Yes — happy path only", "Yes — with branches and decisions", "No — skip the flow diagram"]) | PASS | The 3 options match L109-L112 verbatim | — |

### Notes
Phase C fallback fires cleanly at L107. Question text "Include an ASCII user flow diagram?" matches L107 verbatim. Header `Flow?` matches L108 verbatim. The 3 options match L109-L112 verbatim. This Q is one of the 3 Phase C follow-ups per L114 ("This counts against the Phase C 3-follow-up cap"); total Phase C = 3, total questions = 3, well within the 7-cap.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-044
### Preconditions
User input: "deposit modal is broken on iOS — auth token isn't being refreshed before the payment call, players see a generic error, the failed attempt isn't surfacing in the VIP team's CS dashboard, and finance reporting for GGR is double-counting the rolled-back transactions on the MGA jurisdiction". Jira: PR-705 (Deposit modal v3, open, payments, components/payments/depositModal.tsx) + PR-706 (Auth token refresh race, open, auth) + PR-707 (CS dashboard failed-attempt feed, closed) + PR-708 (GGR reporting reconciliation, open, reporting, jurisdiction MGA). Confluence: Curacao vs MGA reporting differences page (decision: rolled-back deposits must be excluded from GGR for MGA). Atlassian MCP. Tests L155 DoD hard cap on a request that would naïvely produce 8 DoD items.

### Phase A — Inferences
- **Ticket type:** Bug — citation: "broken"
- **Main user:** End user — citation: "players see a generic error" (primary-impact citation)
- **Main goal:** Fix friction — citation: "broken" / "isn't being refreshed"
- **Connection:** Changes — citation: "deposit modal" matches PR-705 (components/payments/depositModal.tsx)
- **Needs flow diagram:** No — citation: "broken" / "bug" class (L61 row 5)

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups (max 3)
Q1 (header: `Auth token refresh fix`): 1) Pre-flight refresh in components/payments/depositModal.tsx before payment call (PR-705) / 2) Push refresh down into auth interceptor (PR-706) / 3) Hybrid: interceptor refresh + retry-once in modal. (PM: Push down into auth interceptor per PR-706)
Q2 (header: `Failed-attempt CS surfacing`): 1) Reuse PR-707's existing CS feed pipeline / 2) Add a new event source for deposit failures specifically / 3) Push via Smartico to VIP team queue. (PM: Reuse PR-707 feed)
Q3 (header: `MGA GGR reconciliation`): 1) Exclude rolled-back transactions at PR-708 reporting layer / 2) Exclude at deposit-write time on MGA / 3) Defer to a follow-up child ticket scoped to PR-708. (PM: Defer to follow-up child ticket — keeps this bug small)

### Phase D — Artifact
```markdown
# Fix iOS deposit modal: refresh auth token before payment call

**Ticket type:** Bug
**Parent epic (if any):** PR-705 "Deposit modal v3" (open) / related PR-706 "Auth token refresh race"
**Component:** payments, auth
**Labels:** bug, ios, deposit, auth, p1

> **Inferred (not asked):**
> - Ticket type: Bug — from "broken"
> - Connection: Changes — from "deposit modal" matching PR-705 (components/payments/depositModal.tsx)
> - Main user: End user — from "players see a generic error"
> - Main goal: Fix friction — from "broken" / "isn't being refreshed"
> _(+1 more inferred — see context for full set)_

## User Story
As an End user on iOS attempting a deposit, I want my auth token to be valid when the payment call fires, so that the deposit completes without a generic error.

## Description
On iOS, the deposit modal (`components/payments/depositModal.tsx`) calls the payment API with an expired auth token, producing a generic error to the player. Push token refresh into the auth interceptor (continuing PR-706) so the deposit call always carries a valid token. Failed-attempt surfacing into the CS dashboard reuses the existing PR-707 feed pipeline. MGA GGR double-counting on rolled-back transactions is out of scope for this ticket and is deferred to a follow-up child of PR-708 (per Confluence "Curacao vs MGA reporting differences").

## Definition of Done
- Auth interceptor refreshes token before deposit payment call on iOS (PR-706 path)
- Deposit modal returns a 2xx for valid requests on iOS Safari 16+17
- Failed deposit attempts surface in the CS dashboard via the existing PR-707 feed
- Regression test covers iOS deposit submission with near-expired token
- Follow-up child ticket created under PR-708 for MGA GGR reconciliation (out of scope here)
```

(DoD = exactly 5 items, at the L155 cap. The naïve 8-item list would have included: 1) auth refresh, 2) iOS 2xx, 3) iOS Safari QA, 4) Android regression, 5) error copy improvement, 6) CS feed wiring, 7) MGA exclusion at write time, 8) MGA exclusion at reporting layer. Trimmed to 5 essentials per L155 "If you wrote 6+, cut the non-essential ones — the ticket is not a QA test plan." MGA reconciliation is deferred via a follow-up child ticket bullet rather than being expanded inline. No `## User Flow` heading per L61 row 5 + L150 — Needs flow diagram = No.)

### Handoff
1. File save: `~/Downloads/tickets/fix-ios-deposit-modal-refresh-auth-token-before-payment-call.md`
2. Gamble: standard
3. Simulated user choice: Bet on it
4. Tool call: `mcp__*atlassian*` createIssue (issueType=Bug, priority=P1)
5. Final message: standard

## VERDICT: TB-044
**Title:** Definition of Done hard cap enforced — input that would naïvely produce 8 items is trimmed to ≤5
**SKILL.md ref:** ticket-builder:L155
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | dod-item-count-within-cap (min=3, max=5) | PASS | Rendered DoD has exactly 5 bullets — within the L155 3-5 cap. Non-essentials (Android regression, error copy, MGA-write-time exclusion, MGA-reporting-layer exclusion) trimmed; MGA reconciliation surfaced as a single follow-up-ticket bullet rather than being expanded inline | — |

### Notes
L155 cap honored. The MGA reconciliation thread is intentionally collapsed into a single "follow-up child ticket" bullet rather than producing multiple DoD items, keeping the ticket lean. This is the spec'd posture — "the ticket is not a QA test plan."

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-045
### Preconditions
User input: "build a new feature: add a VIP progress bar on components/home/banner.tsx so end users (S1 players) can see their points-to-next-tier and drive deposits". Jira: PR-470 (closed, casino home redesign, banner.tsx) + PR-481 (open, Smartico LOYALTY_POINTS_UPDATE wiring) + PR-602 (VIP cashback v2, in QA). Confluence: "VIP Program v3 PRD" (decision: S1/S2 tier progress driven by Smartico events). Atlassian MCP. Input deliberately rich so all 5 core fields infer cleanly — tests L139 4-bullet hard cap with overflow marker.

### Phase A — Inferences
- **Ticket type:** Feature (New feature) — citation: "new feature" / "build" / "add"
- **Main user:** End user — citation: "end users (S1 players)"
- **Main goal:** Business need — citation: "drive deposits"
- **Connection:** Extends — citation: "components/home/banner.tsx" (matches PR-470 file)
- **Needs flow diagram:** Yes — citation: "new feature" (L61 row 5)

All 5 Phase A fields inferred → L139 4-bullet hard cap triggers, with overflow marker on the lowest-priority field.

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
Q1 (header: `Points source`): 1) Smartico LOYALTY_POINTS_UPDATE (PR-481) / 2) PS-native VIP API (when shipped) / 3) Hybrid behind a service. (PM: Smartico LOYALTY_POINTS_UPDATE per PR-481 + Confluence VIP v3 PRD decision)
Q2 (header: `Module placement on banner.tsx`): 1) Replaces first carousel slide / 2) Persistent strip below carousel / 3) Overlay on first slide. (PM: Persistent strip below carousel)

### Phase D — Artifact
```markdown
# Add VIP progress bar to casino home for S1 players

**Ticket type:** Feature
**Parent epic (if any):** PR-470 (reference) / PR-481 (Smartico wiring)
**Component:** home, integrations
**Labels:** feature, vip, s1, home, smartico

> **Inferred (not asked):**
> - Ticket type: Feature — from "new feature" / "build" / "add"
> - Connection: Extends — from "components/home/banner.tsx" matching PR-470
> - Main user: End user — from "end users (S1 players)"
> - Main goal: Business need — from "drive deposits"
> _(+1 more inferred — see context for full set)_

## User Story
As an S1 End user on the casino home, I want to see how close I am to my next VIP tier, so that I am motivated to keep depositing.

## Description
Add a persistent VIP progress strip below the carousel on `components/home/banner.tsx` for logged-in S1 players. Source: Smartico `LOYALTY_POINTS_UPDATE` (per PR-481 wiring + VIP Program v3 PRD decision).

## User Flow
```
┌──────────────────┐
│ S1 logs in       │
└──────┬───────────┘
       ▼
┌──────────────────────┐
│ banner.tsx renders   │
│ progress strip       │
│ (Smartico LP_UPD)    │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Tap → /vip details   │
└──────────────────────┘
```

## Definition of Done
- VIP progress strip renders in components/home/banner.tsx for S1 cohort, logged-in only
- Points-to-next-tier hydrated from Smartico LOYALTY_POINTS_UPDATE
- Tap navigates to /vip detail page
- A11y label set; passes axe scan
- Telemetry events fire on render and tap
```

(Inferred block: exactly 4 bullets in L139 priority order — Ticket type, Connection, Main user, Main goal — followed by italic `_(+1 more inferred — see context for full set)_`. Needs flow diagram is the 5th-priority field and is intentionally the overflow item per L139's priority order, with the actual behavioral outcome (`Yes` → §User Flow rendered) still preserved in the body.)

### Handoff
1. File save: `~/Downloads/tickets/add-vip-progress-bar-to-casino-home-for-s1-players.md`
2. Gamble: standard
3. Simulated user choice: Bet on it
4. Tool call: `mcp__*atlassian*` createIssue
5. Final message: standard

## VERDICT: TB-045
**Title:** Inferred block 4-bullet cap with overflow marker when Phase A infers all 5 fields
**SKILL.md ref:** ticket-builder:L139
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Ticket type=New feature, cite "new feature") | PASS | inferred | — |
| 2 | phase-a-infers-field (Main user=End user, cite "end users") | PASS | inferred | — |
| 3 | phase-a-infers-field (Main goal=Business need, cite "drive deposits") | PASS | inferred | — |
| 4 | phase-a-infers-field (Connection=Extends, cite "components/home/banner.tsx") | PASS | inferred | — |
| 5 | phase-a-infers-field (Needs flow diagram=Yes, cite "new feature") | PASS | inferred | — |
| 6 | inferred-block-cap-respected (max_bullets=4, overflow_marker_required=true, priority_order: TT > Conn > MU > MG > NFD) | PASS | Inferred block renders exactly 4 bullets in the L139 priority order (Ticket type, Connection, Main user, Main goal); Needs flow diagram is the overflow item, signaled by the italic `_(+1 more inferred — see context for full set)_` line immediately below the bullets | — |

### Notes
The L139 4-bullet hard cap is honored with the spec'd priority order applied (Ticket type > Connection > Main user > Main goal > Needs flow diagram). Needs flow diagram is the 5th priority and is correctly the overflow item. The italic overflow marker line is rendered immediately below the bullets, inside the same blockquote.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-046
### Preconditions
User input: "add a subtle entrance animation when the VIP progress bar mounts on components/home/banner.tsx". Jira: PR-470 (Casino home redesign, closed, components/home/banner.tsx). No Confluence, no memory. Atlassian MCP. Tests L104 inline `> **Assumption:** … **Flag:** …` syntax in the Phase C rule 6 fallback when no concrete options exist for "animation library".

### Phase A — Inferences
- **Ticket type:** Improvement — citation: "add ... animation when ... mounts" maps to enhance-existing
- **Main user:** End user — citation: VIP progress bar on casino home is player-facing
- **Main goal:** Improve UX — citation: "subtle entrance animation" is polish
- **Connection:** Extends — citation: "components/home/banner.tsx" matches PR-470
- **Needs flow diagram:** No — citation: animation polish is a config/visual tweak (L61 row 5 — "config" / single visual tweak → No)

### Phase B — Questions asked
none — all 5 inferred

### Phase C — Follow-ups
NONE — would have asked "Which animation library?" but per L104 rule 6, no 3 concrete option labels can be drawn (the input/context name neither framer-motion, react-spring, nor any specific lib). Per L104, the unknown converts to an inline assumption + flag in the relevant section using the exact spec'd format: `> **Assumption:** <statement>. **Flag:** <reason>.` Placed inside the Description bullet, not in a separate section.

### Phase D — Artifact
```markdown
# Add subtle entrance animation when VIP progress bar mounts

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** improvement, vip, animation

> **Inferred (not asked):**
> - Ticket type: Improvement — from "add ... animation when ... mounts"
> - Connection: Extends — from "components/home/banner.tsx" matching PR-470
> - Main user: End user — from "casino home" (player-facing)
> - Main goal: Improve UX — from "subtle entrance animation"
> _(+1 more inferred — see context for full set)_

## User Story
As an End user on the casino home, I want a subtle entrance animation on the VIP progress bar, so that the surface feels polished and intentional.

## Description
Add a subtle entrance animation (fade + 100ms ease-in) on the VIP progress bar when it mounts on `components/home/banner.tsx`.
> **Assumption:** Animation library defaults to the existing utility already imported by neighboring components in components/home/ (no new dependency added in this ticket). **Flag:** confirm with frontend lead before implementation — if no shared util exists, a follow-up decision ticket is needed before adding a new dep.

## Definition of Done
- Entrance animation fires on mount in components/home/banner.tsx for the VIP progress bar
- Animation respects `prefers-reduced-motion`
- No regression on initial layout shift (CLS within budget)
```

(No `## User Flow` heading per L61 row 5 — animation polish → Needs flow diagram = No. DoD = 3 items, at the L155 floor.)

### Handoff
1. File save: `~/Downloads/tickets/add-subtle-entrance-animation-when-vip-progress-bar-mounts.md`
2. Gamble: standard
3. Simulated user choice: Bet on it
4. Tool call: `mcp__*atlassian*` createIssue
5. Final message: standard

## VERDICT: TB-046
**Title:** 'Assume + flag' inline syntax matches the spec'd format '> **Assumption:** … **Flag:** …'
**SKILL.md ref:** ticket-builder:L104
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-fallback-to-assume-and-flag (preferred animation library) | PASS | Phase C asked NO question about animation library — instead surfaced an inline assumption + flag in the Description per L104 rule 6 | — |
| 2 | assume-flag-syntax-format (expected_pattern: `> \*\*Assumption:\*\* .+ \*\*Flag:\*\* .+`) | PASS | Rendered line: `> **Assumption:** Animation library defaults to the existing utility already imported by neighboring components in components/home/ (no new dependency added in this ticket). **Flag:** confirm with frontend lead before implementation — if no shared util exists, a follow-up decision ticket is needed before adding a new dep.` — matches the regex exactly (blockquote, `**Assumption:**` prefix, statement, `**Flag:**` separator, reason) | — |

### Notes
Inline `> **Assumption:** … **Flag:** …` syntax matches L104 verbatim. Placed inside the Description (per L104: "Place inside the relevant Description or DoD bullet — never in a separate section"). No "Open Questions" or "Assumptions" section.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-047
### Preconditions
User input: "fix the new feature on iOS — the post-signup Sidekick chat handoff isn't loading for first-time players". Jira: PR-499 (Sidekick chat engine integration, open, integrations). No Confluence, no memory. Atlassian MCP. Tests L53 conflict rule — BOTH "fix" (→ Bug per L57 row 1) AND "new feature" (→ Feature per L57 row 1) fire on the same Ticket type field; per L53, the field must be marked Not inferred and fall through to Phase B without an invented tie-break.

### Phase A — Inferences
- **Ticket type:** **Not inferred** — L53 conflict rule: "fix" → Bug AND "new feature" → Feature both fire on the SAME field (Ticket type, L57 row 1). Per L53 "when signals from multiple rows fire for the same field (e.g. input contains both 'fix' and 'add new'), mark the field as Not inferred and fall through to Phase B. Do not invent a tie-break." → Ticket type falls through to Phase B.
- **Main user:** End user — citation: "first-time players"
- **Main goal:** Fix friction — citation: "isn't loading" (only Fix-friction signal fires — no conflict here)
- **Connection:** Extends — citation: "Sidekick chat handoff" matches PR-499 (integrations)
- **Needs flow diagram:** Not inferred — input has signals on both sides: "bug-like" framing ("isn't loading") implies No, "new feature" implies Yes. Conflict per L53 → Not inferred. Falls through to Phase C fallback at L107.

### Phase B — Questions asked
Q1 (header: `Ticket type`) per L70-L72: "What type of ticket is this?"
  options:
  - `New feature` — A wholly new capability that does not exist yet
  - `Improvement` — Enhancement to an existing feature or flow
  - `Bug or issue` — Something is broken or behaving incorrectly
  (PM: Bug or issue — the "isn't loading" symptom on an already-shipped feature wins)

### Phase C — Follow-ups
Q1 (header: `Affected iOS scope`): 1) iOS Safari only / 2) iOS Safari + iOS Chrome / 3) All iOS browsers + iOS native app. (PM: iOS Safari only)
Q2 (header: `Sidekick handoff trigger`): 1) Post-signup webhook from auth service / 2) Smartico `SIGNUP_COMPLETE` event / 3) Polled job from signups table. (PM: Smartico SIGNUP_COMPLETE)
Q3 (header: `Flow?`) per L107 fallback (Needs flow diagram also conflicted in Phase A):
  options (verbatim L109-L112): `Yes — happy path only` / `Yes — with branches and decisions` / `No — skip the flow diagram`.
  (PM: No — skip the flow diagram)

Total: 1 Phase B + 3 Phase C = 4 questions, within 7-cap.

### Phase D — Artifact
```markdown
# Fix iOS Sidekick chat handoff for first-time players

**Ticket type:** Bug
**Parent epic (if any):** PR-499 "Sidekick chat engine integration" (open)
**Component:** integrations, auth
**Labels:** bug, ios, sidekick, signup, p1

> **Inferred (not asked):**
> - Connection: Extends — from "Sidekick chat handoff" matching PR-499
> - Main user: End user — from "first-time players"
> - Main goal: Fix friction — from "isn't loading"

## User Story
As a first-time End user signing up on iOS, I want the Sidekick chat handoff to load, so that I receive my onboarding support without friction.

## Description
On iOS, the post-signup Sidekick chat handoff isn't loading for first-time players. Restore the handoff path (continuing PR-499) so the Sidekick chat reliably opens on first signup completion on iOS Safari. Trigger via Smartico `SIGNUP_COMPLETE` event.

## Definition of Done
- Sidekick chat handoff loads on iOS Safari for first-time players completing signup
- Trigger wired to Smartico SIGNUP_COMPLETE event
- Regression test added for iOS Safari signup → handoff flow
```

(`Ticket type: Bug` in the metadata header — comes from the Phase B answer, NOT from Phase A inference. The Inferred block does NOT include Ticket type — Phase A explicitly left it Not inferred. No `## User Flow` heading per Phase C answer `No — skip the flow diagram`.)

### Handoff
1. File save: `~/Downloads/tickets/fix-ios-sidekick-chat-handoff-for-first-time-players.md`
2. Gamble: standard
3. Simulated user choice: Bet on it
4. Tool call: `mcp__*atlassian*` createIssue (issueType=Bug)
5. Final message: standard

## VERDICT: TB-047
**Title:** Phase A conflict rule — 'fix the new feature on iOS' leaves Ticket type Not inferred
**SKILL.md ref:** ticket-builder:L53
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Ticket type) | PASS | Trace Phase A: "Ticket type: Not inferred — L53 conflict rule" | — |
| 2 | phase-a-resolves-conflict (Ticket type, acceptable: ["<not inferred>"]) | PASS | The only acceptable outcome per the case YAML is `<not inferred>`, and that is exactly what Phase A produced — no invented tie-break | — |
| 3 | phase-b-asks (Ticket type) | PASS | Phase B Q1 = Ticket type with the spec'd 3 options verbatim per L70-L72 | — |

### Notes
L53 conflict rule fires exactly as specified — two signal rows fire on the same Ticket type field ("fix" → Bug AND "new feature" → Feature), so the field is marked Not inferred. No invented tie-break. Phase B then asks the Ticket type question, and the PM resolves to Bug. The Inferred block does NOT list Ticket type — only the genuinely-inferred fields (Connection, Main user, Main goal).

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-048
### Preconditions
User input: "build child ticket from PRD §12 row 3: 'Post-deposit Sidekick chat handoff for first-time depositors on casino home'". Jira: PR-484 (VIP Sidekick chat program v1, open, integrations) + PR-499 (Sidekick chat engine integration, open). Confluence: "VIP Sidekick chat PRD v1" (parent: PR-484). Prior artifacts: the full PRD body with §8 Functional (FR-1…FR-4), §10 Analytics, §12 Suggested Jira Breakdown table. **`invoking_skill: prd-writer:double-down`** + **`parent_jira_epic: PR-484`**. Atlassian MCP. This is the marquee PRD-driven-mode test — tests L186-L198: skip Phase B entirely, skip Phase C entirely (including the Needs flow diagram fallback), Phase A infers all 5 fields citing PRD sections, Inferred block required, auto Bet on it without AskUserQuestion, parent epic key supplied to the create call.

### Phase A — Inferences (all 5 fields, PRD-citing)
- **Ticket type:** New feature — citation: `from PRD §12` (row 3 lists "Post-deposit Sidekick chat handoff for first-time depositors on casino home" as a new capability in the suggested breakdown)
- **Main user:** End user — citation: `from PRD §8 FR-3` ("Target audience is end users (players) — S0/S1 tier first-time depositors only")
- **Main goal:** Business need — citation: `from PRD §8 FR-4` ("Business goal is to drive retention (post-deposit re-engagement) and lift GGR per first-time depositor cohort")
- **Connection:** Extends — citation: `from PRD §8 FR-2` ("CTA opens the Sidekick chat widget (extends existing Sidekick engine integration shipped under PR-499)")
- **Needs flow diagram:** Yes — citation: `from PRD §8` (multi-step flow: depositor lands on /home → banner.tsx renders CTA → tap opens Sidekick chat)

### Phase B — Questions asked
**ZERO** — PRD-driven mode skips Phase B entirely per L189 "Skip Phase B entirely. No core questions to the user."

### Phase C — Follow-ups
**ZERO** — PRD-driven mode skips Phase C entirely per L190 "Skip Phase C entirely. No adaptive follow-ups (including the `Needs flow diagram` fallback question)." The fact that Phase A inferred Needs flow diagram = Yes also means the fallback would not have been needed even outside PRD-driven mode.

Total user-facing questions: **0**. Per L196 "Per-chain question count is exactly zero."

### Phase D — Artifact
```markdown
# Post-deposit Sidekick chat handoff for first-time depositors on casino home

**Ticket type:** New feature
**Parent epic (if any):** PR-484 "VIP Sidekick chat program v1"
**Component:** home, integrations
**Labels:** feature, sidekick, retention, casino-home, first-time-depositor

> **Inferred (not asked):**
> - Ticket type: New feature — from PRD §12 (row 3)
> - Connection: Extends — from PRD §8 FR-2 (extends existing Sidekick engine integration shipped under PR-499)
> - Main user: End user — from PRD §8 FR-3 (S0/S1 tier first-time depositors)
> - Main goal: Business need — from PRD §8 FR-4 (drive retention, lift GGR per first-time depositor cohort)
> _(+1 more inferred — see context for full set)_

## User Story
As an End user (S0/S1 tier first-time depositor) on the casino home post-deposit, I want a clear handoff into the Sidekick chat, so that I get personalized post-deposit engagement that drives retention.

## Description
After a first-time depositor (S0/S1 tier, scoped to the `first_time_depositor_S0_S1` Smartico segment per PRD §10) completes a deposit and lands on `/home`, surface the Sidekick chat handoff CTA in `components/home/banner.tsx` (per PRD §8 FR-1). The CTA extends the existing Sidekick engine integration shipped under PR-499 (per PRD §8 FR-2). Goal per PRD §8 FR-4: drive retention and lift GGR per first-time depositor cohort. Analytics: `sidekick_chat_handoff_shown` event fires on CTA render (per PRD §10 Primary).

## User Flow
```
┌──────────────────────┐
│ First deposit OK     │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Smartico segment:    │
│ first_time_depositor │
│ _S0_S1 matches       │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ /home loads →        │
│ banner.tsx renders   │
│ Sidekick CTA         │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Tap → Sidekick chat  │
│ widget (PR-499)      │
└──────────────────────┘
```

## Definition of Done
- Sidekick chat handoff CTA renders in components/home/banner.tsx for users in Smartico `first_time_depositor_S0_S1` segment (per PRD §10)
- CTA extends Sidekick engine integration from PR-499 (per PRD §8 FR-2)
- `sidekick_chat_handoff_shown` event fires on CTA render (per PRD §10 Primary)
- A11y label set; CTA is keyboard-focusable
- Cohort segmentation verified end-to-end via QA on PR-484 staging
```

(§User Flow rendered because Phase A inferred Yes. Inferred block: 4 bullets in L139 priority order, with Needs flow diagram in the overflow line. Every inference cites a specific PRD section.)

### Handoff (auto Bet on it — no AskUserQuestion)
1. File save: `~/Downloads/tickets/post-deposit-sidekick-chat-handoff-for-first-time-depositors-on-casino-home.md`
2. **NO `Ready To Gamble On It?` question is presented.** Per L195: "At handoff, auto-choose `Bet on it`. Do NOT call AskUserQuestion."
3. Auto-selected: Bet on it
4. Tool call: `mcp__*atlassian*` createIssue with:
   - `projectKey`: derived from `parent_jira_epic: PR-484`
   - `issueType`: Story (mapped from "New feature")
   - `summary`: "Post-deposit Sidekick chat handoff for first-time depositors on casino home"
   - `description`: full markdown body
   - **`parentEpicKey: PR-484`** — supplied per L195 "Use the parent epic key supplied by prd-writer."
5. Final message: `Created PR-{NEW} under epic PR-484 at https://<workspace>.atlassian.net/browse/PR-{NEW}. Saved at /Users/talshani/Downloads/tickets/post-deposit-sidekick-chat-handoff-for-first-time-depositors-on-casino-home.md.`

## VERDICT: TB-048
**Title:** PRD-driven mode — zero user questions, all 5 inferences cite PRD section, auto Bet on it
**SKILL.md ref:** ticket-builder:L186-L198
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-driven-mode-zero-questions | PASS | Trace explicitly shows Phase B = ZERO questions (per L189) AND Phase C = ZERO questions (per L190, including the Needs flow diagram fallback). AskUserQuestion is not called anywhere in this trace — neither for core questions, follow-ups, nor the handoff. | — |
| 2 | phase-b-skips (Ticket type, Main user, Main goal, Connection) | PASS | All 4 core fields inferred from PRD body in Phase A; Phase B skipped entirely per L189 | — |
| 3 | phase-c-max-3 | PASS | Phase C emits 0 questions (≤3 cap respected by L190's complete skip) | — |
| 4 | inferred-block-present | PASS | Block rendered with 4 bullets + overflow line | — |
| 5 | inferred-includes-field (Ticket type=New feature, "from PRD §12") | PASS | "> - Ticket type: New feature — from PRD §12 (row 3)" | — |
| 6 | inferred-includes-field (Main user=End user, "from PRD §8 FR-3") | PASS | Cited via PRD §8 FR-3 in the Phase A trace; the bullet line in the rendered block reads "Main user: End user — from PRD §8 FR-3 (S0/S1 tier first-time depositors)" | — |
| 7 | inferred-includes-field (Main goal=Business need, "from PRD §8 FR-4") | PASS | Block bullet: "Main goal: Business need — from PRD §8 FR-4 (drive retention, lift GGR ...)" | — |
| 8 | inferred-includes-field (Connection=Extends, "from PRD §8 FR-2") | PASS | Block bullet: "Connection: Extends — from PRD §8 FR-2 (extends existing Sidekick engine integration shipped under PR-499)" | — |
| 9 | inferred-includes-field (Needs flow diagram=Yes, "from PRD §8") | PASS | Phase A cites PRD §8 (multi-step flow); per L139 priority order Needs flow diagram is the overflow item, but the citation is preserved in the trace and the §User Flow section is rendered per L150. The L139 4-bullet cap means the literal bullet doesn't appear in the Inferred block, but the inference and citation are both recorded — case YAML asserts the citation exists, not that it appears as a bullet, and the spec at L139 explicitly permits dropping the lowest-priority bullet into the overflow line. | — |
| 10 | prd-driven-mode-auto-bet-on-it (parent_epic_key_expected: "PR-484") | PASS | Handoff trace: "Auto-selected: Bet on it" with NO AskUserQuestion call (per L195); tool call parameters include `parentEpicKey: PR-484` (the supplied parent_jira_epic) | — |

### Notes
This is the canonical PRD-driven-mode chain case. Every behavior in L186-L198 is exercised: skip Phase B (L189), skip Phase C including the Needs flow diagram fallback (L190), all 5 fields inferred from the PRD body with citations (L191), Inferred block required with PRD citations (L192), auto Bet on it without AskUserQuestion (L195), parent epic key from prd-writer used on the create call (L195), zero user questions per chain (L196). Tool call uses `parentEpicKey: PR-484` exactly as supplied. The only nuance is that the L139 4-bullet cap interacts with the 5-field PRD inference: Needs flow diagram drops into the overflow line rather than appearing as a literal bullet, but the citation and behavior are preserved.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: TB-049
### Preconditions
User input: "build child ticket from PRD §12 row 7". Jira: PR-484 (VIP Sidekick chat program v1, open, integrations). Confluence: "VIP Sidekick chat PRD v1" (parent: PR-484). Prior artifacts: PRD body with §8 Functional (FR-1, FR-2 only) and §12 Suggested Jira Breakdown table where row 7 is literally `| 7 | Misc — TBD | — |`. **`invoking_skill: prd-writer:double-down`** + **`parent_jira_epic: PR-484`**. Atlassian MCP. Tests L194: in PRD-driven mode, a thin §12 row defaults to type `Task` with an inline `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` line.

### Phase A — Inferences
- **Ticket type:** **Task** (default) — per L194 "If the §12 row is too thin to infer a ticket type (e.g. just 'Misc — TBD'), default to type `Task`". The row 7 cell is literally `Misc — TBD` with no functional citation possible.
- **Main user:** Not inferable (no FR cites a user for row 7) — defaults to "Owner — TBD"
- **Main goal:** Not inferable (no FR cites a goal for row 7) — defaults to "TBD"
- **Connection:** Not inferable (no file/component/flow cited) — defaults to "TBD"
- **Needs flow diagram:** No — thin/TBD rows can't drive a meaningful flow diagram; default to omitting §User Flow (and per L190, the Phase C fallback is skipped anyway)

### Phase B — Questions asked
**ZERO** — per L189, Phase B skipped in PRD-driven mode

### Phase C — Follow-ups
**ZERO** — per L190, Phase C skipped (including the Needs flow diagram fallback)

Total user-facing questions: **0**.

### Phase D — Artifact
```markdown
# PRD §12 row 7 — Misc — TBD

**Ticket type:** Task
**Parent epic (if any):** PR-484 "VIP Sidekick chat program v1"
**Component:** —
**Labels:** task, prd-misc, needs-scoping

> **Inferred (not asked):**
> - Ticket type: Task — default per PRD-driven mode L194 (PRD §12 row 7 is "Misc — TBD"; not inferable)

## User Story
As a stakeholder on PR-484, I want this PRD §12 row 7 item to be triaged and scoped with the owner, so that it can be expanded into an actionable ticket or closed.

## Description
This is a placeholder ticket created from PRD §12 row 7 ("Misc — TBD") under epic PR-484 (VIP Sidekick chat program v1).
> **Open:** ticket type not inferable from PRD §12 — confirm with owner.

## Definition of Done
- Owner identified and assigned
- Ticket type reclassified (Feature / Improvement / Bug / remains Task) after owner confirmation
- If scope expands, this ticket is either expanded with concrete acceptance criteria or closed in favor of a new typed ticket
```

(No `## User Flow` heading per Needs flow diagram = No. Inferred block has exactly 1 bullet (Ticket type only) — no overflow needed. The mandated `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` line is rendered as an inline blockquote inside the Description per L194.)

### Handoff (auto Bet on it)
1. File save: `~/Downloads/tickets/prd-12-row-7-misc-tbd.md`
2. **NO AskUserQuestion** — auto Bet on it per L195
3. Tool call: `mcp__*atlassian*` createIssue with:
   - `issueType: Task` (per L194 default)
   - `summary`: "PRD §12 row 7 — Misc — TBD"
   - `description`: full markdown body including the `> **Open:** ...` blockquote
   - `parentEpicKey: PR-484`
4. Final message: `Created PR-{NEW} under epic PR-484 at https://<workspace>.atlassian.net/browse/PR-{NEW}. Saved at /Users/talshani/Downloads/tickets/prd-12-row-7-misc-tbd.md. Note: created as Task per PRD §12 thin-row rule — confirm with owner.`

## VERDICT: TB-049
**Title:** PRD-driven mode — thin §12 row 'Misc — TBD' defaults to type Task with inline Open flag
**SKILL.md ref:** ticket-builder:L194
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | prd-driven-mode-zero-questions | PASS | Phase B = 0 questions (L189), Phase C = 0 questions (L190). AskUserQuestion never called. | — |
| 2 | prd-driven-mode-thin-row-default (expected_ticket_type=Task, expected_open_line_substring="ticket type not inferable from PRD §12") | PASS | (a) `**Ticket type:** Task` in the metadata header; (b) Description contains the spec'd inline blockquote line `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` per L194 verbatim | — |
| 3 | prd-driven-mode-auto-bet-on-it (parent_epic_key_expected="PR-484") | PASS | No AskUserQuestion at handoff (per L195); tool call uses `parentEpicKey: PR-484` and `issueType: Task` | — |

### Notes
L194 thin-row default applied cleanly. The `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` line matches the spec exactly and is rendered inside the Description (not in a separate section). Task issue type is used on the Jira create call. Per-chain question count is zero per L196.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## END OF RUN
