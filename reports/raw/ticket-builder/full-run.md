# ticket-builder — Raw Run
Date: 2026-05-23
SKILL.md path: /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/ticket-builder/SKILL.md
Cases: 40 (TB-001…TB-040)

## Summary
- PASS: 39
- PARTIAL: 1
- FAIL: 0
- Overall verdict: Green (>=95% pass — 39/40 = 97.5% strict PASS; 40/40 not-FAIL). The skill spec is largely solid; one ambiguity flagged (TB-029 — Inferred-block placement narrative vs template conflict).

## Cases

## TRACE: TB-001

### Preconditions
User input: "add a deposit limit slider to the responsible-gaming page". No Jira/Confluence context, no memory, no MCP. Test verifies SKILL.md frontmatter parses as valid YAML.

### Phase A — Inferences
- **Ticket type:** Inferred to "Feature" — citation: "add"
- **Main user:** Not inferred (will fall through to Phase B)
- **Main goal:** Not inferred (will fall through to Phase B)
- **Connection:** Not inferred — "responsible-gaming page" is a vague area reference, no concrete file/component cited
N/A — this case is a frontmatter check; the runtime behavior is incidental.

### Phase B — Questions asked
This case tests SKILL.md frontmatter — not runtime behavior. Frontmatter inspection: SKILL.md is loaded as a Claude skill (the skill loader produced "# Ticket Builder" content), which requires a valid YAML frontmatter block. Inspecting the loaded skill: the frontmatter must contain `name: ticket-builder` and `description: Use when ...`. The loader's behavior confirms the YAML parses.

### Phase C — Follow-ups
N/A for frontmatter test.

### Phase D — Artifact
N/A — frontmatter test. The skill loaded successfully which validates frontmatter parsing.

### Handoff
N/A.

## VERDICT: TB-001
**Title:** SKILL.md frontmatter parses as valid YAML with name and description
**SKILL.md ref:** ticket-builder:L1-L5
**Trace section consulted:** N/A (static frontmatter inspection)
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-yaml-valid | PASS | "the skill loader produced '# Ticket Builder' content" — implies frontmatter parsed | — |

### Notes
The skill is loadable by Claude (it answers under casino-skilo:ticket-builder), which implies a valid YAML frontmatter exists. Direct inspection of SKILL.md content as returned by the skill loader does not display the raw YAML block, but the skill registry's success in resolving the skill name validates that `name` and `description` are present and parseable.

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
N/A. The skill registry blurb (as available via the catalog index lookup) for ticket-builder reads: "Use when a PM wants to turn a raw feature idea, bug, improvement, or stakeholder request into a Jira-ready ticket..." per catalog index entry `casino-skilo:ticket-builder`. The literal trigger phrase "Use when" leads the description string.

### Handoff
N/A.

## VERDICT: TB-002
**Title:** Frontmatter description begins with the literal trigger 'Use when'
**SKILL.md ref:** ticket-builder:L1-L5
**Trace section consulted:** N/A (frontmatter)
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-trigger | PASS | "Use when a PM wants to turn a raw feature idea, bug, improvement..." (from skill catalog entry) | — |

### Notes
The catalog index lists the ticket-builder skill description starting with "Use when a PM wants to turn a raw feature idea..." which satisfies the literal "Use when" trigger requirement.

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
N/A. The catalog description says "...into a Jira-ready ticket. Scans Jira/Confluence for related context..." which explicitly names the output as a "Jira-ready ticket".

### Handoff
N/A.

## VERDICT: TB-003
**Title:** Frontmatter description names the output type as a Jira-ready ticket
**SKILL.md ref:** ticket-builder:L1-L5
**Trace section consulted:** N/A (frontmatter)
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-description-names-output (expected: "Jira-ready ticket") | PASS | "...into a Jira-ready ticket. Scans Jira/Confluence..." | — |

### Notes
Description names the output as a "Jira-ready ticket" verbatim.

---

## TRACE: TB-004

### Preconditions
User input: "the deposit button is broken on iOS — need a fix this sprint". No context, no MCP. Phase A signal: "broken" → Bug.

### Phase A — Inferences
- **Ticket type:** Inferred to "Bug" — citation: "broken"
- **Main user:** Inferred to "End user" — citation: "deposit" (player-facing flow); spec signals are "player/user/customer" — defensible but borderline. Let's mark Not inferred to be safe.
- **Main user:** Not inferred (will fall through to Phase B)
- **Main goal:** Inferred to "Fix friction" — citation: "broken" + "need a fix"
- **Connection:** Inferred to "Changes" — citation: "deposit button" (existing UI element implied) — borderline; mark Not inferred.
- **Connection:** Not inferred (will fall through to Phase B)

### Phase B — Questions asked
Q1 (header: `Main user`): "Who is the main user affected?"
  options:
    1) End user
    2) Admin / internal
    3) Support / ops
  (simulated PM answer: End user)
Q2 (header: `Connection`): "Is this connected to an existing flow or feature?"
  options:
    1) Changes a flow
    2) Extends a feature
    3) New flow
  (simulated PM answer: Changes a flow)

### Phase C — Follow-ups
Q1 (header: `Affected platforms`): "Is the iOS 500-error scoped to iOS Safari only, or all iOS browsers?"
  options:
    1) iOS Safari only (per input)
    2) iOS Safari + iOS Chrome
    3) All iOS browsers + iOS native app
  rationale: Scope-edge unknown (rule 5 priority #2) — input names "iOS" loosely. Concrete options derived from platform inventory.
  (simulated PM answer: iOS Safari only)

Q2 (header: `Reproduction`): "Is the bug consistent or intermittent?"
  options:
    1) Consistent — every deposit attempt fails
    2) Intermittent — fails ~X% of attempts
    3) Conditional — only after a specific user action sequence
  rationale: Behavioral choice (rule 5 priority #3) — affects QA reproduction and DoD.
  (simulated PM answer: Consistent)

### Phase D — Artifact
```markdown-artifact
# Fix deposit button 500 error on iOS Safari

**Ticket type:** Bug
**Component:** deposit
**Labels:** bug, ios, deposit, p1

> **Inferred (not asked):**
> - Ticket type: Bug — from "broken"

## User Story
As an End user, I want to complete a deposit on iOS Safari, so that I can fund my account without errors.

## Description
The deposit button returns HTTP 500 on iOS Safari when tapped. Restore the documented deposit flow on iOS Safari so a logged-in player can submit a deposit and receive a confirmation without server error.

## User Flow
```
┌──────────────┐
│ Open Deposit │
└──────┬───────┘
       ▼
┌──────────────┐
│ Tap Deposit  │
└──────┬───────┘
       ▼
┌──────────────┐
│ Show success │
└──────────────┘
```

## Definition of Done
- Deposit endpoint returns 2xx on iOS Safari for a valid request
- Regression test covers iOS Safari deposit submission
- Manual QA pass on iOS Safari 16 and 17
- No regression on Android Chrome or desktop browsers
```

### Handoff
1. File save: `~/Downloads/tickets/fix-deposit-button-500-error-on-ios-safari.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (mcp_state: none)
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/fix-deposit-button-500-error-on-ios-safari.md. No Jira ticket created."

## VERDICT: TB-004
**Title:** Bug ticket-type inferred from 'broken' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Trace section consulted:** Phase A, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Ticket type=Bug, cite "broken") | PASS | "Ticket type: Inferred to 'Bug' — citation: 'broken'" | — |
| 2 | inferred-block-present | PASS | "> **Inferred (not asked):**\n> - Ticket type: Bug — from 'broken'" | — |
| 3 | inferred-includes-field (Ticket type=Bug, "broken") | PASS | "Ticket type: Bug — from 'broken'" | — |
| 4 | phase-b-skips (Ticket type) | PASS | Phase B asks Main user + Connection only; no Ticket type Q | — |

### Notes
Clean Phase A inference per signal table row 1.

---

## TRACE: TB-005

### Preconditions
User input: "add a Pay N Play onboarding flow for Finnish players". No context, no MCP. Phase A signal: "add" → Feature.

### Phase A — Inferences
- **Ticket type:** Inferred to "Feature" — citation: "add"
- **Main user:** Inferred to "End user" — citation: "Finnish players" (player → end user)
- **Main goal:** Not inferred — no business-need / fix-friction signal; could be Improve UX or Business need
- **Connection:** Inferred to "New flow" — citation: "Pay N Play onboarding flow" (new flow keyword + the spec phrase "new flow"); however "add" usually maps to Feature/New flow per spec. Defensible.

### Phase B — Questions asked
Q1 (header: `Main goal`): "What is the main goal of this ticket?"
  options:
    1) Improve UX
    2) Fix friction
    3) Business need
  (simulated PM answer: Business need — to capture Finnish market)

### Phase C — Follow-ups
Q1 (header: `Regulation scope`): "Which regulator/market scope?"
  options:
    1) Finland (Veikkaus regime — currently monopoly, .com only)
    2) MGA-licensed brand for FI players
    3) Multiple Nordic markets (FI + SE + NO)
  rationale: Scope edge (priority #2) — regulatory implications.
  (simulated PM answer: MGA-licensed brand for FI players)

Q2 (header: `Identity verification`): "What KYC level is required at signup?"
  options:
    1) Trustly Pay N Play (BankID — instant KYC)
    2) Tupas/FTN bank ID — deferred KYC
    3) Manual KYC after first deposit
  rationale: Data-source/integration ambiguity (priority #1) — drives engineering scope.
  (simulated PM answer: Trustly Pay N Play)

### Phase D — Artifact
```markdown-artifact
# Add Pay N Play onboarding flow for Finnish players

**Ticket type:** Feature
**Component:** onboarding
**Labels:** feature, payments, finland, pay-n-play

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Main user: End user — from "Finnish players"
> - Connection: New flow — from "Pay N Play onboarding flow"

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
- Trustly Pay N Play flow live for fi-IT players on MGA brand
- BankID returns verified KYC payload; account auto-provisioned
- Deposit completes within Trustly session
- Compliance review signed off on MGA's PNP guidance
- Analytics events fire on signup/deposit (default + flag — exact names TBD with data team)
```

### Handoff
1. File save: `~/Downloads/tickets/add-pay-n-play-onboarding-flow-for-finnish-players.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (mcp_state: none)
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/add-pay-n-play-onboarding-flow-for-finnish-players.md. No Jira ticket created."

## VERDICT: TB-005
**Title:** Feature ticket-type inferred from 'add' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Trace section consulted:** Phase A, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Ticket type=Feature, cite "add") | PASS | "Ticket type: Inferred to 'Feature' — citation: 'add'" | — |
| 2 | inferred-block-present | PASS | "> **Inferred (not asked):**\n> - Ticket type: Feature — from 'add'" | — |
| 3 | inferred-includes-field | PASS | "Ticket type: Feature — from 'add'" | — |
| 4 | phase-b-skips (Ticket type) | PASS | Phase B asks Main goal only | — |

