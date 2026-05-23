# CasinoSkilo v1.1.0 — Skill Updates & Brevity Redesign

**Date:** 2026-05-23
**Author:** Tal Shani (designed via brainstorming session with Claude)
**Status:** Draft — awaiting user review before plan
**Target plugin version:** `1.1.0` (current: `1.0.0`)

## Context

CasinoSkilo v1.0.0 ships three PM skills (ticket-builder, prd-writer, competitor-research). A 120-case behavioral test run on 2026-05-23 found 18 actionable items: 4 P0, 5 P1, 9 P2. Two real bugs surfaced (competitor-research screenshot path co-location; prd-writer ↔ ticket-builder cross-skill contract gap). See [`reports/summary.md`](../../../reports/summary.md) for the full audit.

Separately, the user identified a brevity-drift problem in ticket-builder: tickets routinely overshoot the "lean" rule the spec promises. Root cause is **enforcement** (the spec mentions caps but doesn't force them), not a flawed design principle. Confirmed during brainstorming that humans (not LLM agents) consume these tickets, so the "lean" rule is correct as-is — we just need to enforce it harder.

This spec defines the v1.1.0 changes that resolve both: the audit-driven fixes and the brevity-drift fixes.

## Goals

1. Apply the 4 P0 fixes (cross-skill contract + competitor-research path/conflict/spec gaps).
2. Apply all 5 P1 fixes (Phase A inference table gaps in prd-writer; description ordering in competitor-research).
3. Apply the 9 P2 polish items.
4. Enforce ticket-builder brevity with hard caps on Definition of Done and Inferred block, plus opt-in User Flow.
5. Bump plugin version to `1.1.0` and redeploy via `/plugin update`.
6. Re-run the test catalog against v1.1.0 and confirm targeted PARTIAL/FAIL cases flip to PASS without regressions.

## Non-Goals

- No new skill in v1.1.0. The three deferred skills (product-discovery, experiment-planner, ux-copy) stay deferred.
- No changes to the four-phase architecture (Phase A → B → C → D). Edits are surgical within phases.
- No changes to the Atlassian PKB space ID (`772571142`) or parent page ID (`772571521`) — those remain hardcoded per spec.
- No automated CI test-runner. The harness stays sub-agent dispatch in-session.

## Design

### Architecture (unchanged)

Three SKILL.md files in `skills/<skill>/SKILL.md`. Each file is the canonical spec. Plugin metadata at `.claude-plugin/plugin.json`. Source-of-truth on GitHub at `talshani8499-netizen/CasinoSkilo`; `/plugin update CasinoSkilo` refreshes the local plugin cache from GitHub.

### Per-skill changes

#### ticket-builder (current: 169 lines → projected: ~210 lines)

##### TB-Δ-1 — User Flow becomes optional via Phase A heuristic
**Where:** Phase A signal table (`SKILL.md:L55-L60`) and Output template (`L138-L139`).
**What:** Add a 5th inferred field `Needs flow diagram`.

Inference signals (new row in the L55 table):
| Signal | Inference |
|---|---|
| "bug", "copy change", "content tweak", "analytics-only", "config", "toggle" | `No` (skip §User Flow) |
| "new feature", "new flow", "navigation change", "multi-step", "admin task" | `Yes` |
| Anything else | Not inferred → fall through to Phase C |

Phase C addition (only if Phase A didn't infer): one AskUserQuestion with header `Flow?`:
- `Yes — happy path only`
- `Yes — with branches and decisions`
- `No — skip the flow diagram`

Output template change: when `Needs flow diagram = No`, the `## User Flow` heading and code block are **omitted entirely** (not rendered as "N/A" or empty).

##### TB-Δ-2 — Definition of Done hard cap: 3–5 items
**Where:** Output template (`SKILL.md:L141-L143`).
**What:** Replace `[DoD item 1] / [DoD item 2]` placeholders with: *"3–5 items. Never 6+. If you can't write 3 essential items, name the gap. If you wrote 6+, cut non-essential ones — the ticket is not a QA test plan."*

##### TB-Δ-3 — Inferred (not asked) hard cap: 4 bullets
**Where:** Output template (`SKILL.md:L128-L130`) and Phase D narrative (`L116`).
**What:** When Phase A inferred 5+ fields (now possible because of TB-Δ-1's new field), surface the 4 most-actionable in the block and append a single italic line: `_(+N more inferred — see context for full set)_`. "Most-actionable" priority order: Ticket type > Connection > Main user > Main goal > Needs flow diagram.

##### TB-Δ-4 — Description: guidance, not hard cap
**Where:** Output template (`SKILL.md:L135-L136`).
**What:** Keep "2–4 sentences" guidance. Append a soft audit hint: *"If your description exceeds 4 sentences, audit whether you've smuggled in Background, Rationale, or Context that the banned-sections list forbids."* (Per user call — Description stays editorial, not mechanical.)

##### TB-Δ-5 — Clarify Inferred-block placement (from TB-029)
**Where:** Phase D narrative (`SKILL.md:L116`) — currently says "block at the top of the ticket"; template at L121-129 shows it after the 4 metadata header lines.
**What:** Update L116 to: *"Surface the `Inferred (not asked)` block immediately after the 4 metadata header lines (Ticket type / Parent epic / Component / Labels), before `## User Story`. See template below for exact placement."*

##### TB-Δ-6 — Define "assume + flag" syntax (from TB-022)
**Where:** Phase C rule 6 (`SKILL.md:L96` and `L103`).
**What:** Append: *"Inline assumption format: `> **Assumption:** <statement>. **Flag:** <one-line reason this needs confirmation>.` Place inside the relevant Description or DoD bullet, not in a separate section."*

##### TB-Δ-7 — Phase A conflict-resolution rule (mirrors PRD-Δ-3)
**Where:** Phase A narrative (`SKILL.md:L52`).
**What:** Insert: *"When signals from multiple rows fire for the same field (e.g. input contains both 'fix' and 'add new'), mark the field as Not inferred and fall through to Phase B."*

##### TB-Δ-8 — Add `## PRD-driven mode` section (P0, mirrors PRD-Δ-1)
**Where:** New section in `SKILL.md`, placed after `## Quality rules` (after L168).
**What:** New section that authoritatively documents the chain contract that currently lives only in `prd-writer/SKILL.md:L191-L204`:

```markdown
## PRD-driven mode (when chained by prd-writer Double down)

When `prd-writer` invokes this skill as part of its Double-down chain, run in PRD-driven mode:

- **Skip Phase B entirely.** No core questions to the user.
- **Skip Phase C entirely.** No adaptive follow-ups.
- **Phase A infers all 5 core fields from the PRD body.** Every inference must cite the PRD section it came from (e.g. `from PRD §10 FR-2`, `from PRD §8 Functional`). Never invent context.
- **`Inferred (not asked)` block is required** and cites PRD sections for each entry.
- **If the §12 row is too thin to infer a ticket type** (e.g. just "Misc — TBD"), default to type `Task` with an inline `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` line in the Description.
- **At handoff, auto-choose `Bet on it`.** Do NOT call AskUserQuestion. Use the parent epic key supplied by prd-writer.
- **Per-chain question count is exactly zero.** A 14-row §12 produces 14 child tickets with zero user questions.

prd-writer authoritatively governs the upstream contract at `prd-writer/SKILL.md:L191-L204`. This section is the downstream half; the two must stay in sync.
```

#### prd-writer (current: 205 lines → projected: ~230 lines)

##### PRD-Δ-1 — Cross-link to ticket-builder PRD-driven mode (P0)
**Where:** `SKILL.md:L198` (the "Hard instruction to ticket-builder" block).
**What:** Append one sentence: *"This contract is authoritatively documented in `ticket-builder/SKILL.md → PRD-driven mode`. This skill enforces upstream; ticket-builder enforces downstream. The two sections must stay in sync."*

##### PRD-Δ-2 — Expand Main user sub-segment guidance (P1)
**Where:** Phase A signal table (`SKILL.md:L55-L56`).
**What:** Append two sub-segment hints to the `Main user` row (not new option-bank values — just inference guidance):
- *"VIP / high-roller / 'whale' signals → End user with `vip` tag surfaced in User Story."*
- *"CRM operator / campaign manager / 'lifecycle' signals → Admin / internal with `crm` tag surfaced in User Story."*

##### PRD-Δ-3 — Add Retention as a 4th Main problem value (P1)
**Where:** Phase A signal table (`SKILL.md:L57`) and Phase B option bank (`L77-L80`).
**What:**
- Add to signal table: *"'retention', 'lapsed', 're-engage', 'win-back', 'reactivation' → Retention / re-engagement."*
- Add to option bank as a 4th option: `Retention / re-engagement — Re-activate lapsed users or extend lifecycle`.

##### PRD-Δ-4 — Phase A conflict-resolution rule (P1)
**Where:** Phase A narrative (`SKILL.md:L52`, just before the signal table).
**What:** Insert: *"When signals from multiple rows fire for the same field (e.g. input contains both 'we already have' and 'from scratch'), mark the field as Not inferred and fall through to Phase B. Do not invent a tie-break."*

##### PRD-Δ-5 — Add "Double down" verbatim to frontmatter description (P2)
**Where:** Frontmatter `description:` (`SKILL.md:L3`).
**What:** Ensure the literal phrase `"Double down"` appears in the description. Current description names the chain behavior; making the keyword literal helps Claude trigger-match. Suggested wording: *"…optionally chain the **ticket-builder** skill via the **Double down** option to create the Jira epic + child tickets…"*

##### PRD-Δ-6 — GGR / revenue lift sub-tag in Success table (P2)
**Where:** Phase A signal table (`SKILL.md:L58`).
**What:** Refine the `Success signal` row: *"GGR-specific signals ('GGR', 'NGR', 'revenue lift', 'ARPU') → Conversion with `revenue` sub-tag (surfaced in §10 Primary Metric)."*

##### PRD-Δ-7 — Confluence parentId fallback (P2)
**Where:** Handoff `Bet on it` branch (`SKILL.md:L184`).
**What:** Append: *"If create fails with 404 (parent moved/deleted), retry once without `parentId` and report which space-root the page landed at. If second attempt also fails, save markdown locally and report the error — do not silently drop."*

##### PRD-Δ-8 — Cap Double-down chain at 25 children (P2)
**Where:** Notes on Double down chain (`SKILL.md:L204`).
**What:** Append: *"**Cap: 25 child tickets per chain.** If §12 has 26+ rows, abort the chain before any Jira call and prompt: 'Chain length <N> exceeds 25 — split the PRD into multiple sub-PRDs, or use `Bet on it` to publish the Confluence page and create tickets manually.'"*

##### PRD-Δ-9 — Clarify 7-question cap scope (P2)
**Where:** Adaptive questions intro (`SKILL.md:L48`).
**What:** Append: *"The 7-question cap is per single skill invocation by the user. Chained `ticket-builder` calls in PRD-driven mode are zero-question by contract, so the cap is never breached by the chain itself."*

#### competitor-research (current: 248 lines → projected: ~275 lines)

##### CR-Δ-1 — Resolve Phase A vs Phase B memory path conflict (P0)
**Where:** Phase A inference (`SKILL.md:L69`) and Phase B option bank (`L86`).
**What:** Add a clarifying line at L69: *"Phase A is the canonical reuse path — if memory has a `**Competitors:**` line, infer `Competitors` here and skip the Phase B Competitors question entirely. The Phase B memory-substitution label on L86 is a fallback only used when Phase A could not infer Competitors (i.e. memory is empty and the user did not name competitors in the prompt)."*

Append to L86: *"(Fallback path. The primary memory-reuse path is Phase A — see L69.)"*

##### CR-Δ-2 — Fix screenshot path co-location bug (P0)
**Where:** Handoff (`SKILL.md:L224`).
**What:** Change markdown save path from `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` to `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. The `screenshots/` subdir (already at `~/Downloads/competitor-research/<focus-slug>/screenshots/`, per L131) is then a sibling of the .md and the relative `screenshots/<file>.png` references in §5 resolve correctly.

##### CR-Δ-3 — Specify memory-differs confirmation (P0, part 1)
**Where:** Notes on memory caching (`SKILL.md:L247`).
**What:** Replace the vague "confirm with one inline message" with an explicit AskUserQuestion spec:

```markdown
When runtime competitor input differs from the cached list, present this question (do NOT silently overwrite memory):

  - Question: `The cached competitor list differs from your runtime input. Which set should drive this run?`
  - Header: `Competitors?`
  - Options:
    - `Use cached` — Use the cached competitors (<list-from-memory>) and ignore runtime input
    - `Use runtime + update memory` — Use runtime input (<list-from-input>) and overwrite the memory cache
    - `Use runtime, keep memory` — Use runtime input just for this run; leave cache untouched
```

##### CR-Δ-4 — Drop robots.txt enforcement claim (P0, part 2)
**Where:** Playwright strict limits (`SKILL.md:L141`).
**What:** Replace L141 — *"Respect robots.txt; if blocked, note 'couldn't access <page>' in the report and skip"* — with: *"Public pages only. If a page returns HTTP 403/451 or shows a CAPTCHA / bot-detection wall, note `couldn't access <page> — <reason>` inline in §5 UX Flow Notes and skip. This skill does not perform robots.txt pre-flight (Playwright does not enforce robots.txt natively); rely on the page response."*

##### CR-Δ-5 — Reorder frontmatter description (P1)
**Where:** Frontmatter `description:` (`SKILL.md:L3`).
**What:** Move the canonical noun phrase ("returns a lean 7-section comparison report") earlier in the sentence — within the first 15 words — to maximize Claude trigger-match. Suggested rewording: *"Use when a PM wants a structured competitor research report. Returns a lean 7-section comparison report. Reads competitor list from auto-memory, scans Jira/Confluence for company baseline…"*

##### CR-Δ-6 — Add trust-signal keywords to Phase A Focus row (P2)
**Where:** Phase A signal table (`SKILL.md:L68`).
**What:** Append to the Focus row: *"'trust signals', 'social proof', 'reviews', 'ratings', 'badges' → Core feature experience (trust surface)."*

##### CR-Δ-7 — Confluence-attachment offer for screenshots (P2)
**Where:** Handoff `Bet on it` branch (`SKILL.md:L239`).
**What:** Append a new step: *"After surfacing the screenshots-local-only note, if N ≥ 1 screenshots exist, present one AskUserQuestion: `Upload <N> screenshots to the Confluence page as attachments? (fixes the inline image references)` with options `Upload all` / `Upload none`. If `Upload all`, iterate the screenshots/ directory and attach each via the Atlassian MCP's create-attachment tool; rewrite the inline `![desc](screenshots/<file>.png)` references to point at the Confluence attachment URLs."*

### Plugin metadata change

##### PJ-Δ-1 — Version bump
**Where:** `.claude-plugin/plugin.json` and new `CHANGELOG.md` at repo root.
**What:**
- Bump `version: "1.0.0"` to `version: "1.1.0"` in `.claude-plugin/plugin.json`.
- Create `CHANGELOG.md` at repo root using the Keep-a-Changelog format. v1.1.0 entry sections: `### Added` (Retention Main problem value, PRD-driven mode section in ticket-builder, Confluence-attachment offer in competitor-research), `### Changed` (User Flow gating, DoD cap, Inferred-block cap, screenshot path), `### Fixed` (Phase A/B memory conflict, Inferred placement, robots.txt overclaim).

### Redeploy mechanism

1. **Edit in plugin cache as scratch.** All edits live in `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/<skill>/SKILL.md`. This is the active spec — edits take effect immediately on next skill invocation, before any commit/push.
2. **Mirror edits into the GitHub repo** at `/Users/talshani/Documents/GitHub/CasinoSkilo/skills/<skill>/SKILL.md` (the repo is currently empty; this is the initial commit of the production plugin).
3. **Commit 1 (production plugin):** `feat(skills): apply test-driven fixes + brevity redesign (v1.1.0)` — includes `skills/`, `skills-deferred/`, `.claude-plugin/`, `LICENSE`, `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, `.gitignore`.
4. **Commit 2 (test harness):** `test: add 120-case behavioral test catalog + v1.0.0 audit reports` — includes `tests/`, `reports/`, `docs/`.
5. **Push both** to `talshani8499-netizen/CasinoSkilo` main.
6. **`/plugin update CasinoSkilo`** in local Claude Code to refresh the plugin cache from GitHub.
7. **Re-run the test catalog** against v1.1.0. Aim: TB stays Green; PRD flips Yellow → Green; CR flips Yellow → Green.
8. If regressions appear, hotfix locally, re-run, then publish as v1.1.0 GitHub release.

### Data flow & error handling

- **Spec edits are text-only.** No data flow changes. No new external dependencies.
- **The path-co-location fix (CR-Δ-2) is the only file-system-affecting change.** Existing competitor-research outputs saved at the old path will not be migrated; users running v1.1.0 will save new reports at the new path while old reports stay where they are.
- **Confluence parentId fallback (PRD-Δ-7)** is graceful — if both attempts fail, the markdown file is still saved. No data loss.

### Testing strategy after v1.1.0

The test catalog at `tests/` re-runs unchanged. The expected delta vs the v1.0.0 baseline:

| Skill | v1.0.0 baseline | v1.1.0 target | Cases that should flip |
|---|---|---|---|
| ticket-builder | 39 / 1 / 0 Green | 40 / 0 / 0 Green | TB-029 (Inferred placement) flips PARTIAL→PASS via TB-Δ-5 |
| prd-writer | 32 / 8 / 0 Yellow | ~38 / 2 / 0 Green | All 8 PARTIALs should flip to PASS or improve; cross-skill contract P0 resolved by TB-Δ-8 + PRD-Δ-1 |
| competitor-research | 34 / 4 / 2 Yellow | ~38 / 2 / 0 Green | CR-038 (path bug) flips via CR-Δ-2; CR-016 (memory conflict) flips via CR-Δ-1; CR-002/CR-025 stay as catalog-drift notes |

After the re-run, the per-skill reports + summary.md get regenerated and committed as a follow-up. Any regressions or unexpected new FAILs trigger a hotfix patch before v1.1.0 is tagged as a GitHub release.

## Out of Scope

- Migration of existing competitor-research outputs from the old to new path.
- Live Atlassian MCP testing — all MCP behavior in the test re-run remains stubbed.
- Verification that PKB space/parent IDs (`772571142` / `772571521`) are still valid in the live Confluence instance.
- Building a CI gate that runs the test catalog on every PR.
- New cases for the catalog covering v1.1.0 additions (new Phase A `Needs flow diagram` field, new Phase B Retention option, etc.) — these should be added in v1.2.0 testing scope.

## Open Items

None. All design decisions are pinned.

## Approval

Once the user reviews this spec and confirms (or requests edits), the next step is to invoke the `writing-plans` skill to produce the executable implementation plan: file-by-file edit list, commit boundaries, push sequence, re-test invocation.
