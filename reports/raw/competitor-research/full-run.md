# competitor-research — Raw Run
Date: 2026-05-23
SKILL.md path: /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/competitor-research/SKILL.md
Cases: 40 (CR-001…CR-040)

## Summary
- PASS: 34
- PARTIAL: 4
- FAIL: 2
- Overall verdict: Yellow (PASS rate 85%, several real spec defects identified)

## Cases

---

## TRACE: CR-001

### Preconditions
User input: "look at how Stake handles signup vs us". No Jira/Confluence context, no active memory, no MCP connected. The case is a sanity check on SKILL.md frontmatter.

### Phase A — Inferences
- **Focus:** Inferred to "Onboarding" — citation: "signup"
- **Competitors:** Inferred to "Stake" — citation: "Stake"
- **Output emphasis:** Not inferred (will fall through to Phase B)
- **Depth:** Not inferred (will fall through to Phase B)

### Phase B — Questions asked
Q1 (header: Output): "What should the report emphasize?"
  options: 1) Comparison + opportunities 2) Screenshots + UX notes 3) Strategic recommendations
  (simulated PM answer: Comparison + opportunities)

Q2 (header: Depth): "How deep should the research go?"
  options: 1) Quick scan 2) Detailed comparison 3) Deep UX flow
  (simulated PM answer: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): "What region for this research?"
  options: 1) 21.com licensed markets only (Curacao + MGA) 2) Global, no jurisdiction filter 3) LATAM + Africa (CS_Africa / CSO spaces)
  rationale: Region scope is the top-priority CR follow-up; user didn't specify a market.
  (simulated PM answer: Global, no jurisdiction filter)

### Playwright actions (if mcp_state includes playwright)
Playwright not available — no screenshots captured; §1 Research Scope will note this.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
> - Competitors: Stake — from "Stake" in prompt

| Field | Value |
|---|---|
| **Status** | Draft v1.0 |
| **Author** | Tal |
| **Date** | 2026-05-23 |
| **Depth** | Detailed comparison |
| **Region scope** | global |

## 1. Research Scope
- Stake homepage + signup flow; comparison vs 21.com signup
- Method: Playwright not available — no screenshots captured; text-only observations from public Stake pages
- Jira/Confluence context not available (no MCP connected)
- 4 surfaces compared in matrix below

## 2. Competitors Reviewed
- Stake — https://stake.com

## 3. Executive Summary
Stake's signup is a single-page, crypto-native flow that minimizes form friction versus 21.com's multi-step KYC-first approach. Stake leans on social-proof CTAs ("Join 25M+ players") and inline bonus presentation, while 21.com surfaces compliance copy first. Three opportunities: shorten the signup form, surface bonus inline, defer KYC to first deposit.

## 4. Comparison Table
| Area | Our Product (21.com) | Stake | Opportunity |
|---|---|---|---|
| Homepage messaging | Compliance + license-first | Social proof + bonus-first | Lead with social proof above the fold |
| Signup flow | Multi-step (email → KYC → deposit) | Single-page (email + password) | Collapse to one screen, defer KYC |
| Pricing | Welcome bonus T&C visible | Welcome bonus inline on signup | Surface bonus value pre-form |
| Trust signals | License badges + responsible-gaming icons | "25M+ players", live-win ticker | Add live activity widget |
| Core feature | Lobby grid | Lobby grid + crypto-native ticker | Add crypto-native trust signals |

## 5. UX Flow Notes
### Stake
- Single-field email entry above the fold (no screenshot captured — Playwright unavailable)
- Bonus inline shown as "$3,000 + 200 free spins" before form submission
- KYC deferred to first deposit (mentioned in TOS, not signup form)

## 6. Key Patterns
**Table stakes:** License footer, responsible-gaming icons, T&C link, mobile-responsive form.
**Differentiation:** Stake's social-proof header ("25M+ players"), inline bonus pre-form, KYC deferral.

## 7. Gaps & Opportunities
- **Surface bonus value pre-form** — Missing: 21.com hides bonus behind T&C link. Why it matters: Stake's bonus inline likely lifts signup conversion. Action: A/B test inline bonus reveal on 21.com signup page.
- **Defer KYC to first deposit** — Missing: 21.com asks KYC upfront. Why it matters: Stake's flow has fewer abandon points. Action: PRD on KYC deferral, validate with compliance team.
- **Add live activity / social proof widget** — Missing: 21.com lacks "live wins" or counter. Why it matters: Stake uses this to justify scale. Action: scope a homepage social-proof widget.
```

### Handoff
1. File save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Screenshots subdir: `~/Downloads/competitor-research/onboarding/screenshots/` (empty — no Playwright)
3. Gamble question: "Ready To Gamble On It?" (header: Gamble?) options: Bet on it / Hold the chip (NO Double down)
4. Simulated user choice: Hold the chip (no atlassian MCP)
5. Tool call: none (Atlassian MCP not connected)
6. Final message: "Saved at /Users/talshani/Downloads/competitor-research/onboarding-2026-05-23.md. No Confluence page created."

### Memory caching
- Memory file: `~/.claude/memory/21com.md` (or whatever active project slug — undefined here since active_memory is null)
- Action: no action — no project slug resolved, no memory to update; competitor list came only from runtime prompt

## VERDICT: CR-001
**Title:** SKILL.md frontmatter parses as valid YAML with name and description
**SKILL.md ref:** competitor-research:L1-L5
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-yaml-valid | PASS | Skill loaded successfully via Skill tool; description begins "Run structured competitor research..." (loaded by harness as valid frontmatter) | — |

### Notes
This is purely a static check on SKILL.md. The skill loaded correctly via the Skill tool, confirming the frontmatter parses and contains the required fields. Trace is informational only.

---

## TRACE: CR-002

### Preconditions
User input: "what are other crypto casinos doing on the homepage that we aren't?". No context, no memory, no MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Homepage" — citation: "homepage"
- **Competitors:** Not inferred (will fall through to Phase B)
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Targets): "Which competitors should be included?"
  options: 1) Memory default (no memory — generic list) 2) Memory + best-in-class 3) Custom list — I'll provide URLs at runtime
  (simulated PM answer: Custom list)
Q2 (header: Output): "What should the report emphasize?" options as spec. (sim: Comparison + opportunities)
Q3 (header: Depth): "How deep should the research go?" options as spec. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete region options. (sim: Global)

### Playwright actions
Playwright not available — §1 will note this.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Homepage
> **Inferred (not asked):**
> - Focus: Homepage — from "homepage"

| Field | Value |
|---|---|
| **Status** | Draft v1.0 |
| **Author** | Tal |
| **Date** | 2026-05-23 |
| **Depth** | Detailed comparison |
| **Region scope** | global |

## 1. Research Scope
- Crypto-casino homepages of 3 competitors (PM provided at runtime)
- Method: Playwright not available — no screenshots captured
- No Jira/Confluence context (no MCP)

## 2. Competitors Reviewed
- (PM-provided list)

## 3. Executive Summary
[...]

## 4. Comparison Table
| Area | Our Product | Comp A | Comp B | Comp C | Opportunity |
|---|---|---|---|---|---|
| Homepage messaging | ... | ... | ... | ... | ... |
| Signup flow | ... | ... | ... | ... | ... |
| Pricing | ... | ... | ... | ... | ... |
| Trust signals | ... | ... | ... | ... | ... |
| Core feature | ... | ... | ... | ... | ... |

## 5. UX Flow Notes
[per competitor]

## 6. Key Patterns
**Table stakes:** ...
**Differentiation:** ...

## 7. Gaps & Opportunities
- ...
```

### Handoff
1. File save: `~/Downloads/competitor-research/homepage-2026-05-23.md`
2. Gamble: Bet on it / Hold the chip
3. Simulated: Hold the chip
4. Final: "Saved at <path>. No Confluence page created."

### Memory caching
- Action: Phase B asked Competitors; append a `**Competitors:**` line with PM-provided list to `~/.claude/memory/<project-slug>.md` before rendering report.

## VERDICT: CR-002
**Title:** Description begins with 'Use when' trigger phrase
**SKILL.md ref:** competitor-research:L3-L5
**Overall:** FAIL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | frontmatter-description-trigger | FAIL | SKILL.md `description` starts with "Run structured competitor research..." not "Use when..." | Spec violation per pass-criteria-vocabulary "frontmatter-description-trigger". |

### Notes
The loaded SKILL.md description opens with "Run structured competitor research against a known competitor list and produce consistent competitive insights..." — it does NOT begin with the literal phrase "Use when". This is a real defect against the assertion vocabulary's `frontmatter-description-trigger`.

### Suggested SKILL.md edit
Priority: P1
Location: skills/competitor-research/SKILL.md frontmatter (description field)
Symptom: Description does not start with "Use when" so Claude's intent matcher cannot rely on the canonical trigger phrase.
Proposed edit:
```
description: Use when the user wants competitor research against a known competitor list — runs structured Phase A/B/C interview, optionally uses Playwright to capture screenshots, and returns a lean 7-section comparison report. Research-only — does NOT create Jira tickets.
```

---

## TRACE: CR-003