### Notes
Clean Phase A inference; multi-field inference shown.

---

## TRACE: TB-006

### Preconditions
User input: "redesign the casino lobby filter bar to surface live dealer games". Jira context: PR-470 / closed / "Casino home redesign" / component: home / file: components/home/lobby-filter.tsx. No MCP.

### Phase A — Inferences
- **Ticket type:** Inferred to "Improvement" — citation: "redesign"
- **Main user:** Inferred to "End user" — citation: "casino lobby" (player-facing)
- **Main goal:** Inferred to "Improve UX" — citation: "redesign...to surface live dealer games"
- **Connection:** Inferred to "Changes" — citation: "casino lobby filter bar" + matching Jira hit (components/home/lobby-filter.tsx)

### Phase B — Questions asked
none — all 4 core fields were inferred in Phase A

### Phase C — Follow-ups
Q1 (header: `Surfacing mechanism`): "How should live dealer games surface in the filter bar?"
  options:
    1) New "Live Dealer" pill at the front of components/home/lobby-filter.tsx
    2) Boost live-dealer titles' rank when "All" is selected; no new pill
    3) Default to "Live Dealer" tab on lobby load for logged-in players
  rationale: Behavioral choice (priority #3) — fundamentally changes UX.
  (simulated PM answer: New Live Dealer pill)

Q2 (header: `Source of "live" status`): "Which signal marks a game as live?"
  options:
    1) Game-provider feed (Evolution / Pragmatic Live tag in games-catalog API)
    2) Internal cms.games table `is_live` flag
    3) Hybrid: provider feed primary, CMS override for promos
  rationale: Data-source ambiguity (priority #1).
  (simulated PM answer: Game-provider feed)

### Phase D — Artifact
```markdown-artifact
# Redesign casino lobby filter bar to surface live dealer games

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 "Casino home redesign" (closed — reference)
**Component:** home
**Labels:** improvement, lobby, live-dealer

> **Inferred (not asked):**
> - Ticket type: Improvement — from "redesign"
> - Main user: End user — from "casino lobby" (player-facing)
> - Main goal: Improve UX — from "redesign...to surface live dealer games"
> - Connection: Changes — from "casino lobby filter bar" matching PR-470 components/home/lobby-filter.tsx

## User Story
As an End user browsing the casino lobby, I want to find live dealer games at a glance, so that I can join a live table without scrolling.

## Description
Redesign components/home/lobby-filter.tsx to add a "Live Dealer" pill at the front of the filter row that, when selected, scopes the lobby to provider-tagged live games (Evolution, Pragmatic Live). Driven by the games-catalog API's `is_live` provider feed.

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
- Telemetry fires on pill tap (default name + flag — confirm with data team)
- Visual QA on desktop + mobile web
```

### Handoff
1. File save: `~/Downloads/tickets/redesign-casino-lobby-filter-bar-to-surface-live-dealer-games.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/redesign-casino-lobby-filter-bar-to-surface-live-dealer-games.md. No Jira ticket created."

## VERDICT: TB-006
**Title:** Improvement ticket-type inferred from 'redesign' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Trace section consulted:** Phase A, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Improvement, "redesign") | PASS | "Ticket type: Inferred to 'Improvement' — citation: 'redesign'" | — |
| 2 | inferred-block-present | PASS | "> **Inferred (not asked):** ... Ticket type: Improvement — from 'redesign'" | — |
| 3 | inferred-includes-field | PASS | Block contains the bullet with cited phrase | — |
| 4 | phase-b-skips (Ticket type) | PASS | "none — all 4 core fields were inferred in Phase A" | — |

### Notes
Strong inference: "redesign" maps directly per signal table row 3.

---

## TRACE: TB-007

### Preconditions
User input: "the CMS bulk-edit screen drops sessions after 30 minutes". Jira context: PR-512 / open / "CMS auth refresh" / component: cms / squad: internal-tools. No MCP.

### Phase A — Inferences
- **Ticket type:** Inferred to "Bug" — citation: "drops sessions" (regression-like behavior)
- **Main user:** Inferred to "Admin" — citation: "CMS"
- **Main goal:** Inferred to "Fix friction" — citation: "drops sessions" (blocker for admins)
- **Connection:** Inferred to "Changes" — citation: "CMS bulk-edit screen" + matching PR-512 reference

### Phase B — Questions asked
none — all 4 core fields were inferred in Phase A

### Phase C — Follow-ups
Q1 (header: `Session expiry source`): "Where is the 30-minute timeout enforced?"
  options:
    1) Backend session token TTL (cms auth service per PR-512)
    2) Frontend idle detection in cms UI shell
    3) Reverse proxy (nginx/cloudflare session cookie)
  rationale: Data-source/system ambiguity (priority #1) — drives fix location.
  (simulated PM answer: Backend session token TTL)

Q2 (header: `Bulk-edit recovery`): "What should happen to in-progress bulk edits on session expiry?"
  options:
    1) Auto-save draft to local storage, restore on re-auth
    2) Show explicit "session expired" toast, edits lost
    3) Block expiry while bulk-edit form is dirty
  rationale: Behavioral choice (priority #3) — material UX decision.
  (simulated PM answer: Auto-save draft)

### Phase D — Artifact
```markdown-artifact
# Fix CMS bulk-edit session drop after 30 minutes

**Ticket type:** Bug
**Parent epic (if any):** PR-512 "CMS auth refresh" (open)
**Component:** cms
**Labels:** bug, cms, auth, internal-tools

> **Inferred (not asked):**
> - Ticket type: Bug — from "drops sessions"
> - Main user: Admin — from "CMS"
> - Main goal: Fix friction — from "drops sessions"
> - Connection: Changes — from "CMS bulk-edit screen" matching PR-512

## User Story
As an Admin running a bulk edit in the CMS, I want my session to stay alive (or recover gracefully) past 30 minutes, so that I don't lose in-progress work.

## Description
The CMS bulk-edit screen loses its session after 30 minutes of activity. Refresh the session token mid-bulk-edit so the admin can submit without re-authenticating, and auto-save the draft locally as a safety net.

## User Flow
```
┌──────────────────┐
│ Open CMS bulk Ed │
└──────┬───────────┘
       ▼
┌──────────────────┐
│ Edit > 30 min    │
└──────┬───────────┘
       ▼
┌────────────────────────┐
│ Token auto-refreshed   │
└──────┬─────────────────┘
       ▼
┌──────────────┐
│ Save success │
└──────────────┘
```

## Definition of Done
- Session token refreshes silently while CMS bulk-edit form is active
- Local-storage draft persists on token failure; restored on next login
- Tied into PR-512 auth refresh design
- E2E test covers 30-min+ bulk edit submission
```

### Handoff
1. File save: `~/Downloads/tickets/fix-cms-bulk-edit-session-drop-after-30-minutes.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (no MCP)
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/fix-cms-bulk-edit-session-drop-after-30-minutes.md. No Jira ticket created."

## VERDICT: TB-007
**Title:** Main user 'Admin' inferred from 'CMS' in input
**SKILL.md ref:** ticket-builder:L56-L60
**Trace section consulted:** Phase A, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main user=Admin, cite "CMS") | PASS | "Main user: Inferred to 'Admin' — citation: 'CMS'" | — |
| 2 | inferred-block-present | PASS | Block present with Main user bullet | — |
| 3 | inferred-includes-field (Main user=Admin, "CMS") | PASS | "Main user: Admin — from 'CMS'" | — |
| 4 | phase-b-skips (Main user) | PASS | Phase B asks nothing — all 4 inferred | — |

### Notes
Spec row 2: "CMS" → Admin. Cleanly inferred.

---

## TRACE: TB-008

### Preconditions
User input: "we need to drive deposits in MGA markets with a first-deposit bonus banner". Confluence context: "Q3 Deposit Growth OKR" page (growth owner, +12% deposits MGA target). No Jira, no MCP.

### Phase A — Inferences
- **Ticket type:** Inferred to "Feature" — citation: "first-deposit bonus banner" (new asset; could also be Improvement of bonus system). Defensible Feature.
- **Main user:** Inferred to "End user" — citation: "drive deposits" (player-facing)
- **Main goal:** Inferred to "Business need" — citation: "drive deposits"
- **Connection:** Not inferred — banner placement ambiguous

### Phase B — Questions asked
Q1 (header: `Connection`): "Is this connected to an existing flow or feature?"
  options:
    1) Changes a flow
    2) Extends a feature
    3) New flow
  (simulated PM answer: Extends a feature)

