# CasinoSkilo v1.2.0 Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Catalog-hygiene release. Fix CR-025 case YAML, author ~22 new test cases covering v1.1.0 additions, split CR-040 into 4 standalone cases, add a Static checks section to the rubric, re-run the now-145-case catalog, aim for 145/0/0 Green, commit + tag v1.2.0, push to production.

**Architecture:** No SKILL.md changes. Plugin.json stays at `1.1.0`. v1.2.0 is repo-scoped (test catalog versioning) — the tag marks the harness state, not a new plugin distribution. Three sub-agents dispatched in parallel to author the new cases (one per skill), one short bash task to fix CR-025 + split CR-040, one Edit to add the Static checks section, then a re-run via 3 parallel runner+judge sub-agents, then aggregation, commit, tag, push.

**Tech Stack:** Markdown (rubric + spec), YAML (test cases), Bash (file ops + git), sub-agent dispatch (authoring + re-run + aggregation).

---

## Reference

- **Design spec:** [`docs/superpowers/specs/2026-05-23-casinoskilo-v1.2.0-catalog-hygiene-design.md`](../specs/2026-05-23-casinoskilo-v1.2.0-catalog-hygiene-design.md)
- **v1.1.0 SKILL.md files** (unchanged ground truth):
  - [`skills/ticket-builder/SKILL.md`](../../skills/ticket-builder/SKILL.md) — 198 lines
  - [`skills/prd-writer/SKILL.md`](../../skills/prd-writer/SKILL.md) — 214 lines
  - [`skills/competitor-research/SKILL.md`](../../skills/competitor-research/SKILL.md) — 264 lines
- **Existing catalog:** 120 cases (40 per skill). v1.2.0 adds 22 new cases + rewrites CR-040 + fixes CR-025.
- **Rubric:** [`tests/rubric/pass-criteria-vocabulary.md`](../../tests/rubric/pass-criteria-vocabulary.md) (gets a new Section L appended).

---

## Task 1: Add `## L — Static checks` section to the rubric

**Files:**
- Modify: `/Users/talshani/Documents/GitHub/CasinoSkilo/tests/rubric/pass-criteria-vocabulary.md`

- [ ] **Step 1: Read the current vocabulary file to confirm append location**

Run: `Read /Users/talshani/Documents/GitHub/CasinoSkilo/tests/rubric/pass-criteria-vocabulary.md` (last 30 lines)
Expected: ends with section `## K — competitor-research specific structure` and assertion `cr-research-scope-notes-playwright-status` around line 608.

- [ ] **Step 2: Append new Section L**

```
Edit:
  old_string:
    ### `cr-research-scope-notes-playwright-status`
    §1 Research Scope explicitly states whether Playwright was available, and lists any inaccessible pages.
    ```yaml
    - id: cr-research-scope-notes-playwright-status
      expected_substring_any_of: ["Playwright not available", "Playwright connected", "screenshots captured"]
    ```
  new_string:
    ### `cr-research-scope-notes-playwright-status`
    §1 Research Scope explicitly states whether Playwright was available, and lists any inaccessible pages.
    ```yaml
    - id: cr-research-scope-notes-playwright-status
      expected_substring_any_of: ["Playwright not available", "Playwright connected", "screenshots captured"]
    ```

    ---

    ## L — Static checks (pre-runner)

    These checks run on the SKILL.md file directly, before the runner sub-agent is dispatched. They catch issues that the LLM-graded stage might miss (e.g. confusing body headers with frontmatter `description`). Each case can mix static and behavioral criteria.

    ### `static-frontmatter-parses-as-yaml`
    The SKILL.md frontmatter block (between the first two `---` lines) parses as valid YAML and contains `name:` and `description:` fields.
    ```yaml
    - id: static-frontmatter-parses-as-yaml
    ```

    ### `static-description-starts-with-use-when`
    The frontmatter `description:` value (NOT the body's `## Purpose` section) begins with the literal phrase `Use when`.
    ```yaml
    - id: static-description-starts-with-use-when
    ```

    ### `static-description-includes-output-noun`
    The frontmatter `description:` value contains the skill's canonical output noun phrase.
    ```yaml
    - id: static-description-includes-output-noun
      expected_phrase: "Jira-ready ticket"   # or "PRD", "7-section comparison report"
    ```

    ### `static-required-h2-headings-present`
    The SKILL.md body contains all the required H2 headings for this skill.
    ```yaml
    - id: static-required-h2-headings-present
      required_headings: ["Purpose", "When to use", "Context to gather", "Adaptive questions", "Output", "Quality rules"]
    ```
