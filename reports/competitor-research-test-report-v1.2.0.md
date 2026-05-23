# competitor-research — Test Report v1.2.0

**Skill:** [`competitor-research/SKILL.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/skills/competitor-research/SKILL.md) (264 lines, **unchanged from v1.1.0**)
**Catalog:** [`tests/competitor-research/cases/`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/) — 48 cases (40 original + 1 rewrite + 8 backfill)
**Coverage map:** [`tests/competitor-research/coverage-map.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/coverage-map.md)
**Run date:** 2026-05-23
**Raw run (v1.2.0):** [`reports/raw/competitor-research/full-run-v1.2.0.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/competitor-research/full-run-v1.2.0.md)
**Previous report (v1.1.0):** [`reports/competitor-research-test-report-v1.1.0.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/competitor-research-test-report-v1.1.0.md)

## Executive Summary

| Verdict | Count | % |
|---|---|---|
| PASS | 48 | 100% |
| PARTIAL | 0 | 0% |
| FAIL | 0 | 0% |
| **Total** | 48 | 100% |

**Overall verdict:** 🟢 Green (100% PASS) — up from v1.1.0's 39/1/0 🟢 Green (97.5%). The lone v1.1.0 PARTIAL (CR-025 catalog drift) is now PASS via the case YAML fix. CR-040 rewritten from 4-sub-rule bundle to focused memory-differs case (also PASS). +8 new backfill cases all PASS. **No SKILL.md changes.**

## Per-Category Breakdown

| Category | Cases | PASS | PARTIAL | FAIL | % PASS | Δ vs v1.1.0 |
|---|---|---|---|---|---|---|
| A. Frontmatter & metadata | 3 | 3 | 0 | 0 | 100% | — |
| B. Phase A inference | 10 | 10 | 0 | 0 | 100% | +2 backfill (CR-041, CR-042) |
| C. Phase B core questions | 6 | 6 | 0 | 0 | 100% | +1 backfill (CR-046) |
| D. Phase C follow-ups | 8 | 8 | 0 | 0 | 100% | — |
| E. Output structure | 7 | 7 | 0 | 0 | 100% | CR-025 PARTIAL → PASS (catalog fix) |
| F. Depth adaptation | 3 | 3 | 0 | 0 | 100% | — |
| G. Handoff & MCP integration | 6 | 6 | 0 | 0 | 100% | +2 backfill (CR-043, CR-044) |
| H. Quality & specificity | 1 | 1 | 0 | 0 | 100% | — |
| I. Edge cases & failure modes | 4 | 4 | 0 | 0 | 100% | CR-040 rewritten; +3 backfill (CR-045, CR-047, CR-048) |
| **Total** | 48 | 48 | 0 | 0 | **100%** | **+9 PASS, 0 regressions** |

## Detailed Results

### A. Frontmatter & metadata

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| CR-001 | SKILL.md frontmatter parses as valid YAML with name and description | PASS | PASS → PASS | L1-L4 | Frontmatter unchanged. |
| CR-002 | Description begins with 'Use when' trigger phrase | PASS | PASS → PASS | L3 | Description ordering preserved. |
| CR-003 | Description names output type and clarifies research-only (no Jira tickets) | PASS | PASS → PASS | L3 + L253 | Research-only clarification preserved at L253. |