### Preconditions
User input: "I want a competitive scan of Stake's loyalty program". No context, no memory, no MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Core feature experience (Loyalty)" — citation: "loyalty program"
- **Competitors:** Inferred to "Stake" — citation: "Stake"
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard options. (sim: Comparison + opportunities)
Q2 (header: Depth): standard options. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete options. (sim: Global)
Q2 (header: Sources): "Include third-party reviews?" — Direct only / Direct + Trustpilot/AskGamblers / Direct + CasinoMeister. (sim: Direct only)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Loyalty Program
... (7 sections; ends at §7 Gaps & Opportunities; no Jira section)
```

### Handoff
1. Save path: `~/Downloads/competitor-research/loyalty-program-2026-05-23.md`
2. Gamble options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip (no MCP)
4. Final: "Saved at <path>. No Confluence page created."

### Memory caching
- Action: no memory at all yet for this project; if a project slug were resolved, would append Competitors line. Since none resolved, prompt the user inline.

## VERDICT: CR-003
**Title:** Description names output type and clarifies research-only (no Jira tickets)
**SKILL.md ref:** competitor-research:L3-L5
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | frontmatter-description-names-output | PARTIAL | Description names "structured competitor research" and "competitive insights" but does NOT use the literal phrase "7-section comparison report" | Description does not name the canonical output type per spec. |
| 2 | cr-no-jira-tickets-generated | PASS | SKILL.md L242-L244 explicitly states "research-only. It does NOT create Jira tickets." Artifact ends at §7 Gaps & Opportunities. | — |

### Notes
Body of SKILL.md is correct (research-only, no Jira), but the description string does not explicitly say "7-section comparison report" nor "research-only — does NOT create Jira tickets" in the frontmatter. The constraint is in the body text rather than the discoverable description.

### Suggested SKILL.md edit
Priority: P1
Location: skills/competitor-research/SKILL.md frontmatter (description)
Symptom: Frontmatter description does not name the 7-section comparison report nor clarify research-only status.
Proposed edit:
```
description: Use when the user wants competitor research. Returns a lean 7-section comparison report adapted to depth and company format. Research-only — does NOT create Jira tickets.
```

---

## TRACE: CR-004

### Preconditions
User input: "compare our signup to competitors — what are the leaders doing differently?". Active memory has 21com competitors (Stake, 1Xbet, Rollbit, Bc.Game). No MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Onboarding" — citation: "signup"
- **Competitors:** Inferred to "Stake, 1Xbet, Rollbit, Bc.Game" — citation: "memory `~/.claude/memory/21com.md`"
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard 3 options. (sim: Comparison + opportunities)
Q2 (header: Depth): standard 3 options. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): "21.com licensed markets only (Curacao + MGA)" / "Global, no jurisdiction filter" / "LATAM + Africa". (sim: 21.com licensed markets)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
> - Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`

| Field | Value |
|---|---|
| **Status** | Draft v1.0 |
| **Author** | Tal |
| **Date** | 2026-05-23 |
| **Depth** | Detailed comparison |
| **Region scope** | 21.com licensed markets (Curacao + MGA) |

## 1. Research Scope ... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble options: Bet on it / Hold the chip
3. Simulated user choice: Hold the chip
4. Final: "Saved at <path>. No Confluence page created."

### Memory caching
- Memory file: `~/.claude/memory/21com.md`
- Action: no action — memory already has the right Competitors line and runtime did not introduce new names.

## VERDICT: CR-004
**Title:** Focus inferred as 'Onboarding' from 'compare our signup to competitors'
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Focus → Onboarding) | PASS | "signup" → Onboarding per SKILL.md L68 | — |
| 2 | phase-a-infers-field (Competitors → Stake, 1Xbet, Rollbit, Bc.Game) | PASS | Memory has the **Competitors:** line; per SKILL.md L69, Phase A reads from memory | — |
| 3 | phase-b-skips (Focus, Competitors) | PASS | Both were inferred — Phase B asks only Output + Depth | — |
| 4 | inferred-block-present | PASS | Inferred (not asked) block at top includes both fields with phrase citations | — |

### Notes
Clean Phase A inference cascade — both Focus and Competitors inferred unambiguously.

---

## TRACE: CR-005

### Preconditions
User input: "how do Stake and Rollbit price their welcome bonuses versus us?". Memory has 21com competitor list. No MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Pricing/Bonuses" — citation: "price their welcome bonuses"
- **Competitors:** Inferred to "Stake, Rollbit" — citation: "Stake and Rollbit" (explicit names in prompt override memory list)
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)
Q2 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete options. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Pricing/Bonuses
> **Inferred (not asked):**
> - Focus: Pricing/Bonuses — from "welcome bonuses" / "price"
> - Competitors: Stake, Rollbit — from prompt "Stake and Rollbit" (overrides memory subset)
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/pricing-bonuses-2026-05-23.md`
2. Gamble: Bet on it / Hold the chip → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- Memory has Stake/1Xbet/Rollbit/Bc.Game; runtime only used Stake+Rollbit (a subset, not new names).
- Action: no append — runtime is subset of memory. Spec L247 only requires confirm-inline when runtime DIFFERS from memory; subset is ambiguous. Per literal reading, since Stake+Rollbit are in memory, no confirmation needed.

## VERDICT: CR-005
**Title:** Focus inferred as 'Pricing/Bonuses' from 'how do they price welcome bonuses?'
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Focus → Pricing/Bonuses) | PASS | SKILL.md L70: "pricing", "bonus" → Pricing focus | — |
| 2 | phase-a-infers-field (Competitors → Stake, Rollbit) | PASS | Explicit names in prompt cited per SKILL.md L69 | — |
| 3 | phase-b-skips (Focus, Competitors) | PASS | Both inferred | — |

### Notes
Phase A correctly resolves the explicit names-over-memory precedence per L69 ("If user named specific competitors in the prompt → use those"). The spec at L247 about confirming runtime-vs-memory differences is technically not triggered for a subset (no defect, but the spec is silent on subset behavior — flagging as a documentation gap not a case defect).

---

## TRACE: CR-006

### Preconditions
User input: "walk me through Bc.Game's deposit flow step-by-step with screenshots". Memory has 21com competitors. Playwright MCP available.

### Phase A — Inferences
- **Focus:** Inferred to "Checkout flow" — citation: "deposit flow"
- **Competitors:** Inferred to "Bc.Game" — citation: "Bc.Game"
- **Output emphasis:** Inferred to "Screenshots + UX notes" — citation: "step-by-step" / "with screenshots"
- **Depth:** Inferred to "Deep UX flow" — citation: "step-by-step"

### Phase B — Questions asked
none — all 4 core fields inferred.

### Phase C — Follow-ups
Q1 (header: Region): "21.com licensed markets only" / "Global" / "LATAM + Africa". (sim: Global)

### Playwright actions
- Navigated to: https://bc.game/, https://bc.game/deposit (and a few flow steps)
- Screenshots captured: screenshots/bcgame-home.png, screenshots/bcgame-deposit-1.png, screenshots/bcgame-deposit-2.png, screenshots/bcgame-deposit-3.png, screenshots/bcgame-deposit-confirmed.png

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Checkout Flow (Deposit)
> **Inferred (not asked):**
> - Focus: Checkout flow — from "deposit flow"
> - Competitors: Bc.Game — from "Bc.Game"
> - Output emphasis: Screenshots + UX notes — from "step-by-step with screenshots"
> - Depth: Deep UX flow — from "step-by-step"
... (7 sections, screenshots inline in §5)
```

### Handoff
1. Save: `~/Downloads/competitor-research/checkout-flow-2026-05-23.md` with screenshots subdir
2. Gamble: Bet on it / Hold the chip → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- Bc.Game in memory — no append needed.

## VERDICT: CR-006
**Title:** Output emphasis inferred as 'UX flow + screenshots' from 'walk me through their flow'
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Output emphasis → Screenshots + UX notes) | PASS | SKILL.md L71: "screenshots", "visual", "annotated" → Screenshots + UX notes. "step-by-step" matches Deep UX which implies same emphasis path | — |
| 2 | phase-a-infers-field (Competitors → Bc.Game) | PASS | Explicit name in prompt | — |
| 3 | phase-b-skips (Output emphasis, Competitors) | PASS | Both inferred | — |

### Notes
Phase A inference cascade succeeds on 4 of 4 core fields, allowing Phase B to be entirely skipped.

---

## TRACE: CR-007

### Preconditions
User input: "I want a deep UX flow on Stake's onboarding — every screen, frame by frame". Memory has 21com competitors. Playwright available.

### Phase A — Inferences
- **Focus:** Inferred to "Onboarding" — citation: "onboarding"
- **Competitors:** Inferred to "Stake" — citation: "Stake"
- **Output emphasis:** Inferred to "Screenshots + UX notes" — citation: "frame by frame"
- **Depth:** Inferred to "Deep UX flow" — citation: "every screen, frame by frame"

### Phase B — Questions asked
none — all 4 core fields inferred.

### Phase C — Follow-ups
Q1 (header: Region): standard 3 concrete options. (sim: Global)

### Playwright actions
- Navigated to Stake homepage, signup page, multi-step signup screens
- Screenshots: screenshots/stake-home.png, screenshots/stake-signup-1.png … step-N

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> **Inferred (not asked):**
> - Focus: Onboarding — from "onboarding"
> - Competitors: Stake — from "Stake"
> - Output emphasis: Screenshots + UX notes — from "frame by frame"
> - Depth: Deep UX flow — from "every screen, frame by frame"
... (7 sections, deep UX with per-step screenshots, friction analysis, side-by-side, experiments)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action — Stake in memory.

## VERDICT: CR-007
**Title:** Depth inferred as 'Deep UX flow' from 'every screen, frame by frame'
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Depth → Deep UX flow) | PASS | SKILL.md L72: "deep", "step-by-step", "every screen" → Deep UX flow | — |
| 2 | phase-a-infers-field (Focus → Onboarding) | PASS | "onboarding" keyword | — |
| 3 | phase-b-skips (Depth, Focus, Competitors) | PASS | All 3 + Output emphasis inferred | — |

### Notes
Cascading Phase A inferences all clean; all 4 core fields inferred.

---

## TRACE: CR-008

### Preconditions
User input: "give me a quick 30-minute scan of how Stake and 1Xbet handle responsible gaming". No memory, no MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Core feature experience (Responsible Gaming)" — citation: "responsible gaming"
- **Competitors:** Inferred to "Stake, 1Xbet" — citation: "Stake and 1Xbet"
- **Output emphasis:** Not inferred
- **Depth:** Inferred to "Quick scan" — citation: "quick 30-minute scan"

### Phase B — Questions asked
Q1 (header: Output): standard 3 options. (sim: Comparison + opportunities)

### Phase C — Follow-ups
Q1 (header: Region): concrete options. (sim: 21.com licensed markets only)

### Playwright actions
Not available — §1 will note it.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Responsible Gaming
> **Inferred (not asked):**
> - Focus: Responsible Gaming — from "responsible gaming"
> - Competitors: Stake, 1Xbet — from "Stake and 1Xbet"
> - Depth: Quick scan — from "quick 30-minute scan"
| Depth | Quick scan |
... (7 sections, 3-5 opportunities, screenshots optional)
```

### Handoff
1. Save: `~/Downloads/competitor-research/responsible-gaming-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- Action: no memory at all; no project slug. If resolved, would prompt user to confirm caching. Spec is silent on this exact scenario.

## VERDICT: CR-008
**Title:** Depth inferred as 'Quick scan' from '30-minute scan'
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Depth → Quick scan) | PASS | SKILL.md L72: "quick", "fast", "scan", "30 min" → Quick scan | — |
| 2 | phase-a-infers-field (Competitors → Stake, 1Xbet) | PASS | Explicit names in prompt | — |
| 3 | phase-b-skips (Depth, Competitors) | PASS | Both inferred | — |