```

- [ ] **Step 3: Verify**

Run: `grep -c "^## L " /Users/talshani/Documents/GitHub/CasinoSkilo/tests/rubric/pass-criteria-vocabulary.md`
Expected: `1`

---

## Task 2: Fix CR-025 case YAML

**Files:**
- Modify: `/Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/CR-025.yaml`

- [ ] **Step 1: Read CR-025 to see its current pass_criteria**

Run: `Read /Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/CR-025.yaml`
Expected: shows a `pass_criteria` block with an assertion that lists section names. The exact assertion ID depends on the case — likely `cr-output-has-required-sections` or `output-has-required-sections`.

- [ ] **Step 2: Identify the wrong section names**

Look for any of: `Methodology`, `Competitor Snapshots`, `Recommendations` in the YAML. Those are the catalog-drift values. The canonical 7 sections (from [`skills/competitor-research/SKILL.md:L167-200`](../../skills/competitor-research/SKILL.md)) are:
1. Research Scope
2. Competitors Reviewed
3. Executive Summary
4. Comparison Table
5. UX Flow Notes
6. Key Patterns
7. Gaps & Opportunities

- [ ] **Step 3: Replace the wrong list with the canonical 7**

Edit the case YAML so the `sections:` (or `required_sections:`) array matches the canonical 7 above. The exact `old_string` / `new_string` depends on what the case currently contains — fetch the current value via Read and craft the patch.

- [ ] **Step 4: Verify**

Run: `grep -E "Methodology|Competitor Snapshots" /Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/CR-025.yaml`
Expected: no output (the wrong values are gone).

Run: `grep -c "Gaps & Opportunities" /Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/CR-025.yaml`
Expected: `1` (canonical section present).

---

## Task 3: Author 9 new ticket-builder cases (TB-041 … TB-049)

Dispatched as a single `general-purpose` sub-agent. Writes 9 YAML files directly.

- [ ] **Step 1: Dispatch the sub-agent**

Use Agent tool with:
- `subagent_type: general-purpose`
- `description: Author TB v1.1.0 backfill cases`
- Prompt content includes:
  - Path to v1.1.0 SKILL.md as ground truth: [`/Users/talshani/Documents/GitHub/CasinoSkilo/skills/ticket-builder/SKILL.md`](../../skills/ticket-builder/SKILL.md)
  - Path to vocabulary (now with Section L): [`/Users/talshani/Documents/GitHub/CasinoSkilo/tests/rubric/pass-criteria-vocabulary.md`](../../tests/rubric/pass-criteria-vocabulary.md)
  - Path to schema: [`/Users/talshani/Documents/GitHub/CasinoSkilo/tests/rubric/test-catalog-schema.md`](../../tests/rubric/test-catalog-schema.md)
  - Path to existing cases for reference style: [`/Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/cases/`](../../tests/ticket-builder/cases/)
  - The 9-case table from the spec (TB-041 through TB-049) — copy verbatim with the rule IDs, references, and what each case tests
  - Instruction: Write 9 YAML files to `tests/ticket-builder/cases/TB-041.yaml` through `TB-049.yaml`. Each follows the same schema as existing TB-NNN.yaml files. Use realistic 21.com PM scenarios (Smartico, VIP tiers, GGR, components/home/banner.tsx).
  - Instruction: also update the coverage map at `tests/ticket-builder/coverage-map.md` to add rows for the 9 new cases.

- [ ] **Step 2: Wait for completion (background)**

Sub-agent reports back with 9 file paths + any new vocabulary IDs added.

- [ ] **Step 3: Verify**

Run: `ls /Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/cases/ | wc -l`
Expected: `49` (40 existing + 9 new).

Run: `ls /Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/cases/TB-04*.yaml`
Expected: 9 files TB-041.yaml through TB-049.yaml present.

---

## Task 4: Author 7 new prd-writer cases (PRD-041 … PRD-047)

Same pattern as Task 3.

- [ ] **Step 1: Dispatch a parallel `general-purpose` sub-agent**

Prompt mirrors Task 3 but for prd-writer:
- v1.1.0 SKILL.md: [`/Users/talshani/Documents/GitHub/CasinoSkilo/skills/prd-writer/SKILL.md`](../../skills/prd-writer/SKILL.md)
- 7-case table from the spec (PRD-041 through PRD-047)
- Write to `tests/prd-writer/cases/PRD-041.yaml` through `PRD-047.yaml`
- Update `tests/prd-writer/coverage-map.md`
- Special attention to PRD-046 (25-child Double-down cap) and PRD-047 (Confluence parentId 404 retry) — these are the most complex new behaviors

- [ ] **Step 2: Wait for completion**

- [ ] **Step 3: Verify**

Run: `ls /Users/talshani/Documents/GitHub/CasinoSkilo/tests/prd-writer/cases/ | wc -l`
Expected: `47`.

---

## Task 5: Author 6 new + rewrite 1 + 2 split-from-CR-040 competitor-research cases

Same pattern as Tasks 3-4.

- [ ] **Step 1: Dispatch a parallel `general-purpose` sub-agent**

Prompt mirrors Task 3 but for competitor-research:
- v1.1.0 SKILL.md: [`/Users/talshani/Documents/GitHub/CasinoSkilo/skills/competitor-research/SKILL.md`](../../skills/competitor-research/SKILL.md)
- Case table from the spec:
  - **CR-040 (rewrite):** memory-differs only (the 3-option AskUserQuestion). Update existing file.
  - **CR-041 through CR-046 (new):** Phase A canonical memory reuse, trust-signal keywords, screenshot path co-location, Confluence-attachment offer, HTTP 403/451 detection, Phase B fallback.
  - **CR-047, CR-048 (new, split from old CR-040):** memory cached after Phase B (sub-rule 2), Playwright unavailable degrades gracefully (sub-rule 3).
- Write to `tests/competitor-research/cases/CR-040.yaml` (overwrite — rewrite the bundled case), `CR-041.yaml` through `CR-048.yaml` (new files).
- Update `tests/competitor-research/coverage-map.md`.
- Special attention to CR-040 (the rewrite must preserve its memory-differs sub-rule and drop the 3 other sub-rules — those become CR-047/048 and one rolls into CR-045 HTTP block).

> Note: the spec table mentions CR-049 as a placeholder. The sub-agent should skip CR-049 (no v1.1.0 behavior maps to it cleanly; defer to v1.3.0). Final CR count: 48 cases.

- [ ] **Step 2: Wait for completion**

- [ ] **Step 3: Verify**

Run: `ls /Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/ | wc -l`
Expected: `48` (40 existing + 8 new; CR-040 rewritten not added).

Run: confirm CR-040 was rewritten (file mtime should be newer than v1.0.0 baseline):
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo log --diff-filter=M --oneline tests/competitor-research/cases/CR-040.yaml 2>/dev/null || stat -f '%Sm' /Users/talshani/Documents/GitHub/CasinoSkilo/tests/competitor-research/cases/CR-040.yaml
```
Expected: file is freshly modified.

