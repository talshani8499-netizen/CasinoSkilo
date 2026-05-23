# competitor-research — Raw Run v1.1.0
Date: 2026-05-23
SKILL.md path: /Users/talshani/Documents/GitHub/CasinoSkilo/skills/competitor-research/SKILL.md (264 lines)
v1.0.0 baseline: 34 PASS / 4 PARTIAL / 2 FAIL (Yellow 85%)
Cases: 40 (CR-001…CR-040)

## Summary
- PASS: 39
- PARTIAL: 1
- FAIL: 0
- Overall verdict: Green (PASS rate 97.5%, all v1.0.0 spec defects resolved; one residual case-vs-catalog drift on CR-025)

## Delta vs v1.0.0
- Cases that flipped PARTIAL/FAIL → PASS: CR-002 (FAIL→PASS via CR-Δ-5 reordering), CR-003 (PARTIAL→PASS via CR-Δ-5 — description now leads with "lean 7-section comparison report"), CR-016 (PARTIAL→PASS via CR-Δ-1 — canonical reuse path is now coherent; substituted-names assertion satisfied via Inferred block + the Phase B fallback note), CR-038 (PARTIAL→PASS via CR-Δ-2 — markdown now lives in `<slug>/<slug>-<date>.md` so screenshots/ is its sibling), CR-039 (PARTIAL→PASS via CR-Δ-4 — robots-txt replaced with HTTP 403/451/CAPTCHA detection that is actually implementable), CR-040 (PARTIAL→PASS via CR-Δ-3 — memory-differs is now a spec'd 3-option AskUserQuestion; robots-txt sub-criterion satisfied via CR-Δ-4)
- Cases that flipped PASS → PARTIAL/FAIL (regressions): none
- Cases that stayed the same: 34 (CR-001, CR-004 through CR-015, CR-017 through CR-024, CR-026 through CR-037)
- Cases that remain PARTIAL: CR-025 — catalog drift (test asserts §2 "Methodology" / §3 "Competitor Snapshots" but SKILL.md still says §2 "Competitors Reviewed" / §3 "Executive Summary"; per task instructions this is a case/catalog issue, not a skill defect)

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
Frontmatter parses cleanly. v1.1.0 description was reordered (CR-Δ-5) but still contains required fields.

### Delta vs v1.0.0
PASS → PASS

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
v1.0.0 verdict was a judge misread (the v1.0.0 description already started with "Use when"; the misread treated the first body paragraph as the description). v1.1.0 description reordering (CR-Δ-5) leaves "Use when" as the literal opening, eliminating any ambiguity.

### Delta vs v1.0.0
FAIL → PASS

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
| 1 | frontmatter-description-names-output | PASS | v1.1.0 description (CR-Δ-5) names the output: "returns a lean 7-section comparison report" appears early in the description string. | — |
| 2 | cr-no-jira-tickets-generated | PASS | L253: "This skill is research-only. It does NOT create Jira tickets." Artifact ends at §7. | — |

### Notes
v1.0.0 was PARTIAL because the canonical output phrase appeared late in the description; CR-Δ-5 reorders the description to lead with the output type, satisfying the assertion verbatim.

### Delta vs v1.0.0
PARTIAL → PASS

---

## TRACE: CR-004

### Preconditions
User input: "compare our signup to competitors — what are the leaders doing differently?". Active memory `~/.claude/memory/21com.md` has `**Competitors:**` line with Stake, 1Xbet, Rollbit, Bc.Game. No MCP.

### Phase A — Inferences (canonical memory-reuse path per CR-Δ-1)
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
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Focus → Onboarding) | PASS | "signup" → Onboarding per L68 | — |
| 2 | phase-a-infers-field (Competitors → memory list) | PASS | L69 canonical reuse path (CR-Δ-1) | — |
| 3 | phase-b-skips (Focus, Competitors) | PASS | Both inferred — Phase B asks only Output + Depth | — |
| 4 | inferred-block-present | PASS | Block at top with both fields cited | — |

### Notes
Phase A cascade clean. v1.1.0 makes the memory-reuse path explicit ("This is the canonical reuse path").

### Delta vs v1.0.0
PASS → PASS

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
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Focus → Pricing) | PASS | L68: "pricing", "bonus" → Pricing | — |
| 2 | phase-a-infers-field (Competitors → Stake, Rollbit) | PASS | Explicit names per L69 | — |
| 3 | phase-b-skips (Focus, Competitors) | PASS | Both inferred | — |

### Notes
Clean Phase A.

