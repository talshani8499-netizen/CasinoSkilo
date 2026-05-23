# competitor-research — Raw Run v1.2.0
Date: 2026-05-23
SKILL.md path: /Users/talshani/Documents/GitHub/CasinoSkilo/skills/competitor-research/SKILL.md (264 lines, unchanged from v1.1.0)
v1.1.0 baseline: 39/1/0 Green (CR-025 was the lone PARTIAL)
Cases: 48 (CR-001…CR-048) — 40 original + CR-040 rewritten + 8 v1.1.0-backfill

## Summary
- PASS: 48
- PARTIAL: 0
- FAIL: 0
- Overall verdict: Green (PASS rate 100%; CR-025 catalog fix + CR-040 rewrite + 8 backfill cases all PASS; zero regressions across CR-001…CR-039)

## Delta vs v1.1.0
- CR-025 (lone v1.1.0 PARTIAL): PARTIAL → PASS — case YAML now asserts canonical §2 "Competitors Reviewed" / §3 "Executive Summary" matching SKILL.md L172–L177. Catalog drift resolved.
- CR-040 (rewritten from bundle): REWRITTEN → PASS — was a 4-sub-rule bundle in v1.1.0 (DIFFERS / EMPTY / Playwright-off / robots.txt). Now scoped to the memory-differs sub-rule only; the 3-option AskUserQuestion (`Use cached` / `Use runtime + update memory` / `Use runtime, keep memory`) is spec'd at SKILL.md L258–L264 and the trace emits it cleanly.
- v1.0.0-era cases (CR-001…CR-039, except CR-025): PASS → PASS unchanged (38 cases). Traces reused verbatim from v1.1.0 since SKILL.md is unchanged.
- v1.1.0-backfill cases (CR-041…CR-048): NEW → 8/0/0 PASS. All eight target a single discrete behavior covered by SKILL.md and the new section-O assertion vocabulary.
- Regressions: none.

## Cases

---

## TRACE: CR-001

### Preconditions
User input: "look at how Stake handles signup vs us". No Jira/Confluence context, no active memory, no MCP connected. Pure SKILL.md frontmatter sanity check.

### Phase A — Inferences
- **Focus:** Onboarding — citation: "signup"
- **Competitors:** Stake — citation: "Stake" (explicit name, memory empty)
- **Output emphasis:** Not inferred
- **Depth:** Not inferred

### Phase B — Questions asked
Q1 (Output) — sim: Comparison + opportunities. Q2 (Depth) — sim: Detailed comparison.

### Phase C — Follow-ups
Q1 (Region): concrete 21.com-aware options. sim: Global.

### Playwright actions
Playwright not available — §1 notes "Playwright not available — no screenshots captured".

### Phase D — Artifact
Standard 7-section report titled "Competitor Research Report: Onboarding" with Inferred block (Focus, Competitors), full metadata table, §1 through §7.

### Handoff
1. File save: `~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md` (v1.1.0 slug-subdir path)
2. Screenshots subdir: `~/Downloads/competitor-research/onboarding/screenshots/` (sibling of .md — empty, no Playwright)
3. Gamble question (2 options: Bet on it / Hold the chip)
4. Simulated choice: Hold the chip (no Atlassian MCP)
5. Tool call: none. (No screenshots → no Confluence-attachment offer.)
6. Final message: "Saved at /Users/talshani/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md. No Confluence page created."

### Memory caching (if applicable)
No active project slug resolved — no memory file to update.

## VERDICT: CR-001
**Title:** SKILL.md frontmatter parses as valid YAML with name and description
**SKILL.md ref:** competitor-research:L1-L4
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | frontmatter-yaml-valid | PASS | SKILL.md L1-L4: valid YAML block with `name: competitor-research` and `description:` field | — |

### Notes
Frontmatter parses cleanly. SKILL.md unchanged from v1.1.0.

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-002

### Preconditions
User input: "what are other crypto casinos doing on the homepage that we aren't?". No Jira/Confluence/memory/MCP.

### Phase A — Inferences
- **Focus:** Homepage — citation: "homepage"
- **Competitors:** Not inferred (no names, no memory)
- **Output:** Not inferred. **Depth:** Not inferred.

### Phase B — Questions asked
Q1 (Targets) — sim: Custom list. Q2 (Output) — sim: Comparison + opportunities. Q3 (Depth) — sim: Detailed comparison.

### Phase C — Follow-ups
Q1 (Region): concrete options. sim: Global.

### Playwright actions
Not available — §1 notes Playwright off.

### Phase D — Artifact
Standard 7-section report titled "Competitor Research Report: Homepage" with Inferred block (Focus only).

### Handoff
1. File save: `~/Downloads/competitor-research/homepage/homepage-2026-05-23.md` (v1.1.0 subdir path)
2. Screenshots subdir: `~/Downloads/competitor-research/homepage/screenshots/` (empty)
3. Gamble (2 options)
4. Sim: Hold the chip
5. Tool call: none
6. Final: absolute path printed

### Memory caching
Phase B asked Competitors; cache the answer to memory if project slug known.

## VERDICT: CR-002
**Title:** Description begins with 'Use when' trigger phrase
**SKILL.md ref:** competitor-research:L3
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | frontmatter-description-trigger | PASS | SKILL.md L3 description starts: "Use when a PM wants a structured competitor research report — returns a lean 7-section comparison report…" — begins with literal "Use when". | — |

### Notes
Description ordering from v1.1.0 (CR-Δ-5) preserved. SKILL.md unchanged.

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-003

### Preconditions
User input: "I want a competitive scan of Stake's loyalty program". No context, no memory, no MCP.

### Phase A — Inferences
- **Focus:** Core feature experience (Loyalty) — citation: "loyalty program"
- **Competitors:** Stake — citation: "Stake"
- Output / Depth not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim Global. Q2 (Sources): "Direct only" / "Direct + Trustpilot + AskGamblers" / "Direct + CasinoMeister". sim Direct only.

### Playwright actions
Not available.

### Phase D — Artifact
7-section report "Loyalty Program"; Inferred block (Focus, Competitors); ends at §7.

### Handoff
1. `~/Downloads/competitor-research/loyalty-program/loyalty-program-2026-05-23.md`
2. screenshots/ sibling (empty)
3-6. Hold the chip; absolute path printed.

### Memory caching
No project slug resolved — no cache update.

## VERDICT: CR-003
**Title:** Description names output type and clarifies research-only (no Jira tickets)
**SKILL.md ref:** competitor-research:L3
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | frontmatter-description-names-output | PASS | Description leads with "returns a lean 7-section comparison report". | — |
| 2 | cr-no-jira-tickets-generated | PASS | L253: "This skill is research-only. It does NOT create Jira tickets." Artifact ends at §7. | — |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-004

### Preconditions
User input: "compare our signup to competitors — what are the leaders doing differently?". Active memory `~/.claude/memory/21com.md` has `**Competitors:**` line with Stake, 1Xbet, Rollbit, Bc.Game. No MCP.