### B. Phase A inference

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| CR-004 | Focus inferred as 'Onboarding' from 'compare our signup to competitors' | PASS | PASS → PASS | L68-L73 | Memory-reuse canonical path. |
| CR-005 | Focus inferred as 'Pricing/Bonuses' from 'how do they price welcome bonuses?' | PASS | PASS → PASS | L68 | — |
| CR-006 | Output emphasis inferred as 'UX flow + screenshots' from 'walk me through their flow' | PASS | PASS → PASS | L70-L72 | — |
| CR-007 | Depth inferred as 'Deep UX flow' from 'every screen, frame by frame' | PASS | PASS → PASS | L71 | — |
| CR-008 | Depth inferred as 'Quick scan' from '30-minute scan' | PASS | PASS → PASS | L71 | — |
| CR-009 | Competitors NOT inferred when memory has no list and input is generic | PASS | PASS → PASS | L69 + L90-L92 | Phase B fallback path holds. |
| CR-010 | Ambiguous fall-through: vague 'check what others are doing' infers nothing | PASS | PASS → PASS | L67-L73 | — |
| CR-011 | Multi-signal conflict: 'quick deep dive' resolves to one Depth or stays uninferred | PASS | PASS → PASS | L64 | — |
| **CR-041** | **Phase A canonical memory reuse — memory has `**Competitors:**` line; Phase A infers; Phase B skipped** | **PASS** | **NEW → PASS** | **L69** | **Backfill.** Verifies the primary (canonical) reuse path; negative-control sibling is CR-046. |
| **CR-042** | **Phase A trust-signal keywords — 'trust signals' / 'social proof' / 'reviews' → Focus = Core feature experience (trust surface)** | **PASS** | **NEW → PASS** | **L68** | **Backfill.** Verifies the v1.1.0 L68 keyword extension (was CR-Δ-6); trust routed through Core feature experience with `(trust surface)` qualifier. |

### C. Phase B core questions

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| CR-012 | Phase B asks only the questions Phase A didn't infer | PASS | PASS → PASS | L75-L98 | — |
| CR-013 | Each Phase B question has exactly 3 concrete options matching the spec verbatim | PASS | PASS → PASS | L78-L100 | — |
| CR-014 | Phase B headers match spec verbatim: Focus / Targets / Output / Depth | PASS | PASS → PASS | L80-L97 | — |
| CR-015 | When Phase A infers zero fields, Phase B asks all 4 core questions | PASS | PASS → PASS | L75-L100 | — |
| CR-016 | Competitors question label substitutes real names from memory at runtime | PASS | PASS → PASS | L69 + L86 + L90-L92 | Phase A reuse remains canonical. |
| **CR-046** | **Phase B fallback path — memory empty AND user didn't name competitors → Phase B asks; fallback options shown** | **PASS** | **NEW → PASS** | **L86-L95** | **Backfill.** Negative-control sibling to CR-041. Confirms bifurcation at L69 + L90–L92: memory absent + no explicit names → Phase B asks with the 3 spec'd fallback options. |

### D. Phase C follow-ups

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| CR-017 | Phase C emits at most 3 follow-up questions | PASS | PASS → PASS | L102-L116 | — |
| CR-018 | Phase C rejects banned placeholder options | PASS | PASS → PASS | L105-L107 | — |
| CR-019 | Phase C skips region question when input already names a market | PASS | PASS → PASS | L108-L109 | — |
| CR-020 | Phase C does NOT ask about screenshot filenames | PASS | PASS → PASS | L109 + L133 | — |
| CR-021 | Phase C does NOT re-ask 'use existing competitors or different ones?' | PASS | PASS → PASS | L121-L124 | — |
| CR-022 | Phase C respects CR-specific priority order (region > source mix > time horizon > auth) | PASS | PASS → PASS | L110-L115 | — |
| CR-023 | Phase C falls back to assume+flag when no 3 concrete options exist | PASS | PASS → PASS | L115-L116 | — |
| CR-024 | Good follow-ups: 21.com region + third-party source-mix asks both with concrete options | PASS | PASS → PASS | L117-L122 | — |

