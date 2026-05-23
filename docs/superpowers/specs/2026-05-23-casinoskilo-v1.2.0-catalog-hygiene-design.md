# CasinoSkilo v1.2.0 — Test Catalog Hygiene

**Date:** 2026-05-23
**Author:** Tal Shani (designed in session)
**Status:** Approved (catalog-only scope)
**Plugin version:** stays at `1.1.0` (no SKILL.md changes — the catalog version diverges from the plugin version starting at v1.2.0)

## Context

v1.1.0 shipped 24 SKILL.md spec changes that resolved every actionable item from the v1.0.0 audit. The post-fix re-run hit 119/120 PASS. But the test catalog itself still has gaps that v1.1.0 didn't address:

1. **CR-025 catalog drift** — case YAML asserts `§2 = "Methodology"` and `§3 = "Competitor Snapshots"`, but the spec canonically says `"Competitors Reviewed"` / `"Executive Summary"`. The case is wrong, not the skill. It's the lone PARTIAL holding CR back from a perfect 40/0/0.
2. **No coverage for v1.1.0 additions** — the 120 cases were authored against v1.0.0 and grade v1.1.0 by inheritance only. New behaviors (Phase A `Needs flow diagram` field, Retention Main problem value, GGR `revenue` sub-tag, 25-child Double-down cap, memory-differs 3-option question, Confluence-attachment offer, parentId 404 retry, etc.) aren't directly exercised.
3. **CR-040 bundles 4 sub-rules** — DIFFERS / EMPTY / PLAYWRIGHT-off / ROBOTS-blocked are graded as a single case. The aggregator demoted CR-040 to PARTIAL when one sub-rule was weak, masking the others. Splitting into 4 standalone cases gives cleaner per-rule grading.
4. **Judge-misread class** — v1.0.0 CR-002 was graded FAIL because the judge confused the body `## Purpose` header with the frontmatter `description` field. A static frontmatter check in the rubric (pre-runner) would catch this before the LLM-graded stage.

Nothing in scope changes skill behavior. The plugin distribution stays at 1.1.0. v1.2.0 is a **repo-scoped tag** marking the test catalog version, not a new plugin release. Downstream users see no behavior change; the harness gets sharper.

## Goals

1. Fix CR-025 case YAML to assert canonical §2/§3 section names. CR re-runs to 40/0/0.
2. Author ~22 new test cases (TB-041…TB-049 + PRD-041…PRD-047 + CR-041…CR-046) covering each v1.1.0 behavior.
3. Split CR-040 into 4 standalone cases (CR-040 rewritten as "differs only" + CR-047/048/049 for empty/Playwright-off/HTTP-block).
4. Add a `## Static checks` section to the rubric — describes pre-runner frontmatter / SKILL.md structure checks the harness runs before invoking the LLM-graded stage.
5. Re-run the full v1.2.0 catalog (now ~145 cases) against the v1.1.0 SKILL.md to confirm: all new cases PASS, no regressions to existing cases.
6. Commit + push + tag `v1.2.0`. Update `CHANGELOG.md` with a `[Unreleased]` → `[1.2.0]` catalog-only entry.

## Non-Goals

- No SKILL.md edits.
- No `plugin.json` version bump (stays at `1.1.0`).
- No live MCP smoke test.
- No catalog re-architecture (keep YAML + sub-agent dispatch).
- No CI/automation harness — execution stays in-session sub-agent dispatch.
- The 3 deferred skills under `skills-deferred/` stay deferred.

## Design

### Per-skill new cases

#### ticket-builder (TB-041 … TB-049 — 9 new cases)