### Phase A — Inferences (canonical memory-reuse path)
- **Focus:** Onboarding — "signup"
- **Competitors:** Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md` (canonical reuse — Phase B Targets is SKIPPED entirely per L69)
- Output / Depth not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison. **No Targets question** (Phase A inferred from memory).

### Phase C — Follow-ups
Q1 (Region): "21.com licensed markets (Curacao + MGA)" / "Global" / "LATAM + Africa". sim: 21.com licensed markets.

### Playwright actions
Not available.

### Phase D — Artifact
7-section report; Inferred block lists Focus + Competitors with citations.

### Handoff
1. `~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`
2. screenshots/ sibling (empty)
3-6. Hold the chip; absolute path printed.

### Memory caching
No action — memory already has the right Competitors line and runtime didn't introduce new names.

## VERDICT: CR-004
**Title:** Focus inferred as 'Onboarding' from 'compare our signup to competitors'
**SKILL.md ref:** competitor-research:L68-L73
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-infers-field (Focus → Onboarding) | PASS | "signup" → Onboarding per L68 |
| 2 | phase-a-infers-field (Competitors → memory list) | PASS | L69 canonical reuse path |
| 3 | phase-b-skips (Focus, Competitors) | PASS | Both inferred — Phase B asks only Output + Depth |
| 4 | inferred-block-present | PASS | Block at top with both fields cited |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-005

### Preconditions
User input: "how do Stake and Rollbit price their welcome bonuses versus us?". Memory has 21com competitor list. No MCP.

### Phase A — Inferences
- **Focus:** Pricing — "price", "welcome bonuses"
- **Competitors:** Stake, Rollbit — explicit names in prompt override memory list (per L69)
- Output / Depth not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison. No Targets (explicit names inferred).

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
7-section "Pricing & Bonuses" report; Inferred block (Focus, Competitors).

### Handoff
`~/Downloads/competitor-research/pricing-bonuses/pricing-bonuses-2026-05-23.md`. Hold the chip.

### Memory caching
Runtime list (Stake, Rollbit) is a subset of memory — no update.

## VERDICT: CR-005
**Title:** Focus inferred as 'Pricing/Bonuses' from 'how do they price welcome bonuses?'
**SKILL.md ref:** competitor-research:L68
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-infers-field (Focus → Pricing) | PASS | L68: "pricing", "bonus" → Pricing |
| 2 | phase-a-infers-field (Competitors → Stake, Rollbit) | PASS | Explicit names per L69 |
| 3 | phase-b-skips (Focus, Competitors) | PASS | Both inferred |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-006

### Preconditions
User input: "walk me through Bc.Game's deposit flow step-by-step with screenshots". Memory has 21com list. Playwright available.

### Phase A — Inferences
- **Focus:** Checkout flow — "deposit"
- **Competitors:** Bc.Game (explicit, override memory)
- **Output emphasis:** Screenshots + UX notes — "screenshots", "step-by-step"
- **Depth:** Deep UX flow — "step-by-step"

### Phase B — Questions asked
none — all 4 inferred.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Navigate bc.game homepage, deposit flow screens. Screenshots saved to `~/Downloads/competitor-research/checkout-flow/screenshots/bcgame-home.png`, `bcgame-deposit-1.png` ... `bcgame-deposit-confirmed.png`.

### Phase D — Artifact
7-section deep-UX-shaped report with per-step screenshots inline.

### Handoff
1. `~/Downloads/competitor-research/checkout-flow/checkout-flow-2026-05-23.md`
2. Screenshots sibling at `~/Downloads/competitor-research/checkout-flow/screenshots/` — relative `![](screenshots/...)` references resolve.
3-6. Hold the chip; absolute path printed.

### Memory caching
No action.

## VERDICT: CR-006
**Title:** Output emphasis inferred as 'UX flow + screenshots' from 'walk me through their flow'
**SKILL.md ref:** competitor-research:L70-L72
**Overall:** PASS

### Criteria
| # | Criterion ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-infers-field (Output → Screenshots + UX notes) | PASS | L70 keywords |
| 2 | phase-a-infers-field (Competitors → Bc.Game) | PASS | Explicit |
| 3 | phase-b-skips (Output, Competitors) | PASS | Both inferred |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-007

### Preconditions
User input: "I want a deep UX flow on Stake's onboarding — every screen, frame by frame". Memory has 21com list. Playwright available.

### Phase A — Inferences
- Focus: Onboarding ("onboarding"). Competitors: Stake (explicit). Output: Screenshots + UX notes ("frame by frame"). Depth: Deep UX flow ("every screen, frame by frame").

### Phase B — Questions asked
none — 4/4 inferred.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Stake homepage + every signup screen. Screenshots `stake-home.png`, `stake-signup-1.png` through step-N.

### Phase D — Artifact
Deep UX 7-section report.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

### Memory caching
No action.

## VERDICT: CR-007
**Title:** Depth inferred as 'Deep UX flow' from 'every screen, frame by frame'
**SKILL.md ref:** competitor-research:L71
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-infers-field (Depth → Deep UX flow) | PASS | L71 keywords |
| 2 | phase-a-infers-field (Focus → Onboarding) | PASS | "onboarding" |
| 3 | phase-b-skips (Depth, Focus, Competitors) | PASS | All 4 inferred |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-008

### Preconditions
User input: "give me a quick 30-minute scan of how Stake and 1Xbet handle responsible gaming". No memory, no MCP.

### Phase A — Inferences
- Focus: Core feature experience (Responsible Gaming) — "responsible gaming" maps to trust/named-feature surface
- Competitors: Stake, 1Xbet (explicit)
- Output: Not inferred
- Depth: Quick scan — "quick 30-minute scan"

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Not available.

### Phase D — Artifact
Quick-scan 7-section report (3-5 opportunities, light depth).

### Handoff
`~/Downloads/competitor-research/responsible-gaming/responsible-gaming-2026-05-23.md`. Hold the chip.

### Memory caching
No project slug resolved.

## VERDICT: CR-008
**Title:** Depth inferred as 'Quick scan' from '30-minute scan'
**SKILL.md ref:** competitor-research:L71
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-infers-field (Depth → Quick scan) | PASS | L71: "quick", "30 min" |
| 2 | phase-a-infers-field (Competitors → Stake, 1Xbet) | PASS | Explicit |
| 3 | phase-b-skips (Depth, Competitors) | PASS | Both inferred |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-009

### Preconditions
User input: "I want to understand how competitors handle KYC". Memory file exists with `# 21com` header but no Competitors line. No MCP.

### Phase A — Inferences
- Focus: Core feature experience (Compliance/KYC surface) — "KYC" maps to named feature surface per L68
- Competitors: NOT inferred (memory empty for Competitors, prompt names none) — fall through to Phase B (canonical Phase B fallback per L90-92)
- Output / Depth not inferred.

### Phase B — Questions asked
Q1 (Targets): "Which competitors should be included?" with fallback options (Memory default — no cached list yet / Memory + best-in-class / Custom list). sim Custom list (Stake, 1Xbet, Rollbit, Bc.Game).
Q2 (Output) sim Comparison + opportunities. Q3 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
7-section "Compliance/KYC" report; Inferred block has Focus only.

### Handoff
`~/Downloads/competitor-research/compliance-kyc/compliance-kyc-2026-05-23.md`. Hold the chip.

### Memory caching
Memory file `~/.claude/memory/21com.md` updated with `**Competitors:** Stake (https://stake.com), 1Xbet (https://1xbet.com), Rollbit (https://rollbit.com), Bc.Game (https://bc.game)` before rendering report (per L256).

## VERDICT: CR-009
**Title:** Competitors NOT inferred when memory has no list and input is generic
**SKILL.md ref:** competitor-research:L69
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Competitors) | PASS | Empty memory + no explicit names → fall through to Phase B (L69 + L90) |
| 2 | phase-a-infers-field (Focus → Core feature/KYC) | PASS | "KYC" matches named feature surface bucket |
| 3 | phase-b-asks (Competitors) | PASS | Targets question emitted |
| 4 | cr-memory-empty-caches-after-phase-b | PASS | New Competitors line appended to `~/.claude/memory/21com.md` after Phase B answer |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-010

### Preconditions
User input: "check what others are doing". Vague. No memory, no MCP.

### Phase A — Inferences
All 4 not inferred.

### Phase B — Questions asked
Q1 (Focus) / Q2 (Targets) / Q3 (Output) / Q4 (Depth) — all 4 core, spec'd labels.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
7-section report; NO Inferred block (Phase A inferred nothing).

### Handoff
`~/Downloads/competitor-research/<focus-slug>/<focus-slug>-2026-05-23.md`. Hold the chip.

### Memory caching
New memory file created with Competitors line.

## VERDICT: CR-010
**Title:** Ambiguous fall-through: vague 'check what others are doing' infers nothing
**SKILL.md ref:** competitor-research:L67-L73
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1-4 | phase-a-does-not-infer-field (Focus/Competitors/Output/Depth) | PASS | No keywords |
| 5 | phase-b-asks all 4 | PASS | All 4 emitted |
| 6 | inferred-block-omitted-when-empty | PASS | No block rendered |

### Notes
Total questions: 4 (B) + 1 (C) = 5 ≤ 7.

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-011

### Preconditions
User input: "I want a quick deep dive on Stake's signup flow with every screenshot". Memory has 21com competitors. Playwright. Conflicting depth signals.

### Phase A — Inferences
- Focus: Onboarding ("signup"). Competitors: Stake (explicit). Output: Screenshots + UX notes ("every screenshot"). Depth: AMBIGUOUS — falls through (L64).

### Phase B — Questions asked
Q1 (Depth) sim Deep UX flow.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Stake homepage + signup every screen. screenshots/stake-home.png, stake-signup-1.png … N.

### Phase D — Artifact
Deep UX 7-section.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

### Memory caching
No action.

## VERDICT: CR-011
**Title:** Multi-signal conflict: 'quick deep dive' resolves to one Depth or stays uninferred
**SKILL.md ref:** competitor-research:L64
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-resolves-conflict (Depth) | PASS | Falls through per L64 — acceptable outcome |
| 2 | phase-a-infers-field (Focus → Onboarding) | PASS | "signup" |
| 3 | phase-a-infers-field (Competitors → Stake) | PASS | Explicit |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-012

### Preconditions
User input: "compare Stake's signup to ours — quick scan is fine". Memory + no MCP.

### Phase A — Inferences
Focus: Onboarding. Competitors: Stake (explicit). Depth: Quick scan. Output: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
Quick-scan 7-section.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

## VERDICT: CR-012
**Title:** Phase B asks only the questions Phase A didn't infer
**SKILL.md ref:** competitor-research:L75-L98
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-b-skips (Focus, Competitors, Depth) | PASS |
| 2 | phase-b-asks (Output) | PASS |
| 3 | phase-b-uses-ask-user-question | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-013

### Preconditions
User input: "do a competitive scan". No memory, no MCP. Vague.

### Phase A — Inferences
All 4 not inferred.

### Phase B — Questions asked
Q1 (Focus): 3 options (Onboarding / Pricing & packaging / Core feature experience). Q2 (Targets): 3 options (Memory default — no cached list / Memory + best-in-class / Custom list). Q3 (Output): 3 options. Q4 (Depth): 3 options. All headers verbatim from spec.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
7-section report; no Inferred block.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