### Notes
Clean Depth inference. Note: there is no project slug because active_memory is null — flag as a related but not blocking defect (project-slug resolution rule undefined; see CR-009).

---

## TRACE: CR-009

### Preconditions
User input: "I want to understand how competitors handle KYC". Memory file exists but has no **Competitors:** line. No MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Compliance/KYC" — citation: "KYC"
- **Competitors:** Not inferred (memory has no list; prompt names none)
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Targets): "Which competitors should be included?"
  options: 1) Memory default — Use the competitor list from active product memory (no memory list — falls back to generic prompt) 2) Memory + best-in-class 3) Custom list — I'll provide URLs at runtime
  Runtime label substitution: memory has none — label reads "Memory default (no cached list — please provide names)" or similar. Spec L86 says "substitute the real names from memory into this label at runtime" but is silent on empty-memory rendering. **Defect: spec doesn't define this label when memory is empty.**
  (sim: Custom list — PM provides Stake/1Xbet/Rollbit/Bc.Game)
Q2 (header: Output): standard. (sim: Comparison + opportunities)
Q3 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Compliance/KYC
> **Inferred (not asked):**
> - Focus: Compliance/KYC — from "KYC"
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/compliance-kyc-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- Memory file: `~/.claude/memory/21com.md` (project slug inferred from active_memory header "# 21com")
- Action: appended **Competitors:** line with PM's runtime answer before rendering report (per SKILL.md L211 and L243).
- New memory content: `**Competitors:** Stake (https://stake.com), 1Xbet (https://1xbet.com), Rollbit (https://rollbit.com), Bc.Game (https://bc.game)`

## VERDICT: CR-009
**Title:** Competitors NOT inferred when memory has no list and input is generic
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Competitors) | PASS | Memory has no **Competitors:** line; prompt names none; Phase A correctly falls through per SKILL.md L69 | — |
| 2 | phase-a-infers-field (Focus → Compliance/KYC) | PARTIAL | "KYC" not in the inference signal table (L68-L72). SKILL.md table only enumerates onboarding/pricing/homepage/checkout/named-feature. "KYC" arguably triggers "Compliance/KYC" via the "named feature surface" bucket but the spec is implicit. | Spec silent on KYC keyword. |
| 3 | phase-b-asks (Competitors) | PASS | Phase B emits the Targets question because Phase A couldn't infer | — |

### Notes
Phase A correctly doesn't infer Competitors. However, Focus inference for "KYC" depends on the implicit "named feature surface" bucket — SKILL.md L68-L72 doesn't list a compliance/KYC inference keyword. Minor spec gap, not a case fail.

### Suggested SKILL.md edit
Priority: P2
Location: skills/competitor-research/SKILL.md L68-L72 (Phase A inference table)
Symptom: Inference table omits compliance/KYC and several common research topics.
Proposed edit:
```
| **Focus** | "signup", "registration", "onboarding" → Onboarding. "pricing", "tiers", "promo", "bonus" → Pricing. "homepage", "landing" → Homepage. "checkout", "deposit", "withdraw" → Checkout flow. "KYC", "AML", "responsible gaming", "compliance" → Compliance. Named feature surface (e.g. "game lobby", "VIP page") → Core feature experience. |
```

---

## TRACE: CR-010

### Preconditions
User input: "check what others are doing". No memory, no MCP. Fully vague.

### Phase A — Inferences
- **Focus:** Not inferred
- **Competitors:** Not inferred
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Focus): "What is this research focused on?" options: Onboarding / Pricing / Core feature experience. (sim: Onboarding)
Q2 (header: Targets): "Which competitors should be included?" options: Memory default (no cached list) / Memory + best-in-class / Custom list. (sim: Custom list)
Q3 (header: Output): standard. (sim: Comparison + opportunities)
Q4 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
(NO Inferred block — Phase A inferred nothing)
| Field | Value |
| **Status** | Draft v1.0 |
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No active memory; if a project slug were resolved at runtime via PM prompt, would create memory file and append Competitors line.

## VERDICT: CR-010
**Title:** Ambiguous fall-through: vague 'check what others are doing' infers nothing
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Focus) | PASS | No keyword matches | — |
| 2 | phase-a-does-not-infer-field (Competitors) | PASS | No memory, no names in prompt | — |
| 3 | phase-a-does-not-infer-field (Output emphasis) | PASS | No keyword matches | — |
| 4 | phase-a-does-not-infer-field (Depth) | PASS | No keyword matches | — |
| 5 | phase-b-asks all 4 | PASS | All 4 Phase B questions emitted | — |
| 6 | inferred-block-omitted-when-empty | PASS | No Inferred block rendered | — |

### Notes
Phase A correctly infers nothing on fully vague input. Phase B asks all 4 core questions. Total questions = 4 (B) + 1 (C region) = 5, under cap of 7.

---

## TRACE: CR-011

### Preconditions
User input: "I want a quick deep dive on Stake's signup flow with every screenshot". Memory has 21com competitors. Playwright available. Conflicting depth signals.

### Phase A — Inferences
- **Focus:** Inferred to "Onboarding" — citation: "signup"
- **Competitors:** Inferred to "Stake" — citation: "Stake"
- **Output emphasis:** Inferred to "Screenshots + UX notes" — citation: "every screenshot"
- **Depth:** AMBIGUOUS — "quick" suggests Quick scan; "deep dive" + "every screenshot" suggests Deep UX flow. Per SKILL.md L67 "Mark an answer inferred only if the signal is unambiguous; otherwise fall through to Phase B" — the skill SHOULD fall back to Phase B for Depth.

### Phase B — Questions asked
Q1 (header: Depth): "How deep should the research go?" options: Quick scan / Detailed comparison / Deep UX flow. (sim: Deep UX flow — based on "every screenshot")

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
- Stake homepage + multi-step signup screens
- screenshots/stake-home.png, stake-signup-1.png … step-N

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
> - Competitors: Stake — from "Stake"
> - Output emphasis: Screenshots + UX notes — from "every screenshot"
... (7 sections, deep UX shape)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action — Stake in memory.

## VERDICT: CR-011
**Title:** Multi-signal conflict: 'quick deep dive' resolves to one Depth or stays uninferred
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-resolves-conflict (Depth) | PASS | Acceptable outcomes include "<not inferred>"; trace falls back to Phase B which is acceptable per SKILL.md L67 | — |
| 2 | phase-a-infers-field (Focus → Onboarding) | PASS | "signup" → Onboarding | — |
| 3 | phase-a-infers-field (Competitors → Stake) | PASS | Explicit name | — |

### Notes
Spec L67 "Mark an answer inferred only if the signal is unambiguous" gives the skill correct guidance for this case — Depth falls through to Phase B, which is in the acceptable_outcomes list.

---

## TRACE: CR-012

### Preconditions
User input: "compare Stake's signup to ours — quick scan is fine". Memory has 21com competitors. No MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Onboarding" — citation: "signup"
- **Competitors:** Inferred to "Stake" — citation: "Stake"
- **Output emphasis:** Not inferred
- **Depth:** Inferred to "Quick scan" — citation: "quick scan"

### Phase B — Questions asked
Q1 (header: Output): "What should the report emphasize?" options: Comparison + opportunities / Screenshots + UX notes / Strategic recommendations. (sim: Comparison + opportunities)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
> - Competitors: Stake — from "Stake"
> - Depth: Quick scan — from "quick scan"
... (7 sections, 3-5 opportunities, light depth)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action — Stake in memory.

## VERDICT: CR-012
**Title:** Phase B asks only the questions Phase A didn't infer
**SKILL.md ref:** competitor-research:L78-L98
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-b-skips (Focus, Competitors, Depth) | PASS | All three inferred in Phase A | — |
| 2 | phase-b-asks (Output) | PASS | Only Output asked | — |
| 3 | phase-b-uses-ask-user-question | PASS | Question emitted via AskUserQuestion (simulated) | — |

### Notes
Phase B correctly asks only the one remaining core question.

---

## TRACE: CR-013

### Preconditions
User input: "do a competitive scan". No memory, no MCP. Vague.

### Phase A — Inferences
- **Focus:** Not inferred
- **Competitors:** Not inferred
- **Output emphasis:** Not inferred
- **Depth:** Not inferred ("scan" alone is ambiguous; "Quick scan" needs more signal like "quick" / "30 min" / "fast")

### Phase B — Questions asked
Q1 (header: Focus): "What is this research focused on?" options:
  1) Onboarding / signup flow — Landing through first deposit
  2) Pricing & packaging — Tiers, promotions, bonus structure
  3) Core feature experience — A specific surface (game lobby, profile, search, etc.)
  (sim: Onboarding)
Q2 (header: Targets): options:
  1) Memory default (no cached list — please provide names) [note: per spec L86 substitute memory names; empty memory rendering is undefined]
  2) Memory + best-in-class — Memory list plus 2–3 indirect references
  3) Custom list — I'll provide URLs at runtime
  (sim: Custom list)
Q3 (header: Output): options:
  1) Comparison + opportunities — Side-by-side matrix + gap analysis
  2) Screenshots + UX notes — Annotated screenshots + step-by-step observations
  3) Strategic recommendations — Positioning, market patterns, leadership-friendly summary
  (sim: Comparison + opportunities)