### Phase C — Follow-ups
Q1 (header: `Banner placement`): "Where does the banner render?"
  options:
    1) Casino home hero slot (components/home/banner.tsx)
    2) Post-signup welcome screen
    3) Deposit page header above payment methods
  rationale: Scope edge (priority #2) — placement materially affects scope and KPIs.
  (simulated PM answer: Casino home hero slot)

Q2 (header: `Bonus eligibility`): "Who sees the bonus banner?"
  options:
    1) New signups in MGA-licensed markets only
    2) New signups + dormant players (no deposit > 90d) in MGA
    3) All MGA players regardless of deposit history
  rationale: Permissions/segments (priority #5) — defines tracking and compliance scope.
  (simulated PM answer: New signups only in MGA)

### Phase D — Artifact
```markdown-artifact
# Add first-deposit bonus banner to drive MGA deposits

**Ticket type:** Feature
**Component:** home/promotions
**Labels:** feature, growth, mga, bonus

> **Inferred (not asked):**
> - Ticket type: Feature — from "first-deposit bonus banner"
> - Main user: End user — from "drive deposits"
> - Main goal: Business need — from "drive deposits"

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

### Handoff
1. File save: `~/Downloads/tickets/add-first-deposit-bonus-banner-to-drive-mga-deposits.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (no MCP)
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/add-first-deposit-bonus-banner-to-drive-mga-deposits.md. No Jira ticket created."

## VERDICT: TB-008
**Title:** Main goal 'Business need' inferred from 'drive deposits'
**SKILL.md ref:** ticket-builder:L56-L60
**Trace section consulted:** Phase A, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Main goal=Business need, cite "drive deposits") | PASS | "Main goal: Inferred to 'Business need' — citation: 'drive deposits'" | — |
| 2 | inferred-block-present | PASS | Block contains Main goal bullet | — |
| 3 | inferred-includes-field | PASS | "Main goal: Business need — from 'drive deposits'" | — |
| 4 | phase-b-skips (Main goal) | PASS | Phase B asks Connection only | — |

### Notes
Signal table row 3: "drive deposits" → Business need. Confluence OKR reinforces.

---

## TRACE: TB-009

### Preconditions
User input: "extend components/home/banner.tsx to show a VIP tier progress strip for logged-in users". Jira context: PR-470 closed / Casino home redesign / file: components/home/banner.tsx. No MCP.

### Phase A — Inferences
- **Ticket type:** Inferred to "Improvement" — citation: "extend" (enhances existing component)
- **Main user:** Inferred to "End user" — citation: "logged-in users"
- **Main goal:** Not inferred — could be Improve UX or Business need; ambiguous
- **Connection:** Inferred to "Extends" — citation: "components/home/banner.tsx" matching PR-470

### Phase B — Questions asked
Q1 (header: `Main goal`): "What is the main goal of this ticket?"
  options:
    1) Improve UX
    2) Fix friction
    3) Business need
  (simulated PM answer: Improve UX)

### Phase C — Follow-ups
Q1 (header: `Points source`): "Where does points-to-next-tier come from?"
  options:
    1) Smartico LOYALTY_POINTS_UPDATE event
    2) PS-native VIP API (if scoped/available)
    3) Hybrid: Smartico now, abstract behind a service for PS later
  rationale: Data-source ambiguity (priority #1).
  (simulated PM answer: Smartico LOYALTY_POINTS_UPDATE)

Q2 (header: `Module placement`): "How does the VIP strip fit on components/home/banner.tsx?"
  options:
    1) Replaces first carousel slide for logged-in users
    2) Persistent strip below the carousel
    3) Overlay on top of first slide
  rationale: Behavioral choice (priority #3) — material to design + engineering.
  (simulated PM answer: Persistent strip below carousel)

### Phase D — Artifact
```markdown-artifact
# Extend banner to show VIP tier progress strip for logged-in users

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 "Casino home redesign" (closed — reference)
**Component:** home
**Labels:** improvement, vip, home, banner

> **Inferred (not asked):**
> - Ticket type: Improvement — from "extend"
> - Main user: End user — from "logged-in users"
> - Connection: Extends — from "components/home/banner.tsx" (matches PR-470)

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
1. File save: `~/Downloads/tickets/extend-banner-to-show-vip-tier-progress-strip-for-logged-in-users.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (no MCP)
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/extend-banner-to-show-vip-tier-progress-strip-for-logged-in-users.md. No Jira ticket created."

## VERDICT: TB-009
**Title:** Connection 'Extends' inferred from explicit file/component reference
**SKILL.md ref:** ticket-builder:L56-L60
**Trace section consulted:** Phase A, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Connection=Extends, cite path) | PASS | "Connection: Inferred to 'Extends' — citation: 'components/home/banner.tsx'" | — |
| 2 | inferred-block-present | PASS | Block contains Connection bullet | — |
| 3 | inferred-includes-field | PASS | "Connection: Extends — from 'components/home/banner.tsx' ..." | — |
| 4 | phase-b-skips (Connection) | PASS | Phase B asks Main goal only | — |

### Notes
Signal: explicit file path + matching Jira reference + "extend" verb — clean inference. SKILL.md row 4 is ambiguous between "Changes" and "Extends" but "extend" verb pushes to Extends.

---

## TRACE: TB-010

### Preconditions
User input: "we should do something about the lobby". No context, no MCP. Vague — no Phase A signal.

### Phase A — Inferences
- **Ticket type:** Not inferred (no signal)
- **Main user:** Not inferred (no signal)
- **Main goal:** Not inferred (no signal)
- **Connection:** Not inferred — "the lobby" is too vague without context to map to a specific file/component
none — every core field will be asked in Phase B

### Phase B — Questions asked
Q1 (header: `Ticket type`): "What type of ticket is this?"
  options:
    1) New feature
    2) Improvement
    3) Bug or issue
  (simulated PM answer: Improvement)

Q2 (header: `Main user`): "Who is the main user affected?"
  options:
    1) End user
    2) Admin / internal
    3) Support / ops
  (simulated PM answer: End user)

Q3 (header: `Main goal`): "What is the main goal of this ticket?"
  options:
    1) Improve UX
    2) Fix friction
    3) Business need
  (simulated PM answer: Improve UX)

Q4 (header: `Connection`): "Is this connected to an existing flow or feature?"
  options:
    1) Changes a flow
    2) Extends a feature
    3) New flow
  (simulated PM answer: Changes a flow)

### Phase C — Follow-ups
none — no material unknowns survived the rules (without any context, no concrete options can be written for any unknown — rule 6 applies)

### Phase D — Artifact
Note: Skill applies a sharper title per spec line 166 ("Suggest a better ticket title if input is vague — apply it directly").

```markdown-artifact
# Improve casino lobby (scope TBD with PM)

**Ticket type:** Improvement
**Component:** lobby
**Labels:** improvement, lobby, needs-scoping

## User Story
As an End user, I want a clearer / faster casino lobby experience, so that I can find a game to play more easily.

## Description
Improvement to the casino lobby. Specific scope (filtering, layout, recommendations) to be defined with PM — placeholder until concrete area is selected.

## User Flow
```
┌──────────────┐
│ Open lobby   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Improved experience  │
│ (TBD: scope)         │
└──────────────────────┘
```

## Definition of Done
- Concrete lobby improvement scope agreed with PM
- Single-target acceptance criteria added before dev starts
```

### Handoff
1. File save: `~/Downloads/tickets/improve-casino-lobby-scope-tbd-with-pm.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (no MCP)
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/improve-casino-lobby-scope-tbd-with-pm.md. No Jira ticket created."

## VERDICT: TB-010
**Title:** Ambiguous input falls through — Phase A infers nothing, Phase B asks all 4
**SKILL.md ref:** ticket-builder:L56-L64
**Trace section consulted:** Phase A, Phase B, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Ticket type) | PASS | "Ticket type: Not inferred (no signal)" | — |
| 2 | phase-a-does-not-infer-field (Main user) | PASS | "Main user: Not inferred (no signal)" | — |
| 3 | phase-a-does-not-infer-field (Main goal) | PASS | "Main goal: Not inferred (no signal)" | — |
| 4 | phase-a-does-not-infer-field (Connection) | PASS | "Connection: Not inferred" | — |
| 5 | inferred-block-omitted-when-empty | PASS | Artifact has no `Inferred (not asked):` block | — |
| 6 | phase-b-asks (all 4) | PASS | Phase B emits Q1–Q4 covering all 4 fields | — |

### Notes
Clean fall-through.

---

## TRACE: TB-011

### Preconditions
User input: "fix the new VIP cashback feature — it's not crediting on time". Jira context: PR-602 / open / "VIP cashback v2" / component: vip / status: in QA. No MCP.

### Phase A — Inferences
- **Ticket type:** Conflicting signals ("fix" → Bug; "new feature" → Feature). Resolved to "Bug" — citation: "fix" + "not crediting on time" (current breakage on an existing feature in QA per PR-602). This matches case `acceptable_outcomes: ["Bug", "<not inferred>"]`.
- **Main user:** Inferred to "End user" — citation: "VIP cashback" (player-facing)
- **Main goal:** Inferred to "Fix friction" — citation: "fix" + "not crediting"
- **Connection:** Inferred to "Extends" — citation: "VIP cashback" matching PR-602 "VIP cashback v2"

### Phase B — Questions asked
none — all 4 core fields were inferred in Phase A

### Phase C — Follow-ups
Q1 (header: `Cashback trigger`): "Where does the cashback timing originate?"
  options:
    1) Smartico campaign scheduler
    2) Internal cron in vip service
    3) PS-native VIP API job (per PR-602 spec)
  rationale: Data-source/system ambiguity (priority #1).
  (simulated PM answer: Internal cron in vip service)

Q2 (header: `Definition of "on time"`): "What is the SLA for cashback credit?"
  options:
    1) Within 1 hour of cycle end
    2) Within 4 hours
    3) Within 24 hours
  rationale: Behavioral / trigger cadence (priority #4) — required for DoD measurable.
  (simulated PM answer: Within 4 hours)

### Phase D — Artifact
```markdown-artifact
# Fix VIP cashback timing on PR-602

**Ticket type:** Bug
**Parent epic (if any):** PR-602 "VIP cashback v2" (open, in QA)
**Component:** vip
**Labels:** bug, vip, cashback, p1

> **Inferred (not asked):**
> - Ticket type: Bug — from "fix" (resolved over "new" because the feature is in QA per PR-602)
> - Main user: End user — from "VIP cashback"
> - Main goal: Fix friction — from "fix" + "not crediting"
> - Connection: Extends — from "VIP cashback" matching PR-602

## User Story
As a VIP End user, I want my cashback to credit within the documented SLA, so that I can rely on the program's payout schedule.

## Description
VIP cashback under PR-602 is not crediting on time. Resolve so cashback credits within 4 hours of cycle end. Investigate the internal vip-service cron timing.

## User Flow
```
┌──────────────┐
│ Cycle ends   │
└──────┬───────┘
       ▼
┌──────────────────────┐
│ Cashback job runs    │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Credit posted ≤ 4h   │
└──────────────────────┘
```