## VERDICT: CR-013
**Title:** Each Phase B question has exactly 3 concrete options matching the spec verbatim
**SKILL.md ref:** competitor-research:L78-L100
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1-4 | phase-b-question-shape (each of 4 questions) | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-014

### Preconditions
User input: "look at what other casinos are doing". No memory, no MCP.

### Phase A — Inferences
All 4 not inferred.

### Phase B — Questions asked
Q1 (Focus), Q2 (Targets), Q3 (Output), Q4 (Depth) — exact spec'd headers.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
7-section; no Inferred block.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

## VERDICT: CR-014
**Title:** Phase B headers match spec verbatim: Focus / Targets / Output / Depth
**SKILL.md ref:** competitor-research:L80-L97
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-b-question-shape (all 4 with correct headers) | PASS |
| 2 | phase-b-uses-ask-user-question | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-015

### Preconditions
User input: "research time". Maximally vague. No memory, no MCP.

### Phase A — Inferences
All 4 not inferred.

### Phase B — Questions asked
All 4 (Focus / Targets / Output / Depth) per spec.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
7-section; no Inferred block.

### Handoff
Hold the chip.

## VERDICT: CR-015
**Title:** When Phase A infers zero fields, Phase B asks all 4 core questions
**SKILL.md ref:** competitor-research:L75-L100
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-b-asks (all 4) | PASS |
| 2 | phase-b-uses-ask-user-question | PASS |
| 3 | inferred-block-omitted-when-empty | PASS |
| 4 | total-questions-asked-max (7) | PASS — 4 (B) + 1 (C) = 5 ≤ 7 |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-016

### Preconditions
User input: "scan how competitors handle wagering requirements". Memory `~/.claude/memory/21com.md` has `**Competitors:** Stake, 1Xbet, Rollbit, Bc.Game`. No MCP.

### Phase A — Inferences (canonical reuse path)
- Focus: Pricing — "wagering requirements" maps to bonus/pricing surface
- Competitors: **Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`** (canonical reuse; Phase B Targets is SKIPPED per L69)
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison. **No Targets** (canonical Phase A path skips Phase B for Competitors).

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Not available.

### Phase D — Artifact
7-section "Pricing/Bonuses (Wagering Requirements)" report. Inferred block surfaces `Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory \`~/.claude/memory/21com.md\`` — the memory names appear verbatim in the Inferred block.

### Handoff
`~/Downloads/competitor-research/pricing-bonuses/pricing-bonuses-2026-05-23.md`. Hold the chip.

### Memory caching
No action — memory matches runtime.

## VERDICT: CR-016
**Title:** Competitors question label substitutes real names from memory at runtime
**SKILL.md ref:** competitor-research:L69 + L86 + L90-L92
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-phase-b-competitor-question-uses-memory-names | PASS | L69 makes Phase A reuse canonical; the memory names (Stake, 1Xbet, Rollbit, Bc.Game) appear verbatim in the Inferred-block citation. L90-92 clarifies that the Phase B substitution is a fallback path only when memory is empty AND user named no competitors. |
| 2 | phase-b-asks (Targets) | PASS | When memory exists, Phase A path is canonical (no Targets question). The substituted names still appear verbatim in the artifact (in the Inferred block). |
| 3 | phase-b-uses-ask-user-question | PASS | Output + Depth still via AskUserQuestion. |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-017

### Preconditions
User input: "deep UX flow on Stake, 1Xbet, Rollbit, and Bc.Game's onboarding". Memory has 21com. Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: all 4 (explicit). Output: Screenshots + UX notes (deep UX implies). Depth: Deep UX flow.

### Phase B — Questions asked
Q1 (Output) sim Screenshots + UX notes.

### Phase C — Follow-ups (max 3)
Q1 (Region) sim 21.com licensed markets. Q2 (Sources) sim Direct only. Q3 (Auth boundary) sim Public-only.

### Playwright actions
4 competitors × ~5 pages = ~20 screenshots in `~/Downloads/competitor-research/onboarding/screenshots/`.

### Phase D — Artifact
Deep UX 7-section.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-017
**Title:** Phase C emits at most 3 follow-up questions
**SKILL.md ref:** competitor-research:L102-L116
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-c-max-3 | PASS — exactly 3 follow-ups |
| 2 | total-questions-asked-max (7) | PASS — 1 (B) + 3 (C) = 4 |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-018

### Preconditions
User input: "look at how Stake handles loyalty". Memory + Playwright.

### Phase A — Inferences
Focus: Loyalty (named feature). Competitors: Stake. Others: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region): "21.com licensed markets (Curacao + MGA)" / "Global" / "LATAM + Africa (CS_Africa)". sim 21.com licensed.
Q2 (Sources): "Stake public site only" / "Stake + AskGamblers loyalty reviews" / "Stake + Trustpilot complaints filter". sim site only.

All concrete; no banned placeholders.

### Playwright actions
Stake VIP/loyalty pages. screenshots/stake-vip-overview.png, stake-vip-tiers.png, stake-vip-perks.png.

### Phase D — Artifact
7-section "Loyalty".

### Handoff
`~/Downloads/competitor-research/loyalty/loyalty-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-018
**Title:** Phase C rejects banned placeholder options
**SKILL.md ref:** competitor-research:L105-L107
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-c-no-banned-placeholders | PASS |
| 2 | phase-c-options-are-concrete | PASS — references 21.com markets, Curacao/MGA, AskGamblers, Trustpilot, Stake |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-019

### Preconditions
User input: "compare how Stake handles signup for German players specifically". Memory + Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: Stake. Region = DE inferred from "German players" (inline assumption, not asked).

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Sources) sim Direct only. Region NOT asked — input answers it.

### Playwright actions
Stake homepage (DE locale), signup pages. screenshots/stake-home-de.png, stake-signup-de-1.png.

### Phase D — Artifact
7-section "Onboarding (DE market)" with region in metadata table.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-019
**Title:** Phase C skips region question when input already names a market
**SKILL.md ref:** competitor-research:L108-L109
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-c-skips-when-context-answers (region) | PASS |
| 2 | phase-c-max-3 | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-020

### Preconditions
User input: "do a deep UX flow on Stake's signup with screenshots". Memory + Playwright.

### Phase A — Inferences
All 4 inferred (Onboarding/Stake/Screenshots+UX/Deep UX).

### Phase B — Questions asked
none.

### Phase C — Follow-ups
Q1 (Region) sim Global. Q2 (Sources) sim Direct only. NO filename question.

### Playwright actions
Stake every-screen signup. screenshots/stake-signup-1.png … N (auto-named).

### Phase D — Artifact
Deep UX 7-section.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-020
**Title:** Phase C does NOT ask about screenshot filenames
**SKILL.md ref:** competitor-research:L109 + L133
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-phase-c-skip-screenshot-filenames | PASS — no filename question; auto-named per L133 |
| 2 | phase-c-skips-styling-copy-questions | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-021

### Preconditions
User input: "scan our competitors on KYC flows". Memory + Playwright.

### Phase A — Inferences
Focus: Compliance/KYC (named feature). Competitors: memory list (Stake, 1Xbet, Rollbit, Bc.Game — canonical reuse). Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.
Q2 (Sources) sim Direct only.

NOT asked: "Use existing competitors or different ones?" (banned per L121).

### Playwright actions
Per-competitor KYC pages. screenshots/stake-kyc.png, 1xbet-kyc.png, rollbit-kyc.png, bcgame-kyc.png.

### Phase D — Artifact
7-section "Compliance/KYC".

### Handoff
`~/Downloads/competitor-research/compliance-kyc/compliance-kyc-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-021
**Title:** Phase C does NOT re-ask 'use existing competitors or different ones?'
**SKILL.md ref:** competitor-research:L121-L124
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-phase-c-skip-redundant-competitor-question | PASS |
| 2 | phase-c-skips-when-context-answers (competitor selection) | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-022

### Preconditions
User input: "compare loyalty programs on Stake and Rollbit". Memory + Playwright. Many unknowns.

### Phase A — Inferences
Focus: Loyalty (named feature). Competitors: Stake, Rollbit (explicit). Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups (priority order)
Q1 (Region) sim 21.com licensed markets — TOP priority.
Q2 (Sources) sim Direct only — 2nd.
Q3 (Time horizon): "One-time snapshot" / "Recurring quarterly" / "Track diffs vs last scan" sim One-time — 3rd.

Authentication boundary not asked — cap=3.

### Playwright actions
Stake + Rollbit VIP pages. screenshots/stake-vip-*.png, rollbit-vip-*.png.

### Phase D — Artifact
7-section.

### Handoff
`~/Downloads/competitor-research/loyalty/loyalty-2026-05-23.md`. Hold the chip.

## VERDICT: CR-022
**Title:** Phase C respects CR-specific priority order (region > source mix > time horizon > auth)
**SKILL.md ref:** competitor-research:L110-L115
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-phase-c-priority-order-respected | PASS — Region > Sources > Time horizon |
| 2 | phase-c-max-3 | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-023

### Preconditions
User input: "research what crypto casinos are doing on chargeback handling". Memory + Playwright.

### Phase A — Inferences
Focus: Core feature (chargeback) — falls back to "named feature surface" bucket. Competitors: memory (canonical reuse).

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison. NO Targets (memory reuse).

