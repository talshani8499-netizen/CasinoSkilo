# competitor-research — Test Report

**Skill:** [`competitor-research/SKILL.md`](/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/competitor-research/SKILL.md) (248 lines)
**Catalog:** [`tests/competitor-research/cases/`](/Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/) — 40 cases
**Run date:** 2026-05-23
**Raw run:** [`reports/raw/competitor-research/full-run.md`](/Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/competitor-research/full-run.md)

## Executive Summary

| Verdict | Count | % |
|---|---|---|
| PASS | 34 | 85.0% |
| PARTIAL | 4 | 10.0% |
| FAIL | 2 | 5.0% |
| **Total** | 40 | 100% |

**Overall verdict:** 🟡 Yellow (85% PASS) — the skill handles the happy path cleanly across inference, Phase B/C interview, output shape, and handoff, but two real design defects (memory-vs-Phase-B conflict and screenshot path co-location) and several spec gaps (KYC keyword, robots.txt enforcement, memory-differs prompt format) prevent a Green.

**High-risk findings:** 2 FAILs — **CR-002** (frontmatter description begins with "Run structured…" rather than the canonical "Use when…" trigger — see "Important judging notes" below; this is a judge misread of the body header vs frontmatter, so it has been demoted out of the actionables) and **CR-025** (test catalog expects "§2 Methodology / §3 Competitor Snapshots" but SKILL.md L170-L175 spec'd "§2 Competitors Reviewed / §3 Executive Summary" — catalog drift, not skill defect).

## Per-Category Breakdown

| Category | Cases | PASS | PARTIAL | FAIL | % PASS |
|---|---|---|---|---|---|
| A. Frontmatter & metadata | 3 | 1 | 1 | 1 | 33.3% |
| B. Phase A inference | 8 | 8 | 0 | 0 | 100% |
| C. Phase B core questions | 5 | 4 | 1 | 0 | 80.0% |
| D. Phase C follow-ups | 8 | 8 | 0 | 0 | 100% |
| E. Output structure | 7 | 6 | 0 | 1 | 85.7% |
| F. Depth adaptation | 3 | 3 | 0 | 0 | 100% |
| G. Handoff & MCP integration | 4 | 3 | 1 | 0 | 75.0% |
| H. Quality & specificity | 1 | 1 | 0 | 0 | 100% |
| I. Edge cases & failure modes | 1 | 0 | 1 | 0 | 0% |
| **Total** | 40 | 34 | 4 | 2 | 85.0% |

## Detailed Results

### A. Frontmatter & metadata

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-001 | SKILL.md frontmatter parses as valid YAML with name and description | PASS | L1-L5 | — |
| CR-002 | Description begins with 'Use when' trigger phrase | FAIL | L3-L5 | Judge misread — frontmatter description does begin with "Use when…"; the "Run structured…" text is from the body `## Purpose` header (L9). See catalog-quality notes. |
| CR-003 | Description names output type and clarifies research-only (no Jira tickets) | PARTIAL | L3-L5 | Frontmatter description does not contain the literal phrase "7-section comparison report"; constraint is in body L242-L244 only. |

### B. Phase A inference

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-004 | Focus inferred as 'Onboarding' from 'compare our signup to competitors' | PASS | L67-L73 | — |
| CR-005 | Focus inferred as 'Pricing/Bonuses' from 'how do they price welcome bonuses?' | PASS | L67-L73 | — |
| CR-006 | Output emphasis inferred as 'UX flow + screenshots' from 'walk me through their flow' | PASS | L67-L73 | — |
| CR-007 | Depth inferred as 'Deep UX flow' from 'every screen, frame by frame' | PASS | L67-L73 | — |
| CR-008 | Depth inferred as 'Quick scan' from '30-minute scan' | PASS | L67-L73 | — |
| CR-009 | Competitors NOT inferred when memory has no list and input is generic | PASS | L67-L73 | Spec gap noted — inference table doesn't list "KYC"/"compliance" keywords explicitly. |
| CR-010 | Ambiguous fall-through: vague 'check what others are doing' infers nothing | PASS | L67-L73 | — |
| CR-011 | Multi-signal conflict: 'quick deep dive' resolves to one Depth or stays uninferred | PASS | L67-L73 | — |

### C. Phase B core questions

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-012 | Phase B asks only the questions Phase A didn't infer | PASS | L78-L98 | — |
| CR-013 | Each Phase B question has exactly 3 concrete options matching the spec verbatim | PASS | L80-L98 | — |
| CR-014 | Phase B headers match spec verbatim: Focus / Targets / Output / Depth | PASS | L80-L98 | — |
| CR-015 | When Phase A infers zero fields, Phase B asks all 4 core questions | PASS | L78-L98 | — |
| CR-016 | Competitors question label substitutes real names from memory at runtime | PARTIAL | L85-L88 | Design conflict — L69 "memory → infer" makes the L86 Phase-B substitution rule unreachable when memory already has names. |

### D. Phase C follow-ups

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-017 | Phase C emits at most 3 follow-up questions | PASS | L103-L113 | — |
| CR-018 | Phase C rejects banned placeholder options | PASS | L106-L108 | — |
| CR-019 | Phase C skips region question when input already names a market | PASS | L109-L110 | — |
| CR-020 | Phase C does NOT ask about screenshot filenames | PASS | L111-L120 | — |
| CR-021 | Phase C does NOT re-ask 'use existing competitors or different ones?' | PASS | L111-L122 | — |
| CR-022 | Phase C respects CR-specific priority order (region > source mix > time horizon > auth) | PASS | L111-L113 | — |
| CR-023 | Phase C falls back to assume+flag when no 3 concrete options exist | PASS | L112-L113 | — |
| CR-024 | Good follow-ups: 21.com region + third-party source-mix scenario asks both with concrete options | PASS | L115-L122 | — |

### E. Output structure

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-025 | Output contains all 7 numbered sections in order | FAIL | L155-L200 | Test catalog uses §2 "Methodology" / §3 "Competitor Snapshots"; SKILL.md spec says §2 "Competitors Reviewed" / §3 "Executive Summary". Catalog drift — SKILL.md is canonical. |
| CR-026 | Metadata table at top has Status / Author / Date / Depth / Region scope rows | PASS | L159-L165 | — |
| CR-027 | §4 Comparison Table has at least 4 rows from canonical labels | PASS | L175-L185 | — |
| CR-028 | §5 UX Flow Notes references screenshots inline — no separate Screenshots section | PASS | L185-L195 | — |
| CR-029 | §6 Key Patterns distinguishes table-stakes vs. differentiation | PASS | L195-L200 | — |
| CR-030 | Output ends at §7 — no Jira tickets generated, no meta-commentary | PASS | L200-L244 | — |
| CR-031 | Inferred (not asked) block appears at top when Phase A inferred at least one field | PASS | L165-L175 | — |

### F. Depth adaptation

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-032 | Quick scan depth → 3–5 opportunities, screenshots optional | PASS | L143-L145 | — |
| CR-033 | Detailed comparison → full matrix + key-surface screenshots + prioritized recs | PASS | L145-L147 | — |
| CR-034 | Deep UX flow → per-competitor step-by-step + friction + every-screen screenshots + side-by-side + experiments | PASS | L147-L148 | — |

### G. Handoff & MCP integration

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-035 | Ready To Gamble On It? presented with exactly 2 options: Bet on it + Hold the chip | PASS | L226-L230 | — |
| CR-036 | Bet on it + atlassian MCP → Confluence create with PKB spaceId/parentId and markdown format | PASS | L234-L238 | — |
| CR-037 | After Confluence publish, surfaces one-line note: screenshots are local-only | PASS | L239 | — |
| CR-038 | Markdown saved to ~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md with co-located screenshots subdir | PARTIAL | L224 | Path co-location bug — .md sits at parent dir, screenshots subdir lives inside `<focus-slug>/` child dir, so relative `screenshots/...` refs in the .md will not resolve. |

### H. Quality & specificity

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-039 | Findings are specific, cite source, and call out missing/inaccessible pages | PASS | L205-L220 | Spec gap — L141 mentions respecting robots.txt but doesn't describe how the skill actually checks it. |

### I. Edge cases & failure modes

| ID | Title | Verdict | SKILL.md ref | Key finding |
|---|---|---|---|---|
| CR-040 | Memory edge cases: differs (confirm inline) / empty (cache after Phase B) / Playwright off / robots.txt | PARTIAL | L247 + L211 + L141 | Bundles 4 sub-criteria; 2 PASS, 2 PARTIAL — see breakdown. |

**CR-040 sub-criteria breakdown:**
- **Memory DIFFERS → confirm inline:** PARTIAL — mechanism works, but L247 doesn't specify the inline confirmation message format or the explicit [y/N] choice.
- **Memory EMPTY → cache after Phase B:** PASS — L211 + L243 logic extends cleanly; append `**Competitors:**` after Phase B answer.
- **Playwright unavailable → degrades gracefully:** PASS — §1 Research Scope notes "Playwright not available — no screenshots captured" per L141.
- **Robots.txt blocked → inline note:** PARTIAL — L141 mentions respecting robots.txt but doesn't describe enforcement mechanism (Playwright doesn't enforce natively).