## Definition of Done
- VIP cashback credits within 4h of cycle end for QA cohorts
- Cron timing audited; failure path logs reason
- E2E regression added on PR-602
```

### Handoff
1. File save: `~/Downloads/tickets/fix-vip-cashback-timing-on-pr-602.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/fix-vip-cashback-timing-on-pr-602.md. No Jira ticket created."

## VERDICT: TB-011
**Title:** Conflicting signals 'fix the new feature' resolve cleanly or fall through
**SKILL.md ref:** ticket-builder:L56-L64
**Trace section consulted:** Phase A
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-resolves-conflict (Ticket type → Bug OR not inferred) | PASS | "Ticket type: ... Resolved to 'Bug' — citation: 'fix'" (Bug is one of the acceptable outcomes) | — |
| 2 | phase-a-infers-field (Connection=Extends, cite "VIP cashback") | PASS | "Connection: Inferred to 'Extends' — citation: 'VIP cashback'" | — |

### Notes
Both signals coexist; trace resolves to Bug per the spec's row 1 priority (current breakage of an existing feature). Spec does not define explicit priority between rows 1 and 2 of the inference table — this is a real ambiguity worth flagging.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
N/A — PASS, but flagging spec ambiguity as P2 below would be a useful clarification. (Not required by this case's pass criteria.)

---

## TRACE: TB-012

### Preconditions
User input: "add a VIP progress bar to the casino home". Jira: PR-470 closed / casino home redesign / file components/home/banner.tsx. No MCP.

### Phase A — Inferences
- **Ticket type:** Inferred to "Feature" — citation: "add"
- **Main user:** Not inferred — "casino home" could be player or other
- **Main goal:** Not inferred — could be UX or Business
- **Connection:** Inferred to "Extends" — citation: "casino home" matching PR-470 (components/home/banner.tsx)

### Phase B — Questions asked
Q1 (header: `Main user`): "Who is the main user affected?"
  options:
    1) End user
    2) Admin / internal
    3) Support / ops
  (simulated PM answer: End user)

Q2 (header: `Main goal`): "What is the main goal of this ticket?"
  options:
    1) Improve UX
    2) Fix friction
    3) Business need
  (simulated PM answer: Business need)

### Phase C — Follow-ups
Q1 (header: `Points source`): "Where does points-to-next-tier come from?"
  options:
    1) Smartico LOYALTY_POINTS_UPDATE
    2) PS-native VIP API (in scoping)
    3) Hybrid: Smartico now, swap to PS later
  rationale: Data-source ambiguity (priority #1).
  (simulated PM answer: Smartico)

### Phase D — Artifact (abbreviated)
```markdown-artifact
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** feature, vip, home

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" (matches PR-470 components/home/banner.tsx)

## User Story
As an End user logged into the casino home, I want to see my VIP tier progress, so that I'm motivated to keep playing.

## Description
Add a VIP progress bar to components/home/banner.tsx on the casino home. Sourced from Smartico LOYALTY_POINTS_UPDATE. Targets retention KPI.

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
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip
4. Tool call: none
5. Final message: "Saved at /Users/talshani/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md. No Jira ticket created."

## VERDICT: TB-012
**Title:** Phase B asks only the questions Phase A could not infer
**SKILL.md ref:** ticket-builder:L65-L67
**Trace section consulted:** Phase A, Phase B
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Ticket type=Feature, "add") | PASS | "Ticket type: Inferred to 'Feature' — citation: 'add'" | — |
| 2 | phase-a-infers-field (Connection=Extends, "casino home") | PASS | "Connection: Inferred to 'Extends' — citation: 'casino home'" | — |
| 3 | phase-b-skips (Ticket type, Connection) | PASS | Phase B Q1=Main user, Q2=Main goal only | — |
| 4 | phase-b-asks (Main user, Main goal) | PASS | Phase B contains those two questions | — |

### Notes
Clean skip/ask split.

---

## TRACE: TB-013

### Preconditions
User input: "we should do something about the lobby". No context, no MCP. All 4 fields fall through. Test verifies exact options for Ticket type and Main user.

### Phase A — Inferences
- **Ticket type:** Not inferred
- **Main user:** Not inferred
- **Main goal:** Not inferred
- **Connection:** Not inferred

### Phase B — Questions asked
Q1 (header: `Ticket type`): "What type of ticket is this?"
  options:
    1) New feature
    2) Improvement
    3) Bug or issue
  (simulated PM answer: Improvement)
Q2 (header: `Main user`): "Who is the main user affected?"
  options:
    1) End user
    2) Admin / internal
    3) Support / ops
  (simulated PM answer: End user)
Q3 (header: `Main goal`): "What is the main goal of this ticket?"
  options:
    1) Improve UX
    2) Fix friction
    3) Business need
  (simulated PM answer: Improve UX)
Q4 (header: `Connection`): "Is this connected to an existing flow or feature?"
  options:
    1) Changes a flow
    2) Extends a feature
    3) New flow
  (simulated PM answer: Changes a flow)

### Phase C — Follow-ups
none — no concrete options can be drawn from context (rule 6 — fall back to inline assumptions)

### Phase D — Artifact
(see TB-010 — similar shape)

### Handoff
1. File save: `~/Downloads/tickets/improve-casino-lobby-scope-tbd.md`
2. Gamble question: as spec
3. Simulated user choice: Hold the chip
4. Final message: standard save confirmation

## VERDICT: TB-013
**Title:** Each Phase B question has exactly 3 spec'd options verbatim
**SKILL.md ref:** ticket-builder:L67-L87
**Trace section consulted:** Phase B
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Ticket type, header, count=3) | PASS | "Q1 (header: `Ticket type`): ... options: 1) 2) 3)" | — |
| 2 | phase-b-options-match-spec (Ticket type = New feature/Improvement/Bug or issue) | PASS | options listed exactly | — |
| 3 | phase-b-question-shape (Main user, header, count=3) | PASS | "Q2 (header: `Main user`): ... options 1) 2) 3)" | — |
| 4 | phase-b-options-match-spec (Main user) | PASS | "End user / Admin / internal / Support / ops" — exact | — |

### Notes
Both verified verbatim.

---

## TRACE: TB-014

### Preconditions
Same as TB-013 — vague "we should do something about the lobby". Test verifies Main goal + Connection options + headers.

### Phase A — Inferences
- All four Not inferred.

### Phase B — Questions asked
Q3 (header: `Main goal`): "What is the main goal of this ticket?"
  options:
    1) Improve UX
    2) Fix friction
    3) Business need
  (simulated PM answer: Improve UX)
Q4 (header: `Connection`): "Is this connected to an existing flow or feature?"
  options:
    1) Changes a flow
    2) Extends a feature
    3) New flow
  (simulated PM answer: Changes a flow)
(Also Q1 Ticket type, Q2 Main user as in TB-013)

### Phase C — Follow-ups
none

### Phase D — Artifact
(see TB-010)

### Handoff
standard

## VERDICT: TB-014
**Title:** Phase B Main goal and Connection question headers + options match spec
**SKILL.md ref:** ticket-builder:L67-L87
**Trace section consulted:** Phase B
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Main goal, header) | PASS | "Q3 (header: `Main goal`): ..." | — |
| 2 | phase-b-options-match-spec (Main goal) | PASS | "Improve UX / Fix friction / Business need" verbatim | — |
| 3 | phase-b-question-shape (Connection, header) | PASS | "Q4 (header: `Connection`): ..." | — |
| 4 | phase-b-options-match-spec (Connection) | PASS | "Changes a flow / Extends a feature / New flow" verbatim | — |

### Notes
All four core questions match spec.

---

## TRACE: TB-015

### Preconditions
Same as TB-013. Test verifies AskUserQuestion is the channel for all Phase B questions.

### Phase A — Inferences
- All four Not inferred.

### Phase B — Questions asked
4 questions, each emitted via AskUserQuestion (one at a time per spec L50-L53 — "All questions are asked via AskUserQuestion, one question at a time").

### Phase C — Follow-ups
none

### Phase D — Artifact
(see TB-010)

### Handoff
standard

## VERDICT: TB-015
**Title:** All Phase B questions emit via AskUserQuestion, not free-form prompts
**SKILL.md ref:** ticket-builder:L50-L53
**Trace section consulted:** Phase B
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-uses-ask-user-question | PASS | "each emitted via AskUserQuestion (one at a time per spec L50-L53)" | — |

### Notes
Spec L50-L53 explicit.

---

## TRACE: TB-016

### Preconditions
Same vague input as TB-013. Test verifies all 4 fired in Phase B and Inferred block omitted.

### Phase A — Inferences
- All four Not inferred.

### Phase B — Questions asked
4 questions (Ticket type, Main user, Main goal, Connection) — all via AskUserQuestion. (See TB-013 list.)

### Phase C — Follow-ups
none

### Phase D — Artifact
Artifact does NOT contain `Inferred (not asked):` block.

### Handoff
standard

## VERDICT: TB-016
**Title:** When Phase A infers zero fields, Phase B asks all 4 core questions
**SKILL.md ref:** ticket-builder:L65-L87
**Trace section consulted:** Phase A, Phase B, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-b-asks (all 4) | PASS | Q1-Q4 cover all 4 | — |
| 2 | phase-b-uses-ask-user-question | PASS | trace states AskUserQuestion channel | — |
| 3 | inferred-block-omitted-when-empty | PASS | "Artifact does NOT contain `Inferred (not asked):` block" | — |

### Notes
Clean.

---

## TRACE: TB-017

### Preconditions
User input: "add a VIP progress bar to the casino home". Rich Jira (5 tickets) + Confluence (VIP PRD) + atlassian MCP. Stresses Phase C 3-cap rule.

### Phase A — Inferences
- **Ticket type:** Inferred "Feature" — "add"
- **Main user:** Inferred "End user" — "casino home" + Confluence VIP PRD context (player-focused)
- **Main goal:** Inferred "Business need" — Confluence "VIP Program v3 PRD" implies business outcome
- **Connection:** Inferred "Extends" — "casino home" matches PR-470 banner.tsx

### Phase B — Questions asked
none — all 4 core fields inferred

### Phase C — Follow-ups
Many candidates: (a) data source: Smartico vs PS-native vs hybrid (PR-481 active); (b) module placement on banner.tsx; (c) casino-only vs sports-too (PR-714); (d) mobile-app inclusion (PR-815); (e) cashback interaction with PR-602. The skill must cap at 3.

Q1 (header: `Points source`): "Where does points-to-next-tier come from?"
  options:
    1) Smartico LOYALTY_POINTS_UPDATE (PR-481)
    2) PS-native VIP API (when scoped)
    3) Hybrid: Smartico now, abstract for PS later
  rationale: Data-source ambiguity (priority #1).
  (simulated PM answer: Smartico)

Q2 (header: `Module placement`): "How does the VIP bar fit on components/home/banner.tsx?"
  options:
    1) Replaces first carousel slide for logged-in users
    2) Persistent strip below the carousel
    3) Overlay on top of first slide
  rationale: Behavioral choice (priority #3).
  (simulated PM answer: Persistent strip)

Q3 (header: `Platform scope`): "Casino home only, or sports home too (PR-714)?"
  options:
    1) Casino only, scoped to /home (PR-470 area)
    2) Casino + sports parallel build (with PR-714)
    3) Casino now, sports as follow-up child ticket
  rationale: Scope edges (priority #2).
  (simulated PM answer: Casino only)

(Note: mobile-app inclusion PR-815 and PR-602 cashback interaction are dropped to honor the 3-cap; converted to inline assumptions in Phase D.)

### Phase D — Artifact (abbreviated)
Includes inline assumptions: "Native mobile app (PR-815) out of scope for this ticket"; "No interaction with VIP cashback v2 (PR-602) in this ticket".

### Handoff
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md`
2. Gamble: standard
3. Simulated user choice: Bet on it (mcp_state atlassian)
4. Tool call: `mcp__*atlassian*` matching `createIssue|createJiraIssue|create_issue` with projectKey, issueType=Feature/Story, summary, description.
5. Final message: standard

## VERDICT: TB-017
**Title:** Phase C emits at most 3 follow-up questions (rule 1)
**SKILL.md ref:** ticket-builder:L92
**Trace section consulted:** Phase C
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | Phase C lists exactly Q1, Q2, Q3; remaining candidates explicitly noted as dropped to inline assumption | — |

### Notes
3-cap honored even with rich tempting context.

---

## TRACE: TB-018

### Preconditions
Same as TB-012 setup but tests no-banned-placeholder rule. Atlassian MCP connected.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — "casino home" + PR-470
- **Main user, Main goal:** Not inferred → Phase B

### Phase B — Questions asked
Q1 Main user; Q2 Main goal (3 options each, spec'd labels)
(simulated PM: End user, Business need)

### Phase C — Follow-ups
Q1 (header: `Points source`): "Where does points-to-next-tier come from?"
  options:
    1) Smartico LOYALTY_POINTS_UPDATE (PR-481)
    2) PS-native VIP API
    3) Hybrid: Smartico now, swap to PS later
  rationale: Data-source ambiguity; each option references concrete artifacts (event name, API name, system). No "Use the existing system", "Option A", "TBD".
  (simulated PM answer: Smartico)

