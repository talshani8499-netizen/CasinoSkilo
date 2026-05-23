# CasinoSkilo — Cross-Skill Test Summary

**Date:** 2026-05-23
**Skills tested:** 3 (ticket-builder, prd-writer, competitor-research)
**Total cases:** 120 (40 per skill)
**Methodology:** Two-stage sub-agent dispatch — a runner simulates each skill against the case preconditions and produces a structured trace; a judge grades the trace against the case's `pass_criteria` referenced to the SKILL.md as ground truth.

Per-skill reports:
- [`ticket-builder-test-report.md`](ticket-builder-test-report.md)
- [`prd-writer-test-report.md`](prd-writer-test-report.md)
- [`competitor-research-test-report.md`](competitor-research-test-report.md)

Raw runner+judge transcripts are in [`raw/`](raw/).

---

## Cross-Skill Roll-up

| Skill | Cases | PASS | PARTIAL | FAIL | % PASS | Verdict |
|---|---|---|---|---|---|---|
| ticket-builder | 40 | 39 | 1 | 0 | 97.5% | 🟢 Green |
| prd-writer | 40 | 32 | 8 | 0 | 80.0% | 🟡 Yellow |
| competitor-research | 40 | 34 | 4 | 2 | 85.0% | 🟡 Yellow |
| **Total** | **120** | **105** | **13** | **2** | **87.5%** | 🟡 Yellow |

### What this tells us
- **The Phase A / Phase B / Phase C architecture works.** The shared four-phase pattern (inference → core questions → adaptive follow-ups → render) passes consistently across all three skills. No case in any skill shows the architecture breaking down — only individual rule ambiguities surface.
- **ticket-builder is the most polished spec.** Only two minor (P2) ambiguities — both about cosmetic placement, not behavior.
- **prd-writer is the most exposed spec.** Yellow at the Green/Yellow boundary (80% exactly). The Double-down chain works end-to-end but has a P0 cross-skill contract gap with ticket-builder.
- **competitor-research has the most real defects.** Two genuine FAILs and three P0 actionable items. The skill is functional but the spec has unresolved branches that will bite under edge-case use.

---

## Top 10 Actionable Items (cross-skill, prioritized)

### 1. P0 — Cross-skill contract: mirror "PRD-driven mode" in ticket-builder/SKILL.md
**Skill:** prd-writer (chain dependency on ticket-builder)
**Location:** `skills/prd-writer/SKILL.md:L191–L204` defines the contract; **ticket-builder/SKILL.md** has no acknowledgment of this mode at all.
**Symptom:** The "Hard instruction" on L198 says ticket-builder must run with Phase B/C skipped, every Phase A inference cites the PRD section, and auto-Bet-on-it at handoff — but ticket-builder's own SKILL.md never names this mode. An independent edit to ticket-builder (e.g. "always ask user at handoff") can silently break Double down without any catalog test catching it from the ticket-builder side.
**Fix:** Add a new "PRD-driven mode" section to ticket-builder/SKILL.md (≈10 lines) that mirrors the contract from prd-writer L198. Cross-link both directions.

### 2. P0 — Competitor-research: Phase A vs Phase B memory-substitution path conflict
**Skill:** competitor-research
**Location:** `skills/competitor-research/SKILL.md:L69` (Phase A infers Competitors from memory) and `L86` (Phase B substitutes memory names into the option label).
**Symptom:** If Phase A already inferred Competitors from memory, Phase B is skipped — so the memory-substitution rule on L86 is effectively unreachable in the normal flow. The skill has two mutually-exclusive paths for the same behavior, with no spec on which wins under partial memory or stale cache.
**Fix:** Pick one path. Either (a) Phase A inference is opportunistic and Phase B's memory-substitution is the canonical reuse path, OR (b) Phase B's memory-substitution is dead code and should be removed.