Q4 (header: Depth): options:
  1) Quick scan — Public homepage + main flow, ~30 min equivalent
  2) Detailed comparison — Full matrix + screenshots of key surfaces, ~2-hour equivalent
  3) Deep UX flow — Step-by-step per competitor with friction analysis + screenshots of every screen
  (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
(no Inferred block)
| Field | Value | ... |
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- New memory file created with **Competitors:** line.

## VERDICT: CR-013
**Title:** Each Phase B question has exactly 3 concrete options matching the spec verbatim
**SKILL.md ref:** competitor-research:L80-L98
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-b-question-shape (Focus, 3 options, header Focus) | PASS | 3 options per spec L82-L85 | — |
| 2 | phase-b-question-shape (Targets, 3 options, header Targets) | PASS | 3 options per spec L86-L89 | — |
| 3 | phase-b-question-shape (Output, 3 options, header Output) | PASS | 3 options per spec L90-L93 | — |
| 4 | phase-b-question-shape (Depth, 3 options, header Depth) | PASS | 3 options per spec L94-L97 | — |

### Notes
All 4 questions render with the spec'd headers and 3 concrete options each. AskUserQuestion auto-adds Other.

---

## TRACE: CR-014

### Preconditions
User input: "look at what other casinos are doing". No memory, no MCP.

### Phase A — Inferences
All 4 fields not inferred.

### Phase B — Questions asked
Q1 (header: Focus), Q2 (header: Targets), Q3 (header: Output), Q4 (header: Depth) — exact spec'd labels.
Simulated PM picks Onboarding / Custom list / Comparison + opportunities / Detailed comparison.

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
(no Inferred block)
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- New memory + Competitors line appended.

## VERDICT: CR-014
**Title:** Phase B headers match spec verbatim: Focus / Targets / Output / Depth
**SKILL.md ref:** competitor-research:L80-L98
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-b-question-shape (all 4 with correct headers) | PASS | Headers match spec: Focus / Targets / Output / Depth | — |
| 2 | phase-b-uses-ask-user-question | PASS | All emitted via AskUserQuestion | — |

### Notes
Headers verbatim per spec L82, L86, L90, L94.

---

## TRACE: CR-015

### Preconditions
User input: "research time". No memory, no MCP. Maximally vague.

### Phase A — Inferences
All 4 fields not inferred.

### Phase B — Questions asked
All 4 (Focus / Targets / Output / Depth) per spec.

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: <PM-chosen Focus>
(no Inferred block)
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/<slug>-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- New memory + Competitors line appended.

## VERDICT: CR-015
**Title:** When Phase A infers zero fields, Phase B asks all 4 core questions
**SKILL.md ref:** competitor-research:L78-L98
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-b-asks (Focus, Targets, Output, Depth) | PASS | All 4 emitted | — |
| 2 | phase-b-uses-ask-user-question | PASS | via AskUserQuestion | — |
| 3 | inferred-block-omitted-when-empty | PASS | No Inferred block | — |
| 4 | total-questions-asked-max (7) | PASS | 4 (B) + 1 (C) = 5 ≤ 7 | — |

### Notes
Total question budget respected.

---

## TRACE: CR-016

### Preconditions
User input: "scan how competitors handle wagering requirements". Memory has Stake/1Xbet/Rollbit/Bc.Game. No MCP.

### Phase A — Inferences
- **Focus:** Inferred to "Pricing/Bonuses" — citation: "wagering requirements" (relates to bonus terms — per SKILL.md L70 "bonus" keyword)
- **Competitors:** Inferred to "Stake, 1Xbet, Rollbit, Bc.Game" — citation: "memory"
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

Wait — the case's pass_criteria says phase-b-asks (Targets). So Competitors should NOT be inferred from memory? Let me re-read… The case wants Targets to be asked with the memory-name substitution. That means: even when memory has names, Phase B still asks Targets (with memory names substituted in the label), to confirm. SKILL.md L69 says "If active product memory has a **Competitors:** line → use it" (Phase A infers). But case pass_criteria asks for Targets to be asked. **Possible spec/test conflict.**

Re-reading L86: "Memory default — Use the competitor list from active product memory (substitute the real names from memory into this label at runtime)" — this is a Phase B option. The substitution only happens if Phase B is actually asking the Targets question. So the test case assumes Phase A does NOT infer Competitors from memory (so that Phase B can ask Targets and show the substituted label). This contradicts L69.

Per literal spec: Phase A would infer Competitors. So my simulation: Phase A infers Competitors → Phase B does NOT ask Targets. The case pass_criteria expects the opposite.

### Phase B — Questions asked (per spec literal)
Q1 (header: Output): standard. (sim: Comparison + opportunities)
Q2 (header: Depth): standard. (sim: Detailed comparison)
(NO Targets question because Phase A inferred Competitors from memory)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Not available.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Pricing/Bonuses (wagering requirements)
> **Inferred (not asked):**
> - Focus: Pricing/Bonuses — from "wagering requirements"
> - Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/pricing-bonuses-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action — memory matches runtime.

## VERDICT: CR-016
**Title:** Competitors question label substitutes real names from memory at runtime
**SKILL.md ref:** competitor-research:L85-L88
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-phase-b-competitor-question-uses-memory-names | PARTIAL | Spec L86 says substitute names when Phase B asks Targets — but Phase A L69 says infer from memory and skip Phase B. The two paths conflict: if Phase A always infers from memory, Phase B never renders the Targets question and never substitutes names. The substitution only manifests when (a) memory is empty + Phase B asks AND PM picks Memory default (impossible — no names to substitute) OR (b) memory differs and Phase B re-asks to confirm (not spec'd) | Spec conflict between L69 (Phase A infers) and L86 (Phase B substitutes). |
| 2 | phase-b-asks (Targets) | FAIL | Per literal L69 reading, Phase A infers from memory and Phase B does NOT ask Targets | Spec L69 contradicts test expectation. |
| 3 | phase-b-uses-ask-user-question | PASS | Other questions emitted via AskUserQuestion | — |

### Notes
Real defect: SKILL.md L69 ("memory → use it" = Phase A infers) directly conflicts with L86 ("substitute the real names from memory into this label at runtime") which assumes Phase B is asking. The substitution rule is effectively unreachable in normal flow. This is a design conflict.

### Suggested SKILL.md edit
Priority: P0
Location: skills/competitor-research/SKILL.md L69 + L86
Symptom: Phase A inference from memory and Phase B substitution-when-asking are mutually exclusive paths.
Proposed edit:
```
| **Competitors** | If active product memory (`~/.claude/memory/<project-slug>.md`) has a `**Competitors:**` line → present the Phase B Targets question with the memory names substituted in the "Memory default" option so the PM can confirm or override. If user named specific competitors in the prompt → use those (skip the question). Otherwise ask without a Memory default option. |
```
Plus on L86: keep the substitution rule and clarify it's the confirm-the-cached-list path.

---

## TRACE: CR-017

### Preconditions
User input: "deep UX flow on Stake, 1Xbet, Rollbit, and Bc.Game's onboarding". Memory has 21com competitors. Playwright available.

### Phase A — Inferences
- **Focus:** Inferred to "Onboarding" — citation: "onboarding"
- **Competitors:** Inferred to "Stake, 1Xbet, Rollbit, Bc.Game" — citation: explicit names in prompt
- **Output emphasis:** Not inferred (but Deep UX implies screenshots — could go to Screenshots + UX notes)
- **Depth:** Inferred to "Deep UX flow" — citation: "deep UX flow"

### Phase B — Questions asked
Q1 (header: Output): standard 3. (sim: Screenshots + UX notes)

### Phase C — Follow-ups (max 3)
Q1 (header: Region): concrete. (sim: 21.com licensed markets)
Q2 (header: Sources): "Include third-party reviews?" — concrete: Direct only / Direct + Trustpilot + AskGamblers / Direct + CasinoMeister. (sim: Direct only)
Q3 (header: Auth boundary): "Use only logged-out public pages, or also logged-in PRD screenshots?" — Public-only / Public + internal PRD screenshots / Public + Confluence references. (sim: Public-only)

### Playwright actions
- 4 competitors × ~5 pages each = ~20 screenshots
- screenshots/stake-signup-{1..5}.png, screenshots/1xbet-signup-{1..5}.png, etc.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> **Inferred (not asked):**
> - Focus: Onboarding — from "onboarding"
> - Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from prompt
> - Depth: Deep UX flow — from "deep UX flow"
... (7 sections, deep UX shape with per-step screenshots, friction analysis, side-by-side, experiments)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action.

## VERDICT: CR-017
**Title:** Phase C emits at most 3 follow-up questions
**SKILL.md ref:** competitor-research:L103-L113
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | Exactly 3 follow-ups emitted (region, source mix, auth boundary) | — |
| 2 | total-questions-asked-max (7) | PASS | 1 (B) + 3 (C) = 4 ≤ 7 | — |

### Notes
Total 4 questions. Phase C correctly capped at 3.

---

## TRACE: CR-018

### Preconditions
User input: "look at how Stake handles loyalty". Memory has 21com competitors. Playwright available.

### Phase A — Inferences
- **Focus:** Inferred to "Core feature experience (Loyalty)" — citation: "loyalty"
- **Competitors:** Inferred to "Stake" — citation: "Stake"
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)
Q2 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): "21.com licensed markets only (Curacao + MGA)" / "Global, no jurisdiction filter" / "LATAM + Africa (matches CS_Africa Confluence)". (sim: 21.com licensed markets)
Q2 (header: Sources): "Stake public site only" / "Stake site + AskGamblers loyalty reviews" / "Stake site + Trustpilot complaints filter". (sim: site only)

All option labels concrete, no banned placeholders.

### Playwright actions
- Stake homepage + VIP/loyalty pages
- screenshots/stake-vip-overview.png, stake-vip-tiers.png, stake-vip-perks.png

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Loyalty
> **Inferred (not asked):**
> - Focus: Loyalty — from "loyalty"
> - Competitors: Stake — from "Stake"
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/loyalty-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action.

## VERDICT: CR-018
**Title:** Phase C rejects banned placeholder options
**SKILL.md ref:** competitor-research:L106-L108
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-c-no-banned-placeholders | PASS | No "Use the existing source", "Option A", "TBD", "I'll specify later" present | — |
| 2 | phase-c-options-are-concrete | PASS | All options reference real entities (21.com markets, Curacao/MGA, AskGamblers, Trustpilot, Stake site) | — |

### Notes
Per SKILL.md L106 — concrete labels enforced.

---

## TRACE: CR-019

### Preconditions
User input: "compare how Stake handles signup for German players specifically". Memory has 21com competitors. Playwright available.

### Phase A — Inferences
- **Focus:** Inferred to "Onboarding" — citation: "signup"
- **Competitors:** Inferred to "Stake" — citation: "Stake"
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

Region = DE inferred from "German players" → does NOT ask region in Phase C; instead converts to inline assumption "Assumed: DE market view".

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)
Q2 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Sources): concrete. (sim: Direct only)
(Region NOT asked — covered inline)

