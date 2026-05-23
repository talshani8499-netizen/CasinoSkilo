# CasinoSkilo v1.2.0 — Catalog Hygiene Summary

**Date:** 2026-05-23
**Catalog version:** v1.2.0
**Plugin version:** unchanged at v1.1.0 (no SKILL.md edits, no downstream behavior change)
**Skills tested:** 3 (ticket-builder, prd-writer, competitor-research)
**Total cases:** 144 (up from 120 in v1.1.0 — added 24 new, rewrote 1, fixed 1)
**Methodology:** Two-stage sub-agent dispatch identical to v1.0.0 and v1.1.0 baselines. Same runner + judge prompts. Vocab grew from 608 → 791 lines with new sections L (Static checks), M (TB v1.1.0 additions), N (PRD v1.1.0 additions), O (CR v1.1.0 additions).

Per-skill v1.2.0 reports:
- [`ticket-builder-test-report-v1.2.0.md`](ticket-builder-test-report-v1.2.0.md)
- [`prd-writer-test-report-v1.2.0.md`](prd-writer-test-report-v1.2.0.md)
- [`competitor-research-test-report-v1.2.0.md`](competitor-research-test-report-v1.2.0.md)

v1.0.0 and v1.1.0 baseline reports preserved alongside for delta comparison.

Raw transcripts at [`raw/<skill>/full-run-v1.2.0.md`](raw/).

---

## Cross-Skill Roll-up

| Skill | v1.0.0 | v1.1.0 | v1.2.0 | Δ vs v1.1.0 | Verdict |
|---|---|---|---|---|---|
| ticket-builder | 39/1/0 (97.5%) | 40/0/0 (100%) | **49/0/0 (100%)** | +9 cases, 0 regressions | 🟢 Green |
| prd-writer | 32/8/0 (80.0%) | 40/0/0 (100%) | **47/0/0 (100%)** | +7 cases, 0 regressions | 🟢 Green |
| competitor-research | 34/4/2 (85.0%) | 39/1/0 (97.5%) | **48/0/0 (100%)** | +8 cases + CR-040 rewrite + CR-025 fix, 0 regressions | 🟢 Green |
| **Total** | **105/13/2 (87.5%)** | **119/1/0 (99.2%)** | **144/0/0 (100%)** | **+24 new + 1 rewrite + 1 fix, 0 regressions** | 🟢 **Perfect** |

**Headline:** First-ever 100% PASS across the entire catalog. Every v1.1.0-added behavior now has dedicated test coverage. The lone v1.1.0 PARTIAL (CR-025) is resolved. Zero regressions on any of the 120 v1.1.0 cases.

---

## What Got Added (24 new + 1 rewrite + 1 fix)

### ticket-builder — 9 new (TB-041…TB-049)
| ID | Tests |
|---|---|
| TB-041 | Phase A `Needs flow diagram = Yes` from "new feature" signal |
| TB-042 | Phase A `Needs flow diagram = No` → artifact omits §User Flow entirely |
| TB-043 | Phase A doesn't infer → Phase C `Flow?` fallback fires with 3 spec'd options |
| TB-044 | DoD hard cap (3–5 items) enforced — naïve 8 items trimmed to 5 |
| TB-045 | Inferred-block 4-bullet cap with `_(+N more inferred)_` overflow line |
| TB-046 | "Assume + flag" inline syntax matches `> **Assumption:** … **Flag:** …` |
| TB-047 | Phase A conflict rule — input "fix the new feature" leaves Ticket type Not inferred |
| TB-048 | **PRD-driven mode marquee case** — zero questions, all 5 inferences cite PRD section, auto Bet on it |
| TB-049 | PRD-driven mode — thin §12 row defaults to `Task` with inline `> **Open:**` flag |

### prd-writer — 7 new (PRD-041…PRD-047)
| ID | Tests |
|---|---|
| PRD-041 | Phase A infers Retention / re-engagement from "re-engage lapsed" signal |
| PRD-042 | User Story surfaces `vip` tag when input names VIP players |
| PRD-043 | User Story surfaces `crm` tag when input names CRM operator |
| PRD-044 | §10 Primary Metric shows `revenue` sub-tag when input mentions NGR/ARPU |
| PRD-045 | Phase A conflict rule — "v2 of raffles from scratch" leaves Maturity Not inferred |
| PRD-046 | **Double-down 25-row cap marquee case** — `Chain too long?` question fires BEFORE any Jira call (verified in trace order) |
| PRD-047 | Confluence parentId 404 → retry without parentId, report landing URL |