### E. Output structure

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| **CR-025** | **Output contains all 7 numbered sections in order** | **PASS** | **PARTIAL → PASS** | **L155-L201** | **Catalog fix verified.** v1.2.0 case YAML now asserts canonical §2 "Competitors Reviewed" and §3 "Executive Summary" matching SKILL.md L172–L177. The v1.1.0 catalog-drift PARTIAL is resolved without any SKILL.md edit — the skill behavior was always correct. |
| CR-026 | Metadata table at top has Status / Author / Date / Depth / Region scope rows | PASS | PASS → PASS | L161-L168 | — |
| CR-027 | §4 Comparison Table has at least 4 rows from canonical labels | PASS | PASS → PASS | L181-L188 | — |
| CR-028 | §5 UX Flow Notes references screenshots inline — no separate Screenshots section | PASS | PASS → PASS | L188-L197 | Relative `![](screenshots/...)` paths resolve via co-located subdir. |
| CR-029 | §6 Key Patterns distinguishes table-stakes vs. differentiation | PASS | PASS → PASS | L198-L201 | — |
| CR-030 | Output ends at §7 — no Jira tickets generated, no meta-commentary | PASS | PASS → PASS | L201-L253 | — |
| CR-031 | Inferred (not asked) block appears at top when Phase A inferred at least one field | PASS | PASS → PASS | L156-L160 | — |

### F. Depth adaptation

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| CR-032 | Quick scan depth → 3–5 opportunities, screenshots optional | PASS | PASS → PASS | L147-L148 | — |
| CR-033 | Detailed comparison → full matrix + key-surface screenshots + prioritized recs | PASS | PASS → PASS | L149-L150 | — |
| CR-034 | Deep UX flow → per-competitor step-by-step + friction + every-screen screenshots + side-by-side + experiments | PASS | PASS → PASS | L150-L151 | — |

### G. Handoff & MCP integration

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| CR-035 | Ready To Gamble On It? presented with exactly 2 options: Bet on it + Hold the chip | PASS | PASS → PASS | L227-L232 | Attachment-offer is a different question (different header) — does not violate single-gamble rule. |
| CR-036 | Bet on it + atlassian MCP → Confluence create with PKB spaceId/parentId and markdown format | PASS | PASS → PASS | L234-L241 | spaceId=772571142, parentId=772571521, contentFormat=markdown. |
| CR-037 | After Confluence publish, surfaces one-line note: screenshots are local-only | PASS | PASS → PASS | L241 + L243-L249 | Note surfaced verbatim per L241. |
| CR-038 | Markdown saved to `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` with co-located screenshots subdir | PASS | PASS → PASS | L226 + L133 | Semantic co-location holds via v1.1.0 slug-subdir path scheme. |
| **CR-043** | **Screenshot path co-location — markdown saved at `~/Downloads/competitor-research/<slug>/<slug>-<date>.md`** | **PASS** | **NEW → PASS** | **L226** | **Backfill — directly exercises the v1.1.0 screenshot-path bug fix (CR-Δ-2).** The fix that was indirectly verified by CR-038 in v1.1.0 now has its own dedicated case. Confirms `homepage/homepage-2026-05-23.md` with sibling `homepage/screenshots/` — relative `![](screenshots/...)` references resolve from the markdown's directory. |
| **CR-044** | **Confluence-attachment offer — after Bet on it with N≥1 screenshots, skill presents 'Attach screenshots?' AskUserQuestion** | **PASS** | **NEW → PASS** | **L242-L250** | **Backfill.** Verifies full Bet-on-it+screenshots handoff sequence: page create → local-only note → attachment-offer question (header `Attach screenshots?`, options `Upload all` / `Upload none`) → optional attachment upload + inline-ref rewrite. |

### H. Quality & specificity

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| CR-039 | Findings are specific, cite source, and call out missing/inaccessible pages | PASS | PASS → PASS | L143 + L207-L213 | HTTP 403/451/CAPTCHA detection path holds. |

### I. Edge cases & failure modes