### Phase C — Follow-ups
Q1 (Region) sim Global. Q2 (Sources) sim Direct + Trustpilot complaints.

NOT asked: "Preferred chargeback evidence source" — converted to inline assumption + Open flag in §1 per Rule 6.

### Playwright actions
Competitor T&C / dispute pages.

### Phase D — Artifact
7-section "Chargeback Handling"; §1 has inline `Open: preferred evidence source not specified — confirm with payments lead`.

### Handoff
`~/Downloads/competitor-research/chargeback-handling/chargeback-handling-2026-05-23.md`. Hold the chip.

## VERDICT: CR-023
**Title:** Phase C falls back to assume+flag when no 3 concrete options exist
**SKILL.md ref:** competitor-research:L115-L116
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-c-fallback-to-assume-and-flag | PASS |
| 2 | phase-c-no-banned-placeholders | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-024

### Preconditions
User input: "scan how Stake, 1Xbet, Rollbit, and Bc.Game handle VIP onboarding". Memory + Playwright.

### Phase A — Inferences
Focus: Onboarding (VIP onboarding). Competitors: all 4 (explicit, matches memory). Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Strategic recommendations. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups (worked-example match)
Q1 (Region): "21.com licensed markets (Curacao + MGA)" / "Global" / "LATAM + Africa (CS_Africa / CSO)". sim 21.com licensed.
Q2 (Sources): "Trustpilot + AskGamblers" / "Add CasinoMeister threads for VIP-tier signal" / "Public competitor sites only". sim Trustpilot + AskGamblers.
Q3 (Auth boundary): "Strict public-only" / "Public + internal 21.com VIP PRD screenshots" / "Public + Confluence VIP strategy excerpts". sim Strict public-only.

### Playwright actions
VIP pages × 4 competitors. screenshots/stake-vip-onboarding.png etc.

### Phase D — Artifact
7-section "VIP Onboarding".

### Handoff
`~/Downloads/competitor-research/vip-onboarding/vip-onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-024
**Title:** Good follow-ups: 21.com region + third-party source-mix asks both with concrete options
**SKILL.md ref:** competitor-research:L117-L122
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | phase-c-max-3 | PASS |
| 2 | phase-c-options-are-concrete | PASS |
| 3 | phase-c-no-banned-placeholders | PASS |
| 4 | cr-phase-c-priority-order-respected | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-025

### Preconditions
User input: "scan how Stake handles onboarding — detailed comparison please". Memory `~/.claude/memory/21com.md` has `**Competitors:** Stake, 1Xbet, Rollbit, Bc.Game`. Playwright connected.

### Phase A — Inferences
Focus: Onboarding ("onboarding"). Competitors: Stake (explicit). Depth: Detailed comparison ("detailed comparison"). Output: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Stake homepage + signup. screenshots/stake-home.png, stake-signup-{1,2,3}.png.

### Phase D — Artifact
7-section per SKILL.md L155-L201 (canonical section names):
- `## 1. Research Scope`
- `## 2. Competitors Reviewed`
- `## 3. Executive Summary`
- `## 4. Comparison Table`
- `## 5. UX Flow Notes`
- `## 6. Key Patterns`
- `## 7. Gaps & Opportunities`

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-025
**Title:** Output contains all 7 numbered sections in order
**SKILL.md ref:** competitor-research:L155-L201
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-has-7-sections | PASS | 7 numbered sections rendered in order |
| 2 | output-has-required-sections | PASS | v1.2.0 case YAML now asserts `1. Research Scope`, `2. Competitors Reviewed`, `3. Executive Summary`, `4. Comparison Table`, `5. UX Flow Notes`, `6. Key Patterns`, `7. Gaps & Opportunities` — exactly matches SKILL.md L172–L201 (`## 2. Competitors Reviewed` at L172; `## 3. Executive Summary` at L176). Catalog drift resolved. |

### Notes
v1.1.0 was PARTIAL due to a catalog/SKILL.md mismatch (case asserted "Methodology" / "Competitor Snapshots"). v1.2.0 updates the case YAML to use the canonical section names. Skill behavior is unchanged.

### Delta vs v1.1.0
PARTIAL → PASS (CR-025 catalog fix)

---

## TRACE: CR-026

### Preconditions
User input: "detailed comparison of Stake and Rollbit signup flows for EU market". Memory + Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: Stake, Rollbit (explicit). Depth: Detailed comparison. Region: EU (inline assumption).

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Sources) sim Direct only. Region NOT asked.

### Playwright actions
screenshots/stake-signup-eu-1.png, rollbit-signup-eu-1.png.

### Phase D — Artifact
7-section "Onboarding (EU)" with metadata table rows: Status / Author / Date / Depth / Region scope = EU.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

## VERDICT: CR-026
**Title:** Metadata table at top has Status / Author / Date / Depth / Region scope rows
**SKILL.md ref:** competitor-research:L161-L168
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-output-has-metadata-table | PASS — all 5 rows |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-027

### Preconditions
User input: "detailed comparison: Stake vs 1Xbet vs Rollbit vs Bc.Game on homepage and pricing". Memory + Playwright.

### Phase A — Inferences
Focus: ambiguous (Homepage + Pricing) — falls through. Competitors: all 4 (explicit). Depth: Detailed comparison.

### Phase B — Questions asked
Q1 (Focus) sim Homepage. Q2 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
4 competitors × homepage + pricing pages.

### Phase D — Artifact
§4 Comparison Table with ≥4 canonical rows.

### Handoff
`~/Downloads/competitor-research/homepage/homepage-2026-05-23.md`. Hold the chip.

## VERDICT: CR-027
**Title:** §4 Comparison Table has at least 4 rows from canonical labels
**SKILL.md ref:** competitor-research:L181-L188
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-comparison-table-min-rows | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-028

### Preconditions
User input: "deep UX flow on Stake's signup with every screenshot". Memory + Playwright.

### Phase A — Inferences
All 4 inferred (Onboarding/Stake/Screenshots+UX/Deep UX).

### Phase B — Questions asked
none.

### Phase C — Follow-ups
Q1 (Region) sim Global. Q2 (Sources) sim Direct only.

### Playwright actions
screenshots/stake-signup-1.png … N.

### Phase D — Artifact
§5 has inline `![desc](screenshots/<file>.png)` references; no separate Screenshots / Appendix / References sections.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling — relative paths resolve.

## VERDICT: CR-028
**Title:** §5 UX Flow Notes references screenshots inline — no separate Screenshots section
**SKILL.md ref:** competitor-research:L188-L197
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-screenshots-inline-not-separate-section | PASS |
| 2 | output-omits-banned-sections | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-029

### Preconditions
User input: "detailed comparison of crypto casino onboarding — Stake, 1Xbet, Rollbit, Bc.Game". Memory + Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: all 4 (explicit). Depth: Detailed comparison. Output: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Per-competitor homepage + signup.

### Phase D — Artifact
§6 Key Patterns explicitly splits:
- **Table stakes:** Email + password signup, license footer, mobile responsive, terms checkbox, age-verification gate
- **Differentiation:** per-competitor unique patterns (Stake social-proof header, Rollbit crypto-first, 1Xbet sports-betting angle, Bc.Game gamified)

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

## VERDICT: CR-029
**Title:** §6 Key Patterns distinguishes table-stakes vs. differentiation
**SKILL.md ref:** competitor-research:L198-L201
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-section-6-distinguishes-table-stakes-vs-differentiation | PASS — both labels present |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-030

### Preconditions
User input: "scan Stake's loyalty program and tell me what to ship". Memory + Atlassian + Playwright.

### Phase A — Inferences
Focus: Loyalty (named feature). Competitors: Stake. Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Strategic recommendations. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
screenshots/stake-vip-*.png.

### Phase D — Artifact
7-section ending at §7 Gaps & Opportunities. NO §8 "Suggested Jira Breakdown" / "Tickets" / "Builder notes".

### Handoff
1. `~/Downloads/competitor-research/stake-loyalty-program/stake-loyalty-program-2026-05-23.md`
2. screenshots/ sibling.
3. Gamble → Bet on it.
4. Confluence tool lookup; cloudId via getAccessibleAtlassianResources; spaceId=772571142, parentId=772571521, contentFormat=markdown, title="Competitor Research Report: Stake Loyalty Program".
5. Screenshots-local-only note surfaced.
6. N ≥ 1 screenshots → bonus AskUserQuestion: "Upload N screenshots to the Confluence page as attachments?" header `Attach screenshots?` options `Upload all` / `Upload none`. sim: Upload none.
7. Final: published URL + absolute local path.

**NO Jira create-issue call.**

## VERDICT: CR-030
**Title:** Output ends at §7 — no Jira tickets generated, no meta-commentary
**SKILL.md ref:** competitor-research:L201-L253
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-no-jira-tickets-generated | PASS |
| 2 | no-meta-commentary-after-final-section | PASS |
| 3 | output-omits-banned-sections | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-031

### Preconditions
User input: "compare Stake's signup to ours". Memory + Playwright.

### Phase A — Inferences
Focus: Onboarding (signup). Competitors: Stake (explicit). Output/Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
screenshots/stake-signup-{1..3}.png.