### competitor-research — 8 new (CR-041…CR-048) + CR-040 rewritten + CR-025 fixed
| ID | Status | Tests |
|---|---|---|
| CR-025 | PARTIAL → PASS | Canonical §2/§3 names ("Competitors Reviewed" / "Executive Summary") replace catalog drift |
| CR-040 | REWRITTEN → PASS | Focused single-sub-rule case (memory-differs only); old 4-in-1 bundle split out |
| CR-041 | NEW → PASS | Phase A canonical memory reuse — Phase B skips Competitors when memory has the line |
| CR-042 | NEW → PASS | Trust-signal keywords → Focus = Core feature experience |
| CR-043 | NEW → PASS | **Screenshot path co-location** — real v1.1.0 bug fix now directly exercised |
| CR-044 | NEW → PASS | Confluence-attachment offer after Bet on it with N≥1 screenshots |
| CR-045 | NEW → PASS | HTTP 451 inline note (replaces robots.txt over-claim) |
| CR-046 | NEW → PASS | Phase B fallback — negative control for CR-041 |
| CR-047 | NEW → PASS | Memory cached after Phase B (split from old CR-040 sub-rule 2) |
| CR-048 | NEW → PASS | Playwright unavailable degrades gracefully (split from old CR-040 sub-rule 3) |

---

## New Vocabulary Sections (4 sections, 14 new assertion IDs)

Appended to [`tests/rubric/pass-criteria-vocabulary.md`](../tests/rubric/pass-criteria-vocabulary.md):

| Section | Topic | New IDs |
|---|---|---|
| **L** | Static checks (pre-runner) | `static-frontmatter-parses-as-yaml`, `static-description-starts-with-use-when`, `static-description-includes-output-noun`, `static-required-h2-headings-present` |
| **M** | ticket-builder v1.1.0 additions | `dod-item-count-within-cap`, `inferred-block-cap-respected`, `assume-flag-syntax-format`, `prd-driven-mode-zero-questions`, `prd-driven-mode-auto-bet-on-it`, `prd-driven-mode-thin-row-default` |
| **N** | prd-writer v1.1.0 additions | `phase-a-sub-segment-tag-applied`, `analytics-primary-metric-has-revenue-tag`, `double-down-chain-cap-question-fires`, `confluence-parentid-404-retry-fallback` |
| **O** | competitor-research v1.1.0 additions | `cr-memory-differs-three-option-question`, `cr-markdown-saved-in-focus-subdir`, `cr-confluence-attachment-offer-fires`, `cr-http-error-noted-inline` |

The 4 Section L static-check IDs are deliberately under-used in v1.2.0 — they're harness primitives that future cases (v1.3.0+) can adopt to pre-filter judge-misreads of the kind that caused the v1.0.0 CR-002 FAIL.

---

## Regressions

**None.** Every v1.1.0 PASS stayed PASS in v1.2.0 across all 120 unchanged cases. This is the expected outcome — SKILL.md is byte-identical to v1.1.0 (no spec changes in v1.2.0). The 49 + 47 + 48 v1.2.0 cases include the v1.1.0 cases unchanged plus the 24 new + 1 rewrite + 1 fix.

Regression-risk checks explicitly verified:
- TB-001…TB-040: all PASS (40/40 unchanged from v1.1.0).
- PRD-001…PRD-040: all PASS (40/40 unchanged).
- CR-001…CR-039: all PASS (39/39 unchanged, since CR-040 was rewritten).

---

## What's Left

### Skill-level
**Nothing.** Plugin distribution stays at v1.1.0 — no SKILL.md changes shipped in this release.

### Catalog-level
**Nothing actionable.** 144/0/0 across the catalog. Section L's static checks are available for future cases to adopt.

### Parked for v1.3.0 (not in this release)
- **Live MCP smoke test** — invoke each skill against your actual Claude Code with real Atlassian + Playwright MCP connected; validate that the simulated runs match runtime behavior.
- **Confluence PKB ID verification** — confirm `spaceId=772571142` and `parentId=772571521` still resolve in the live instance.
- **Promote one or more deferred skills** from `skills-deferred/` (product-discovery, experiment-planner, ux-copy) to active. This would be a real plugin release (v1.2.0 or v2.0.0) — not catalog-only.
- **CI gate** — wire the test catalog into a GitHub Actions workflow that re-runs on every PR to `skills/`.
- **Section L adoption** — retrofit existing cases to use the static frontmatter checks as a first-line filter, eliminating the class of judge-misreads.

---

## Release Decision

Per the v1.2.0 plan's release criteria:
- All 3 skills 100% Green ✅
- Zero regressions ✅
- Plugin manifest unchanged ✅

**Decision:** Tag v1.2.0 on GitHub. This is a repo-scoped tag marking the test catalog version. `/plugin update CasinoSkilo` is a no-op for downstream users (plugin distribution stays at v1.1.0).

---

## Out of Scope

- No SKILL.md edits — v1.1.0 spec is the spec under test, unchanged.
- No `plugin.json` version bump.
- No GitHub Release UI creation (deferred to user — install `gh` and run `gh release create v1.2.0` or use the web UI).
- No real Atlassian / Playwright MCP calls — all MCP state stubbed in case preconditions.
- The 3 deferred skills under `skills-deferred/` were not tested.