| ID | Title | Verdict | v1.1.0 → v1.2.0 | SKILL.md ref | Key finding |
|---|---|---|---|---|---|
| **CR-040** | **Memory-differs handling — runtime competitors differ from cache; skill emits 3-option AskUserQuestion** | **PASS** | **REWRITTEN → PASS** | **L255-L264** | **Rewrite verified.** v1.1.0 packed 4 sub-rules (DIFFERS / EMPTY / Playwright-off / robots.txt) into one bundle. v1.2.0 narrows CR-040 to the memory-differs sub-rule only. Trace shows: skill detects divergence (memory: Stake/1Xbet/Rollbit/Bc.Game vs runtime: BetMGM/DraftKings), emits the L258–L264 AskUserQuestion verbatim — header `Competitors?`, exactly 3 options (`Use cached` / `Use runtime + update memory` / `Use runtime, keep memory`). The 3 sibling sub-rules migrated to CR-045 / CR-047 / CR-048 for cleaner failure attribution. |
| **CR-045** | **HTTP 403/451/CAPTCHA detection — Playwright hit on a 451 page produces inline 'couldn't access <page> — 451' note** | **PASS** | **NEW → PASS** | **L141-L143** | **Backfill (migrated from v1.1.0 CR-040 bundle).** Stake `/signup` returns HTTP 451 → §5 under Stake subheading contains `couldn't access /signup — 451 geoblocked` per L143 pattern. Other Stake pages still render. Confirms skill does NOT pre-flight robots.txt. |
| **CR-047** | **Memory cached after Phase B — empty memory → Phase B asks Competitors → answer appended as `**Competitors:**` line** | **PASS** | **NEW → PASS** | **L211 + L256** | **Backfill (migrated from v1.1.0 CR-040 bundle).** Empty memory → Targets question → PM provides BetMGM/DraftKings/FanDuel → memory file `~/.claude/memory/21com.md` created with `**Competitors:**` marker BEFORE report renders. Closes the empty-memory lifecycle so CR-041 (canonical reuse) is satisfiable on the next run. |
| **CR-048** | **Playwright unavailable degrades gracefully — mcp_state: none produces text-only report; §1 notes 'Playwright not available'** | **PASS** | **NEW → PASS** | **L127-L134 + L208** | **Backfill (migrated from v1.1.0 CR-040 bundle).** Full 7-section report renders without screenshots. §1 contains exact substring "Playwright not available — no screenshots captured". §5 omits all `![](screenshots/...)` references — no broken links rendered. |

## Delta vs v1.1.0

### Cases that flipped PARTIAL/FAIL → PASS (1)

| Case | v1.1.0 | v1.2.0 | Root cause resolved by |
|---|---|---|---|
| CR-025 | PARTIAL | PASS | **Catalog YAML fix.** Case now asserts canonical §2 "Competitors Reviewed" / §3 "Executive Summary" matching SKILL.md L172–L177. No SKILL.md edit was needed — the v1.1.0 PARTIAL was always catalog drift, not a skill defect. |

### Cases rewritten (1)

| Case | v1.1.0 | v1.2.0 | Change |
|---|---|---|---|
| CR-040 | PARTIAL (bundled 4 sub-rules) → PASS in v1.1.0 | REWRITTEN → PASS | Scope narrowed to the memory-differs sub-rule only. The 3 sibling sub-rules (HTTP 451, memory cache after Phase B, Playwright unavailable) split into CR-045 / CR-047 / CR-048 for cleaner failure attribution. The L258–L264 3-option AskUserQuestion is now the single focused assertion. |

### New backfill cases (8) — all PASS first time

| Case | Category | What it verifies | Backfills |
|---|---|---|---|
| CR-041 | phase-a-inference | Canonical memory-reuse path (L69) | Primary path for CR-Δ-1 (v1.1.0 delta) |
| CR-042 | phase-a-inference | Trust-signal keyword routing (L68) | CR-Δ-6 (v1.1.0 keyword expansion) |
| CR-043 | handoff | **Screenshot path co-location at `<slug>/<slug>-<date>.md` (L226)** | **The real v1.1.0 screenshot-path bug fix (CR-Δ-2) now directly exercised by its own dedicated case.** Previously only indirectly verified by CR-038's "semantic" assertion. |
| CR-044 | handoff | Confluence-attachment offer question (L242–L250) | CR-Δ-7 (v1.1.0 bonus attachment-offer AskUserQuestion) |
| CR-045 | edge-case | HTTP 403/451/CAPTCHA detection (L141–L143) | CR-Δ-4 — migrated from CR-040 sub-rule |
| CR-046 | phase-b-core-questions | Phase B fallback when memory empty (L86–L95) | Negative-control sibling to CR-041 |
| CR-047 | edge-case | Memory cache after Phase B (L211 + L256) | Migrated from CR-040 sub-rule (EMPTY) |
| CR-048 | edge-case | Playwright unavailable graceful degradation (L127–L134 + L208) | Migrated from CR-040 sub-rule (Playwright-off) |

### Regressions (PASS → PARTIAL/FAIL): 0

None. Every v1.1.0 PASS (38 cases excluding CR-025 and CR-040) reused its trace verbatim — SKILL.md is byte-identical to v1.1.0.

**Net change:** +9 PASS, -1 PARTIAL, 0 FAIL. PASS rate: 97.5% → **100%** (+2.5pp). Overall verdict: 🟢 Green → 🟢 Green (saturated).

## Actionable Items

**No actionable items at v1.2.0.** All categories at 100% PASS. SKILL.md is unchanged from v1.1.0 and continues to satisfy its full case catalog. The v1.1.0 catalog-drift item (CR-025) is closed. CR-040 rewrite is closed. 8 backfill cases are merged and green.

## Note on Section O vocabulary additions

The v1.2.0 catalog introduces 4 new assertion IDs in SKILL.md Section O (criterion vocabulary) used by the 8 backfill cases and CR-040 rewrite:

- **`cr-memory-differs-three-option-question`** — verifies the L258–L264 3-option AskUserQuestion fires with the exact options `Use cached` / `Use runtime + update memory` / `Use runtime, keep memory`. Used by CR-040.
- **`cr-markdown-saved-in-focus-subdir`** — verifies the v1.1.0 path pattern `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md` (slug-subdir co-location). Used by CR-043.
- **`cr-confluence-attachment-offer-fires`** — verifies the bonus AskUserQuestion (header `Attach screenshots?`, options `Upload all` / `Upload none`) fires after the screenshots-local-only note when N≥1 screenshots exist. Used by CR-044.
- **`cr-http-error-noted-inline`** — verifies the L143 pattern `couldn't access <page> — <reason>` for HTTP 403/451/CAPTCHA hits. Used by CR-045.