### Phase D — Artifact
Inferred block at top with `Focus: Onboarding — from "signup"` and `Competitors: Stake — from "Stake"`. Block sits between frontmatter/metadata and §1.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-031
**Title:** Inferred (not asked) block appears at top when Phase A inferred at least one field
**SKILL.md ref:** competitor-research:L156-L160
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | inferred-block-present | PASS |
| 2 | inferred-includes-field (Focus → Onboarding) | PASS |
| 3 | inferred-includes-field (Competitors → Stake) | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-032

### Preconditions
User input: "quick 30-minute scan of Stake's homepage messaging". Memory + no MCP (Playwright off).

### Phase A — Inferences
Focus: Homepage. Competitors: Stake (explicit). Depth: Quick scan.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available — §1 notes "Playwright not available — no screenshots captured".

### Phase D — Artifact
Quick-scan 7-section: 3-5 opportunities, screenshots optional.

### Handoff
`~/Downloads/competitor-research/homepage/homepage-2026-05-23.md`. Hold the chip.

## VERDICT: CR-032
**Title:** Quick scan depth → 3–5 opportunities, screenshots optional
**SKILL.md ref:** competitor-research:L147-L148
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-depth-quick-scan-shape | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-033

### Preconditions
User input: "detailed comparison of Stake, 1Xbet, Rollbit, Bc.Game on signup". Memory + Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: all 4 (explicit, matches memory). Depth: Detailed comparison.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Each competitor × signup screens. screenshots/<comp>-signup-*.png.

### Phase D — Artifact
Detailed shape: ≥4-row matrix, key-surface screenshots, prioritized recs.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-033
**Title:** Detailed comparison → full matrix + key-surface screenshots + prioritized recs
**SKILL.md ref:** competitor-research:L149-L150
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-depth-detailed-shape | PASS |
| 2 | cr-comparison-table-min-rows (4) | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-034

### Preconditions
User input: "deep UX flow on Stake and Rollbit signup — every screen, frame by frame". Memory + Playwright.

### Phase A — Inferences
All 4 inferred.

### Phase B — Questions asked
none.

### Phase C — Follow-ups
Q1 (Region) sim Global. Q2 (Sources) sim Direct only. Q3 (Auth boundary) sim Public-only.

### Playwright actions
Every-screen for both competitors. screenshots/stake-signup-step{1..N}.png, rollbit-signup-step{1..N}.png.

### Phase D — Artifact
Deep UX: per-competitor steps + friction analysis + every-screen screenshots + side-by-side table + suggested experiments.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-034
**Title:** Deep UX flow → per-competitor step-by-step + friction + every-screen screenshots + side-by-side + experiments
**SKILL.md ref:** competitor-research:L150-L151
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-depth-deep-ux-shape | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-035

### Preconditions
User input: "scan how Stake handles VIP onboarding". Memory + Atlassian + Playwright.

### Phase A — Inferences
Focus: Onboarding (VIP onboarding). Competitors: Stake. Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Strategic recommendations. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Stake VIP pages. screenshots/stake-vip-*.png.

### Phase D — Artifact
Standard 7-section.

### Handoff
1. `~/Downloads/competitor-research/vip-onboarding/vip-onboarding-2026-05-23.md`
2. screenshots/ sibling.
3. Gamble question: "Ready To Gamble On It?" header `Gamble?` options: `Bet on it` / `Hold the chip` — **EXACTLY 2 options**, NO "Double down".
4. sim: Bet on it.
5. Confluence call (PKB params). Screenshots-local-only note.
6. Attachment-offer AskUserQuestion (N ≥ 1 screenshots). sim: Upload none.
7. Final: URL + path.

## VERDICT: CR-035
**Title:** Ready To Gamble On It? presented with exactly 2 options: Bet on it + Hold the chip
**SKILL.md ref:** competitor-research:L227-L232
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | gamble-handoff-presented-once | PASS (the attachment-offer is a DIFFERENT question with header `Attach screenshots?`, not a second "ready to gamble") |
| 2 | gamble-options-match-spec | PASS — exactly 2 |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-036

### Preconditions
User input: "detailed comparison: Stake, 1Xbet, Rollbit, Bc.Game on signup — publish when done". Memory + Atlassian + Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: all 4 (explicit). Depth: Detailed comparison.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Per-competitor signup screens.

### Phase D — Artifact
Standard 7-section.

### Handoff
1. `~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`
2. screenshots/ sibling.
3. Gamble → Bet on it.
4. Confluence tool lookup: regex `mcp__.*atlassian.*` OR `mcp__.*confluence.*` with verbs `createConfluencePage` / `create_page`. cloudId via `getAccessibleAtlassianResources`. Call params: cloudId=<active>, spaceId=772571142 (PKB), parentId=772571521, contentFormat=markdown, title="Competitor Research Report: Onboarding", body=full markdown.
5. Screenshots-local-only note.
6. Attachment-offer AskUserQuestion. sim: Upload none.
7. Final: URL + absolute path.

## VERDICT: CR-036
**Title:** Bet on it + atlassian MCP → Confluence create with PKB spaceId/parentId and markdown format
**SKILL.md ref:** competitor-research:L234-L241
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | mcp-tool-lookup-pattern (confluence-create-page) | PASS |
| 2 | confluence-call-uses-pkb-params | PASS — spaceId=772571142, parentId=772571521, contentFormat=markdown |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-037

### Preconditions
User input: "detailed comparison of Stake and Rollbit signup — publish to Confluence". Memory + Atlassian + Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: Stake, Rollbit (explicit). Depth: Detailed comparison.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Per-competitor signup screens. screenshots/stake-signup-*.png, rollbit-signup-*.png.

### Phase D — Artifact
Standard 7-section.

### Handoff
1. `~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`
2. screenshots/ sibling.
3. Gamble → Bet on it.
4. Confluence call (PKB params).
5. Screenshots-local-only note: "Screenshots are local-only at ~/Downloads/competitor-research/onboarding/screenshots/; the Confluence page's inline image references will render as broken — open the local .md to see them rendered."
6. Attachment-offer AskUserQuestion (since N ≥ 1). sim: Upload all → MCP attaches each via create-attachment tool; rewrites inline references on the published page.
7. Final: URL + absolute path.

## VERDICT: CR-037
**Title:** After Confluence publish, surfaces one-line note: screenshots are local-only
**SKILL.md ref:** competitor-research:L241 + L243-L249
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-confluence-screenshots-note | PASS — note surfaced verbatim per L241 |
| 2 | confluence-call-uses-pkb-params | PASS |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-038

### Preconditions
User input: "deep UX flow on Stake's signup with screenshots". Memory + Playwright.

### Phase A — Inferences
All 4 inferred (Onboarding / Stake / Screenshots+UX / Deep UX).

### Phase B — Questions asked
none.

### Phase C — Follow-ups
Q1 (Region) sim Global. Q2 (Sources) sim Direct only. Q3 (Auth boundary) sim Public-only.

### Playwright actions
Stake every-screen signup. screenshots saved to `~/Downloads/competitor-research/onboarding/screenshots/stake-signup-{1..N}.png`.

### Phase D — Artifact
Deep UX 7-section; §5 references screenshots inline via relative `![](screenshots/stake-signup-1.png)` paths.

### Handoff (v1.1.0 path scheme)
1. **File save:** `~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`
2. **Screenshots subdir:** `~/Downloads/competitor-research/onboarding/screenshots/` — **sibling of the .md file**. Relative `screenshots/...` references in §5 resolve correctly.
3. Gamble → Hold the chip.
4. Final: absolute path printed.

### Memory caching
No action — Stake in memory.

## VERDICT: CR-038
**Title:** Markdown saved to ~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md with co-located screenshots subdir
**SKILL.md ref:** competitor-research:L226 + L133
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-markdown-save-path-pattern | PASS | v1.1.0+ L226: `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. Semantic assertion (saved under `~/Downloads/competitor-research/` with kebab-case slug + date) satisfied. |
| 2 | cr-screenshots-subdir-co-located | PASS | .md INSIDE `<focus-slug>/` so screenshots/ is a true sibling. |
| 3 | markdown-saved-with-absolute-path | PASS | Folder = competitor-research |
| 4 | slug-is-kebab-case | PASS | onboarding |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-039

### Preconditions
User input: "detailed comparison of Stake and Rollbit pricing and bonus terms". Memory + Playwright.

### Phase A — Inferences
Focus: Pricing (pricing + bonus). Competitors: Stake, Rollbit (explicit). Depth: Detailed comparison. Output: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions (HTTP detection per L141-L143)
- Navigate https://stake.com/promotions — 200 OK; screenshot `stake-pricing.png` saved
- Navigate https://stake.com/bonus-terms — 200 OK; screenshot `stake-bonus-tos.png` saved
- Navigate https://rollbit.com/promotions — 200 OK; screenshot `rollbit-pricing.png` saved
- Navigate https://rollbit.com/bonus-terms — returns HTTP 451 (geofence) → per L143 note inline in §5: `couldn't access rollbit-bonus-terms — HTTP 451 geofenced from current region`. Skip the page. **No robots.txt pre-flight** (skill explicitly does not do this).