### Playwright actions
- Stake homepage from DE locale, Stake signup
- screenshots/stake-home-de.png, stake-signup-de-1.png

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding (DE market)
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
> - Competitors: Stake — from "Stake"
> - Region: DE — from "German players" (inline assumption)
| Region scope | Germany (DE) |
... (7 sections)
```

### Handoff
1. Save path with DE inferred slug.
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action.

## VERDICT: CR-019
**Title:** Phase C skips region question when input already names a market
**SKILL.md ref:** competitor-research:L109-L110
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-c-skips-when-context-answers (region/market scope, inline assumption) | PASS | "German players" answers region — converted to inline assumption per Rule 3 (L107) | — |
| 2 | phase-c-max-3 | PASS | Only 1 follow-up emitted | — |

### Notes
Spec L107 ("Skip the question entirely if input or context already answers it. Convert that answer into an inline assumption in the report instead") correctly applied.

---

## TRACE: CR-020

### Preconditions
User input: "do a deep UX flow on Stake's signup with screenshots". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding (signup)
- **Competitors:** Stake
- **Output emphasis:** Screenshots + UX notes (screenshots)
- **Depth:** Deep UX flow (deep UX)

### Phase B — Questions asked
none — all 4 core fields inferred.

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)
Q2 (header: Sources): concrete. (sim: Direct only)

NOT asked: "What should the screenshot filenames be?" (banned per Rule 4 + spec L111).

### Playwright actions
- Stake signup flow, every screen
- screenshots/stake-signup-1.png, stake-signup-2.png, … (auto-named)

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding (Stake deep UX)
... (7 sections, every-screen screenshots inline)
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action.

## VERDICT: CR-020
**Title:** Phase C does NOT ask about screenshot filenames
**SKILL.md ref:** competitor-research:L111-L120
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-phase-c-skip-screenshot-filenames | PASS | No filename question emitted. Files auto-named (stake-signup-1.png etc.) per spec L132 | — |
| 2 | phase-c-skips-styling-copy-questions | PASS | No styling/copy questions emitted | — |

### Notes
Rule 4 (L108) "NOT exact phrasing of observations, exact screenshot names, exact ticket titles" applied.

---

## TRACE: CR-021

### Preconditions
User input: "scan our competitors on KYC flows". Memory has 21com competitors. Playwright available.

### Phase A — Inferences
- **Focus:** Inferred to "Compliance/KYC" — citation: "KYC"
- **Competitors:** Inferred to "Stake, 1Xbet, Rollbit, Bc.Game" — from memory
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)
Q2 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: 21.com licensed markets)
Q2 (header: Sources): "Direct only" / "Direct + AskGamblers" / "Direct + reddit threads". (sim: Direct only)

NOT asked: "Use existing competitors or different ones?" (banned per L118).

### Playwright actions
- Each competitor's KYC pages (where accessible)
- screenshots/stake-kyc.png, 1xbet-kyc.png, rollbit-kyc.png, bcgame-kyc.png

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Compliance/KYC
... (7 sections)
```

### Handoff
1. Save: `~/Downloads/competitor-research/compliance-kyc-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action.

## VERDICT: CR-021
**Title:** Phase C does NOT re-ask 'use existing competitors or different ones?'
**SKILL.md ref:** competitor-research:L111-L122
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-phase-c-skip-redundant-competitor-question | PASS | Phase B resolved competitors; Phase C does not re-ask | — |
| 2 | phase-c-skips-when-context-answers (competitor selection) | PASS | Memory + Phase A already answered; not re-asked | — |

### Notes
SKILL.md L121 ("Use the existing competitors or different ones?" listed as bad follow-up) correctly avoided.

---

## TRACE: CR-022

### Preconditions
User input: "compare loyalty programs on Stake and Rollbit". Memory has 21com competitors. Playwright available. Many unknowns survive.

### Phase A — Inferences
- **Focus:** Inferred to "Core feature experience (Loyalty)" — citation: "loyalty programs"
- **Competitors:** Inferred to "Stake, Rollbit" — citation: explicit names
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)
Q2 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups (priority order: region > source mix > time horizon > auth)
Q1 (header: Region): concrete options. (sim: 21.com licensed markets) — TOP priority
Q2 (header: Sources): concrete options. (sim: Direct only) — 2nd priority
Q3 (header: Time horizon): "One-time snapshot" / "Recurring quarterly" / "Track diffs vs last scan". (sim: One-time snapshot) — 3rd priority

Authentication boundary NOT asked — capped at 3.

### Playwright actions
- screenshots/stake-vip-overview.png, stake-vip-tiers.png, rollbit-vip-overview.png, rollbit-vip-tiers.png, etc.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Loyalty Program Comparison
... (7 sections)
```

### Handoff
1. Save path; Gamble → Hold the chip; Final: "Saved at <path>."

### Memory caching
- No action.

## VERDICT: CR-022
**Title:** Phase C respects CR-specific priority order (region > source mix > time horizon > auth)
**SKILL.md ref:** competitor-research:L111-L113
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-phase-c-priority-order-respected | PASS | Order: Region (1) > Source mix (2) > Time horizon (3); auth boundary not asked (cap=3) | — |
| 2 | phase-c-max-3 | PASS | 3 follow-ups | — |

### Notes
Priority order from SKILL.md L111-L114 respected exactly.

---

## TRACE: CR-023

### Preconditions
User input: "research what crypto casinos are doing on chargeback handling". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Not cleanly inferred (chargeback isn't in the inference table — falls to "named feature surface")
- **Competitors:** Inferred from memory
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Focus): standard. (sim: Core feature experience — chargeback)
Q2 (header: Output): standard. (sim: Comparison + opportunities)
Q3 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete options. (sim: Global)
Q2 (header: Sources): "Direct only" / "Direct + Trustpilot complaints" / "Direct + reddit threads". (sim: Direct + Trustpilot complaints)

NOT asked: "Preferred chargeback evidence source" (cannot write 3 concrete options for this unknown — converted to inline assumption + flag per Rule 6). The artifact says: "Assumption: chargeback evidence sourced from competitor T&C pages + Trustpilot complaints. Open: preferred evidence source not specified — confirm with payments lead."

### Playwright actions
- Competitor T&C and dispute pages

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Chargeback Handling
... (7 sections, with the inline flag in §1)
```

### Handoff
Standard.

### Memory caching
- No action.

## VERDICT: CR-023
**Title:** Phase C falls back to assume+flag when no 3 concrete options exist
**SKILL.md ref:** competitor-research:L112-L113
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-c-fallback-to-assume-and-flag (preferred chargeback evidence source) | PASS | Unknown dropped; inline assumption + Open flag in §1 | — |
| 2 | phase-c-no-banned-placeholders | PASS | No banned placeholders | — |

### Notes
Rule 6 (L113) applied — when you can't write 3 concrete options, drop the question and flag inline.

---

## TRACE: CR-024

### Preconditions
User input: "scan how Stake, 1Xbet, Rollbit, and Bc.Game handle VIP onboarding". Memory has 21com competitors. Playwright available.

### Phase A — Inferences
- **Focus:** Onboarding (VIP onboarding) — citation: "VIP onboarding"
- **Competitors:** All 4 from prompt (matches memory)
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Strategic recommendations)
Q2 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups (worked-example from L115-L122)
Q1 (header: Region): "21.com licensed markets only (Curacao + MGA)" / "Global, no jurisdiction filter" / "LATAM + Africa (CS_Africa / CSO)". (sim: 21.com licensed markets)
Q2 (header: Sources): "Trustpilot + AskGamblers (English) only" / "Add CasinoMeister threads for VIP-tier signal" / "Public competitor sites only — no third-party". (sim: Trustpilot + AskGamblers)
Q3 (header: Auth boundary): "Strict public-only" / "Public + internal 21.com VIP PRD screenshots" / "Public + Confluence VIP strategy excerpts". (sim: Strict public-only)

### Playwright actions
- VIP/loyalty pages × 4 competitors
- screenshots/stake-vip-onboarding.png etc.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: VIP Onboarding
... (7 sections)
```

### Handoff
Standard.

### Memory caching
- No action.

## VERDICT: CR-024
**Title:** Good follow-ups: 21.com region + third-party source-mix scenario asks both with concrete options
**SKILL.md ref:** competitor-research:L115-L122
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-c-max-3 | PASS | 3 follow-ups | — |
| 2 | phase-c-options-are-concrete | PASS | References AskGamblers, Trustpilot, CasinoMeister, 21.com markets, Curacao/MGA | — |
| 3 | phase-c-no-banned-placeholders | PASS | All concrete | — |
| 4 | cr-phase-c-priority-order-respected | PASS | Region > Sources > Auth — matches L111-L114 | — |

### Notes
Matches the worked example in SKILL.md L115-L122 exactly.

---

## TRACE: CR-025

### Preconditions
User input: "scan how Stake handles onboarding — detailed comparison please". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding (onboarding)
- **Competitors:** Stake (explicit)
- **Output emphasis:** Not inferred
- **Depth:** Detailed comparison (explicit "detailed comparison")

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: 21.com licensed markets)

### Playwright actions
- Stake homepage + signup
- screenshots/stake-home.png, stake-signup-1.png … 3

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> Inferred (not asked): Focus, Competitors, Depth
| Field | Value | ... |

## 1. Research Scope
## 2. Competitors Reviewed
## 3. Executive Summary
## 4. Comparison Table
## 5. UX Flow Notes
## 6. Key Patterns
## 7. Gaps & Opportunities
```

### Handoff
Standard.

### Memory caching
- No action.

## VERDICT: CR-025
**Title:** Output contains all 7 numbered sections in order
**SKILL.md ref:** competitor-research:L155-L200
**Overall:** FAIL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-has-7-sections | PASS | 7 numbered sections per spec | — |
| 2 | output-has-required-sections (test expects "2. Methodology", "3. Competitor Snapshots") | FAIL | SKILL.md L156-L200 defines sections as: 1. Research Scope / 2. Competitors Reviewed / 3. Executive Summary / 4. Comparison Table / 5. UX Flow Notes / 6. Key Patterns / 7. Gaps & Opportunities. Test case expects "2. Methodology" and "3. Competitor Snapshots" — these names don't match SKILL.md. | Test case section names diverge from SKILL.md. |

### Notes
**Critical defect:** the test case CR-025 names sections "2. Methodology" and "3. Competitor Snapshots" — but SKILL.md says "2. Competitors Reviewed" and "3. Executive Summary". Either the test catalog or the SKILL.md is wrong. Since SKILL.md is declared ground truth, the test case fails against it. But this could equally be a spec defect: ground truth's section names may not be the canonical 7-section list per the broader vocabulary.

### Suggested SKILL.md edit
Priority: P0
Location: skills/competitor-research/SKILL.md L157-L200 + tests/competitor-research/cases/CR-025.yaml
Symptom: SKILL.md and the test catalog disagree on §2 and §3 section names.
Proposed edit (align SKILL.md to test expectations OR update test case):
```
## 1. Research Scope
## 2. Methodology
## 3. Competitor Snapshots
## 4. Comparison Table
## 5. UX Flow Notes
## 6. Key Patterns
## 7. Gaps & Opportunities
```
(Recommend updating SKILL.md to use the test-catalog's canonical names since "Methodology" and "Competitor Snapshots" are clearer per-section semantics than "Competitors Reviewed" + "Executive Summary".)

---

## TRACE: CR-026

### Preconditions
User input: "detailed comparison of Stake and Rollbit signup flows for EU market". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding (signup)
- **Competitors:** Stake, Rollbit (explicit)
- **Output emphasis:** Not inferred
- **Depth:** Detailed comparison (explicit)
- Region = EU (from "EU market") → inline assumption

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)

### Phase C — Follow-ups
Q1 (header: Sources): concrete. (sim: Direct only)
(Region not asked — inferred from input as EU.)

### Playwright actions
- screenshots/stake-signup-eu-1.png, rollbit-signup-eu-1.png

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding (EU)
> **Inferred:** Focus / Competitors / Depth / Region
| Field | Value |
| **Status** | Draft v1.0 |
| **Author** | Tal |
| **Date** | 2026-05-23 |
| **Depth** | Detailed comparison |
| **Region scope** | EU |
... (7 sections)
```