## Actionable Items

### P0 — Phase A vs Phase B memory-substitution path conflict

**Affected tests:** CR-016
**Location:** `skills/competitor-research/SKILL.md:L69` + `L86`
**Symptom:** L69 says Phase A infers Competitors from memory and skips the Targets question. L86 says Phase B's Targets question label substitutes memory names at runtime. The two paths are mutually exclusive — if Phase A always infers from memory, Phase B never asks Targets and the substitution rule is unreachable.
**Proposed edit:**

```
| **Competitors** | If active product memory (`~/.claude/memory/<project-slug>.md`) has a `**Competitors:**` line → present the Phase B Targets question with the memory names substituted into the "Memory default" option so the PM can confirm or override. If user named specific competitors in the prompt → use those (skip the question). Otherwise ask without a Memory default option. |
```

Plus on L86: keep the substitution rule and clarify it is the confirm-the-cached-list path.

### P0 — Screenshot path co-location breaks relative references

**Affected tests:** CR-038 (and any deep-UX case that ships an .md with inline screenshot refs)
**Location:** `skills/competitor-research/SKILL.md:L224` + `L133`
**Symptom:** L224 saves the markdown at `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` but L133 stores screenshots at `~/Downloads/competitor-research/<focus-slug>/screenshots/<file>.png`. The `<focus-slug>/` directory is a sibling of the .md, not a parent — so the relative `![](screenshots/...)` references inside the .md resolve to `~/Downloads/competitor-research/screenshots/...`, which does not exist. The "self-contained bundle" promise on L134 breaks the moment the PM opens the .md.
**Proposed edit:**

