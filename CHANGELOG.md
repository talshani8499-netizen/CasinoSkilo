# Changelog

All notable changes to the CasinoSkilo plugin follow the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format and adhere to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] — 2026-05-23

### Added
- **prd-writer:** `Retention / re-engagement` as a 4th value for the `Main problem` core question. Triggered by keywords "retention", "lapsed", "re-engage", "win-back", "reactivation". (PRD-Δ-3)
- **prd-writer:** Sub-segment hints on the `Main user` Phase A row — VIP / high-roller signals add a `vip` tag in the User Story; CRM operator / lifecycle signals add a `crm` tag. (PRD-Δ-2)
- **prd-writer:** Hard cap of 25 child tickets per Double-down chain, with an explicit AskUserQuestion when §12 has 26+ rows. (PRD-Δ-8)
- **ticket-builder:** New `## PRD-driven mode` section mirrors the cross-skill contract that previously lived only in `prd-writer/SKILL.md`. (TB-Δ-8)
- **ticket-builder:** New 5th Phase A inferred field `Needs flow diagram` — auto-skips `## User Flow` for bugs/copy/config tickets, requires it for new features and multi-step admin tasks; ambiguous cases trigger a Phase C `Flow?` question. (TB-Δ-1)
- **competitor-research:** Bonus AskUserQuestion after Confluence publish offering to upload screenshots as Confluence attachments. (CR-Δ-7)
- **competitor-research:** Trust-signal keywords ("trust signals", "social proof", "reviews", "ratings", "badges") in the Phase A Focus row. (CR-Δ-6)

### Changed
- **ticket-builder:** `## User Flow` is now optional (driven by the new `Needs flow diagram` Phase A inference). (TB-Δ-1)
- **ticket-builder:** Definition of Done now has a hard cap of 3–5 items (never 6+). (TB-Δ-2)
- **ticket-builder:** `Inferred (not asked)` block now has a hard cap of 4 bullets; if Phase A inferred 5+ fields, the 4 most-actionable are shown with a `_(+N more inferred)_` overflow line. (TB-Δ-3)
- **ticket-builder:** Description guidance now includes a soft audit hint reminding the writer to check for smuggled-in banned sections. (TB-Δ-4)
- **competitor-research:** Markdown save path changed from `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md` to `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. The `screenshots/` subdir is now a sibling of the markdown file so relative image references resolve correctly. (CR-Δ-2)
- **prd-writer:** Frontmatter description now contains the literal phrase "Double down" for better trigger matching. (PRD-Δ-5)
- **competitor-research:** Frontmatter description reordered so "returns a lean 7-section comparison report" appears within the first 15 words. (CR-Δ-5)

### Fixed
- **ticket-builder + prd-writer:** Cross-skill contract gap — the `PRD-driven mode` rule that governs ticket-builder during Double-down chains is now documented in both SKILL.md files with explicit cross-links. (TB-Δ-8, PRD-Δ-1)
- **ticket-builder:** `Inferred (not asked)` block placement narrative on L116 now matches the template (immediately after metadata header lines, before `## User Story`). (TB-Δ-5)
- **ticket-builder:** "Assume + flag" inline syntax is now explicitly defined: `> **Assumption:** <statement>. **Flag:** <reason>`. (TB-Δ-6)
- **prd-writer + ticket-builder:** Phase A conflict-resolution rule added — when signals from multiple table rows fire for the same field, the field falls through to Phase B unanswered. (PRD-Δ-4, TB-Δ-7)
- **prd-writer:** Confluence create-page now retries once without `parentId` on HTTP 404 before falling back to the markdown-only path. (PRD-Δ-7)
- **prd-writer:** The 7-question cap is now explicitly per-invocation, not per-chain. (PRD-Δ-9)
- **prd-writer:** GGR signals (GGR/NGR/revenue lift/ARPU) now flag a `revenue` sub-tag in §10 Primary Metric instead of being silently conflated with generic Conversion. (PRD-Δ-6)
- **competitor-research:** Phase A vs Phase B memory-substitution path conflict resolved — Phase A is the canonical reuse path; Phase B substitution is the fallback. (CR-Δ-1)
- **competitor-research:** Memory-differs handling now uses an explicit 3-option AskUserQuestion instead of a vague "confirm with one inline message". (CR-Δ-3)
- **competitor-research:** robots.txt enforcement claim dropped — the skill instead reacts to HTTP 403/451 or CAPTCHA walls in §5 UX Flow Notes. (CR-Δ-4)

### Test catalog
- 120-case behavioral test catalog added to `tests/` (40 cases per skill) with rubric, coverage maps, and per-skill execution reports under `reports/`.
- v1.0.0 baseline: ticket-builder 39/1/0 Green, prd-writer 32/8/0 Yellow, competitor-research 34/4/2 Yellow.
- v1.1.0 target: all three skills Green ≥ 95% PASS.

## [1.0.0] — 2026-05-22

### Added
- Initial release: three PM skills — ticket-builder, prd-writer, competitor-research.
- Four-phase adaptive interview architecture (Phase A inference → Phase B core questions → Phase C ≤3 follow-ups → Phase D output).
- "Ready To Gamble On It?" handoff with Bet on it / Hold the chip / Double down (PRD-only) options.
- Atlassian MCP integration for Jira ticket creation and Confluence page publishing to the Product Knowledge Base space.
- Three deferred skills under `skills-deferred/` (product-discovery, experiment-planner, ux-copy).