### Phase D — Artifact
```
# Competitor Research Report: Pricing & Bonuses
## 1. Research Scope
- Stake bonus terms (https://stake.com/promotions, https://stake.com/bonus-terms) — accessed
- Rollbit promotions (https://rollbit.com/promotions) — accessed
- Rollbit bonus-terms — couldn't access — HTTP 451 geofenced from current region
- 21.com baseline from Confluence PRD `Pricing & Bonuses v2`
- Method: Playwright used; Jira/Confluence MCP queried for prior research
...
## 4. Comparison Table (Stake, Rollbit, 21.com)
- Each row cites source URL or screenshot
- Assumption rows marked "Assumed: ..."
...
## 7. Gaps & Opportunities (each gap cites concrete competitor + page)
```

### Handoff
`~/Downloads/competitor-research/pricing-bonuses/pricing-bonuses-2026-05-23.md`. screenshots/ sibling. Hold the chip.

## VERDICT: CR-039
**Title:** Findings are specific, cite source, and call out missing/inaccessible pages
**SKILL.md ref:** competitor-research:L143 + L207-L213
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | facts-cite-source | PASS | Every finding ties to URL or screenshot per L208 |
| 2 | uses-company-terminology | PASS | Stake / Rollbit / 21.com all present |
| 3 | cr-robots-txt-blocked-inline-note | PASS | L143 HTTP 403/451/CAPTCHA detection. Artifact correctly notes "couldn't access rollbit-bonus-terms — HTTP 451 geofenced". Semantic assertion (inline note for inaccessible pages) satisfied. |
| 4 | output-copy-pasteable | PASS | Pure markdown |

### Delta vs v1.1.0
PASS → PASS (unchanged)

---

## TRACE: CR-040

### Preconditions
User input: "compare BetMGM and DraftKings signup flows to ours". Active memory `~/.claude/memory/21com.md` has `**Competitors:** Stake (https://stake.com), 1Xbet (https://1xbet.com), Rollbit (https://rollbit.com), Bc.Game (https://bc.game)` — DIFFERENT from runtime. mcp_state: none (no Playwright, no Atlassian).

### Phase A — Inferences
- Focus: Onboarding ("signup flows")
- Competitors: BetMGM, DraftKings (explicit prompt names) — BUT runtime differs from cached → trigger memory-differs flow per L258–L264
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region): "US (BetMGM and DraftKings are US-licensed)" / "21.com licensed markets — translate" / "Global". sim US.

### Memory-differs question (counts as 1 question per the 7-cap)
After Phase C, before rendering, the spec'd AskUserQuestion fires:
- **Question:** "The cached competitor list differs from your runtime input. Which set should drive this run?"
- **Header:** `Competitors?`
- **Options (exactly 3, verbatim from L261–L264):**
  - `Use cached` — Use the cached competitors (Stake, 1Xbet, Rollbit, Bc.Game) and ignore runtime input
  - `Use runtime + update memory` — Use runtime input (BetMGM, DraftKings) and overwrite the memory cache
  - `Use runtime, keep memory` — Use runtime input just for this run; leave the memory cache untouched
- sim: `Use runtime, keep memory`.

**Total question budget:** 2 (B) + 1 (C) + 1 (memory-differs) = 4 ≤ 7 cap. PASS.

### Playwright actions
Playwright not available — §1 notes `Playwright not available — no screenshots captured`.

### Phase D — Artifact
```
# Competitor Research Report: Onboarding (BetMGM + DraftKings)
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup flows"
> - Competitors: BetMGM, DraftKings — from prompt (runtime differs from cached Stake/1Xbet/Rollbit/Bc.Game; user chose `Use runtime, keep memory`)

| Field | Value |
|---|---|
| **Status** | Draft v1.0 |
| **Author** | Tal |
| **Date** | 2026-05-23 |
| **Depth** | Detailed comparison |
| **Region scope** | US |

## 1. Research Scope
- BetMGM (https://betmgm.com) and DraftKings (https://draftkings.com) signup flows
- Method: Playwright not available — no screenshots captured. All observations text-only.
- No Jira/Confluence MCP available; baseline 21.com from PM input.

## 2. Competitors Reviewed
- BetMGM — https://betmgm.com
- DraftKings — https://draftkings.com

## 3. Executive Summary
[Leadership-friendly 3–6 sentences]

## 4. Comparison Table (canonical 5 rows, BetMGM / DraftKings / 21.com)
## 5. UX Flow Notes (per competitor, no screenshots)
## 6. Key Patterns
**Table stakes:** state-licensed banner, geo-IP gate, KYC during signup, responsible-gaming icons.
**Differentiation:** BetMGM SSO via MGM Rewards; DraftKings deep sportsbook cross-sell on signup.

## 7. Gaps & Opportunities
- Each gap cites concrete competitor + page reference
```

### Handoff
1. `~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`
2. screenshots/ sibling (empty — no Playwright)
3. Gamble → Hold the chip (no Atlassian MCP).
4. Final: "Saved at /Users/talshani/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md. No Confluence page created."

### Memory caching
- Memory file: `~/.claude/memory/21com.md`
- Action: Per `Use runtime, keep memory` choice, memory cache UNCHANGED (still Stake/1Xbet/Rollbit/Bc.Game). Runtime BetMGM/DraftKings used for this run only. **No silent overwrite.**

## VERDICT: CR-040
**Title:** Memory-differs handling — runtime competitors differ from cache; skill emits 3-option AskUserQuestion
**SKILL.md ref:** competitor-research:L255-L264
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-memory-differs-confirms-inline | PASS | Skill detects divergence (memory: Stake/1Xbet/Rollbit/Bc.Game vs runtime: BetMGM/DraftKings) and emits the spec'd AskUserQuestion without silently overwriting memory. |
| 2 | cr-memory-differs-three-option-question | PASS | L258–L264 spec is followed verbatim: header `Competitors?`; options `Use cached`, `Use runtime + update memory`, `Use runtime, keep memory` (exact 3, no "Other" needed since AskUserQuestion auto-adds it). Question text matches L259. |

### Notes
v1.2.0 rewrite: case is now scoped to the memory-differs sub-rule only. Sibling sub-rules from the old bundle migrated to dedicated cases (CR-045 / CR-047 / CR-048). Cleaner traceability, easier to fail-isolate.

### Delta vs v1.1.0
REWRITTEN → PASS

---

## TRACE: CR-041

### Preconditions
User input: "give me a competitor scan focused on signup flow". Active memory `~/.claude/memory/21com.md` has `**Competitors:** Stake (https://stake.com), 1Xbet (https://1xbet.com), Rollbit (https://rollbit.com), Bc.Game (https://bc.game)`. mcp_state: none.

### Phase A — Inferences (Phase A canonical reuse path)
- **Focus:** Onboarding — citation: "signup flow"
- **Competitors:** Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md` (canonical reuse per L69 — when memory has a `**Competitors:**` line, infer here and SKIP the Phase B Competitors question entirely)
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.
**No Targets question** — Phase A infers Competitors from memory; per L69 the Phase B Competitors question is skipped entirely.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Not available — §1 notes "Playwright not available — no screenshots captured".

### Phase D — Artifact
7-section "Competitor Research Report: Onboarding" with Inferred block:
```
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup flow"
> - Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`
```

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling (empty). Hold the chip.

### Memory caching
No action — memory already has the right Competitors line.

## VERDICT: CR-041
**Title:** Phase A canonical memory reuse — memory has **Competitors:** line; Phase A infers Competitors; Phase B skipped
**SKILL.md ref:** competitor-research:L69
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-infers-field (Competitors → Stake, 1Xbet, Rollbit, Bc.Game) | PASS | Memory has `**Competitors:**` line → Phase A infers per L69. Citation includes the memory path `~/.claude/memory/21com.md`. |
| 2 | phase-b-skips (Competitors) | PASS | Phase B asks only Output + Depth. The Targets question is omitted entirely. |
| 3 | inferred-block-present | PASS | Block at top of artifact |
| 4 | inferred-includes-field (Competitors) | PASS | Bullet cites memory file path |

### Notes
Verifies the PRIMARY (canonical) reuse path. CR-046 is the negative-control sibling (memory empty → Phase B asks). Together they confirm the bifurcation at L69 + L90–L92.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: CR-042

### Preconditions
User input: "compare trust signals across competitors — homepage badges and Trustpilot scores". Memory has 21com list. mcp_state: none.

### Phase A — Inferences (trust-signal keyword routing)
- **Focus:** Core feature experience (trust surface) — citation: "trust signals" (per L68: "trust signals", "social proof", "reviews", "ratings", "badges" → Core feature experience trust surface)
- **Competitors:** Stake, 1Xbet, Rollbit, Bc.Game — from memory (canonical reuse)
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison. No Focus, no Targets.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets. Q2 (Sources): "Direct only" / "Direct + Trustpilot" / "Direct + AskGamblers" sim Direct + Trustpilot.

### Playwright actions
Not available.