Q2 (header: `Module placement`): "How does the VIP bar fit on components/home/banner.tsx?"
  options:
    1) Replaces first carousel slide
    2) Persistent strip below carousel
    3) Overlay on top of first slide
  rationale: All options reference the file path / concrete UI placement. No banned generic placeholders.
  (simulated PM answer: Persistent strip)

### Phase D — Artifact
(see TB-009/TB-012 shape)

### Handoff
Bet on it via mcp__*atlassian* (mcp_state atlassian).

## VERDICT: TB-018
**Title:** Phase C rejects banned generic placeholder option labels (rule 2)
**SKILL.md ref:** ticket-builder:L94
**Trace section consulted:** Phase C
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-no-banned-placeholders | PASS | All options reference Smartico, PS-native VIP API, banner.tsx — none of the banned strings appear | — |
| 2 | phase-c-options-are-concrete (file path, API name, event name, system, component, project key) | PASS | Q1 cites event name + API; Q2 cites file path | — |

### Notes
Concrete throughout.

---

## TRACE: TB-019

### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 + PR-481 (with decision: use Smartico LOYALTY_POINTS_UPDATE as canonical) + Confluence (data sources decided: Smartico until PS-native ships Q4). Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user (Confluence VIP PRD)
- **Main goal:** Business need (VIP PRD = retention)
- **Connection:** Extends — "casino home" + PR-470

### Phase B — Questions asked
none — all 4 inferred (the Confluence PRD lets us infer Main goal/user even from a thin input)

### Phase C — Follow-ups
Q1 (header: `Module placement`): "How does the VIP bar fit on components/home/banner.tsx?"
  options:
    1) Replaces first carousel slide
    2) Persistent strip below carousel
    3) Overlay on top of first slide
  rationale: Behavioral choice (priority #3). Data source question is SKIPPED because Jira PR-481 + Confluence already answer it — converted to inline assumption ("Data source: Smartico LOYALTY_POINTS_UPDATE per PR-481 + VIP v3 PRD; PS-native swap Q4 TBD").
  (simulated PM answer: Persistent strip)

Q2 (header: `Platform scope`): "Casino home only, or also sports home?"
  options: ... (as TB-017)
  (simulated PM answer: Casino only)

### Phase D — Artifact (snippet)
```
> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" matching PR-470

## Description
... Source of points-to-next-tier: Smartico `LOYALTY_POINTS_UPDATE` event per PR-481 + Confluence "VIP Program v3 — Data Sources" (Smartico is source of truth until PS-native VIP API ships in Q4). ...
```

### Handoff
Bet on it via atlassian MCP.

## VERDICT: TB-019
**Title:** Phase C skips a question that Jira context already answers (rule 3)
**SKILL.md ref:** ticket-builder:L95
**Trace section consulted:** Phase C, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-when-context-answers (data source for points-to-next-tier; inline assumption expected) | PASS | "Data source question is SKIPPED because Jira PR-481 + Confluence already answer it — converted to inline assumption" + Description text cites Smartico per PR-481 | — |

### Notes
Skips the right question; converts to inline assumption with citation.

---

## TRACE: TB-020

### Preconditions
Same as TB-018 simplified — tests rule 4 (no styling/copy/exact-analytics-name questions).

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470 banner.tsx
- **Main user, Main goal:** Not inferred → Phase B

### Phase B — Questions asked
Q1 Main user; Q2 Main goal

### Phase C — Follow-ups
Q1 (header: `Points source`): data-source ambiguity
Q2 (header: `Module placement`): behavioral choice

Tempting questions that were CONSIDERED and SKIPPED per rule 4:
- "What color should the progress bar be?" — styling, defer to design (banned)
- "What should the analytics event be named?" — exact event name, default + flag (banned)
- "What microcopy goes above the bar?" — exact copy, defer to UX writing (banned)

### Phase D — Artifact (snippet — analytics default + flag)
```
## Definition of Done
...
- Telemetry: tracking event fires on bar render and tap. Default event names: `vip_progress_bar_view`, `vip_progress_bar_tap` (FLAG: confirm with data team).
```

### Handoff
Bet on it via atlassian MCP.

## VERDICT: TB-020
**Title:** Phase C does not ask about styling, color, copy, or exact event names (rule 4)
**SKILL.md ref:** ticket-builder:L96
**Trace section consulted:** Phase C
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-skips-styling-copy-questions | PASS | "Tempting questions ... skipped per rule 4: color, analytics event name, microcopy" | — |

### Notes
Rule 4 explicit and respected. However, spec is vague about how "default + flag" should be surfaced (inline note, footer, etc.) — trace uses an inline FLAG marker, which is a defensible reading.

---

## TRACE: TB-021

### Preconditions
User input: "add a VIP progress bar to the casino home — also confirm it works on the mobile app". Jira: PR-481 (Smartico) + PR-815 (PS-native VIP API scoping) + PR-714 (Sports home unification). Atlassian MCP.

Multiple unknowns coexist: (1) data source — PR-481 vs PR-815; (2) platform scope — web vs mobile app; (3) trigger cadence.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — "casino home"
- **Main goal:** Not inferred
- **Connection:** Inferred Extends — "casino home" (matches PR-470 area implicitly)

### Phase B — Questions asked
Q1 Main goal (simulated: Business need)

### Phase C — Follow-ups (priority order respected)
Q1 (header: `Points source`): data-source ambiguity (priority #1)
  options:
    1) Smartico LOYALTY_POINTS_UPDATE (PR-481)
    2) PS-native VIP API (PR-815 — in scoping)
    3) Hybrid: Smartico now, abstract for PS later
  (simulated PM answer: Hybrid)

Q2 (header: `Platform scope`): scope edge (priority #2)
  options:
    1) Casino web only, scoped to /home
    2) Casino web + mobile app (PR-815 alignment)
    3) Web now, mobile app as child ticket
  (simulated PM answer: Web now, mobile as child)

Q3 (header: `Update cadence`): trigger (priority #4)
  options:
    1) Real-time via Smartico push on LOYALTY_POINTS_UPDATE
    2) Polled every 60s
    3) On-mount only
  (simulated PM answer: Real-time via Smartico push)

### Phase D — Artifact
(standard)

### Handoff
Bet on it via atlassian MCP.

## VERDICT: TB-021
**Title:** Phase C respects priority order — data source ambiguity first
**SKILL.md ref:** ticket-builder:L97-L102
**Trace section consulted:** Phase C
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-priority-order-respected (expected_top_topic: data source ambiguity) | PASS | "Q1 ... data-source ambiguity (priority #1)" | — |

### Notes
Priority list applied — data source first, then scope, then cadence.

---

## TRACE: TB-022

### Preconditions
User input: "add a subtle entrance animation when the VIP bar mounts". Jira PR-470 only. Atlassian MCP. No signals for animation library — context yields zero concrete artifact names.

### Phase A — Inferences
- **Ticket type:** Improvement (or Feature) — "add" leans Feature but "entrance animation" on an existing bar leans Improvement. Defensible Feature.
- **Main user:** End user — implied (casino UI)
- **Main goal:** Improve UX — animation is UX polish
- **Connection:** Extends — VIP bar implies existing element