### Handoff
Standard.

## VERDICT: CR-026
**Title:** Metadata table at top has Status / Author / Date / Depth / Region scope rows
**SKILL.md ref:** competitor-research:L159-L165
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-output-has-metadata-table | PASS | All 5 rows present per SKILL.md L161-L165 | — |

### Notes
Metadata table renders all 5 rows.

---

## TRACE: CR-027

### Preconditions
User input: "detailed comparison: Stake vs 1Xbet vs Rollbit vs Bc.Game on homepage and pricing". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Multi-focus: Homepage + Pricing — ambiguous. Likely falls through OR resolves to one.
- **Competitors:** All 4 (explicit)
- **Depth:** Detailed comparison (explicit)
- **Output:** Not inferred

### Phase B — Questions asked
Q1 (header: Focus): standard (since Focus ambiguous). (sim: Homepage)
Q2 (header: Output): standard. (sim: Comparison + opportunities)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
- 4 competitors × homepage + pricing pages

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Homepage
... §4 Comparison Table with ≥4 rows from canonical labels (Homepage messaging, Signup flow, Pricing, Trust signals, Core feature)
```

### Handoff
Standard.

## VERDICT: CR-027
**Title:** §4 Comparison Table has at least 4 rows from canonical labels
**SKILL.md ref:** competitor-research:L175-L185
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-comparison-table-min-rows | PASS | ≥4 rows from the canonical label set per SKILL.md L176-L182 | — |

### Notes
SKILL.md L176-L182 shows the canonical table with all 5 labels.

---

## TRACE: CR-028

### Preconditions
User input: "deep UX flow on Stake's signup with every screenshot". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding (signup)
- **Competitors:** Stake (explicit)
- **Output emphasis:** Screenshots + UX notes
- **Depth:** Deep UX flow

### Phase B — Questions asked
none.

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)
Q2 (header: Sources): concrete. (sim: Direct only)

### Playwright actions
- screenshots/stake-signup-1.png, stake-signup-2.png, stake-signup-3.png (and more for every-screen)

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding (Stake deep UX)
... §5 UX Flow Notes:
### Stake
- Step 1 — Email entry — `![email](screenshots/stake-signup-1.png)`
- Step 2 — Password — `![password](screenshots/stake-signup-2.png)`
- Step 3 — Confirmation — `![confirm](screenshots/stake-signup-3.png)`
... no separate Screenshots section, no Appendix, no References
```

### Handoff
Standard.

## VERDICT: CR-028
**Title:** §5 UX Flow Notes references screenshots inline — no separate Screenshots section
**SKILL.md ref:** competitor-research:L185-L195
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-screenshots-inline-not-separate-section | PASS | Inline `![desc](screenshots/<file>.png)` references per SKILL.md L188-L192; no Screenshots section | — |
| 2 | output-omits-banned-sections (Screenshots, Appendix, References) | PASS | None present | — |

### Notes
Spec L187 explicitly enforces inline-only screenshot references.

---

## TRACE: CR-029

### Preconditions
User input: "detailed comparison of crypto casino onboarding — Stake, 1Xbet, Rollbit, Bc.Game". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding
- **Competitors:** all 4 (explicit)
- **Depth:** Detailed comparison
- **Output:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Comparison + opportunities)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: Global)

### Playwright actions
Per-competitor homepage + signup screenshots.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
...
## 6. Key Patterns
**Table stakes:** Email + password signup, license footer, mobile responsive, terms checkbox, age verification gate.
**Differentiation:**
- Stake: social-proof header with live player count
- Rollbit: crypto-first signup (no fiat option)
- 1Xbet: sports-betting onboarding angle
- Bc.Game: gamified signup with reward reveal
## 7. Gaps & Opportunities
```

### Handoff
Standard.

## VERDICT: CR-029
**Title:** §6 Key Patterns distinguishes table-stakes vs. differentiation
**SKILL.md ref:** competitor-research:L195-L200
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-section-6-distinguishes-table-stakes-vs-differentiation | PASS | Both "Table stakes" and "Differentiation" labels present per SKILL.md L197 | — |

### Notes
SKILL.md L197 explicitly requires the two-group split.

---

## TRACE: CR-030

### Preconditions
User input: "scan Stake's loyalty program and tell me what to ship". Memory + Atlassian + Playwright. User asks "what to ship" → tempting to generate tickets — but skill must not.

### Phase A — Inferences
- **Focus:** Loyalty (named feature)
- **Competitors:** Stake (explicit)
- **Output:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (header: Output): standard. (sim: Strategic recommendations)
Q2 (header: Depth): standard. (sim: Detailed comparison)

### Phase C — Follow-ups
Q1 (header: Region): concrete. (sim: 21.com licensed markets)

### Playwright actions
- screenshots/stake-vip-*.png

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Stake Loyalty Program
... (7 sections; §7 Gaps & Opportunities is FINAL — no §8 "Suggested Jira Breakdown", no "Tickets", no "Builder notes")
```

### Handoff
1. Save: `~/Downloads/competitor-research/stake-loyalty-program-2026-05-23.md`
2. Gamble → Bet on it (atlassian connected)
3. Confluence call: spaceId=772571142, parentId=772571521, contentFormat=markdown
4. Surfaces note: "Screenshots are local-only at ~/Downloads/competitor-research/stake-loyalty-program/screenshots/..."
5. Final: "Published to <Confluence URL>. Saved at <local path>."

**NO Jira ticket created.** Spec L243: "It does NOT create Jira tickets." Even though user said "what to ship", the skill hands off only to Confluence + Gaps & Opportunities — user would feed those to `prd-writer` or `ticket-builder` as a follow-up.

## VERDICT: CR-030
**Title:** Output ends at §7 — no Jira tickets generated, no meta-commentary
**SKILL.md ref:** competitor-research:L200-L244
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-no-jira-tickets-generated | PASS | §7 final; no Jira MCP call | — |
| 2 | no-meta-commentary-after-final-section | PASS | Nothing after §7 in artifact | — |
| 3 | output-omits-banned-sections | PASS | No "Suggested Jira Breakdown" / "Tickets" / "Builder notes" | — |

### Notes
SKILL.md L242-L244 clearly states research-only; skill honors it even when user asks "tell me what to ship".

---

## TRACE: CR-031

### Preconditions
User input: "compare Stake's signup to ours". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding (signup)
- **Competitors:** Stake (explicit)
- Others not inferred.

### Phase B — Questions asked
Q1 (Output): sim Comparison + opportunities. Q2 (Depth): sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region): sim Global.

### Playwright actions
- screenshots/stake-signup-{1..3}.png

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
> - Competitors: Stake — from "Stake"

| Field | Value |
|---|---|
... (metadata)

## 1. Research Scope ... ## 7. Gaps & Opportunities
```

### Handoff
Standard.

## VERDICT: CR-031
**Title:** Inferred (not asked) block appears at top when Phase A inferred at least one field
**SKILL.md ref:** competitor-research:L165-L175
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | inferred-block-present | PASS | Block at top before §1 | — |
| 2 | inferred-includes-field (Focus → Onboarding, cite "signup") | PASS | Bullet present with correct citation | — |
| 3 | inferred-includes-field (Competitors → Stake, cite "Stake") | PASS | Bullet present | — |

### Notes
SKILL.md L167-L172 shows the exact block format.

---

## TRACE: CR-032

### Preconditions
User input: "quick 30-minute scan of Stake's homepage messaging". Memory has 21com competitors. No MCP (Playwright off).

### Phase A — Inferences
- **Focus:** Homepage (homepage)
- **Competitors:** Stake (explicit)
- **Output:** Not inferred
- **Depth:** Quick scan (quick 30-minute scan)

### Phase B — Questions asked
Q1 (Output): sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region): sim Global.

### Playwright actions
Playwright not available — §1 will note "Playwright not available — no screenshots captured".

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Homepage
> **Inferred:** Focus / Competitors / Depth
| Depth | Quick scan |

## 1. Research Scope
- Stake homepage messaging vs 21.com homepage
- Method: Playwright not available — no screenshots captured; text-only observations from public Stake homepage
- No Jira/Confluence context (no MCP)

## 4. Comparison Table (light, 1 competitor)
## 7. Gaps & Opportunities
- (3-5 opportunities, light depth)
- Gap 1
- Gap 2
- Gap 3
```

### Handoff
1. Save: `~/Downloads/competitor-research/homepage-2026-05-23.md`
2. Gamble → Hold the chip
3. Final: "Saved at <path>."

### Memory caching
- No action.

## VERDICT: CR-032
**Title:** Quick scan depth → 3–5 opportunities, screenshots optional
**SKILL.md ref:** competitor-research:L143-L145
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-depth-matches-answer (Quick scan, 3-5, screenshots optional) | PASS | Quick scan shape matches SKILL.md L144 | — |
| 2 | cr-depth-quick-scan-shape | PASS | 3-5 opportunities; screenshots optional | — |

### Notes
SKILL.md L144 spec applied.

---

## TRACE: CR-033

### Preconditions
User input: "detailed comparison of Stake, 1Xbet, Rollbit, Bc.Game on signup". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding (signup)
- **Competitors:** all 4 (explicit)
- **Depth:** Detailed comparison (explicit)
- **Output:** Not inferred