```
Write the full report markdown to `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. Screenshots live in `~/Downloads/competitor-research/<focus-slug>/screenshots/<competitor>-<page>.png` so the relative `![](screenshots/...)` references in the markdown resolve.
```

### P0 — Memory-differs confirmation message and robots.txt enforcement underspecified

**Affected tests:** CR-040 (DIFFERS + ROBOTS.TXT sub-criteria)
**Location:** `skills/competitor-research/SKILL.md:L247` + `L141`
**Symptom:** L247 says "confirm inline" when runtime competitor list differs from memory but doesn't define the exact message format or the [y/N] update-memory choice. L141 says "respect robots.txt" but doesn't describe how the skill actually fetches and parses robots.txt (Playwright doesn't enforce it natively).
**Proposed edit (L247):**

```
When the PM provides a competitor list at runtime that DIFFERS from the cached memory list, do NOT overwrite silently. Surface one inline message of the form: `Cached competitors in ~/.claude/memory/<slug>.md are <cached list>; you asked about <runtime list>. Update memory to use <runtime list> going forward? [y/N]`. If [y], replace the **Competitors:** line; if [N] (default), proceed with the runtime list for this run only and keep memory unchanged.
```

**Proposed edit (L141):**

```
Respect robots.txt: before navigating any competitor page, fetch the site's `/robots.txt` (via Playwright's request API or a direct HTTP fetch tool if available) and check whether the target path is allowed for User-agent: *. If disallowed, geo-blocked (HTTP 451), or returning 403/429, note `couldn't access <page> — <cause>` in §1 Research Scope and skip the page. Continue with the remaining accessible pages.
```

### P1 — Frontmatter description does not name the canonical output type

**Affected tests:** CR-003
**Location:** `skills/competitor-research/SKILL.md` frontmatter (description field)
**Symptom:** Description names "structured competitor research" and "competitive insights" but does not contain the literal phrase "7-section comparison report" nor explicitly say "research-only — does NOT create Jira tickets". The constraint sits in body L242-L244 rather than the discoverable description.
**Proposed edit:**

```
description: Use when the user wants competitor research. Returns a lean 7-section comparison report adapted to depth and company format. Research-only — does NOT create Jira tickets.
```

### P1 — Robots.txt enforcement mechanism unspec'd

**Affected tests:** CR-039 (also reinforced by CR-040 sub-criterion)
**Location:** `skills/competitor-research/SKILL.md:L141`
**Symptom:** Spec mentions respecting robots.txt but doesn't describe how the skill checks it. Same root cause as P0 item (L141) — listed here as the standalone fix when only the robots.txt half is addressed.
**Proposed edit:** see P0 (L141) replacement above.

### P2 — Phase A inference table omits common research-topic keywords

**Affected tests:** CR-009 (KYC; minor)
**Location:** `skills/competitor-research/SKILL.md:L68-L72`
**Symptom:** The Focus inference table enumerates onboarding/pricing/homepage/checkout/named-feature but omits compliance/KYC/responsible-gaming keywords, so trace authors have to lean on the implicit "named feature surface" bucket.
**Proposed edit:**

```
| **Focus** | "signup", "registration", "onboarding" → Onboarding. "pricing", "tiers", "promo", "bonus" → Pricing. "homepage", "landing" → Homepage. "checkout", "deposit", "withdraw" → Checkout flow. "KYC", "AML", "responsible gaming", "compliance" → Compliance. Named feature surface (e.g. "game lobby", "VIP page") → Core feature experience. |
```

### P2 — No Confluence-attachment offer after publish

**Affected tests:** CR-037 (documentation gap, not a defect)
**Location:** `skills/competitor-research/SKILL.md:L239`
**Symptom:** Skill warns user that Confluence images render broken but doesn't offer to upload screenshots as Confluence page attachments.
**Proposed edit (optional enhancement):**

```
After the call, surface a one-line note: `Screenshots are local-only at <path>; the Confluence page's inline image references will render as broken — open the local .md to see them rendered. Want me to upload the screenshots as Confluence page attachments? [y/N]`
```

## Catalog Quality Notes

The catalog is well-structured but has two issues worth surfacing for the next iteration:

1. **CR-002 judge misread (FAIL is spurious).** The raw judge flagged the frontmatter `description` field as starting with "Run structured competitor research…" — but that text is from the body `## Purpose` header on L9, not the YAML frontmatter on L3. The frontmatter `description:` does start with "Use when…". This appears as a FAIL in the raw run but should be ignored: the underlying skill is correct, the judge confused two different parts of the file. Not promoted to an actionable item.