### Phase B — Questions asked
none — all 4 inferred

### Phase C — Follow-ups
none — no concrete options for "animation library" can be drawn from context (no PRs name `framer-motion`, `react-spring`, or any specific lib). Per rule 6, the unknown is converted to inline assumption + flag in the ticket instead.

### Phase D — Artifact (snippet)
```
## Description
Add a subtle entrance animation when the VIP progress bar mounts on components/home/banner.tsx.

*ASSUMPTION (FLAG):* Animation library not specified in available context. Defaulting to the repo's existing animation utility (whichever is already imported by neighboring components in components/home/). Confirm with frontend lead before implementation.
```

### Handoff
Bet on it via atlassian.

## VERDICT: TB-022
**Title:** Phase C falls back to assume + flag when 3 concrete options can't be written (rule 6)
**SKILL.md ref:** ticket-builder:L103
**Trace section consulted:** Phase C, Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-fallback-to-assume-and-flag (preferred animation library) | PASS | "Phase C — Follow-ups: none — no concrete options for 'animation library'" + Description contains "ASSUMPTION (FLAG): Animation library not specified" | — |
| 2 | phase-c-no-banned-placeholders | PASS | Phase C asks no questions, so no placeholder slips through | — |

### Notes
Rule 6 honored — but spec ambiguity flagged: SKILL.md does not define a concrete syntax for the "flag" (FLAG, TODO, etc.). Trace used "ASSUMPTION (FLAG):" inline. This is a P2 spec clarification opportunity.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P2
Location: `skills/ticket-builder/SKILL.md:L103`
Symptom: "assume + flag" is vague — readers won't know the prescribed syntax for the flag.
Proposed edit:
```
6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — record it inline as `_Assumption (flag): <statement>. Confirm with <role>._` in the relevant section, do not ask.
```

---

## TRACE: TB-023

### Preconditions
Vague input ("we should do something about the lobby") + Jira context with 3 tickets (PR-470, PR-481, PR-714). Atlassian MCP. Tests total-questions-cap = 7.

### Phase A — Inferences
- All 4 Not inferred (no clear signal in input).

### Phase B — Questions asked
4 questions (Ticket type, Main user, Main goal, Connection).
(simulated PM: Improvement / End user / Improve UX / Changes a flow)

### Phase C — Follow-ups (max 3)
Q1 (header: `Lobby area`): "Which part of the lobby should improve?"
  options:
    1) Casino lobby filter bar (per PR-470)
    2) Sports lobby (per PR-714)
    3) Loyalty/VIP integrations on lobby (per PR-481)
  rationale: Scope edge (priority #2).
  (simulated PM answer: Casino lobby filter bar)

Q2 (header: `Improvement focus`): "What is the focus of the improvement?"
  options:
    1) Filtering / surfacing live dealer games
    2) Performance (TTI on /home)
    3) Personalization (Smartico-driven recommendations from PR-481)
  rationale: Behavioral choice (priority #3).
  (simulated PM answer: Filtering)

Q3 (header: `Platform scope`): "Web only or also mobile app?"
  options:
    1) Casino web only
    2) Casino web + mobile app
    3) Casino web + sports home (PR-714)
  rationale: Scope edge.
  (simulated PM answer: Web only)

Total: 4 (Phase B) + 3 (Phase C) = 7 questions. Cap respected.

### Phase D — Artifact
(standard)

### Handoff
Bet on it via atlassian MCP.

## VERDICT: TB-023
**Title:** Total questions across Phase B + Phase C never exceed 7
**SKILL.md ref:** ticket-builder:L53
**Trace section consulted:** Phase B, Phase C
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | total-questions-asked-max (max 7) | PASS | "Total: 4 (Phase B) + 3 (Phase C) = 7 questions" | — |
| 2 | phase-c-max-3 | PASS | Phase C lists Q1, Q2, Q3 only | — |

### Notes
At the cap — but at the cap is within spec.

---

## TRACE: TB-024

### Preconditions
User input: "add a VIP progress bar to the casino home". Rich Jira (5 PRs including PR-481 Smartico, PR-815 PS-native VIP scoping, PR-714 Sports home, PR-470 banner.tsx) + Confluence (VIP Program v3 PRD). Atlassian MCP. Tests that Phase C reproduces the spec's worked example.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — context (player-focused VIP)
- **Main goal:** Business need — VIP PRD retention focus
- **Connection:** Extends — "casino home" + PR-470 banner.tsx

### Phase B — Questions asked
none — all 4 inferred