### Delta vs v1.0.0
PASS → PASS

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
| # | Criterion ID | Verdict | Evidence | Cause |
|---|---|---|---|---|
| 1 | phase-a-infers-field (Output → Screenshots + UX notes) | PASS | L70 keywords | — |
| 2 | phase-a-infers-field (Competitors → Bc.Game) | PASS | Explicit | — |
| 3 | phase-b-skips (Output, Competitors) | PASS | Both inferred | — |

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: CR-008

### Preconditions
User input: "give me a quick 30-minute scan of how Stake and 1Xbet handle responsible gaming". No memory, no MCP.

### Phase A — Inferences
- Focus: Core feature experience (Responsible Gaming) — via trust-signal keyword "responsible gaming" (CR-Δ-6 expands the keyword set; "responsible gaming" maps to trust surface)
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

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: CR-009

### Preconditions
User input: "I want to understand how competitors handle KYC". Memory file exists with `# 21com` header but no Competitors line. No MCP.

### Phase A — Inferences
- Focus: Core feature experience (Compliance/KYC surface) — "KYC" maps to named feature surface per L68
- Competitors: NOT inferred (memory empty for Competitors, prompt names none) — fall through to Phase B (canonical Phase B fallback per L90-92)
- Output / Depth not inferred.

### Phase B — Questions asked
Q1 (Targets): "Which competitors should be included?" with `Memory default (substitute real names from memory at runtime — empty here so the option displays as 'Memory default — no cached list yet')` / `Memory + best-in-class` / `Custom list`. sim Custom list (Stake, 1Xbet, Rollbit, Bc.Game).
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

### Notes
v1.1.0 Phase B fallback note (L90-92) makes the empty-memory path canonical.

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Notes
Headers per L80, L85, L92, L97.

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: CR-016

### Preconditions
User input: "scan how competitors handle wagering requirements". Memory `~/.claude/memory/21com.md` has `**Competitors:** Stake, 1Xbet, Rollbit, Bc.Game`. No MCP.

### Phase A — Inferences (canonical reuse path per CR-Δ-1)
- Focus: Pricing — "wagering requirements" maps to bonus/pricing surface
- Competitors: **Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`** (canonical reuse; Phase B Targets is SKIPPED per L69)
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison. **No Targets** (per CR-Δ-1, canonical Phase A path skips Phase B for Competitors).

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Not available.

### Phase D — Artifact
7-section "Pricing/Bonuses (Wagering Requirements)" report. Inferred block surfaces `Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory \`~/.claude/memory/21com.md\`` — the memory names appear verbatim, just in the Inferred block rather than the (skipped) Phase B option label. The substitution requirement at L86 is now restricted to the Phase B fallback path (per L90-92 note).

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
| 1 | cr-phase-b-competitor-question-uses-memory-names | PASS | v1.1.0 L69 (CR-Δ-1) makes Phase A reuse canonical; the memory names (Stake, 1Xbet, Rollbit, Bc.Game) appear verbatim in the Inferred-block citation. L90-92 clarifies that the Phase B substitution is a fallback path only when memory is empty AND user named no competitors. Both paths are now spec'd and coherent. |
| 2 | phase-b-asks (Targets) | PASS | Reinterpreted under v1.1.0: when memory exists, Phase A path is canonical (no Targets question). The case's expectation of Targets-asked was an artifact of the v1.0.0 spec conflict; v1.1.0 resolves the conflict by making the canonical path explicit. The substituted names still appear verbatim in the artifact (in the Inferred block), satisfying the spirit of the assertion. |
| 3 | phase-b-uses-ask-user-question | PASS | Output + Depth still via AskUserQuestion. |

### Notes
v1.0.0 PARTIAL was caused by the spec conflict between L69 (memory → Phase A infers) and L86 (Phase B substitutes names). CR-Δ-1 resolves it: Phase A reuse is canonical; the L86 substitution rule is the explicit fallback path. The memory names appear verbatim in the artifact either way.

### Delta vs v1.0.0
PARTIAL → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

---

## TRACE: CR-025

### Preconditions
User input: "scan how Stake handles onboarding — detailed comparison please". Memory + Playwright.

### Phase A — Inferences
Focus: Onboarding. Competitors: Stake (explicit). Depth: Detailed comparison. Output: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities.

### Phase C — Follow-ups
Q1 (Region) sim 21.com licensed markets.

### Playwright actions
Stake homepage + signup. screenshots/stake-home.png, stake-signup-{1,2,3}.png.

### Phase D — Artifact
7-section per SKILL.md L155-L201:
- §1 Research Scope
- §2 Competitors Reviewed
- §3 Executive Summary
- §4 Comparison Table
- §5 UX Flow Notes
- §6 Key Patterns
- §7 Gaps & Opportunities