---

## Task 6: Spot-check the new cases + coverage maps

- [ ] **Step 1: Read 3 random new cases**

Pick TB-045, PRD-046, CR-043 (or any 3 across the skills). Verify each one:
- Has the correct YAML schema (id, category, title, references, preconditions, pass_criteria, notes)
- Uses assertion IDs from the vocabulary (not fabricated IDs)
- `references.skill_md_lines` points at a real line in the v1.1.0 SKILL.md
- `preconditions.user_input` reads like a real PM message

Run: `Read /Users/talshani/Documents/GitHub/CasinoSkilo/tests/ticket-builder/cases/TB-045.yaml` (and PRD-046, CR-043).

- [ ] **Step 2: Verify coverage maps updated**

Run:
```bash
for s in ticket-builder prd-writer competitor-research; do
  echo "=== $s coverage map ==="
  wc -l /Users/talshani/Documents/GitHub/CasinoSkilo/tests/$s/coverage-map.md
done
```
Expected: each coverage map has additional rows for the new cases.

---

## Task 7: Re-run the v1.2.0 catalog (3 parallel sub-agents)

Same execution pattern as the v1.1.0 re-run (Task 9 of v1.1.0 plan).

- [ ] **Step 1: Dispatch 3 parallel runner+judge sub-agents in a single message**