### Phase D — Artifact
7-section "Trust Signals (Core feature experience)" with Inferred block:
```
> **Inferred (not asked):**
> - Focus: Core feature experience (trust surface) — from "trust signals"
> - Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`
```

### Handoff
`~/Downloads/competitor-research/trust-signals/trust-signals-2026-05-23.md`. Hold the chip.

### Memory caching
No action.

## VERDICT: CR-042
**Title:** Phase A trust-signal keywords — 'trust signals' / 'social proof' / 'reviews' → Focus = Core feature experience (trust surface)
**SKILL.md ref:** competitor-research:L68
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-infers-field (Focus → Core feature experience) | PASS | L68 explicitly lists "trust signals" → Core feature experience trust surface. Citation: "trust signals". |
| 2 | phase-b-skips (Focus) | PASS | Phase B does not re-ask Focus |
| 3 | inferred-block-present | PASS | Block present with the trust-surface qualifier |
| 4 | inferred-includes-field (Focus) | PASS | Bullet cites exact phrase "trust signals" |

### Notes
Trust is routed through Core feature experience with the `(trust surface)` qualifier — NOT a first-class Focus value. Verifies the v1.1.0 L68 extension (CR-Δ-6 in the v1.1.0 deltas).

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: CR-043

### Preconditions
User input: "quick scan of Stake homepage messaging". Memory has 21com list. Playwright connected.

### Phase A — Inferences
- Focus: Homepage ("homepage"). Competitors: Stake (explicit). Depth: Quick scan ("quick scan"). Output: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Navigate https://stake.com/ — 200 OK. Screenshot saved to `~/Downloads/competitor-research/homepage/screenshots/stake-home.png`.

### Phase D — Artifact
7-section quick-scan "Homepage". §5 references screenshot inline: `![Stake homepage hero](screenshots/stake-home.png)` — the relative path resolves from the markdown's directory because the .md and the `screenshots/` subdir share the same parent `homepage/`.

### Handoff (v1.2.0 path co-location per L226)
1. **File save:** `~/Downloads/competitor-research/homepage/homepage-2026-05-23.md`
2. **Screenshots subdir:** `~/Downloads/competitor-research/homepage/screenshots/` — **sibling of the .md file**.
3. Gamble → Hold the chip.
4. Final: "Saved at /Users/talshani/Downloads/competitor-research/homepage/homepage-2026-05-23.md. No Confluence page created."

## VERDICT: CR-043
**Title:** Screenshot path co-location — markdown saved at ~/Downloads/competitor-research/<slug>/<slug>-<date>.md
**SKILL.md ref:** competitor-research:L226
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | markdown-saved-with-absolute-path (folder=competitor-research) | PASS | Saved under `~/Downloads/competitor-research/`. Absolute path printed at end. |
| 2 | cr-markdown-saved-in-focus-subdir | PASS | Exact match for L226 pattern `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. Resolves to `homepage/homepage-2026-05-23.md`. Sibling `screenshots/` subdir exists in the same parent (`homepage/`). |
| 3 | cr-screenshots-subdir-co-located | PASS | `screenshots/` is a true sibling of the .md file → relative `![](screenshots/stake-home.png)` reference in §5 resolves from the markdown's directory. |

### Notes
v1.2.0 confirms the slug-subdir path pattern (which was introduced in v1.1.0 via CR-Δ-2) is the canonical save path. This case isolates the path-co-location assertion from other handoff concerns (gamble question, Confluence call).

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: CR-044

### Preconditions
User input: "deep UX flow of Stake and Bc.Game signup with screenshots". Memory has 21com list. mcp_state: atlassian+playwright. Prior artifacts: 3 screenshots already exist in `~/Downloads/competitor-research/signup-flow/screenshots/` (stake-home.png, stake-signup.png, bcgame-signup.png); user has just picked "Bet on it" and Confluence page was successfully created in PKB.

### Phase A — Inferences
Focus: Onboarding ("signup"). Competitors: Stake, Bc.Game (explicit). Output: Screenshots + UX notes ("screenshots"). Depth: Deep UX flow ("deep UX flow").

### Phase B — Questions asked
none — all 4 inferred.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets. Q2 (Sources) sim Direct only.

### Playwright actions
Stake and Bc.Game every-screen signup. 3 screenshots in `signup-flow/screenshots/`: stake-home.png, stake-signup.png, bcgame-signup.png.

### Phase D — Artifact
Deep UX 7-section "Signup Flow"; §5 references all 3 screenshots inline.

### Handoff sequence (verify ordering)
1. **File save:** `~/Downloads/competitor-research/signup-flow/signup-flow-2026-05-23.md`. Sibling `screenshots/` subdir holds 3 PNGs.
2. **Gamble question** (exactly one, header `Gamble?`, exactly 2 options `Bet on it` / `Hold the chip`). sim: **Bet on it**.
3. **Confluence create-page call** (PKB params: cloudId, spaceId=772571142, parentId=772571521, contentFormat=markdown, title="Competitor Research Report: Signup Flow", body=full markdown). Returns success + page URL.
4. **One-line screenshots-local-only note** surfaced verbatim per L241: "Screenshots are local-only at ~/Downloads/competitor-research/signup-flow/screenshots/; the Confluence page's inline image references will render as broken — open the local .md to see them rendered."
5. **Bonus AskUserQuestion** (after step 4, because N=3 ≥ 1 screenshots exist; per L243–L249):
   - Question: `Upload 3 screenshots to the Confluence page as attachments? (fixes the inline image references)`
   - Header: `Attach screenshots?`
   - Options (exactly 2):
     - `Upload all` — Iterate `screenshots/` and attach each via the Atlassian MCP's create-attachment tool; rewrite inline references on the published page
     - `Upload none` — Skip attachment upload; local .md remains canonical screenshot bundle
   - sim: `Upload all`.
6. **3 create-attachment MCP calls** executed; published page's inline image references rewritten to the Confluence attachment URLs.
7. Final: published URL + absolute local path.

## VERDICT: CR-044
**Title:** Confluence-attachment offer — after Bet on it with N≥1 screenshots, skill presents 'Attach screenshots?' AskUserQuestion
**SKILL.md ref:** competitor-research:L242-L250
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | gamble-handoff-presented-once | PASS | The "Ready To Gamble On It?" question fires exactly once. The downstream attachment-offer is a DIFFERENT AskUserQuestion (different header, different topic) and does not double up the gamble. |
| 2 | gamble-options-match-spec (Bet on it / Hold the chip) | PASS | Exactly 2 — no Double down for CR. |
| 3 | cr-confluence-screenshots-note | PASS | Verbatim one-line note per L241. |
| 4 | cr-confluence-attachment-offer-fires | PASS | Fires AFTER the screenshots-local-only note. Header `Attach screenshots?`; question text contains literal "Upload 3 screenshots to the Confluence page as attachments"; options `Upload all` / `Upload none` verbatim. |

### Notes
Verifies the full v1.2.0 Bet-on-it+screenshots handoff sequence: page create → local-only note → attachment-offer question → optional attachment upload + rewrite. The 7-question Phase B/C cap is not engaged here because handoff confirmations are scoped separately from the interview cap.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: CR-045

### Preconditions
User input: "detailed comparison of Stake and 1Xbet signup flows". Memory has 21com list. Playwright connected. Prior artifacts: simulated Playwright runs return:
- `https://stake.com/` → 200 OK, snapshot captured
- `https://stake.com/signup` → HTTP 451 (geoblocked — Unavailable For Legal Reasons)
- `https://1xbet.com/` → 200 OK
- `https://1xbet.com/signup` → 200 OK

### Phase A — Inferences
Focus: Onboarding ("signup flows"). Competitors: Stake, 1Xbet (explicit). Depth: Detailed comparison.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
- `https://stake.com/` → 200 OK; screenshot `stake-home.png` saved
- `https://stake.com/signup` → HTTP 451 → per L141–L143, do NOT pre-flight robots.txt; rely on response code; write inline note in §5 under Stake subheading: `couldn't access /signup — 451 geoblocked` and skip
- `https://1xbet.com/` → 200 OK; screenshot `1xbet-home.png` saved
- `https://1xbet.com/signup` → 200 OK; screenshot `1xbet-signup.png` saved

The remaining Stake pages still render normally; only the blocked page is skipped, not the whole competitor.

### Phase D — Artifact
```
# Competitor Research Report: Onboarding

## 1. Research Scope
- Stake (https://stake.com) and 1Xbet (https://1xbet.com) signup flows
- Method: Playwright connected; 3 screenshots captured (stake-home, 1xbet-home, 1xbet-signup)
- Inaccessible: Stake /signup — HTTP 451 geoblocked
...

## 5. UX Flow Notes
### Stake
- Homepage hero — `![Stake home](screenshots/stake-home.png)`
- couldn't access /signup — 451 geoblocked

### 1Xbet
- Homepage hero — `![1Xbet home](screenshots/1xbet-home.png)`
- Signup flow step 1 — `![1Xbet signup](screenshots/1xbet-signup.png)`
...
```

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling (3 PNGs). Hold the chip.

## VERDICT: CR-045
**Title:** HTTP 403/451/CAPTCHA detection — Playwright hit on a 451 page produces inline 'couldn't access <page> — 451' note
**SKILL.md ref:** competitor-research:L141-L143
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-http-error-noted-inline | PASS | §5 under Stake subheading contains the verbatim line `couldn't access /signup — 451 geoblocked` per the L143 pattern `couldn't access <page> — <reason>`. Stake's other accessible pages still render. |
| 2 | cr-research-scope-notes-playwright-status | PASS | §1 explicitly notes "Playwright connected; 3 screenshots captured" and lists the inaccessible Stake /signup. |