### Phase B — Questions asked
Q1 (Output): sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region): sim Global.

### Playwright actions
Each competitor × signup screens.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding
| Depth | Detailed comparison |
## 1. Research Scope (4 competitors, signup pages)
## 4. Comparison Table (≥4 canonical rows)
## 5. UX Flow Notes (per-competitor key-surface screenshots)
## 7. Gaps & Opportunities (prioritized 5-12 items)
```

### Handoff
Standard.

## VERDICT: CR-033
**Title:** Detailed comparison → full matrix + key-surface screenshots + prioritized recs
**SKILL.md ref:** competitor-research:L145-L147
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-depth-matches-answer (Detailed, 5-12, screenshots required) | PASS | Per SKILL.md L146 | — |
| 2 | cr-depth-detailed-shape | PASS | Matrix + key-surface screenshots + prioritized recs | — |
| 3 | cr-comparison-table-min-rows (4) | PASS | ≥4 canonical labels | — |

### Notes
SKILL.md L146 spec applied.

---

## TRACE: CR-034

### Preconditions
User input: "deep UX flow on Stake and Rollbit signup — every screen, frame by frame". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding
- **Competitors:** Stake, Rollbit
- **Output:** Screenshots + UX notes
- **Depth:** Deep UX flow

### Phase B — Questions asked
none.

### Phase C — Follow-ups
Q1 (Region): sim Global.
Q2 (Sources): sim Direct only.
Q3 (Auth boundary): sim Public-only.

### Playwright actions
- screenshots/stake-signup-step1.png … stake-signup-stepN.png
- screenshots/rollbit-signup-step1.png … rollbit-signup-stepN.png
- (every screen)

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding (Deep UX)
| Depth | Deep UX flow |
## 5. UX Flow Notes
### Stake
- Step 1 — ... `![](screenshots/stake-signup-step1.png)`
- Step 2 — ...
- Friction: ...
### Rollbit (same shape)
### Side-by-side comparison
| Step | Stake | Rollbit |
| 1 | ... | ... |
## 7. Gaps & Opportunities
- Suggested experiments:
  - Experiment 1: ...
  - Experiment 2: ...
```

### Handoff
Standard.

## VERDICT: CR-034
**Title:** Deep UX flow → per-competitor step-by-step + friction + every-screen screenshots + side-by-side + experiments
**SKILL.md ref:** competitor-research:L147-L148
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-depth-matches-answer (Deep, 8-20, screenshots required) | PASS | Per SKILL.md L148 | — |
| 2 | cr-depth-deep-ux-shape | PASS | All five elements present: per-competitor steps, friction, every-screen screenshots, side-by-side, experiments | — |

### Notes
SKILL.md L148 spec applied exactly.

---

## TRACE: CR-035

### Preconditions
User input: "scan how Stake handles VIP onboarding". Memory + Atlassian + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding (VIP onboarding)
- **Competitors:** Stake (explicit)
- **Output:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (Output): sim Strategic recommendations. Q2 (Depth): sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region): sim Global.

### Playwright actions
Stake VIP pages.

### Phase D — Artifact
Standard 7-section report.

### Handoff
1. Save: `~/Downloads/competitor-research/vip-onboarding-2026-05-23.md`
2. Gamble question: "Ready To Gamble On It?" (header: Gamble?)
   options: 1) Bet on it — Publish to Confluence PKB 2) Hold the chip — Save the .md only
   **EXACTLY 2 options, NOT 3.** No "Double down".
3. Simulated user choice: Bet on it
4. Confluence call: ...
5. Final: "Published. Saved at <path>."

## VERDICT: CR-035
**Title:** Ready To Gamble On It? presented with exactly 2 options: Bet on it + Hold the chip
**SKILL.md ref:** competitor-research:L226-L230
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | gamble-handoff-presented-once | PASS | Exactly one Ready To Gamble On It? question at handoff | — |
| 2 | gamble-options-match-spec (Bet on it, Hold the chip) | PASS | Only 2 options per SKILL.md L228-L230 | — |

### Notes
Spec L228-L230 lists exactly 2 options. Double down is PRD-writer only.

---

## TRACE: CR-036

### Preconditions
User input: "detailed comparison: Stake, 1Xbet, Rollbit, Bc.Game on signup — publish when done". Memory + Atlassian + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding
- **Competitors:** all 4 (explicit)
- **Depth:** Detailed comparison

### Phase B — Questions asked
Q1 (Output): sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region): sim 21.com licensed markets.

### Playwright actions
Per-competitor signup screens.

### Phase D — Artifact
Standard.

### Handoff
1. Save path.
2. Gamble → Bet on it
3. Confluence tool lookup: regex `mcp__.*(atlassian|confluence).*` with verbs `createPage` / `create_page` / `createConfluencePage`. cloudId looked up via `getAccessibleAtlassianResources`. Params: cloudId=<active>, spaceId=772571142 (PKB), parentId=772571521 (PKB homepage), contentFormat=markdown, title="Competitor Research Report: Onboarding", body=full report markdown.
4. Surfaces local-only note.
5. Final: "Published at <Confluence URL>. Saved at <local path>."

## VERDICT: CR-036
**Title:** Bet on it + atlassian MCP → Confluence create with PKB spaceId/parentId and markdown format
**SKILL.md ref:** competitor-research:L234-L238
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | mcp-tool-lookup-pattern (confluence-create-page) | PASS | Regex `mcp__.*(atlassian|confluence).*`, verbs createPage/create_page/createConfluencePage | — |
| 2 | confluence-call-uses-pkb-params | PASS | spaceId=772571142, parentId=772571521, contentFormat=markdown per SKILL.md L235-L237 | — |

### Notes
SKILL.md L234-L238 applied exactly.

---

## TRACE: CR-037

### Preconditions
User input: "detailed comparison of Stake and Rollbit signup — publish to Confluence". Memory + Atlassian + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding
- **Competitors:** Stake, Rollbit
- **Depth:** Detailed comparison

### Phase B — Questions asked
Q1 (Output): sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region): sim 21.com licensed markets.

### Playwright actions
Standard.

### Phase D — Artifact
Standard 7-section.

### Handoff
1. Save.
2. Gamble → Bet on it.
3. Confluence call with PKB params.
4. Surfaces note: "Screenshots are local-only at ~/Downloads/competitor-research/onboarding/screenshots/; the Confluence page's inline image references will render as broken — open the local .md to see them rendered."
5. Final: "Published. Saved at <path>."

## VERDICT: CR-037
**Title:** After Confluence publish, surfaces one-line note: screenshots are local-only
**SKILL.md ref:** competitor-research:L239
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-confluence-screenshots-note ("Screenshots are local-only") | PASS | One-line note surfaced per SKILL.md L239 | — |
| 2 | confluence-call-uses-pkb-params | PASS | PKB params applied | — |

### Notes
SKILL.md L239 spec applied. Note: SKILL.md L239 does NOT mention offering to upload screenshots as attachments — flagging as a documentation gap, not a defect.

### Suggested SKILL.md edit
Priority: P2
Location: skills/competitor-research/SKILL.md L239
Symptom: Skill informs user that Confluence images render broken, but does not offer to upload screenshots as Confluence attachments.
Proposed edit (optional enhancement):
```
After the call, surface a one-line note: `Screenshots are local-only at <path>; the Confluence page's inline image references will render as broken — open the local .md to see them rendered. Want me to upload the screenshots as Confluence page attachments? [y/N]`
```

---

## TRACE: CR-038

### Preconditions
User input: "deep UX flow on Stake's signup with screenshots". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Onboarding
- **Competitors:** Stake
- **Output:** Screenshots + UX notes
- **Depth:** Deep UX flow

### Phase B — Questions asked
none.

### Phase C — Follow-ups
Q1 (Region): sim Global. Q2 (Sources): sim Direct only. Q3 (Auth boundary): sim Public-only.

### Playwright actions
- Stake signup every-screen flow
- Title: "Stake Signup Deep UX Flow"
- Slug (kebab-case): stake-signup-deep-ux-flow
- screenshots/stake-signup-1.png through N

### Phase D — Artifact
Standard deep UX 7-section.

### Handoff
1. Save: `~/Downloads/competitor-research/stake-signup-deep-ux-flow-2026-05-23.md`
2. Screenshots subdir: `~/Downloads/competitor-research/stake-signup-deep-ux-flow/screenshots/`
3. Gamble → Hold the chip.
4. Final: "Saved at /Users/talshani/Downloads/competitor-research/stake-signup-deep-ux-flow-2026-05-23.md."

## VERDICT: CR-038
**Title:** Markdown saved to ~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md with co-located screenshots subdir
**SKILL.md ref:** competitor-research:L224
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-markdown-save-path-pattern | PASS | Save path matches `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` per SKILL.md L224 | — |
| 2 | cr-screenshots-subdir-co-located | PARTIAL | SKILL.md L133 shows screenshots at `~/Downloads/competitor-research/<focus-slug>/screenshots/<competitor>-<page>.png` — that's a focus-slug subdir co-located. But the markdown path is `<focus-slug>-<YYYY-MM-DD>.md` (in the parent directory). So screenshots are in a child of the parent dir, NOT a sibling of the .md file. The "co-located" pattern is ambiguous. | Path scheme ambiguity. |
| 3 | markdown-saved-with-absolute-path (competitor-research) | PASS | Folder = competitor-research | — |
| 4 | slug-is-kebab-case (stake-signup-deep-ux-flow) | PASS | Kebab-case slug | — |

### Notes
Defect: SKILL.md L133 specifies screenshots at `~/Downloads/competitor-research/<focus-slug>/screenshots/` (a subdir named after slug, containing screenshots/), while L224 specifies markdown at `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` (in parent dir with date suffix). The .md and screenshots subdir are NOT siblings — the screenshots live in a child folder. If a user clicks the relative path `screenshots/stake-signup-1.png` from the .md, the relative reference will not resolve unless the .md is moved into the `<focus-slug>/` subdir. **Real defect.**

### Suggested SKILL.md edit
Priority: P0
Location: skills/competitor-research/SKILL.md L224 + L133
Symptom: Relative `screenshots/<file>.png` references in the saved .md won't resolve because the .md is at a different path level than the screenshots subdir.
Proposed edit:
```
Write the full report markdown to `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. Screenshots live in `~/Downloads/competitor-research/<focus-slug>/screenshots/` so the relative `![](screenshots/...)` references resolve.
```
OR
```
Write the full report markdown to `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` AND keep screenshots at `~/Downloads/competitor-research/screenshots/<focus-slug>/<file>.png`, referenced as `screenshots/<focus-slug>/<file>.png` in the markdown.
```