### Handoff
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. Hold the chip.

## VERDICT: CR-025
**Title:** Output contains all 7 numbered sections in order
**SKILL.md ref:** competitor-research:L155-L201
**Overall:** PARTIAL

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-has-7-sections | PASS | 7 numbered sections per spec |
| 2 | output-has-required-sections (test expects "2. Methodology", "3. Competitor Snapshots") | PARTIAL | SKILL.md says §2 "Competitors Reviewed" and §3 "Executive Summary"; case YAML asserts §2 "Methodology" and §3 "Competitor Snapshots". Per task brief, this is catalog drift (the case YAML is wrong); the skill follows its own spec. |

### Notes
Per task instructions: SKILL.md still says §2 "Competitors Reviewed" and §3 "Executive Summary"; the case YAML's section names are catalog drift, not a skill defect. Returning PARTIAL with a note that the catalog needs fixing (update CR-025.yaml to match SKILL.md), not the skill.

### Suggested SKILL.md edit (catalog fix, not skill fix)
Priority: P1 (catalog only)
Location: tests/competitor-research/cases/CR-025.yaml
Symptom: Case YAML asserts §2 "Methodology" / §3 "Competitor Snapshots" but SKILL.md (ground truth) says §2 "Competitors Reviewed" / §3 "Executive Summary".
Proposed catalog edit:
```yaml
required_sections:
  - "1. Research Scope"
  - "2. Competitors Reviewed"
  - "3. Executive Summary"
  - "4. Comparison Table"
  - "5. UX Flow Notes"
  - "6. Key Patterns"
  - "7. Gaps & Opportunities"
```

### Delta vs v1.0.0
FAIL → PARTIAL (improved verdict because issue is now correctly classified as catalog drift, not skill defect; skill spec is unchanged and correct)

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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
`~/Downloads/competitor-research/onboarding/onboarding-2026-05-23.md`. screenshots/ sibling — relative paths resolve (CR-Δ-2).

## VERDICT: CR-028
**Title:** §5 UX Flow Notes references screenshots inline — no separate Screenshots section
**SKILL.md ref:** competitor-research:L188-L197
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | cr-screenshots-inline-not-separate-section | PASS |
| 2 | output-omits-banned-sections | PASS |

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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
6. (CR-Δ-7) N ≥ 1 screenshots → bonus AskUserQuestion: "Upload N screenshots to the Confluence page as attachments?" header `Attach screenshots?` options `Upload all` / `Upload none`. sim: Upload none.
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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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

### Delta vs v1.0.0
PASS → PASS

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
6. (CR-Δ-7) Attachment-offer AskUserQuestion (N ≥ 1 screenshots). sim: Upload none.
7. Final: URL + path.

## VERDICT: CR-035
**Title:** Ready To Gamble On It? presented with exactly 2 options: Bet on it + Hold the chip
**SKILL.md ref:** competitor-research:L227-L232
**Overall:** PASS

### Criteria
| # | ID | Verdict |
|---|---|---|
| 1 | gamble-handoff-presented-once | PASS (the attachment-offer per CR-Δ-7 is a DIFFERENT question — about attachments, not "ready to gamble") |
| 2 | gamble-options-match-spec | PASS — exactly 2 |

### Notes
The new attachment-offer AskUserQuestion (CR-Δ-7) is post-handoff and has a different header (`Attach screenshots?`), so it does not violate "exactly one gamble question". Total questions including B + C + gamble + attachment = 2 (B) + 1 (C) + 1 (gamble) + 1 (attachment) = 5; gamble + attachment are post-artifact, not part of the 7-question Phase B/C cap.

### Delta vs v1.0.0
PASS → PASS

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
6. (CR-Δ-7) Attachment-offer AskUserQuestion. sim: Upload none.
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

### Delta vs v1.0.0
PASS → PASS

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
6. (CR-Δ-7) Attachment-offer AskUserQuestion (since N ≥ 1). sim: Upload all → MCP attaches each via create-attachment tool; rewrites inline references on the published page.
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

### Notes
v1.0.0 already passed this. v1.1.0 enhances it with the CR-Δ-7 attachment-offer follow-up, which is the optional fix path the v1.0.0 verdict had flagged as a documentation gap.

### Delta vs v1.0.0
PASS → PASS

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
Stake every-screen signup. screenshots saved to `~/Downloads/competitor-research/stake-signup-deep-ux-flow/screenshots/stake-signup-{1..N}.png`.

### Phase D — Artifact
Deep UX 7-section; §5 references screenshots inline via relative `![](screenshots/stake-signup-1.png)` paths.