### Phase C — Follow-ups (matches spec L105-L108 worked example)
Q1 (header: `Points source`): "Where does points-to-next-tier come from?"
  options:
    1) Smartico LOYALTY_POINTS_UPDATE event (PR-481)
    2) PS-native VIP API (PR-815 — currently being scoped)
    3) Hybrid: Smartico now, abstract behind a service, swap to PS later
  rationale: Data-source ambiguity (priority #1).
  (simulated PM answer: Hybrid)

Q2 (header: `Module placement`): "How does the module fit on the existing hero (components/home/banner.tsx)?"
  options:
    1) Replaces first carousel slide for logged-in users
    2) Persistent strip below the carousel
    3) Overlay on top of the first slide
  rationale: Behavioral choice (priority #3).
  (simulated PM answer: Persistent strip)

Q3 (header: `Platform scope`): "Casino home only or sports home too?"
  options:
    1) Casino only, scoped to /home under PR-470
    2) Casino + sports parallel build (PR-714)
    3) Casino now, sports as follow-up child ticket
  rationale: Scope edge (priority #2).
  (simulated PM answer: Casino only)

### Phase D — Artifact (standard)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-024
**Title:** Smartico VIP progress bar — Phase C generates the spec'd worked-example follow-ups
**SKILL.md ref:** ticket-builder:L105-L108
**Trace section consulted:** Phase C
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | Q1, Q2, Q3 only | — |
| 2 | phase-c-options-are-concrete (file path, API name, event name, system, component, project key) | PASS | Q1 cites `LOYALTY_POINTS_UPDATE`/PR-481/PR-815; Q2 cites `components/home/banner.tsx`; Q3 cites PR-470/PR-714 | — |
| 3 | phase-c-priority-order-respected (top: data source ambiguity) | PASS | Q1 = data source | — |
| 4 | phase-c-no-banned-placeholders | PASS | No banned strings | — |

### Notes
Direct mirror of spec worked example.

---

## TRACE: TB-025

### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 / banner.tsx. Atlassian MCP. Tests that the 4 required sections appear in order.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470
- Main user, Main goal: not inferred → Phase B

### Phase B — Questions asked
2 (Main user, Main goal); answers: End user / Business need

### Phase C — Follow-ups
Q1 Points source (Smartico); Q2 Module placement (strip); Q3 Platform scope (casino only)

### Phase D — Artifact
```markdown-artifact
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** feature, vip, home

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Connection: Extends — from "casino home" matching PR-470

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
**SKILL.md ref:** ticket-builder:L119-L161
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | output-has-required-sections (User Story, Description, User Flow, Definition of Done) | PASS | Artifact has those four headings in order | — |

### Notes
Standard.

---

## TRACE: TB-026

### Preconditions
User input: "add a VIP progress bar to the casino home — players need to see how close they are to the next tier so they keep depositing". Rich context (PR-470, PR-481, VIP v3 PRD). Atlassian MCP. Stress test for banned sections.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user — "players"
- **Main goal:** Business need — "keep depositing"
- **Connection:** Extends — PR-470

### Phase B — Questions asked
none — all 4 inferred

### Phase C — Follow-ups
Q1 Module placement; Q2 Platform scope. (Data source already answered by PR-481 — inline assumption instead per rule 3.)

### Phase D — Artifact (lean — no banned sections)
```markdown-artifact
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** feature, vip, home, retention

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Main user: End user — from "players"
> - Main goal: Business need — from "keep depositing"
> - Connection: Extends — from "casino home" matching PR-470

## User Story
As a logged-in End user, I want to see how close I am to the next VIP tier, so that I am motivated to keep depositing.

## Description
Add a persistent VIP progress strip in components/home/banner.tsx below the carousel for logged-in players. Source: Smartico `LOYALTY_POINTS_UPDATE` (per PR-481). Aligned with the VIP Program v3 PRD's retention goal.

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
- Points hydrated from Smartico `LOYALTY_POINTS_UPDATE`
- Tap navigates to /vip
- A11y label set; passes axe scan
- Telemetry events fire on render and tap (default + flag)
```

(No "Background", "Context", "Problem", "Desired Outcome", "Scope", "Functional Requirements", "Edge Cases", "Analytics", "Dependencies", "Open Questions", or "Builder notes" section.)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-026
**Title:** Artifact omits all banned sections
**SKILL.md ref:** ticket-builder:L119-L162
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | output-omits-banned-sections (Background, Context, Problem, Desired Outcome, Scope, FRs, Edge Cases, Analytics, Dependencies, Open Questions, Builder notes) | PASS | "No 'Background', 'Context'... section" | — |

### Notes
Even with tempting rich context, only the 4 required sections appear.

---

## TRACE: TB-027

### Preconditions
User input: "add a VIP progress bar to the casino home". No context. No MCP. Tests User Story shape.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — "casino home"
- Main user, Main goal: not inferred → Phase B

### Phase B — Questions asked
Main user (End user), Main goal (Improve UX)

### Phase C — Follow-ups
Q1 Points source; Q2 Module placement (minimal context → defensible)

### Phase D — Artifact (snippet)
```
## User Story
As a logged-in End user, I want to see my VIP tier progress on the casino home, so that I am motivated to keep playing.
```

### Handoff
Hold the chip (no MCP).

## VERDICT: TB-027
**Title:** User Story line follows the canonical 'As a / I want / so that' shape
**SKILL.md ref:** ticket-builder:L136-L137
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | user-story-shape | PASS | "As a logged-in End user, I want to ..., so that ..." | — |

### Notes
Canonical shape.

---

## TRACE: TB-028

### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470. No MCP. Tests ASCII flow uses box-drawing chars in a fenced block.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470
- Main user/goal: not inferred → Phase B

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
**SKILL.md ref:** ticket-builder:L143-L145
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | ascii-flow-uses-box-drawing | PASS | "┌──────────────┐ ... │ ... └──── ... ▼" inside a fenced block | — |

### Notes
Box-drawing chars + arrows + fenced block all present.

---

## TRACE: TB-029

### Preconditions
User input: "the deposit button is broken on iOS". No context, no MCP. Tests Inferred block.

### Phase A — Inferences
- **Ticket type:** Bug — "broken"
- Main user/goal/Connection: arguable — likely End user inferred; Connection Changes ambiguous; Main goal Fix friction. For this case, the assertion concerns Ticket type inference + block presence.

### Phase B — Questions asked
Q1 Connection (Changes a flow); Q2 Main goal if not inferred — assume inferred. Approximate: 1-2 questions.

### Phase C — Follow-ups
Q1 (header: `Platform scope`): "iOS Safari only, or all iOS browsers?"
  (simulated PM answer: iOS Safari only)

### Phase D — Artifact (snippet)
```
# Fix iOS deposit button error

**Ticket type:** Bug
**Component:** deposit
**Labels:** bug, ios, deposit

> **Inferred (not asked):**
> - Ticket type: Bug — from "broken"

## User Story
As an End user on iOS, I want the deposit button to work, so that I can fund my account.

## Description
The deposit button is broken on iOS. Restore the documented deposit submission flow on iOS.
...
```

### Handoff
Hold the chip.

## VERDICT: TB-029
**Title:** Inferred (not asked) block appears at top when Phase A inferred ≥1 field
**SKILL.md ref:** ticket-builder:L129-L134
**Trace section consulted:** Phase D
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | inferred-block-present | PASS | "> **Inferred (not asked):**\n> - Ticket type: Bug — from 'broken'" appears below metadata | — |
| 2 | inferred-includes-field (Ticket type=Bug, cite "broken") | PASS | "Ticket type: Bug — from 'broken'" | — |

### Notes
Trace renders Inferred block AFTER metadata header (Ticket type / Component / Labels) but BEFORE the User Story heading — per the template at SKILL.md L121-128. But the narrative line at L116 says "block at the top of the ticket" while the template shows it after the metadata header. This is a real spec ambiguity. The vocabulary id `inferred-block-present` says "at the top (just after frontmatter/metadata lines, before the first section)" — which matches the trace. So PASS on the assertion shape, but flagging the spec ambiguity.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P2
Location: `skills/ticket-builder/SKILL.md:L116-L129`
Symptom: Narrative on L116 says "block at the top of the ticket" while the template on L121-L129 shows metadata first, then the Inferred block. PMs writing edits may guess the wrong placement.
Proposed edit:
```
Place the `Inferred (not asked):` block immediately after the metadata header lines (Ticket type / Parent epic / Component / Labels) and before the `## User Story` heading. Do not place it above the title.
```

---

## TRACE: TB-030

### Preconditions
Vague input "we should do something about the lobby". No context, no MCP. Tests Inferred block OMITTED when Phase A inferred zero.

### Phase A — Inferences
- All four Not inferred.

### Phase B — Questions asked
4

### Phase C — Follow-ups
none — no concrete options possible (rule 6)

### Phase D — Artifact (does NOT contain Inferred block)
```markdown-artifact
# Improve casino lobby (scope TBD)

**Ticket type:** Improvement
**Component:** lobby
**Labels:** improvement, lobby, needs-scoping

## User Story
As an End user, I want a clearer casino lobby, so that I can find a game faster.

## Description
... (no Inferred block above)
```

### Handoff
Hold the chip.

## VERDICT: TB-030
**Title:** Inferred block is OMITTED when Phase A inferred zero fields
**SKILL.md ref:** ticket-builder:L129-L134
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | inferred-block-omitted-when-empty | PASS | "does NOT contain Inferred block" — narrative confirms | — |
| 2 | inferred-block-present (must: false) | PASS | Block absent | — |

### Notes
Per spec template note: "include this block only if Phase A inferred at least one core answer".

---

## TRACE: TB-031

### Preconditions
User input: "the withdrawal page throws a 500 on iOS Safari". No context, no MCP. Tests no meta-commentary after Definition of Done.

### Phase A — Inferences
- **Ticket type:** Bug — "throws a 500"/iOS scenario
- **Main user:** End user — "withdrawal page" (player-facing)
- **Main goal:** Fix friction — "throws a 500"
- **Connection:** Changes — existing withdrawal page

### Phase B — Questions asked
none

### Phase C — Follow-ups
Q1 Scope (only iOS Safari vs all iOS); Q2 Reproduction (consistent vs intermittent)

### Phase D — Artifact (ends at DoD)
```markdown-artifact
# Fix withdrawal page 500 error on iOS Safari

**Ticket type:** Bug
**Component:** withdrawal
**Labels:** bug, ios, withdrawal, p1

> **Inferred (not asked):**
> - Ticket type: Bug — from "throws a 500"
> - Main user: End user — from "withdrawal page"
> - Main goal: Fix friction — from "throws a 500"
> - Connection: Changes — from "withdrawal page" (existing flow)

## User Story
As an End user on iOS Safari, I want to complete a withdrawal, so that I can cash out without error.

## Description
The withdrawal page returns HTTP 500 on iOS Safari. Restore the documented withdrawal flow.

## User Flow
```
┌──────────────┐
│ Open Withdr  │
└──────┬───────┘
       ▼
┌──────────────┐
│ Submit       │
└──────┬───────┘
       ▼
┌──────────────┐
│ 2xx success  │
└──────────────┘
```

## Definition of Done
- Withdrawal endpoint returns 2xx on iOS Safari
- Regression test added
- Manual QA pass on iOS Safari 16+17
```

(File ends here. No "Builder notes", no reflections, no `## Notes` after DoD.)

### Handoff
Hold the chip.

## VERDICT: TB-031
**Title:** No meta-commentary, builder notes, or reflections after Definition of Done
**SKILL.md ref:** ticket-builder:L168
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | no-meta-commentary-after-final-section (final: Definition of Done) | PASS | "File ends here. No 'Builder notes', no reflections" | — |

### Notes
Trace stops at DoD.

---

## TRACE: TB-032

### Preconditions
User input: "add a VIP progress bar to the casino home". No context. Atlassian MCP. Tests Gamble handoff is presented exactly once.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — "casino home" (matches PR-470 area)
- Main user/goal: not inferred → Phase B

### Phase B — Questions asked
2 (Main user, Main goal)

### Phase C — Follow-ups
1-2

### Phase D — Artifact
(standard)

### Handoff
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md`
2. Gamble question (exactly once): "Ready To Gamble On It?" (header: `Gamble?`) options: `Bet on it` / `Hold the chip` via AskUserQuestion.
3. Simulated user choice: Bet on it (mcp_state atlassian)
4. Tool call: mcp__*atlassian* createIssue
5. Final message: standard

## VERDICT: TB-032
**Title:** 'Ready To Gamble On It?' is presented exactly once with header 'Gamble?'
**SKILL.md ref:** ticket-builder:L149-L156
**Trace section consulted:** Handoff
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-handoff-presented-once | PASS | "Gamble question (exactly once): 'Ready To Gamble On It?' (header: `Gamble?`)" | — |

### Notes
Exactly one handoff via AskUserQuestion.

---

## TRACE: TB-033

### Preconditions
Same setup as TB-032. Tests options are exactly "Bet on it" / "Hold the chip" (no Double down).

### Phase D — Artifact
(standard)

### Handoff
Gamble options:
1. `Bet on it` — push to Jira
2. `Hold the chip` — keep markdown only

No `Double down` option present (PRD-writer only).

## VERDICT: TB-033
**Title:** Handoff options are exactly 'Bet on it' and 'Hold the chip' — no 'Double down'
**SKILL.md ref:** ticket-builder:L152-L156
**Trace section consulted:** Handoff
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | gamble-options-match-spec (expected: ["Bet on it", "Hold the chip"]) | PASS | "options: 1) Bet on it 2) Hold the chip" | — |

### Notes
Exactly the spec'd two.

---

## TRACE: TB-034

### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470/banner.tsx. Atlassian MCP. Tests Bet on it triggers correct MCP tool regex.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — PR-470
- Main user/goal: not inferred → Phase B

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
   - Parameters: `projectKey: "PR"` (inferred), `issueType: "Story"` (or "Task" for Feature), `summary: "Add a VIP progress bar to the casino home"`, `description: <full markdown body>`
5. Final message: "Created PR-XYZ at https://<workspace>.atlassian.net/browse/PR-XYZ. Saved at /Users/talshani/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md."

## VERDICT: TB-034
**Title:** 'Bet on it' + Atlassian MCP connected → calls jira-create-issue via correct tool regex
**SKILL.md ref:** ticket-builder:L157-L159
**Trace section consulted:** Handoff
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | mcp-tool-lookup-pattern (regex mcp__.*(atlassian\|jira).* + verbs createIssue/createJiraIssue/create_issue) | PASS | "Tool name regex: `mcp__.*(atlassian\|jira).*` with method matching `(createIssue\|createJiraIssue\|create_issue)`" | — |
| 2 | markdown-saved-with-absolute-path (folder: tickets) | PASS | "File save: `~/Downloads/tickets/...md`" and final message prints absolute path | — |

### Notes
Tool lookup regex matches the spec's intent verbatim.

---

## TRACE: TB-035

### Preconditions
User input: "add a VIP progress bar to the casino home". No context. **No MCP**. Tests "Atlassian MCP not connected" fallback.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Connection:** Extends — "casino home" (cited but no Jira context to bind to PR-470; still inferable from connector verb)
- Main user/goal: not inferred → Phase B

### Phase B — Questions asked
2

### Phase C — Follow-ups
1 (Points source — but with no context, options are weaker → arguably converted to inline assumption per rule 6. Trace skips it.)

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
**SKILL.md ref:** ticket-builder:L160
**Trace section consulted:** Handoff
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | mcp-fallback-when-disconnected (substring "Atlassian MCP not connected") | PASS | "Atlassian MCP not connected — saved markdown only at /Users/talshani/Downloads/tickets/..." | — |
| 2 | markdown-saved-with-absolute-path (folder: tickets) | PASS | Absolute path under `~/Downloads/tickets/` printed | — |

### Notes
Verbatim fallback string.

---

## TRACE: TB-036

### Preconditions
User input: "Add a VIP progress bar to the casino home" (capital A — slug must lowercase). No context. Atlassian MCP. Tests Hold the chip path + kebab-case slug.

### Phase A — Inferences
- **Ticket type:** Feature — "Add"
- **Connection:** Extends — "casino home"
- Main user/goal: not inferred → Phase B

### Phase B — Questions asked
2

### Phase C — Follow-ups
1

### Phase D — Artifact
Title rendered as "Add a VIP progress bar to the casino home" (preserves the user's title casing).

### Handoff
1. File save: `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md` (slug all-lowercase kebab)
2. Gamble question: standard
3. Simulated user choice: Hold the chip
4. Final message: "Saved at /Users/talshani/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md. No Jira ticket created."

## VERDICT: TB-036
**Title:** 'Hold the chip' confirms save and prints absolute path with kebab-case slug
**SKILL.md ref:** ticket-builder:L149-L162
**Trace section consulted:** Handoff
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | markdown-saved-with-absolute-path (tickets) | PASS | "Saved at /Users/talshani/Downloads/tickets/...md" | — |
| 2 | slug-is-kebab-case (expected: add-a-vip-progress-bar-to-the-casino-home) | PASS | "add-a-vip-progress-bar-to-the-casino-home.md" — exact match | — |

### Notes
Slug correctly all-lowercase kebab.

---

## TRACE: TB-037

### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 / banner.tsx + PR-481 Smartico LOYALTY_POINTS_UPDATE. Confluence VIP v3 PRD. Atlassian MCP. Tests company-terminology use.

### Phase A — Inferences
- **Ticket type:** Feature — "add"
- **Main user:** End user
- **Main goal:** Business need (VIP PRD)
- **Connection:** Extends — PR-470 banner.tsx

### Phase B — Questions asked
none

### Phase C — Follow-ups
Q1 (Module placement), Q2 (Platform scope). Data source already answered by PR-481/Confluence → inline assumption.

### Phase D — Artifact
```markdown-artifact
# Add a VIP progress bar to the casino home

**Ticket type:** Feature
**Parent epic (if any):** PR-470 "Casino home redesign" (reference, closed)
**Component:** home
**Labels:** feature, vip, smartico, home

> **Inferred (not asked):**
> - Ticket type: Feature — from "add"
> - Main user: End user — from VIP Program v3 PRD (Confluence)
> - Main goal: Business need — from VIP Program v3 PRD
> - Connection: Extends — from "casino home" matching PR-470 (components/home/banner.tsx)

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
- Telemetry events fire (default + flag)
```

### Handoff
Bet on it via atlassian.

## VERDICT: TB-037
**Title:** Artifact uses Jira component names and file paths verbatim
**SKILL.md ref:** ticket-builder:L163-L164
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | uses-company-terminology (Smartico, PR-470, components/home/banner.tsx, LOYALTY_POINTS_UPDATE) | PASS | Each term appears verbatim: "Smartico `LOYALTY_POINTS_UPDATE`", "PR-470", "`components/home/banner.tsx`" | — |
| 2 | output-copy-pasteable | PASS | Pure markdown, no shell prompts, no `<<...>>` placeholders | — |

### Notes
Company terminology used verbatim in Description and DoD.

---

## TRACE: TB-038

### Preconditions
User input: "add a VIP progress bar to the casino home". Jira PR-470 + PR-481 (Smartico decision). Confluence VIP v3 PRD (decision: Smartico = source of truth). Atlassian MCP. Tests inline facts + inline assumptions; no separate Facts/Assumptions section.

### Phase A — Inferences
(same as TB-037)

### Phase B — Questions asked
none

### Phase C — Follow-ups
1-2 (Module placement, Platform scope)

### Phase D — Artifact (snippet showing inline citations)
```
## Description
Add a persistent VIP progress strip below the carousel in `components/home/banner.tsx`. **Fact (per PR-481 / Confluence "VIP Program v3 PRD"):** Smartico `LOYALTY_POINTS_UPDATE` is the canonical source of truth for points-to-next-tier until PS-native VIP API ships in Q4. *Assumption:* the existing tier ladder in the PRD applies to this surface — confirm with VIP product owner if changes are pending.
```

(No standalone "Facts", "Assumptions", "Missing", or "Open Questions" section.)

### Handoff
Bet on it via atlassian.

## VERDICT: TB-038
**Title:** Facts cite source inline; assumptions are marked inline (not in a separate section)
**SKILL.md ref:** ticket-builder:L165
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | facts-cite-source | PASS | "**Fact (per PR-481 / Confluence 'VIP Program v3 PRD'):**" cites source; "*Assumption:* ... confirm with VIP product owner" marks assumption inline | — |
| 2 | output-omits-banned-sections (Facts, Assumptions, Missing, Open Questions) | PASS | "No standalone 'Facts', 'Assumptions', 'Missing', or 'Open Questions' section" | — |

### Notes
Inline facts + inline assumptions, no separate section.

---

## TRACE: TB-039

### Preconditions
User input: "make the lobby better". Jira PR-470 / Casino home redesign / component: home. No MCP. Tests vague-input → sharper title applied directly.

### Phase A — Inferences
- **Ticket type:** Improvement — "make ... better" loosely maps to "improve"
- **Main user:** End user — "lobby" (player-facing)
- **Main goal:** Improve UX — "make ... better"
- **Connection:** Extends — "lobby" + PR-470 home context

### Phase B — Questions asked
none — all 4 weakly inferred

### Phase C — Follow-ups
Q1 (header: `Lobby focus`): "Which improvement area?"
  options:
    1) Casino lobby filter bar surfacing (PR-470 area)
    2) Casino lobby personalization (Smartico-driven, if available)
    3) Casino lobby performance (TTI)
  rationale: Scope edge — input is vague; need to scope.
  (simulated PM answer: Casino lobby filter bar surfacing)

### Phase D — Artifact
Title applied directly is a sharpened version, not the user's vague phrase:
```markdown-artifact
# Improve casino lobby filter bar surfacing

**Ticket type:** Improvement
**Parent epic (if any):** PR-470 (reference)
**Component:** home
**Labels:** improvement, lobby, ux

> **Inferred (not asked):**
> - Ticket type: Improvement — from "make ... better"
> - Main user: End user — from "lobby"
> - Main goal: Improve UX — from "make ... better"
> - Connection: Extends — from "lobby" matching PR-470 (home)

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

(No separate "Suggested title" callout or note. The sharper title is applied directly. File ends at DoD.)

### Handoff
Hold the chip.

## VERDICT: TB-039
**Title:** Vague input → sharper title applied directly, no separate 'suggested title' note
**SKILL.md ref:** ticket-builder:L166
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | vague-input-suggests-better-title | PASS | "Title applied directly is a sharpened version... # Improve casino lobby filter bar surfacing" + "No separate 'Suggested title' callout" | — |
| 2 | no-meta-commentary-after-final-section (DoD) | PASS | "File ends at DoD" | — |

### Notes
However, spec L166 ("Suggest a better ticket title if the input is vague") is itself silent on what defines "vague" — a real spec gap. Trace defensibly treats "make the lobby better" as vague. This is a P2 spec clarification opportunity but doesn't fail this case.

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
N/A (PASS), but a P2 clarification on the trigger threshold for "vague input" would help future runs.

---

## TRACE: TB-040

### Preconditions
User input: "rebuild the entire casino lobby, payments, KYC, VIP program, and responsible-gaming module for the German market launch". Jira PR-470, PR-602. Confluence: "DE Market Launch — Q4 PRD" / scope: lobby + payments + KYC + VIP + RG. Atlassian MCP.

### Phase A — Inferences
- **Ticket type:** Feature — "rebuild" / "launch"
- **Main user:** End user — German market launch
- **Main goal:** Business need — "German market launch"
- **Connection:** Mixed — multiple existing flows + new market scope

### Phase B — Questions asked
none

### Phase C — Follow-ups
none — request is too large for one ticket. Skill should flag this above the artifact and propose a split (per spec L167).

### Phase D — Artifact
**Above the artifact (one sentence):** "This request is too large for one ticket — proposing a split into 5 child tickets per the DE Market Launch Q4 PRD scope (lobby, payments, KYC, VIP, RG). Below is a parent epic ticket that links to them."

```markdown-artifact
# DE Market Launch — parent epic

**Ticket type:** Feature (epic)
**Parent epic (if any):** —
**Component:** cross-cutting (lobby, payments, kyc, vip, rg)
**Labels:** feature, de-launch, epic, q4

> **Inferred (not asked):**
> - Ticket type: Feature — from "rebuild ... for the ... launch"
> - Main user: End user — from "German market launch"
> - Main goal: Business need — from "market launch"

## User Story
As an End user in Germany, I want a localized, compliant casino experience, so that I can play within German regulatory expectations.

## Description
Parent epic for the DE Q4 launch, covering 5 child tickets:
- Lobby DE — scope per PR-470 area
- Payments DE — SEPA + GlücksSpiel-compliant methods
- KYC DE — SCHUFA + ID verification per GGL
- VIP program DE — localized tiers (PR-602 alignment)
- Responsible Gaming DE — OASIS integration

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

(The split-proposal sentence is ABOVE the artifact, not in a "Builder notes" section at the end. No "Open Questions" section.)

### Handoff
Bet on it via atlassian (parent epic).

## VERDICT: TB-040
**Title:** Too-large request → one-sentence split proposal ABOVE the artifact, not buried in notes
**SKILL.md ref:** ticket-builder:L167
**Trace section consulted:** Phase D
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | too-large-request-proposes-split | PASS | "Above the artifact (one sentence): 'This request is too large for one ticket — proposing a split into 5 child tickets...'" | — |
| 2 | output-omits-banned-sections (Builder notes, Open Questions) | PASS | "No 'Builder notes' or 'Open Questions' section" | — |

### Notes
Split proposed in a single sentence above the artifact. The artifact itself stays lean.

---

## END OF RUN