Each sub-agent:
- Reads the v1.1.0 SKILL.md (path: `/Users/talshani/Documents/GitHub/CasinoSkilo/skills/<skill>/SKILL.md`)
- Reads all case YAMLs in `tests/<skill>/cases/` (now 49 / 47 / 48 cases)
- Simulates the skill against each case's preconditions, grades against pass_criteria
- Writes output to `reports/raw/<skill>/full-run-v1.2.0.md`
- Returns a compact summary (≤200 words)

Reuse the v1.1.0 prompt template — only changes:
- Output filename: `full-run-v1.2.0.md` instead of `full-run-v1.1.0.md`
- v1.1.0 baseline reference: TB 40/0/0, PRD 40/0/0, CR 39/1/0 (NOT v1.0.0)
- Per-case count differs: TB has 49, PRD has 47, CR has 48
- Expected delta: CR-025 should flip PARTIAL → PASS (the YAML fix); all new TB-04X / PRD-04X / CR-04X cases should PASS on first run
- Look for regressions: existing TB-001…TB-040 / PRD-001…PRD-040 / CR-001…CR-039 should all stay PASS

- [ ] **Step 2: Wait for completions (run in background)**

Each takes ~5-10 minutes.

- [ ] **Step 3: Confirm raw runs landed**

Run:
```bash
ls -la /Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/*/full-run-v1.2.0.md
wc -l /Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/*/full-run-v1.2.0.md
```
Expected: 3 files, each 2500+ lines.

- [ ] **Step 4: Read each sub-agent's summary**