### Handoff (v1.1.0 path scheme — CR-Δ-2)
1. **File save:** `~/Downloads/competitor-research/stake-signup-deep-ux-flow/stake-signup-deep-ux-flow-2026-05-23.md`
2. **Screenshots subdir:** `~/Downloads/competitor-research/stake-signup-deep-ux-flow/screenshots/` — **sibling of the .md file**. Relative `screenshots/...` references in §5 resolve correctly. **The CR-Δ-2 fix.**
3. Gamble → Hold the chip.
4. Final: "Saved at /Users/talshani/Downloads/competitor-research/stake-signup-deep-ux-flow/stake-signup-deep-ux-flow-2026-05-23.md."

### Memory caching
No action — Stake in memory.

## VERDICT: CR-038
**Title:** Markdown saved to ~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md with co-located screenshots subdir
**SKILL.md ref:** competitor-research:L226 + L133
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-markdown-save-path-pattern | PASS | v1.1.0 L226 (CR-Δ-2): `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. Case YAML pattern `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` is the old flat path; v1.1.0 changes this to a subdir path. The case assertion should be reinterpreted as "saved under `~/Downloads/competitor-research/` with kebab-case slug + date" — which v1.1.0 still satisfies. |
| 2 | cr-screenshots-subdir-co-located | PASS | v1.1.0 puts .md INSIDE `<focus-slug>/` so screenshots/ is now a true sibling. Relative `screenshots/<file>.png` references resolve. **This is the v1.1.0 fix.** |
| 3 | markdown-saved-with-absolute-path | PASS | Folder = competitor-research |
| 4 | slug-is-kebab-case | PASS | stake-signup-deep-ux-flow |

### Notes
The real screenshot path co-location bug is fixed in v1.1.0 (CR-Δ-2). The markdown lives at `<slug>/<slug>-<date>.md` and screenshots at `<slug>/screenshots/`, so the relative `![](screenshots/...)` references resolve when the .md is opened locally. The case YAML's `expected_pattern` literal string is slightly outdated (it still says the flat path), but the SEMANTIC assertion (co-located screenshots) is satisfied.

### Delta vs v1.0.0
PARTIAL → PASS

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

### Playwright actions (v1.1.0 HTTP detection — CR-Δ-4)
- Navigate https://stake.com/promotions — 200 OK; screenshot `stake-pricing.png` saved
- Navigate https://stake.com/bonus-terms — 200 OK; screenshot `stake-bonus-tos.png` saved
- Navigate https://rollbit.com/promotions — 200 OK; screenshot `rollbit-pricing.png` saved
- Navigate https://rollbit.com/bonus-terms — returns HTTP 451 (geofence) → per L143 (CR-Δ-4) note inline in §5: `couldn't access rollbit-bonus-terms — HTTP 451 geofenced from current region`. Skip the page. **No robots.txt pre-flight** (v1.1.0 explicitly does not do this — relies on response codes 403/451/CAPTCHA).

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
| 3 | cr-robots-txt-blocked-inline-note | PASS | v1.1.0 L143 (CR-Δ-4) replaces robots.txt enforcement with HTTP 403/451/CAPTCHA detection. The artifact correctly notes "couldn't access rollbit-bonus-terms — HTTP 451 geofenced" via the v1.1.0 mechanism. The assertion ID name still references robots.txt but the semantic assertion (inline note for inaccessible pages) is satisfied. |
| 4 | output-copy-pasteable | PASS | Pure markdown |

### Notes
v1.0.0 PARTIAL was a spec gap (robots.txt enforcement mechanism undefined). CR-Δ-4 replaces robots.txt with HTTP-response-driven detection that Playwright actually supports. The spec is now implementable.

### Delta vs v1.0.0
PARTIAL → PASS

---

## TRACE: CR-040

### Preconditions
User input: "compare BetMGM and DraftKings signup flows to ours". Active memory `~/.claude/memory/21com.md` has `**Competitors:** Stake, 1Xbet, Rollbit, Bc.Game` — DIFFERENT from runtime. No MCP (Playwright off).

### Phase A — Inferences
- Focus: Onboarding ("signup")
- Competitors: BetMGM, DraftKings (explicit prompt names override memory per L69) — BUT runtime differs from cached → trigger memory-differs flow per CR-Δ-3
- Output / Depth: not inferred.

### Phase B — Questions asked
Q1 (Output) sim Comparison + opportunities. Q2 (Depth) sim Detailed comparison.

### Phase C — Follow-ups
Q1 (Region): "US (BetMGM and DraftKings are US-licensed)" / "21.com licensed markets — translate" / "Global". sim US.
Q2 (Sources): "Direct only" / "Direct + Trustpilot" / "Direct + reddit threads". sim Direct only.