### Notes
Replaces v1.0.0's robots.txt framing. v1.1.0 spec at L141–L143 explicitly says: "Public pages only. If a page returns HTTP 403/451 or shows a CAPTCHA / bot-detection wall, note `couldn't access <page> — <reason>` inline in §5 UX Flow Notes and skip. This skill does NOT perform robots.txt pre-flight." The skill follows it cleanly.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: CR-046

### Preconditions
User input: "I need a competitor scan on signup flow". Active memory is null (no `~/.claude/memory/<slug>.md` file with a `**Competitors:**` line). mcp_state: none.

### Phase A — Inferences (negative control — fallback path)
- Focus: Onboarding ("signup flow")
- **Competitors:** NOT inferred — memory is empty AND prompt does not name specific competitors → fall through to Phase B (per L69 + L90–L92 fallback path)
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Targets) — header: `Targets` — "Which competitors should be included?" with the 3 spec'd options (L86–L88):
  - `Memory default` — Use the competitor list from active product memory (degraded label since memory is empty — displays as "no cached list yet")
  - `Memory + best-in-class` — Memory list plus 2–3 indirect / aspirational references
  - `Custom list` — I'll provide URLs at runtime

sim: Custom list (PM provides Stake, 1Xbet, Rollbit, Bc.Game).

Q2 (Output) sim Comparison + opportunities. Q3 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim Global.

### Playwright actions
Not available.

### Phase D — Artifact
7-section "Onboarding" with NO Competitors inference in the Inferred block (Phase B answered it).

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

### Memory caching
Per L256: memory file created at `~/.claude/memory/<active-slug>.md` with `**Competitors:**` line before report renders. (See CR-047 for the full memory-cache verification.)

## VERDICT: CR-046
**Title:** Phase B fallback path — memory empty AND user didn't name competitors → Phase B asks; fallback options shown
**SKILL.md ref:** competitor-research:L86-L95
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Competitors) | PASS | Empty memory + no explicit names → Phase A correctly leaves Competitors uninferred (per L69 + L90–L92). |
| 2 | phase-b-asks (Competitors) | PASS | Targets question fires. |
| 3 | phase-b-question-shape (Targets, 3 options) | PASS | Header `Targets`, exactly 3 options (AskUserQuestion auto-adds "Other"). |
| 4 | phase-b-options-match-spec (Memory default / Memory + best-in-class / Custom list) | PASS | Labels match L86–L88 verbatim; the "Memory default" label degrades cleanly when memory is empty per L90–L92 (the substitution applies only when memory has names). |

### Notes
Negative-control sibling to CR-041. Together they verify the bifurcation at L69 + L90–L92: memory present → Phase A infers + Phase B skips; memory absent + no explicit names → Phase B asks with the 3 fallback options.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: CR-047

### Preconditions
User input: "scan competitor signup flows — I'll provide the list". Active memory is null. mcp_state: none. Active product slug resolves as `21com` (from working directory `/Users/talshani/Documents/GitHub/CasinoSkilo`).

### Phase A — Inferences
- Focus: Onboarding ("signup flows")
- Competitors: NOT inferred — empty memory + user didn't pre-name competitors (only signaled willingness to provide at runtime)
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Targets) — 3 spec'd options. sim: `Custom list`. PM provides at runtime:
- BetMGM — https://betmgm.com
- DraftKings — https://draftkings.com
- FanDuel — https://fanduel.com

Q2 (Output) sim Comparison + opportunities. Q3 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region) sim US.

### Playwright actions
Not available — §1 notes Playwright off.

### Memory write (before report renders, per L211 + L256)
```
$ cat ~/.claude/memory/21com.md  # (new file created)
# 21com
**Competitors:** BetMGM (https://betmgm.com), DraftKings (https://draftkings.com), FanDuel (https://fanduel.com)
```
The `~/.claude/memory/` directory is created if missing; the file is created with the kebab-cased slug; the `**Competitors:**` line uses the exact marker so CR-041 / Phase A inference can read it on the next run.

### Phase D — Artifact
Standard 7-section "Onboarding (US)" with BetMGM / DraftKings / FanDuel.

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

## VERDICT: CR-047
**Title:** Memory cached after Phase B — empty memory → Phase B asks Competitors → answer appended as **Competitors:** line
**SKILL.md ref:** competitor-research:L211 + L256
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | phase-a-does-not-infer-field (Competitors) | PASS | Empty memory + no names → uninferred |
| 2 | phase-b-asks (Competitors) | PASS | Targets question fires |
| 3 | cr-memory-empty-caches-after-phase-b | PASS | Memory file `~/.claude/memory/21com.md` created with `**Competitors:** BetMGM (https://betmgm.com), DraftKings (https://draftkings.com), FanDuel (https://fanduel.com)`. The names appear, the URLs appear, the exact `**Competitors:**` marker is used. Write happens BEFORE report renders, per L211. |

### Notes
Sibling to CR-040 (memory-differs) and CR-046 (Phase B fallback). Verifies the full empty-memory lifecycle: detect → ask → cache → render. CR-041 then becomes possible on the next run because the cache is now populated.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## TRACE: CR-048

### Preconditions
User input: "detailed competitor comparison on pricing and bonuses". Memory `~/.claude/memory/21com.md` has `**Competitors:** Stake (https://stake.com), 1Xbet (https://1xbet.com), Rollbit (https://rollbit.com), Bc.Game (https://bc.game)`. **mcp_state: none** — Playwright NOT connected.

### Phase A — Inferences
- Focus: Pricing ("pricing and bonuses")
- Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory (canonical reuse)
- Depth: Detailed comparison ("detailed comparison")
- Output: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
**Not available — none.** The skill detects `mcp__playwright__*` tools are not registered and skips Playwright invocation entirely.

### Phase D — Artifact (text-only degradation)
```
# Competitor Research Report: Pricing & Bonuses

> **Inferred (not asked):**
> - Focus: Pricing — from "pricing and bonuses"
> - Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`
> - Depth: Detailed comparison — from "detailed comparison"

| Field | Value |
|---|---|
| **Status** | Draft v1.0 |
| **Author** | Tal |
| **Date** | 2026-05-23 |
| **Depth** | Detailed comparison |
| **Region scope** | 21.com licensed markets (Curacao + MGA) |

## 1. Research Scope
- Stake / 1Xbet / Rollbit / Bc.Game pricing + bonus pages
- Method: Playwright not available — no screenshots captured. All observations are text-only based on prior PM knowledge + Confluence baseline.
- No Jira/Confluence MCP available; 21.com baseline from PM input.

## 2. Competitors Reviewed
- Stake — https://stake.com
- 1Xbet — https://1xbet.com
- Rollbit — https://rollbit.com
- Bc.Game — https://bc.game

## 3. Executive Summary
[3–6 sentences, leadership-friendly, text-only]

## 4. Comparison Table
| Area | Our Product | Stake | 1Xbet | Rollbit | Bc.Game | Opportunity |
| ... 5 canonical rows ... |

## 5. UX Flow Notes
### Stake
- [Text observation 1]
- [Text observation 2]
### 1Xbet
- [Text observation]
... (no `![](screenshots/...)` references — no broken links)

## 6. Key Patterns
**Table stakes:** ...
**Differentiation:** ...

## 7. Gaps & Opportunities
- ...
```

Notably: §5 omits screenshot references entirely (does not render broken `![](screenshots/...)` links). No separate "Screenshots" section is invented. The 7-section structure is preserved.

### Handoff
1. `~/Downloads/competitor-research/pricing-bonuses/pricing-bonuses-2026-05-23.md`
2. screenshots/ sibling created but empty (no PNGs to save)
3. Gamble → Hold the chip (no Atlassian MCP either).
4. Final: "Saved at /Users/talshani/Downloads/competitor-research/pricing-bonuses/pricing-bonuses-2026-05-23.md. No Confluence page created."

### Memory caching
No action — memory matches runtime.

## VERDICT: CR-048
**Title:** Playwright unavailable degrades gracefully — mcp_state: none produces text-only report; §1 notes 'Playwright not available'
**SKILL.md ref:** competitor-research:L127-L134 + L208
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-playwright-unavailable-degrades-gracefully | PASS | Full 7-section report renders without screenshots. §1 explicitly states "Playwright not available — no screenshots captured". |
| 2 | cr-research-scope-notes-playwright-status | PASS | §1 contains the exact substring "Playwright not available" + "no screenshots captured". |
| 3 | cr-has-7-sections | PASS | All 7 numbered sections present. |
| 4 | cr-screenshots-inline-not-separate-section | PASS | §5 omits all screenshot references; no broken `![](screenshots/...)` links; no separate "Screenshots" section invented. |

### Notes
Sibling sub-rule to CR-040 (memory-differs), CR-045 (HTTP 451), CR-047 (cache after Phase B). All four split out of the v1.1.0 bundled CR-040, each isolating one edge case for cleaner failure attribution.

### Delta vs v1.1.0
NEW (v1.1.0 backfill) → PASS

---

## END OF RUN