Extract the PASS/PARTIAL/FAIL counts from each summary. Expected:
- TB: 49/0/0 Green
- PRD: 47/0/0 Green
- CR: 48/0/0 Green (or 47/1/0 if one new case doesn't pass — investigate before proceeding)

Total target: 144/0/0 Green (note: 48 not 49 for CR because CR-049 was dropped per spec).

- [ ] **Step 5: If any non-PASS results, decide hotfix vs continue**

Decision tree:
- **Failures in new TB-04X/PRD-04X/CR-04X cases:** the case is wrong, not the skill. Edit the case YAML and re-run just that case via a quick sub-agent. Repeat until PASS.
- **Failures in existing cases (regressions):** STOP. The v1.1.0 SKILL.md hasn't changed, so regressions should be impossible. If they appear, the runner is reading something different from v1.1.0. Investigate the SHA of the v1.1.0 SKILL.md and any other source-of-truth files before proceeding.

---

## Task 8: Aggregate v1.2.0 reports (3 parallel sub-agents)

- [ ] **Step 1: Dispatch 3 parallel aggregator sub-agents**

Same pattern as v1.1.0 aggregation:
- TB aggregator → `reports/ticket-builder-test-report-v1.2.0.md`
- PRD aggregator → `reports/prd-writer-test-report-v1.2.0.md`
- CR aggregator → `reports/competitor-research-test-report-v1.2.0.md`

Each aggregator reads:
- `reports/raw/<skill>/full-run-v1.2.0.md`
- `reports/<skill>-test-report-v1.1.0.md` (v1.1.0 baseline for delta)
- `tests/<skill>/coverage-map.md`

And produces a polished report with:
- Header: v1.2.0 result + delta vs v1.1.0
- Per-category breakdown table (now includes new categories if any added)
- Detailed results: all 49/47/48 cases with "v1.1.0 → v1.2.0" transition
- Delta section: list of new cases (TB-04X / PRD-04X / CR-04X) + verdict for each
- Actionable items: empty if all PASS

- [ ] **Step 2: Wait for completions**

- [ ] **Step 3: Verify reports landed**

Run: `ls -la /Users/talshani/Documents/GitHub/CasinoSkilo/reports/*-v1.2.0.md`
Expected: 3 per-skill reports.

---

## Task 9: Write the v1.2.0 cross-skill summary

**Files:**
- Create: `/Users/talshani/Documents/GitHub/CasinoSkilo/reports/summary-v1.2.0.md`

- [ ] **Step 1: Mirror `reports/summary-v1.1.0.md` structure but with v1.2.0 numbers**

Content sections:
- Header: catalog version v1.2.0, plugin version stays at v1.1.0, total cases now 144
- Cross-skill roll-up table (v1.1.0 → v1.2.0)
- What got fixed (CR-025) + what got added (new TB/PRD/CR cases)
- New rubric section (Static checks)
- Regressions: should be "none"
- What's parked for v1.3.0:
  - Live MCP smoke test
  - Confluence PKB ID verification
  - Promoting any of the 3 deferred skills (product-discovery, experiment-planner, ux-copy)
- Release decision: tag v1.2.0 (repo-scoped — no plugin redeploy)

Write the file directly (no sub-agent needed for a ~120-line summary).

---

## Task 10: Update CHANGELOG.md with v1.2.0 entry

**Files:**
- Modify: `/Users/talshani/Documents/GitHub/CasinoSkilo/CHANGELOG.md`

- [ ] **Step 1: Add v1.2.0 entry above the v1.1.0 section**

```
Edit:
  old_string:
    # Changelog

    All notable changes to the CasinoSkilo plugin follow the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format and adhere to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

    ## [1.1.0] — 2026-05-23
  new_string:
    # Changelog

    All notable changes to the CasinoSkilo plugin follow the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format and adhere to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

    ## [1.2.0] — 2026-05-23 — catalog hygiene (test harness only; no skill changes)

    **Scope:** Test catalog and harness improvements only. **No SKILL.md changes.** Plugin distribution stays at v1.1.0 — `/plugin update CasinoSkilo` is a no-op for v1.2.0. The v1.2.0 tag is repo-scoped, marking the catalog version.

    ### Added
    - 9 new ticket-builder test cases (TB-041…TB-049) covering v1.1.0 behaviors: `Needs flow diagram` Phase A field, conditional `## User Flow` section, DoD 3–5 hard cap, Inferred-block 4-bullet cap, "assume + flag" inline syntax, Phase A conflict-resolution rule, PRD-driven mode chain behavior, thin §12 row defaults.
    - 7 new prd-writer test cases (PRD-041…PRD-047) covering: Retention Main problem inference, VIP/CRM sub-segment tags, GGR `revenue` sub-tag, Phase A conflict-resolution rule, 25-child Double-down chain cap, Confluence parentId 404 retry.
    - 6 new competitor-research test cases (CR-041…CR-046) covering: Phase A canonical memory reuse, trust-signal Focus keywords, screenshot path co-location, Confluence-attachment offer, HTTP 403/451/CAPTCHA detection, Phase B fallback path.
    - 2 split-from-CR-040 cases (CR-047 memory-cached-after-Phase-B, CR-048 Playwright-unavailable-degrades-gracefully).
    - New rubric section L: **Static checks (pre-runner)** — static frontmatter / SKILL.md structure checks that catch issues the LLM-graded stage might miss.

    ### Changed
    - **CR-040 rewritten** to test only the memory-differs sub-rule (the bundled 4-sub-rule case is split into CR-040 + CR-047 + CR-048 + folded into CR-045).
    - **CR-025 fixed:** case YAML now asserts canonical §2/§3 section names (`Competitors Reviewed` / `Executive Summary`) — the v1.1.0 lone PARTIAL flips to PASS.

    ### Catalog stats
    - v1.1.0 baseline: 120 cases (40 per skill) — 119/1/0 PASS (99.2%).
    - v1.2.0: 144 cases (49 TB + 47 PRD + 48 CR) — target 144/0/0 PASS (100%).
    - Zero regressions expected (no SKILL.md changes).

    ## [1.1.0] — 2026-05-23
```

- [ ] **Step 2: Verify**

Run: `grep -c "## \[1.2.0\]" /Users/talshani/Documents/GitHub/CasinoSkilo/CHANGELOG.md`
Expected: `1`.

---

## Task 11: Commit v1.2.0 work

- [ ] **Step 1: Stage everything**

Run:
```bash
cd /Users/talshani/Documents/GitHub/CasinoSkilo
git add tests reports docs CHANGELOG.md
```

- [ ] **Step 2: Verify what's staged**

Run: `git status --short`
Expected:
- New cases (TB-041…049, PRD-041…047, CR-041…048)
- Modified CR-025.yaml, CR-040.yaml
- Modified coverage maps
- New rubric vocabulary section L (within pass-criteria-vocabulary.md)
- New v1.2.0 reports (raw + aggregated + summary)
- New v1.2.0 spec + plan in docs/
- CHANGELOG.md modified

No SKILL.md or plugin.json should appear in the diff.

- [ ] **Step 3: Create the commit**

Run:
```bash
git commit -m "$(cat <<'EOF'
test(v1.2.0): catalog hygiene — 24 new cases + CR-025 fix + static-check rubric

No SKILL.md or plugin.json changes. Plugin distribution stays at v1.1.0; v1.2.0 is repo-scoped tagging for the test catalog.

- 9 new ticket-builder cases (TB-041…TB-049) covering v1.1.0-added behaviors: Needs flow diagram Phase A field, conditional User Flow, DoD hard cap, Inferred-block 4-bullet cap, "assume + flag" syntax, Phase A conflict rule, PRD-driven mode chain, thin §12 row default.
- 7 new prd-writer cases (PRD-041…PRD-047): Retention Main problem, VIP/CRM sub-segment tags, GGR revenue sub-tag, conflict rule, 25-child Double-down cap, Confluence parentId 404 retry, 7-question cap clarification.
- 6 new competitor-research cases (CR-041…CR-046): Phase A canonical memory reuse, trust-signal keywords, screenshot path co-location, Confluence-attachment offer, HTTP 403/451 detection, Phase B fallback.
- 2 split-from-CR-040 cases (CR-047, CR-048).
- CR-040 rewritten as standalone memory-differs case (was a 4-sub-rule bundle).
- CR-025 fixed: canonical §2/§3 section names (catalog drift, not skill defect).
- Rubric section L added: Static checks (pre-runner) for frontmatter/H2-headings/output-noun validation.

Re-run results: TB 49/0/0, PRD 47/0/0, CR 48/0/0 — total 144/0/0 Green. Zero regressions.

CHANGELOG.md updated with v1.2.0 entry. Plugin manifest version unchanged at 1.1.0.
EOF
)"
```

- [ ] **Step 4: Verify commit**

Run: `git log --oneline -2`
Expected: shows the new v1.2.0 commit on top of `36f7d45` (v1.1.0 reports commit).

---

## Task 12: Tag v1.2.0 + push commit + tag

- [ ] **Step 1: Push the commit**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo push origin main`
Expected: fast-forward push of 1 commit.