---

## TRACE: CR-039

### Preconditions
User input: "detailed comparison of Stake and Rollbit pricing and bonus terms". Memory + Playwright.

### Phase A — Inferences
- **Focus:** Pricing/Bonuses (pricing + bonus terms)
- **Competitors:** Stake, Rollbit (explicit)
- **Depth:** Detailed comparison
- **Output:** Not inferred

### Phase B — Questions asked
Q1 (Output): sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region): sim 21.com licensed markets.

### Playwright actions
- screenshots/stake-pricing.png, stake-bonus-tos.png, rollbit-pricing.png
- (Robots.txt check on Rollbit: if blocked, inline "couldn't access rollbit-bonus-tos — geo-blocked")

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Pricing/Bonuses
## 1. Research Scope
- Stake bonus terms (https://stake.com/promotions) — accessed
- Rollbit bonus terms (https://rollbit.com/promotions) — couldn't access pricing-tos page — geo-blocked from current region (Curacao IP)
- 21.com baseline from Confluence PRD `Pricing & Bonuses v2`
- Method: Playwright used; Jira/Confluence MCP queried for prior research
## 4. Comparison Table (with Stake, Rollbit, our 21.com)
- Each row cites source URL or screenshot
- Assumption rows marked "Assumed: ..."
## 7. Gaps & Opportunities
- Each gap cites concrete competitor + page
```

### Handoff
Standard.

## VERDICT: CR-039
**Title:** Findings are specific, cite source, and call out missing/inaccessible pages
**SKILL.md ref:** competitor-research:L205-L220
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | facts-cite-source | PASS | Each finding ties to URL or screenshot per SKILL.md L207 | — |
| 2 | uses-company-terminology (Stake, Rollbit, 21.com) | PASS | All three present | — |
| 3 | cr-robots-txt-blocked-inline-note | PARTIAL | SKILL.md L141 says "Respect robots.txt; if blocked, note 'couldn't access <page>' in the report and skip" — but doesn't specify HOW the skill checks robots.txt programmatically. Playwright doesn't enforce robots.txt natively. The simulated artifact includes the note for geo-block, not robots.txt specifically. | Spec gap on robots.txt enforcement mechanism. |
| 4 | output-copy-pasteable | PASS | Pure markdown, no shell prompts/truncation | — |

### Notes
SKILL.md L141 references robots.txt but doesn't describe enforcement. Real defect — Playwright MCP doesn't auto-check robots.txt; skill would need to fetch it explicitly first. Flag this as a P1 spec defect.

### Suggested SKILL.md edit
Priority: P1
Location: skills/competitor-research/SKILL.md L141
Symptom: Spec mentions respecting robots.txt but doesn't describe how the skill checks it.
Proposed edit:
```
Respect robots.txt: before navigating to a competitor URL, fetch `https://<competitor-domain>/robots.txt` via Playwright's request API and check whether the target path is disallowed for User-agent: *. If disallowed, note `couldn't access <page> — robots.txt disallow` in the report's §1 and skip. Treat HTTP 403/451/429 or geofence redirects similarly with the appropriate cause cited.
```

---

## TRACE: CR-040

### Preconditions
User input: "compare BetMGM and DraftKings signup flows to ours". Active memory has 21com competitors (Stake/1Xbet/Rollbit/Bc.Game — DIFFERENT from runtime BetMGM/DraftKings). No MCP (Playwright off).

### Phase A — Inferences
- **Focus:** Onboarding (signup)
- **Competitors:** Tricky — runtime names BetMGM, DraftKings (not in memory). Per L69 explicit names in prompt take precedence. Memory is NOT used as inference source here because input is explicit. BUT per L247, runtime DIFFERS from memory → confirm inline before proceeding.
- **Output:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (Output): sim Comparison + opportunities.
Q2 (Depth): sim Detailed comparison.

Inline confirmation (NOT a Phase B question): "Cached competitors in `~/.claude/memory/21com.md` are Stake, 1Xbet, Rollbit, Bc.Game — using BetMGM and DraftKings just for this run. Update memory? [y/N]" (sim: N — keep cache).

### Phase C — Follow-ups
Q1 (Region): "US (BetMGM and DraftKings are US-licensed)" / "21.com licensed markets — translate" / "Global". (sim: US)
Q2 (Sources): "Direct only" / "Direct + Trustpilot" / "Direct + reddit threads". (sim: Direct only)

### Playwright actions (mcp_state=none)
Playwright not available — §1 will note "Playwright not available — no screenshots captured".
ROBOTS.TXT scenario: even if Playwright were available, BetMGM/DraftKings often geo-block from non-US IPs — would yield `couldn't access <page> — geo-blocked` inline notes.

### Phase D — Artifact
```markdown-artifact
# Competitor Research Report: Onboarding (BetMGM + DraftKings)
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
> - Competitors: BetMGM, DraftKings — from prompt (NOTE: differs from cached memory list Stake/1Xbet/Rollbit/Bc.Game — confirmed inline, memory not updated)

| Field | Value |
|---|---|
| **Status** | Draft v1.0 |
| **Author** | Tal |
| **Date** | 2026-05-23 |
| **Depth** | Detailed comparison |
| **Region scope** | US |

## 1. Research Scope
- BetMGM (https://betmgm.com) and DraftKings (https://draftkings.com) signup flows
- **Method: Playwright not available — no screenshots captured.** All observations are from public homepage HTML/copy reviewed via prior knowledge or text fetch.
- **Inaccessible pages:** "couldn't access BetMGM /casino — geo-blocked from current region" if accessed via non-US IP; would degrade gracefully.
- No Jira/Confluence MCP available; baseline 21.com from PM input.

## 2. Competitors Reviewed
- BetMGM — https://betmgm.com
- DraftKings — https://draftkings.com

## 3. Executive Summary
[Leadership-friendly 3-6 sentences]

## 4. Comparison Table
| Area | 21.com | BetMGM | DraftKings | Opportunity |
|---|---|---|---|---|
| Homepage messaging | ... | ... | ... | ... |
| Signup flow | ... | ... | ... | ... |
| Pricing | ... | ... | ... | ... |
| Trust signals | ... | ... | ... | ... |
| Core feature | ... | ... | ... | ... |

## 5. UX Flow Notes
### BetMGM
- [Observations] (no screenshots — Playwright unavailable)
### DraftKings
- [Observations]

## 6. Key Patterns
**Table stakes:** state-licensed banner, geo-IP gate, KYC during signup, responsible-gaming icons.
**Differentiation:** BetMGM SSO via MGM Rewards; DraftKings deep sportsbook cross-sell on signup.

## 7. Gaps & Opportunities
- ...
```

### Handoff
1. Save: `~/Downloads/competitor-research/onboarding-2026-05-23.md`
2. Gamble → Hold the chip (no atlassian MCP).
3. Final: "Saved at <path>. No Confluence page created."

### Memory caching
- Memory file: `~/.claude/memory/21com.md`
- Action: confirmed inline because runtime DIFFERS from memory (BetMGM/DraftKings vs cached Stake/1Xbet/Rollbit/Bc.Game). PM chose NOT to update memory. **Original memory preserved.**

## VERDICT: CR-040
**Title:** Memory edge cases: differs (confirm inline) / empty (cache after Phase B) / Playwright off / robots.txt
**SKILL.md ref:** competitor-research:L247 + L211 + L141
**Overall:** PARTIAL

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | cr-memory-differs-confirms-inline | PARTIAL | Skill DOES confirm inline per L247, but spec doesn't specify exact message format or whether user gets [y/N] choice to overwrite/keep. Trace simulates a y/N prompt, which is reasonable but unspec'd. | Spec gap on confirmation message format. |
| 2 | cr-memory-empty-caches-after-phase-b | PASS (sub-criterion logical) | Spec L211 + L243: append **Competitors:** to memory after Phase B answer. This sub-rule applies when memory is empty (covered conceptually). In this case memory was NOT empty (it had Stake et al.), so this rule applies to the sibling "empty" scenario. Logical extension passes. | — |
| 3 | cr-playwright-unavailable-degrades-gracefully | PASS | §1 Research Scope explicitly notes "Playwright not available — no screenshots captured" per spec L141 + L437. Report still renders. | — |
| 4 | cr-robots-txt-blocked-inline-note | PARTIAL | Spec L141 says note "couldn't access <page>" if blocked. The trace mentions geo-block (not robots.txt specifically). Spec doesn't describe robots.txt enforcement mechanism (Playwright doesn't enforce it natively). | Spec gap (carry-forward from CR-039). |
| 5 | cr-research-scope-notes-playwright-status | PASS | §1 explicitly says "Playwright not available — no screenshots captured" per spec L141 + L437 | — |

### Notes
Multiple sub-rules; mixed results. The four sub-criteria break down as:
- **DIFFERS:** PARTIAL (mechanism works but message format unspec'd)
- **EMPTY:** PASS (logical extension)
- **PLAYWRIGHT off:** PASS (clear in §1)
- **ROBOTS.TXT:** PARTIAL (spec gap on enforcement mechanism)

Overall PARTIAL because two of four sub-rules have unresolved spec gaps even though the skill's intent is clear.

### Suggested SKILL.md edit
Priority: P0
Location: skills/competitor-research/SKILL.md L247 + L141
Symptom: Memory-differs confirmation message format unspec'd; robots.txt enforcement mechanism unspec'd.
Proposed edit (L247):
```
When the PM provides a competitor list at runtime that DIFFERS from the cached memory list, do NOT overwrite silently. Surface one inline message of the form: `Cached competitors in ~/.claude/memory/<slug>.md are <cached list>; you asked about <runtime list>. Update memory to use <runtime list> going forward? [y/N]`. If [y], replace the **Competitors:** line; if [N] (default), proceed with the runtime list for this run only and keep memory unchanged.
```
Proposed edit (L141):
```
Respect robots.txt: before navigating any competitor page, fetch the site's `/robots.txt` (via Playwright's request API or a direct HTTP fetch tool if available) and check whether the target path is allowed for User-agent: *. If disallowed, geo-blocked (HTTP 451), or returning 403/429, note `couldn't access <page> — <cause>` in §1 Research Scope and skip the page. Continue with the remaining accessible pages.
```

---

## END OF RUN