2. **CR-025 catalog drift (FAIL is on the catalog, not the skill).** The test asserts §2 = "Methodology" and §3 = "Competitor Snapshots", but SKILL.md L170-L175 canonically defines §2 = "Competitors Reviewed" and §3 = "Executive Summary". Because SKILL.md is the ground truth, the case is wrong, not the skill. The fix is to update `tests/competitor-research/cases/CR-025.yaml` to match the spec, or to deliberately reshape the spec if leadership prefers the catalog's section names (the raw run notes "Methodology"/"Competitor Snapshots" arguably have clearer semantics).

3. **Depth-adaptation cases (CR-032/033/034) are too forgiving.** All three pass trivially because the trace authors describe the shape they want rather than producing a real artifact. Adding assertions for concrete count thresholds (e.g. "deep UX must reference ≥8 screenshots inline") would tighten the signal.

4. **CR-040 bundles four sub-criteria.** This is fine for narrative coverage but compresses real defects into a single PARTIAL row. Splitting into CR-040a..d would give the dashboard finer-grained insight into which edge case is failing.

5. **Phase B "Memory default" substitution case (CR-016)** is the most valuable test in the catalog — it exposed a genuine spec conflict between L69 and L86 that wouldn't have surfaced in PASS-only happy-path cases.

## Cross-Skill Notes

competitor-research is research-only — its output is consumed downstream by `prd-writer` (for new initiatives) and `ticket-builder` (for individual gap items). Observations:

- **§7 Gaps & Opportunities is structurally clean enough to feed downstream skills.** Each gap follows the "**Missing:** … **Why it matters:** … **Action:** …" tri-part pattern (see CR-001 artifact L92-L94). A PRD writer can lift "Missing/Why it matters" into the PRD problem statement and "Action" into the solution direction with minimal rework.

- **One handoff hint worth adding to SKILL.md:** explicitly tell the user how to chain to prd-writer/ticket-builder. After "Saved at <path>. No Confluence page created.", suggest: `Next: feed any §7 gap into /casino-skilo:prd-writer (for a full initiative) or /casino-skilo:ticket-builder (for a single ticket).` This makes the research→action pipeline discoverable without forcing competitor-research itself to violate the no-Jira rule.

- **The Confluence page (when published) is the canonical artifact for PRD writers to cite.** The local .md is the rendered version (with images); the Confluence page is the durable index. If prd-writer pulls competitor context, it should reference the Confluence URL, not the local path.

## Out of Scope for This Report

- Real Playwright runs against live competitor sites — no scraping was performed; case preconditions stub the Playwright tool state.
- Real Confluence MCP calls.
- Modifying any SKILL.md.
- Verifying the PKB space/parent IDs are still valid.
