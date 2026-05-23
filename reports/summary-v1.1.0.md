# CasinoSkilo v1.1.0 — Post-Fix Test Summary

**Date:** 2026-05-23
**Version under test:** v1.1.0 (was: v1.0.0)
**Skills tested:** 3 (ticket-builder, prd-writer, competitor-research)
**Total cases:** 120 (40 per skill — same catalog as v1.0.0, unchanged)
**Methodology:** Two-stage sub-agent dispatch identical to the v1.0.0 baseline. Same runner + judge prompts. Same pass criteria. The only thing that changed is the SKILL.md ground-truth files.

Per-skill v1.1.0 reports:
- [`ticket-builder-test-report-v1.1.0.md`](ticket-builder-test-report-v1.1.0.md)
- [`prd-writer-test-report-v1.1.0.md`](prd-writer-test-report-v1.1.0.md)
- [`competitor-research-test-report-v1.1.0.md`](competitor-research-test-report-v1.1.0.md)

v1.0.0 baseline reports (preserved for comparison):
- [`ticket-builder-test-report.md`](ticket-builder-test-report.md)
- [`prd-writer-test-report.md`](prd-writer-test-report.md)
- [`competitor-research-test-report.md`](competitor-research-test-report.md)
- [`summary.md`](summary.md)

Raw transcripts:
- v1.0.0: [`raw/<skill>/full-run.md`](raw/)
- v1.1.0: [`raw/<skill>/full-run-v1.1.0.md`](raw/)

---

## Cross-Skill Roll-up

| Skill | v1.0.0 | v1.1.0 | Δ Pass | Verdict |
|---|---|---|---|---|
| ticket-builder | 39 / 1 / 0 (Green 97.5%) | 40 / 0 / 0 (Green 100%) | +1 | 🟢 Green |
| prd-writer | 32 / 8 / 0 (Yellow 80.0%) | 40 / 0 / 0 (Green 100%) | +8 | 🟢 Green |
| competitor-research | 34 / 4 / 2 (Yellow 85.0%) | 39 / 1 / 0 (Green 97.5%) | +5 (5 PARTIAL/FAIL → PASS; 1 remains PARTIAL as catalog drift) | 🟢 Green |
| **Total** | **105 / 13 / 2 (87.5%)** | **119 / 1 / 0 (99.2%)** | **+14** | 🟢 **Green** |

**Headline:** All three skills now Green ≥ 95%. Total PASS jumped from 87.5% → 99.2%. **Zero regressions** anywhere in the catalog. The sole remaining PARTIAL is CR-025, which is a known case-YAML drift (catalog asserts wrong §2/§3 section names) — not a skill defect.

---

## What Got Fixed

### ticket-builder — 1 flip
- **TB-029** (PARTIAL → PASS): Inferred-block placement narrative now matches the template after TB-Δ-5.

### prd-writer — 8 flips (largest delta)
- **PRD-003** (PARTIAL → PASS): "Double down" verbatim in frontmatter (PRD-Δ-5).
- **PRD-006, PRD-007, PRD-030** (PARTIAL → PASS): Main user sub-segment hints (VIP / CRM tags) added to Phase A row (PRD-Δ-2).
- **PRD-008** (PARTIAL → PASS): Retention / re-engagement added as 4th Main problem value (PRD-Δ-3).
- **PRD-009** (PARTIAL → PASS): GGR `revenue` sub-tag in Success signal table (PRD-Δ-6).
- **PRD-011** (PARTIAL → PASS): Phase A conflict-resolution rule documented (PRD-Δ-4).
- **PRD-037** (PARTIAL → PASS): The Double-down chain — **the highest-risk feature in the kit** — is now fully spec'd. Cross-skill contract is mirrored in both `prd-writer/SKILL.md` (upstream) and `ticket-builder/SKILL.md` (downstream); chain length capped at 25; child tickets now infer 5 fields (including `Needs flow diagram`) all citing PRD sections.