| ID | Tests | References |
|---|---|---|
| TB-041 | Phase A infers `Needs flow diagram = Yes` from "new feature" signal | TB-Δ-1, [`skills/ticket-builder/SKILL.md:L61`](../../skills/ticket-builder/SKILL.md#L61) |
| TB-042 | Phase A infers `Needs flow diagram = No` from "bug" + "config" signals (artifact omits `## User Flow` entirely) | TB-Δ-1, L150 |
| TB-043 | Phase A does NOT infer `Needs flow diagram` for ambiguous input; Phase C emits the `Flow?` fallback with 3 spec'd options | TB-Δ-1, L106-114 |
| TB-044 | DoD hard cap enforced — input that would naïvely produce 8 items is trimmed to ≤5 | TB-Δ-2, L155 |
| TB-045 | Inferred-block 4-bullet cap — input where Phase A infers all 5 fields produces 4 bullets + `_(+1 more inferred)_` overflow | TB-Δ-3, L139 |
| TB-046 | "Assume + flag" inline syntax matches the spec'd format `> **Assumption:** … **Flag:** …` | TB-Δ-6, L104 |
| TB-047 | Phase A conflict rule — input "fix the new feature on iOS" leaves Ticket type Not inferred (falls through to Phase B) | TB-Δ-7, L53 |
| TB-048 | PRD-driven mode — `invoking_skill: prd-writer:double-down` precondition produces zero questions, all 5 fields inferred from PRD body with `from PRD §N` citations | TB-Δ-8, L186-198 |
| TB-049 | PRD-driven mode — thin §12 row defaults to `Task` type with inline `> **Open:**` flag | TB-Δ-8, L194 |

#### prd-writer (PRD-041 … PRD-047 — 7 new cases)

| ID | Tests | References |
|---|---|---|
| PRD-041 | Phase A infers `Main problem = Retention / re-engagement` from "re-engage lapsed" signal | PRD-Δ-3, [`skills/prd-writer/SKILL.md:L57`](../../skills/prd-writer/SKILL.md#L57) |
| PRD-042 | Phase A surfaces `vip` tag on Main user when input names "VIP players" | PRD-Δ-2, L56 |
| PRD-043 | Phase A surfaces `crm` tag on Main user when input names "CRM operator" + lifecycle | PRD-Δ-2, L56 |
| PRD-044 | Phase A applies GGR `revenue` sub-tag in §10 Primary Metric when input mentions "NGR" / "ARPU" | PRD-Δ-6, L58 |
| PRD-045 | Phase A conflict rule — input "v2 of raffles from scratch" leaves Maturity Not inferred | PRD-Δ-4, L52 |
| PRD-046 | Double-down chain with 26+ §12 rows triggers the chain-too-long AskUserQuestion before any Jira call | PRD-Δ-8, L205-213 |
| PRD-047 | Confluence parentId 404 → retry without parentId, report which space-root the page landed at | PRD-Δ-7, L189 |

#### competitor-research (CR-040 rewrite + CR-041 … CR-049 — 6 new + 3 split)

CR-040 today bundles 4 sub-rules (DIFFERS / EMPTY / PLAYWRIGHT-off / ROBOTS-blocked). Split into 4:

| ID | Tests | References |
|---|---|---|
| CR-040 (rewritten) | Memory-differs only — runtime input names competitors that differ from cache; skill emits the 3-option AskUserQuestion (Use cached / Use runtime + update / Use runtime, keep memory) | CR-Δ-3, [`skills/competitor-research/SKILL.md:L255-263`](../../skills/competitor-research/SKILL.md#L255) |
| CR-041 | Phase A canonical memory reuse — memory has `**Competitors:**` line; Phase A infers Competitors; Phase B skipped | CR-Δ-1, L69 |
| CR-042 | Phase A trust-signal keywords — input "trust signals" / "social proof" → Focus = Core feature experience | CR-Δ-6, L68 |
| CR-043 | Screenshot path co-location — markdown saved at `~/Downloads/competitor-research/<slug>/<slug>-<date>.md` (NOT the legacy flat path) so relative `![](screenshots/...)` references resolve | CR-Δ-2, L232 |
| CR-044 | Confluence-attachment offer — after `Bet on it` with N≥1 screenshots, skill presents the `Attach screenshots?` AskUserQuestion with 2 options | CR-Δ-7, L242-250 |
| CR-045 | HTTP 403/451/CAPTCHA detection — Playwright run hits a 451 page; skill notes `couldn't access <page> — 451` inline and continues | CR-Δ-4, L141 |
| CR-046 | Phase A vs Phase B memory path — Phase B Competitors question label uses the runtime fallback ONLY when memory is empty AND user didn't name competitors (negative case for CR-041) | CR-Δ-1, L92 |
| CR-047 | Memory cached after Phase B — empty memory → Phase B asks → answer appended as `**Competitors:**` line (formerly CR-040 sub-rule 2) | L211, L247 |
| CR-048 | Playwright unavailable — `mcp_state: none` produces report without screenshots; §1 Research Scope notes "Playwright not available" (formerly CR-040 sub-rule 3) | L127-134, L208 |
| CR-049 | (reserved — no v1.1.0 behavior currently maps here; placeholder for v1.3.0 backfill or remove) |

### CR-025 fix (not a new case — edit the existing YAML)

Update [`tests/competitor-research/cases/CR-025.yaml`](../../tests/competitor-research/cases/CR-025.yaml) `pass_criteria` block:

```yaml
# BEFORE
pass_criteria:
  - id: cr-output-has-required-sections
    sections: ["Methodology", "Competitor Snapshots", "Recommendations"]

# AFTER
pass_criteria:
  - id: cr-output-has-required-sections
    sections: ["Research Scope", "Competitors Reviewed", "Executive Summary", "Comparison Table", "UX Flow Notes", "Key Patterns", "Gaps & Opportunities"]
```

(The exact `before` text depends on what the case currently asserts; the goal is to align it with the canonical 7 section names at [`skills/competitor-research/SKILL.md:L167-200`](../../skills/competitor-research/SKILL.md).)

### Rubric addition — Static checks section

Append a new section to [`tests/rubric/pass-criteria-vocabulary.md`](../../tests/rubric/pass-criteria-vocabulary.md):

```markdown
## L — Static checks (pre-runner)

These checks run on the SKILL.md file directly, before the runner sub-agent is dispatched. They catch issues that the LLM-graded stage might miss (e.g. confusing body headers with frontmatter `description`).

### `static-frontmatter-parses-as-yaml`
Read the SKILL.md, extract the block between the first two `---` lines, verify it parses as valid YAML and contains `name:` and `description:` fields.

### `static-description-starts-with-use-when`
The frontmatter `description:` value (NOT the body's `## Purpose` section) begins with the literal phrase `Use when`.

### `static-description-includes-output-noun`
The frontmatter `description:` value contains the skill's canonical output noun phrase (e.g. "Jira-ready ticket", "PRD", "comparison report").

### `static-required-h2-headings-present`
The SKILL.md body contains all the required H2 headings for this skill (e.g. ticket-builder needs `## Purpose`, `## When to use`, `## Context to gather`, `## Adaptive questions`, `## Output`, `## Handoff`, `## Quality rules`).
```

These don't replace the runner+judge stages — they augment them. Each case can mix static and behavioral criteria.

### Re-run plan

After authoring the new cases + fixing CR-025:

1. Re-dispatch 3 parallel sub-agents (same pattern as v1.1.0 run) against the now-145-case catalog.
2. Each sub-agent reads the v1.1.0 SKILL.md (unchanged), the case YAMLs (including new ones), and the rubric (including the new Static checks section).
3. Output goes to `reports/raw/<skill>/full-run-v1.2.0.md`.
4. Aggregate into `reports/<skill>-test-report-v1.2.0.md` + `reports/summary-v1.2.0.md`.

### Expected post-v1.2.0 state

| Skill | v1.1.0 (40 cases) | v1.2.0 target (49 / 47 / 49 cases) |
|---|---|---|
| ticket-builder | 40 / 0 / 0 (Green 100%) | 49 / 0 / 0 (Green 100%) |
| prd-writer | 40 / 0 / 0 (Green 100%) | 47 / 0 / 0 (Green 100%) |
| competitor-research | 39 / 1 / 0 (Green 97.5%) | 49 / 0 / 0 (Green 100%) — CR-025 flipped via the YAML fix |

Total target: **145 / 0 / 0 (Green 100%)**.

## Out of Scope

- No SKILL.md edits — the v1.1.0 skill specs are the spec under test, unchanged.
- No new skill behavior, no new option labels, no new tool-lookup patterns.
- No plugin.json version change.
- No GitHub Release UI work (separate task).
- No live MCP smoke test (separate task).
- Live Atlassian PKB space/parent ID verification (separate task).

## Approval

Approved in session — proceed directly to writing-plans skill output.