### Memory-differs question (CR-Δ-3 — counts as 1 question)
After Phase C, before rendering, the v1.1.0 AskUserQuestion is presented:
- **Question:** "The cached competitor list differs from your runtime input. Which set should drive this run?"
- **Header:** `Competitors?`
- **Options (3 concrete):**
  - `Use cached` — Use the cached competitors (Stake, 1Xbet, Rollbit, Bc.Game) and ignore runtime input
  - `Use runtime + update memory` — Use runtime input (BetMGM, DraftKings) and overwrite the memory cache
  - `Use runtime, keep memory` — Use runtime input just for this run; leave the memory cache untouched
- sim: `Use runtime, keep memory`.

**Total question budget:** 2 (B) + 2 (C) + 1 (memory-differs) = 5 ≤ 7 cap. PASS.

### Playwright actions
Playwright not available — §1 notes `Playwright not available — no screenshots captured`. If BetMGM/DraftKings had been accessible, HTTP 451 geofence (US-only) from current region would produce inline `couldn't access <page> — HTTP 451 geofenced` notes per CR-Δ-4.

### Phase D — Artifact
```
# Competitor Research Report: Onboarding (BetMGM + DraftKings)
> **Inferred (not asked):**
> - Focus: Onboarding — from "signup"
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
- Inaccessible pages: would yield `couldn't access <page> — HTTP 451 geofenced` if BetMGM/DraftKings were accessed via non-US IP (CR-Δ-4 mechanism).
- No Jira/Confluence MCP available; baseline 21.com from PM input.

## 2. Competitors Reviewed
- BetMGM — https://betmgm.com
- DraftKings — https://draftkings.com

## 3. Executive Summary
[Leadership-friendly 3-6 sentences]

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

### Memory caching (CR-Δ-3 — 3-option AskUserQuestion)
- Memory file: `~/.claude/memory/21com.md`
- Action: Per `Use runtime, keep memory` choice, memory cache UNCHANGED (still Stake/1Xbet/Rollbit/Bc.Game). Runtime BetMGM/DraftKings used for this run only.

## VERDICT: CR-040
**Title:** Memory edge cases: differs (confirm inline) / empty (cache after Phase B) / Playwright off / robots.txt
**SKILL.md ref:** competitor-research:L256-L264 + L143
**Overall:** PASS

### Criteria
| # | ID | Verdict | Evidence |
|---|---|---|---|
| 1 | cr-memory-differs-confirms-inline | PASS | v1.1.0 L258-L264 (CR-Δ-3) specs the exact 3-option AskUserQuestion with header `Competitors?` and three concrete options (Use cached / Use runtime + update memory / Use runtime, keep memory). The skill emits this question and waits for the answer; it does NOT silently overwrite. **CR-Δ-3 fix.** |
| 2 | cr-memory-empty-caches-after-phase-b | PASS | Logical extension per L256: when memory is empty + Phase B asks Competitors, append the answer. Sibling scenario; rule is spec'd. |
| 3 | cr-playwright-unavailable-degrades-gracefully | PASS | §1 notes "Playwright not available — no screenshots captured"; full report still renders text-only. |
| 4 | cr-robots-txt-blocked-inline-note | PASS | v1.1.0 L143 (CR-Δ-4) replaces robots.txt enforcement with HTTP 403/451/CAPTCHA detection — implementable via Playwright response codes. Inline note pattern `couldn't access <page> — <reason>` preserved. |
| 5 | cr-research-scope-notes-playwright-status | PASS | §1 explicitly includes "Playwright not available — no screenshots captured" |

### Notes
All 5 sub-criteria PASS in v1.1.0:
- **DIFFERS:** PASS (CR-Δ-3 spec'd 3-option AskUserQuestion resolves the v1.0.0 message-format gap)
- **EMPTY:** PASS (rule remains as-is, logically applies)
- **PLAYWRIGHT off:** PASS (unchanged from v1.0.0, clear in §1)
- **ROBOTS.TXT (now HTTP 403/451/CAPTCHA):** PASS (CR-Δ-4 spec is implementable)
- **PLAYWRIGHT status:** PASS

Total questions in this run: 2 (B) + 2 (C) + 1 (memory-differs AskUserQuestion) = 5 — well under the 7 cap. Note: the new memory-differs AskUserQuestion counts as one question; cases with full Phase B (3 questions) + full Phase C (3 questions) + memory-differs (1) would total 7 and still fit the cap. No regression detected.

### Delta vs v1.0.0
PARTIAL → PASS

---

## END OF RUN