### competitor-research — 6 flips
- **CR-002** (FAIL → PASS): Frontmatter description reordered so canonical noun phrase appears first (CR-Δ-5). The v1.0.0 FAIL was a judge misread, but the v1.1.0 reordering makes the description even cleaner.
- **CR-003** (PARTIAL → PASS): Frontmatter polish.
- **CR-016** (PARTIAL → PASS): Phase A vs Phase B memory-substitution path conflict resolved — Phase A is now canonically the reuse path (CR-Δ-1).
- **CR-038** (PARTIAL → PASS): **REAL BUG FIXED.** Markdown save path is now `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<date>.md` so the `screenshots/` subdir is a true sibling and relative `![](screenshots/...)` references resolve (CR-Δ-2). The "self-contained bundle" promise from L134 now actually holds.
- **CR-039** (PARTIAL → PASS): Quality / specificity rule clarifications.
- **CR-040** (PARTIAL → PASS): Memory-differs handling now uses an explicit 3-option AskUserQuestion (CR-Δ-3); robots.txt over-claim replaced with HTTP 403/451/CAPTCHA detection (CR-Δ-4); all 5 sub-criteria pass.

### CR-025 — the remaining PARTIAL (catalog drift, not a skill defect)
The case YAML asserts §2 = "Methodology" and §3 = "Competitor Snapshots" but the spec canonically defines them as "Competitors Reviewed" and "Executive Summary". The case is wrong, not the skill. **Action:** edit `tests/competitor-research/cases/CR-025.yaml` to match the canonical section names. Tracked as v1.2.0 catalog hygiene.

---

## Regressions

**None.** Every v1.0.0 PASS stayed PASS in v1.1.0 across all 120 cases. The brevity changes (DoD cap, Inferred-block cap, conditional User Flow) didn't break any existing assertion. The new Phase A `Needs flow diagram` field didn't push any case over the 7-question cap. The PRD Main problem option count bump (3 → 4) didn't break the "exactly 3 options" assertion because the v1.1.0 spec explicitly carves out Main problem (per PRD-Δ-9).

Regression-risk mitigations explicitly verified:
- TB-023 (7-question cap): worst case still 4 core + 3 follow-ups = 7 because the new `Flow?` fallback counts against the Phase C 3-cap.
- TB-025 (User Flow required for features): feature-class input still triggers `Needs flow diagram = Yes` per the Phase A signal table.
- TB-011 (conflict resolution): TB-Δ-7's "Not inferred" path is in the case's `acceptable_outcomes`.
- PRD-014 (Phase B 3-option assertion): load-bearing check is header match, not option count; passes despite Main problem now having 4 options.
- CR-035 (gamble question count): the new attachment-offer question is post-handoff with a different header (`Attach screenshots?` vs `Gamble?`) so it doesn't violate the "exactly one gamble question" assertion.

---

## What's Left

### Skill-level
**Nothing.** The 4 P0 + 5 P1 + 9 P2 actionable items from the v1.0.0 audit are all resolved. The 3 SKILL.md files are clean, the cross-skill contract is bidirectionally documented, the screenshot path bug is fixed, and the brevity caps are enforced.

### Catalog-level
**One catalog fix** for v1.2.0 testing: edit `tests/competitor-research/cases/CR-025.yaml` to assert the canonical §2/§3 section names. This is a 30-second YAML edit; not a release blocker.

### Suggested v1.2.0 scope (not in this release)
- Add catalog cases covering the new v1.1.0 behaviors (5th Phase A `Needs flow diagram` field, Retention Main problem value, GGR `revenue` sub-tag, 25-child Double-down cap, memory-differs 3-option AskUserQuestion).
- Add a static frontmatter checker to the harness to eliminate the class of judge-misreads (CR-002 in v1.0.0).
- Split the bundled CR-040 edge case into 4 standalone cases for cleaner grading.

---

## Release Decision

Per the v1.1.0 plan's decision tree:
- All 3 skills Green ≥ 95% ✅
- Zero regressions ✅

**Decision:** Tag v1.1.0 on GitHub. The 119/1/0 result satisfies the release criteria; the lone PARTIAL is documented as catalog drift in the per-skill report.

---

## Out of Scope

- No real Jira / Confluence / Playwright MCP calls — all MCP state was stubbed in case preconditions, identical to v1.0.0.
- The 3 deferred skills under `skills-deferred/` (product-discovery, experiment-planner, ux-copy) were not tested.
- The Confluence PKB space ID (`772571142`) and parent page ID (`772571521`) were not verified against the live Atlassian instance.
- CR-025 catalog fix deferred to v1.2.0 hygiene pass.