### 3. P0 — Competitor-research: Screenshot path co-location breaks relative references
**Skill:** competitor-research
**Location:** `skills/competitor-research/SKILL.md:L224` (markdown path) and `L131` + `L134` (screenshot path + inline reference syntax).
**Symptom:** Markdown is saved to `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` but screenshots are saved to `~/Downloads/competitor-research/<focus-slug>/screenshots/`. The relative `screenshots/<file>.png` references in the .md resolve to `~/Downloads/competitor-research/screenshots/...` — a directory that does not exist. The "self-contained bundle locally" promise on L134 is broken.
**Fix:** Save the markdown inside the focus-slug subdir: `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. The relative `screenshots/...` paths then resolve correctly.

### 4. P0 — Competitor-research: Memory-differs confirmation message + robots.txt enforcement underspecified
**Skill:** competitor-research
**Location:** `skills/competitor-research/SKILL.md:L141` (robots.txt) and `L247` (memory-differs confirmation).
**Symptom:** L247 says "confirm with one inline message if the existing memory list differs from runtime input" but doesn't define the message format or whether the user is given an option to overwrite/keep. L141 says "Respect robots.txt; if blocked, note 'couldn't access <page>' in the report and skip" — but the skill provides no mechanism for actually checking robots.txt (Playwright doesn't enforce it natively).
**Fix:** Specify the exact confirmation message text + 2-option chooser (Use cached / Use runtime). For robots.txt, either drop the enforcement claim or document an explicit pre-flight HTTP fetch of `/robots.txt` and a parser.

### 5. P1 — prd-writer: Expand Main user options to include sub-segments
**Skill:** prd-writer
**Location:** `skills/prd-writer/SKILL.md:L55` (signal table) + `L68–L70` (Phase B option bank)
**Symptom:** The Main user bank lists only `End user` / `Admin / internal` / `Support / ops`. Real PM scenarios (VIP player, CRM operator) don't map cleanly to any of the three; Phase A inference table on L55 omits VIP / CRM / specific player segments.
**Fix:** Either add sub-segment guidance to L55 ("VIP player → End user with a `vip` tag in the User Story") or expand the option bank to 4–5 segments. Same fix mirrors to ticket-builder L58.

### 6. P1 — prd-writer: Add Retention / re-engagement as a Main problem value
**Skill:** prd-writer
**Location:** `skills/prd-writer/SKILL.md:L57` + `L77–L80`
**Symptom:** "churn" currently maps to Drop-off, but PMs distinguish acquisition drop-off from retention re-engagement. Conflating them produces wrong PRD emphasis (Drop-off pushes toward funnel optimization; Retention pushes toward lifecycle messaging).
**Fix:** Add `Retention / re-engagement` as a 4th Main problem value (or split Drop-off into Acquisition drop-off vs Retention drop-off).

### 7. P1 — prd-writer: Document Phase A conflict-resolution rule
**Skill:** prd-writer
**Location:** `skills/prd-writer/SKILL.md:L53–L58`
**Symptom:** Phase A signal table is a flat lookup. When opposing signals fire (input says "brand-new" + "v2 of"), spec doesn't tell the runner which wins. Cases pass only by accident of the runner's chosen tie-break.
**Fix:** Add an explicit conflict-resolution clause: "When signals from multiple rows fire, mark the field as Not inferred and fall through to Phase B." Mirror the same fix to ticket-builder L52.

### 8. P1 — competitor-research: Frontmatter description does not name canonical output type
**Skill:** competitor-research
**Location:** `skills/competitor-research/SKILL.md:L3`
**Symptom:** Per the CR aggregator's review, the description names the chain behavior but doesn't lead with the canonical output noun phrase in a way that maximizes Claude's matching. (Note: this is a soft P1 — the description does include "returns a lean 7-section comparison report", so a counter-argument exists. Treat as a polish item.)
**Fix:** Move "7-section comparison report" earlier in the description, ideally in the first 15 words.

### 9. P1 — competitor-research: Robots.txt enforcement mechanism unspec'd
**Skill:** competitor-research
**Location:** `skills/competitor-research/SKILL.md:L141`
**Symptom:** Duplicate of item #4's robots.txt half — see fix above.

### 10. P2 — prd-writer: Add upper bound on Double-down chain length
**Skill:** prd-writer
**Location:** `skills/prd-writer/SKILL.md:L204`
**Symptom:** Note says "A PRD with 14 child tickets produces 14 Jira tickets" with no upper bound. A 50-row §12 chains 50 ticket-builder calls from a single user click — large blast radius if any step fails partway.
**Fix:** Add a chain-length cap (suggested 25) with a "chain too long — split into multiple PRDs" warning shown before the user picks Double down.

---

## Defect Distribution by Category

| Category | TB defects | PRD defects | CR defects | Notes |
|---|---|---|---|---|
| A. Frontmatter | 0 | 1 P2 | 1 P1 | Both about description-string polish, not behavior. |
| B. Phase A inference | 0 | 2 P1 + 1 P2 | 1 P2 | All in prd-writer — signal table missing values + conflict-resolution. |
| C. Phase B core questions | 0 | 0 | 0 | Cleanest category — every skill nails the 3-option-with-spec'd-header rule. |
| D. Phase C follow-ups | 0 | 0 | 0 | The 6 hard rules are well-defined and consistently enforced. |
| E. Output structure | 1 P2 | 0 | 1 P0 | TB: Inferred-block placement narrative vs template; CR: screenshot path co-location. |
| F. Maturity / Depth adaptation | n/a | 0 | 0 | Cleanly spec'd. |
| G. Handoff & MCP integration | 0 | 1 P0 + 2 P2 | 1 P0 + 1 P2 | The highest-risk category across the kit. |
| H. Quality & specificity | 0 | 0 | 0 | — |
| I. Edge cases & failure modes | 1 P2 | 1 P1 | 1 P0 | CR memory + robots.txt the worst-defined corner. |

**Reading:** Phase B, Phase C, Maturity/Depth, and Quality categories are clean across all three skills — these are the most rigorous parts of the kit. Handoff & MCP integration is the most-defective category, all driven by cross-skill contracts and rare-path documentation gaps.

---

## Cross-Skill Architecture Notes

### Shared patterns that worked
- **Four-phase adaptive interview** (Phase A inference → Phase B unanswered core → Phase C ≤3 follow-ups with 6 hard rules → Phase D output) is uniform across all three skills and never broke.
- **`Inferred (not asked)` block** with phrase citations is consistently rendered when ≥1 field is inferred and consistently omitted when zero fields are inferred (90+ test cases confirm).
- **"Ready To Gamble On It?" handoff** with `Bet on it` / `Hold the chip` (+ `Double down` for prd-writer) is uniform.
- **Markdown-saved + absolute-path-printed** fallback works in every MCP-disconnected scenario.

### Contracts that need shoring up
- **prd-writer Double-down → ticket-builder PRD-driven mode** (P0). The contract is one-sided in the spec.
- **prd-writer §12 thin-row default-to-Task** behavior (per `SKILL.md:L204`) is also a ticket-builder behavior documented only on the prd-writer side. Apply the same mirror fix as item #1.
- **competitor-research → prd-writer/ticket-builder handoff for §7 Gaps & Opportunities** is described in passing (line 200, 244) but not contractually specified. PMs are expected to invoke the downstream skill manually with §7 as input — no documented handoff shape.

---

## Catalog Quality Notes

- **120 cases, 18 actionable items found, 2 real bugs identified** (cross-skill contract gap + CR screenshot path) — strong signal-to-noise ratio.
- **Frontmatter cases (TB-001, PRD-001, CR-001) are weak signals.** A static check on the file is more reliable than asking a runner sub-agent to simulate frontmatter compliance.
- **Phase A inference cases (B category, 8 per skill) provided the strongest behavioral signal** and surfaced the genuine PRD signal-table gaps (items #5, #6, #7 above).
- **Edge-case bundling in CR-040** (4 sub-rules in one case) made grading messy. Future iterations should split bundled edges into separate cases so the per-case verdict isn't all-or-nothing.
- **The judge sometimes confused body headers with frontmatter** (CR aggregator caught this and demoted two false-positive defects). A pre-flight static check on the frontmatter would eliminate this class of judge noise.

---

## Recommended Next Steps

1. **Apply the 4 P0 fixes** to the relevant SKILL.md files (one in ticket-builder/SKILL.md, three in competitor-research/SKILL.md, plus a mirror clause in ticket-builder for the PRD-driven mode contract).
2. **Re-run the test suite** after the fixes to confirm the targeted FAIL/PARTIAL cases flip to PASS without regressing the rest.
3. **Resolve the 5 P1 items** before the next plugin release. These don't break behavior but degrade output quality on common PM scenarios.
4. **Address the 9 P2 items** opportunistically — they're polish, not blockers.
5. **Extend the catalog** with: (a) static frontmatter checks, (b) split edge-case bundles into individual cases, (c) cross-skill chain tests (prd-writer Double-down → ticket-builder simulation across multiple PRDs of varying §12 size).

---

## Out of Scope

- No real Jira / Confluence / Playwright MCP calls were made — all MCP state was stubbed in case preconditions.
- The 3 deferred skills under `skills-deferred/` (product-discovery, experiment-planner, ux-copy) were not tested.
- No SKILL.md file was modified by the test run. The 3 skill specs in the plugin cache are unchanged from when the test run started.
- The Confluence PKB space ID (`772571142`) and parent page ID (`772571521`) were not verified against the live Atlassian instance — left for the user to confirm.
- This report does not stand in for manual PM-driven smoke tests (per `CONTRIBUTING.md` lines 89–101) — it complements them.