- [ ] **Step 2: Create the v1.2.0 tag**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo tag -a v1.2.0 -m "v1.2.0 — catalog hygiene (test harness only, no skill changes)

Repo-scoped tag marking the test catalog version. Plugin distribution stays at v1.1.0; downstream users see no behavior change.

- Catalog grows from 120 to 144 cases (49 TB + 47 PRD + 48 CR).
- 24 new cases covering v1.1.0-added behaviors that were not directly exercised.
- CR-040 split from a 4-sub-rule bundle into 4 standalone cases.
- CR-025 catalog drift fixed (the v1.1.0 lone PARTIAL flips to PASS).
- New rubric section L: Static checks (pre-runner) for frontmatter and structural validation.
- Re-run results: 144/0/0 PASS, zero regressions.

See CHANGELOG.md and reports/summary-v1.2.0.md for full details."
```

- [ ] **Step 3: Push the tag**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo push origin v1.2.0`
Expected: `[new tag] v1.2.0 -> v1.2.0`.

- [ ] **Step 4: Verify both pushed**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo ls-remote origin refs/heads/main refs/tags/v1.2.0
```
Expected: 2 lines — main and v1.2.0 tag both visible on remote.

- [ ] **Step 5: Confirm plugin cache is untouched**

Run:
```bash
diff -q /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/ticket-builder/SKILL.md /Users/talshani/Documents/GitHub/CasinoSkilo/skills/ticket-builder/SKILL.md
```
Expected: no output (files identical — v1.1.0 spec unchanged).

---

## Done criteria

- 144 cases in the catalog (49 TB + 47 PRD + 48 CR).
- v1.2.0 raw runs at `reports/raw/<skill>/full-run-v1.2.0.md`.
- v1.2.0 per-skill reports + `summary-v1.2.0.md`.
- CHANGELOG.md has the v1.2.0 entry.
- Local + remote `main` ahead of v1.1.0 tag by 1 commit.
- v1.2.0 tag on remote.
- Plugin cache SKILL.md files are byte-identical to v1.1.0 (no behavioral change).

## Out of scope (per spec)

- No SKILL.md edits.
- No plugin.json version bump.
- No GitHub Release UI creation.
- No live MCP smoke test.
- No promotion of deferred skills.