These IDs codify behavior that was already spec'd in v1.1.0 but had no dedicated catalog assertion until v1.2.0.

## Cross-Skill Notes

- **competitor-research is research-only.** SKILL.md L253 is unchanged: "This skill is research-only. It does NOT create Jira tickets." Every case (incl. all 8 backfill) ends the artifact at §7 — no §8, no `Suggested Jira Breakdown`, no `Builder notes`.
- **§7 Gaps & Opportunities feeds downstream skills.** When a PM wants research findings turned into work, the §7 gaps list is the handoff to `prd-writer` (for product-shaped specs) or `ticket-builder` (for direct Jira tickets). Neither downstream skill is invoked by competitor-research itself.
- **v1.1.0 contract is unchanged.** SKILL.md is byte-identical to v1.1.0. All v1.1.0 deltas (CR-Δ-1 through CR-Δ-7) remain in force; v1.2.0 only widens the test catalog around them. Consumers depending on v1.1.0 behavior require no migration.

## Out of Scope for This Report

- Real Playwright runs against live competitor sites — no scraping was performed; case preconditions stub the Playwright tool state.
- Real Confluence MCP calls — Confluence handoff traces simulate the create-page + create-attachment calls.
- Modifying SKILL.md — v1.2.0 makes zero SKILL.md edits. All gains come from catalog work (CR-025 YAML fix, CR-040 rewrite, 8 backfill cases).
- Verifying the PKB space/parent IDs are still valid in the live Confluence instance.
- Real Jira MCP calls — competitor-research never creates issues; downstream skills (prd-writer / ticket-builder) handle Jira integration in their own catalogs.
