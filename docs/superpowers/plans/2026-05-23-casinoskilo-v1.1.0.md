# CasinoSkilo v1.1.0 Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Apply the v1.1.0 design (24 SKILL.md edits across 3 skills + plugin metadata bump + brevity redesign), publish to GitHub, redeploy via `/plugin update`, and re-run the 120-case test catalog to confirm targeted PARTIAL/FAIL cases flip to PASS.

**Architecture:** Edit the 3 SKILL.md files in the plugin cache (active spec), mirror to the GitHub repo (empty initial commit), bump `.claude-plugin/plugin.json` to `1.1.0` + add a `CHANGELOG.md`, commit in two phases (production plugin first, then tests/reports/docs), push to `talshani8499-netizen/CasinoSkilo`, run `/plugin update` locally, then dispatch 3 parallel re-run sub-agents and aggregate post-fix reports.

**Tech Stack:** Markdown (skill specs), JSON (plugin manifest), YAML (test cases), Bash (file mirroring + git), sub-agent dispatch (test re-run).

---

## Reference: the design spec

All edits below are derived directly from [`docs/superpowers/specs/2026-05-23-casinoskilo-v1.1.0-skill-updates-design.md`](../specs/2026-05-23-casinoskilo-v1.1.0-skill-updates-design.md). Each task cites the design change ID it implements (TB-Δ-N, PRD-Δ-N, CR-Δ-N, PJ-Δ-N).

Files referenced throughout:
- **TB SKILL.md:** `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/ticket-builder/SKILL.md` (current: 169 lines)
- **PRD SKILL.md:** `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/prd-writer/SKILL.md` (current: 205 lines)
- **CR SKILL.md:** `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/competitor-research/SKILL.md` (current: 248 lines)
- **Plugin manifest:** `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/.claude-plugin/plugin.json`
- **Local repo:** `/Users/talshani/Documents/GitHub/CasinoSkilo/`
- **Remote:** `git@github.com:talshani8499-netizen/CasinoSkilo.git`

A note on TDD: these are spec edits to text files, not code with unit tests. The "test" is the existing 120-case behavioral catalog at `tests/`. We apply all spec edits first, then re-run the full catalog once (Task 9) to verify the v1.0.0 PARTIAL/FAIL cases flip to PASS without regressing the PASS cases. Per-edit TDD would require 24 separate sub-agent runs — not practical, and a batch run gives the same signal.

---

## Task 1: ticket-builder/SKILL.md — all 8 TB-Δ edits

**Files:**
- Modify: `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/ticket-builder/SKILL.md`

This task applies all 8 ticket-builder spec edits in one pass. Each step is one Edit operation with concrete `old_string` / `new_string`. Read the file once before starting.

- [ ] **Step 1: Read the current TB SKILL.md to confirm line text matches the patches below**

Run: `Read /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/ticket-builder/SKILL.md`
Expected: 169 lines, frontmatter on L1–L4, Phase A signal table at L55–L60, Output template starts L121.

- [ ] **Step 2: TB-Δ-7 — Add Phase A conflict-resolution rule (L52)**

This goes first because subsequent edits assume it's present.

```
Edit:
  old_string:
    ### Phase A — Infer answers from input + context
    Before asking anything, attempt to infer each of the 4 core answers from the user's input and the Jira/Confluence context scan. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question.
  new_string:
    ### Phase A — Infer answers from input + context
    Before asking anything, attempt to infer each of the 4 core answers from the user's input and the Jira/Confluence context scan. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question. **Conflict rule:** when signals from multiple rows fire for the same field (e.g. input contains both "fix" and "add new"), mark the field as Not inferred and fall through to Phase B. Do not invent a tie-break.
```

- [ ] **Step 3: TB-Δ-1 (part 1) — Add `Needs flow diagram` row to Phase A signal table**

Add a 5th row to the table immediately after the existing Connection row.

```
Edit:
  old_string:
    | **Connection** | reference to existing component/file/flow → Changes or Extends. "new flow", "from scratch", "doesn't exist today" → New flow. |

    For each inferred answer, record the exact phrase that revealed it — that phrase later appears in the ticket's "Inferred (not asked)" block so the user can audit.
  new_string:
    | **Connection** | reference to existing component/file/flow → Changes or Extends. "new flow", "from scratch", "doesn't exist today" → New flow. |
    | **Needs flow diagram** | "bug", "copy change", "content tweak", "analytics-only", "config", "toggle" → No (skip §User Flow entirely). "new feature", "new flow", "navigation change", "multi-step", "admin task" → Yes. Otherwise → Not inferred, fall through to Phase C. |

    For each inferred answer, record the exact phrase that revealed it — that phrase later appears in the ticket's "Inferred (not asked)" block so the user can audit.
```

- [ ] **Step 4: TB-Δ-1 (part 2) — Add Phase C `Flow?` fallback question**

Insert at the end of the Phase C "Hard rules" block, before Phase D.

```
Edit:
  old_string:
    6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the ticket, do not ask.**

    **Worked example (a VIP progress bar ticket on 21.com — these are the kind of follow-ups the skill should generate, not generic templates):**
  new_string:
    6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the ticket, do not ask.**

    **Phase C fallback for the new `Needs flow diagram` field:** if Phase A could not infer it (input was ambiguous), emit one AskUserQuestion:
    - Question: `Include an ASCII user flow diagram?`
    - Header: `Flow?`
    - Options:
      - `Yes — happy path only` — Single-track flow with no branches
      - `Yes — with branches and decisions` — Full flow with decision diamonds
      - `No — skip the flow diagram` — Omit §User Flow entirely

    This counts against the Phase C 3-follow-up cap.

    **Worked example (a VIP progress bar ticket on 21.com — these are the kind of follow-ups the skill should generate, not generic templates):**
```

- [ ] **Step 5: TB-Δ-6 — Define "assume + flag" syntax**

Append to rule 6's text in Phase C.

```
Edit:
  old_string:
    6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the ticket, do not ask.**
  new_string:
    6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the ticket, do not ask.** Inline assumption format: `> **Assumption:** <statement>. **Flag:** <one-line reason this needs confirmation>.` Place inside the relevant Description or DoD bullet — never in a separate section.
```

- [ ] **Step 6: TB-Δ-5 — Clarify Inferred-block placement narrative (L116)**

```
Edit:
  old_string:
    ### Phase D — Output
    Proceed to the Output section below. If anything was inferred in Phase A, surface it in the "Inferred (not asked)" block at the top of the ticket so the user can audit and correct.
  new_string:
    ### Phase D — Output
    Proceed to the Output section below. If anything was inferred in Phase A, surface the `Inferred (not asked)` block immediately after the 4 metadata header lines (Ticket type / Parent epic / Component / Labels), before `## User Story`. See the template below for exact placement.
```

- [ ] **Step 7: TB-Δ-3 — Inferred block hard cap (4 bullets)**

Modify the Output template's Inferred block parenthetical.

```
Edit:
  old_string:
        > **Inferred (not asked):** _(include this block only if Phase A inferred at least one core answer; one bullet per inference, citing the exact phrase from input or context that revealed it)_
        > - Ticket type: Bug — from "fix the bug where..."
        > - Main user: End user — from "guest profiles"
  new_string:
        > **Inferred (not asked):** _(include this block only if Phase A inferred at least one core answer; one bullet per inference, citing the exact phrase from input or context that revealed it. **Hard cap: 4 bullets.** If Phase A inferred 5+ fields, show the 4 most-actionable by this priority order — Ticket type > Connection > Main user > Main goal > Needs flow diagram — and append `_(+N more inferred — see context for full set)_` as an italic line below the bullets.)_
        > - Ticket type: Bug — from "fix the bug where..."
        > - Main user: End user — from "guest profiles"
```

- [ ] **Step 8: TB-Δ-4 — Description guidance note (soft audit hint)**

Append to the Description placeholder text.

```
Edit:
  old_string:
        ## Description
        [2–4 sentences describing what we are building or fixing, in plain product language. For features/improvements: what the change is and the value it delivers. For bugs: what is broken, where, and what the correct behavior should be. No background, no history, no rationale beyond the value line — just a crisp statement of the work.]
  new_string:
        ## Description
        [2–4 sentences describing what we are building or fixing, in plain product language. For features/improvements: what the change is and the value it delivers. For bugs: what is broken, where, and what the correct behavior should be. No background, no history, no rationale beyond the value line — just a crisp statement of the work. If your description exceeds 4 sentences, audit whether you have smuggled in Background, Rationale, or Context that the banned-sections list forbids.]
```

- [ ] **Step 9: TB-Δ-1 (part 3) — Make User Flow section conditional in Output template**

The `## User Flow` heading should only render when `Needs flow diagram = Yes`. Update the template instruction.

```
Edit:
  old_string:
        ## User Flow
        [ASCII flowchart of the happy-path flow inside a fenced code block. Keep it tight — one diagram, no prose steps before or after unless absolutely needed for clarity. Use box-drawing characters (┌─┐│└┘├┤┬┴) and arrows (▼ → ─▶). Branches/decisions render as ┌─────┐ with a `?` and labeled outgoing arrows.]
  new_string:
        ## User Flow
        _(Conditional — include this section ONLY if `Needs flow diagram = Yes` from Phase A or Phase C. If `No`, omit the entire `## User Flow` heading and code block from the output — do not render as "N/A" or as an empty section.)_

        [ASCII flowchart of the happy-path flow inside a fenced code block. Keep it tight — one diagram, no prose steps before or after unless absolutely needed for clarity. Use box-drawing characters (┌─┐│└┘├┤┬┴) and arrows (▼ → ─▶). Branches/decisions render as ┌─────┐ with a `?` and labeled outgoing arrows.]
```

- [ ] **Step 10: TB-Δ-2 — Definition of Done hard cap (3–5 items)**

```
Edit:
  old_string:
        ## Definition of Done
        - [DoD item 1]
        - [DoD item 2]
  new_string:
        ## Definition of Done
        _(3–5 items. Never 6+. If you cannot write 3 essential items, name the gap. If you wrote 6+, cut the non-essential ones — the ticket is not a QA test plan.)_

        - [DoD item 1]
        - [DoD item 2]
        - [DoD item 3]
```

- [ ] **Step 11: TB-Δ-8 — Add `## PRD-driven mode` section**

Append after the existing `## Quality rules` section (after line 168).

```
Edit:
  old_string:
    - Output must be copy-pasteable into Jira (markdown)
    - Do NOT add any meta-commentary, "builder notes", or post-ticket reflections. The ticket ends at Definition of Done.
  new_string:
    - Output must be copy-pasteable into Jira (markdown)
    - Do NOT add any meta-commentary, "builder notes", or post-ticket reflections. The ticket ends at Definition of Done.

    ## PRD-driven mode (when chained by prd-writer Double down)

    When `prd-writer` invokes this skill as part of its Double-down chain, run in PRD-driven mode:

    - **Skip Phase B entirely.** No core questions to the user.
    - **Skip Phase C entirely.** No adaptive follow-ups (including the `Needs flow diagram` fallback question).
    - **Phase A infers all 5 core fields from the PRD body.** Every inference must cite the PRD section it came from (e.g. `from PRD §10 FR-2`, `from PRD §8 Functional`). Never invent context.
    - **`Inferred (not asked)` block is required** and cites the PRD section for each entry. The 4-bullet hard cap still applies.
    - **If the §12 row is too thin to infer a ticket type** (e.g. just "Misc — TBD"), default to type `Task` with an inline `> **Open:** ticket type not inferable from PRD §12 — confirm with owner.` line in the Description.
    - **At handoff, auto-choose `Bet on it`.** Do NOT call AskUserQuestion. Use the parent epic key supplied by prd-writer.
    - **Per-chain question count is exactly zero.** A 14-row §12 produces 14 child tickets with zero user questions.

    `prd-writer` authoritatively governs the upstream contract at `prd-writer/SKILL.md` (Handoff → Double down branch). This section is the downstream half; the two must stay in sync.
```

- [ ] **Step 12: Verify the file**

Run: `Read /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/ticket-builder/SKILL.md`
Expected: file is ~200 lines (up from 169), no orphaned `old_string` fragments. Verify the new `## PRD-driven mode` section is at the bottom, the `Needs flow diagram` row is in the Phase A table, the Inferred block has the 4-bullet cap text, and the DoD has the 3–5-item cap text.

---

## Task 2: prd-writer/SKILL.md — all 9 PRD-Δ edits

**Files:**
- Modify: `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/prd-writer/SKILL.md`

- [ ] **Step 1: Read the current PRD SKILL.md to confirm line text matches the patches below**

Run: `Read /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/prd-writer/SKILL.md`
Expected: 205 lines, frontmatter on L1–L4, Phase A signal table at L53–L58, Output template starts L125.

- [ ] **Step 2: PRD-Δ-5 — Add "Double down" verbatim to frontmatter description (L3)**

```
Edit:
  old_string:
    description: Use when a PM wants to turn an idea, initiative, or discovery outcome into a full PRD. Scans Jira/Confluence for related context, adaptively asks only the questions input doesn't already answer, adds up to 3 context-derived follow-ups for real unknowns, and returns a maturity-adapted PRD. Ends with a "Ready To Gamble On It?" handoff that can push to Confluence (Product Knowledge Base space) and optionally chain the ticket-builder skill to create the Jira epic + child tickets, or save markdown only.
  new_string:
    description: Use when a PM wants to turn an idea, initiative, or discovery outcome into a full PRD. Scans Jira/Confluence for related context, adaptively asks only the questions input doesn't already answer, adds up to 3 context-derived follow-ups for real unknowns, and returns a maturity-adapted PRD. Ends with a "Ready To Gamble On It?" handoff that can push to Confluence (Product Knowledge Base space) and optionally chain the **ticket-builder** skill via the **Double down** option to create the Jira epic + child tickets, or save markdown only.
```

- [ ] **Step 3: PRD-Δ-4 — Add Phase A conflict-resolution rule (L52)**

```
Edit:
  old_string:
    ### Phase A — Infer answers from input + context
    Before asking anything, attempt to infer each of the 4 core answers from the user's input and the Jira/Confluence context scan. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question.
  new_string:
    ### Phase A — Infer answers from input + context
    Before asking anything, attempt to infer each of the 4 core answers from the user's input and the Jira/Confluence context scan. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question. **Conflict rule:** when signals from multiple rows fire for the same field (e.g. input contains both "we already have" and "from scratch"), mark the field as Not inferred and fall through to Phase B. Do not invent a tie-break.
```

- [ ] **Step 4: PRD-Δ-2 — Add sub-segment guidance to Main user row**

```
Edit:
  old_string:
    | **Main user** | "player", "user", "customer" → End user. "admin", "back office", "BO", "CMS" → Admin. "CS", "support", "ops", "VIP team", "agent" → Support/ops. |
  new_string:
    | **Main user** | "player", "user", "customer" → End user. "admin", "back office", "BO", "CMS" → Admin. "CS", "support", "ops", "VIP team", "agent" → Support/ops. **Sub-segment hints:** VIP / high-roller / "whale" signals → End user with `vip` tag surfaced in User Story. CRM operator / campaign manager / "lifecycle" signals → Admin / internal with `crm` tag surfaced in User Story. |
```

- [ ] **Step 5: PRD-Δ-3 — Add Retention as 4th Main problem signal**

```
Edit:
  old_string:
    | **Main problem** | "blocked", "can't", "confused", "stuck" → Blocked/confused. "drop", "abandon", "churn", "not converting" → Drop-off. "manual", "slow", "tedious", "spreadsheets", "no tool for" → Internal workflow. |
  new_string:
    | **Main problem** | "blocked", "can't", "confused", "stuck" → Blocked/confused. "drop", "abandon", "churn", "not converting" → Drop-off. "manual", "slow", "tedious", "spreadsheets", "no tool for" → Internal workflow. "retention", "lapsed", "re-engage", "win-back", "reactivation" → Retention / re-engagement. |
```

- [ ] **Step 6: PRD-Δ-6 — Refine Success signal row with GGR sub-tag**

```
Edit:
  old_string:
    | **Success signal** | "convert", "activate", "sign up", "deposit", "GGR" → Conversion. "fewer tickets", "support load", "complaints" → Reduced friction. "DAU", "retention", "sessions", "engagement", "stickiness" → Engagement. |
  new_string:
    | **Success signal** | "convert", "activate", "sign up", "deposit" → Conversion. **GGR-specific signals** ("GGR", "NGR", "revenue lift", "ARPU") → Conversion with `revenue` sub-tag (surface in §10 Primary Metric). "fewer tickets", "support load", "complaints" → Reduced friction. "DAU", "retention", "sessions", "engagement", "stickiness" → Engagement. |
```

- [ ] **Step 7: PRD-Δ-3 (part 2) — Add Retention to Phase B option bank**

```
Edit:
  old_string:
    - **Main problem** — header: `Main problem` — "What is the main problem this should solve?"
      - Blocked / confused — Users can't complete or understand the flow
      - Drop-off — Users not converting or churning
      - Internal workflow — Internal teams need a better tool or process
  new_string:
    - **Main problem** — header: `Main problem` — "What is the main problem this should solve?"
      - Blocked / confused — Users can't complete or understand the flow
      - Drop-off — Users not converting or churning
      - Internal workflow — Internal teams need a better tool or process
      - Retention / re-engagement — Re-activate lapsed users or extend lifecycle
```

> Note: this Phase B question now has 4 concrete options. The AskUserQuestion tool's auto-"Other" makes it 5 total. SKILL.md's "exactly 3 concrete option labels per question" rule on L48 should be relaxed for this question — but per the spec, we're keeping the rule wording generic ("provide concrete option labels"). The Retention option is necessary and the count tradeoff is acceptable.

- [ ] **Step 8: PRD-Δ-9 — Clarify 7-question cap scope**

```
Edit:
  old_string:
    The skill is an **adaptive interview**, not a fixed form. Run the four phases below in order. All questions are asked via **AskUserQuestion** (the in-terminal interactive chooser, one question at a time). The tool auto-adds an "Other" option, so provide exactly 3 concrete option labels per question. Total questions asked across all phases must never exceed 7 (any combination of core + adaptive).
  new_string:
    The skill is an **adaptive interview**, not a fixed form. Run the four phases below in order. All questions are asked via **AskUserQuestion** (the in-terminal interactive chooser, one question at a time). The tool auto-adds an "Other" option, so provide concrete option labels per question (3 for most questions; 4 for `Main problem` since the Retention option is a first-class value). Total questions asked across all phases must never exceed 7 (any combination of core + adaptive). **The 7-question cap is per single skill invocation by the user. Chained `ticket-builder` calls in PRD-driven mode are zero-question by contract, so the cap is never breached by the chain itself.**
```

- [ ] **Step 9: PRD-Δ-7 — Confluence parentId fallback**

```
Edit:
  old_string:
          Return the new page URL. If the create fails, report the error and confirm the markdown file is still saved.
        - **`Bet on it` + Atlassian MCP NOT connected:** Report `Atlassian MCP not connected — saved markdown only at <path>` and stop.
  new_string:
          Return the new page URL. **If the create fails with HTTP 404 (parent moved/deleted), retry once without `parentId` and report which space-root the page landed at. If the second attempt also fails, save the markdown locally and report the error — do not silently drop.**
        - **`Bet on it` + Atlassian MCP NOT connected:** Report `Atlassian MCP not connected — saved markdown only at <path>` and stop.
```

- [ ] **Step 10: PRD-Δ-1 — Cross-link to ticket-builder PRD-driven mode**

Append to the "Hard instruction to ticket-builder" block.

```
Edit:
  old_string:
             - **Hard instruction to ticket-builder:** "PRD-driven mode — skip Phase B (no core questions) and Phase C (no adaptive follow-ups). Phase A infers all four core answers from the PRD body; surface them in the ticket's `Inferred (not asked)` block citing the PRD section (e.g. `from PRD §10 FR-2`). If a material unknown is unanswered by the PRD, follow your own rule: assume + flag inline. Do NOT call AskUserQuestion for any ticket in this batch. At the handoff, auto-choose `Bet on it` to push to Jira under the supplied parent epic — do NOT ask the user."
  new_string:
             - **Hard instruction to ticket-builder:** "PRD-driven mode — skip Phase B (no core questions) and Phase C (no adaptive follow-ups). Phase A infers all five core answers from the PRD body (including `Needs flow diagram`); surface them in the ticket's `Inferred (not asked)` block citing the PRD section (e.g. `from PRD §10 FR-2`). If a material unknown is unanswered by the PRD, follow your own rule: assume + flag inline. Do NOT call AskUserQuestion for any ticket in this batch. At the handoff, auto-choose `Bet on it` to push to Jira under the supplied parent epic — do NOT ask the user."
          - **This contract is authoritatively mirrored in `ticket-builder/SKILL.md → PRD-driven mode`. This skill enforces upstream; ticket-builder enforces downstream. The two sections must stay in sync — edits to one require the matching edit on the other.**
```

- [ ] **Step 11: PRD-Δ-8 — Cap Double-down chain at 25 children**

```
Edit:
  old_string:
    ### Notes on the Double down chain
    The PRD is the source of truth for the chained ticket-builder calls — every Phase A inference must cite the PRD section it came from, never invent context. The user is asked exactly **one** question during this branch (the Gamble handoff itself), regardless of how many child tickets §12 contains. A PRD with 14 child tickets produces 14 Jira tickets + 1 epic + 1 Confluence page from a single user click. If the PRD §12 row is too thin for Phase A to infer a ticket type (e.g. just "Misc — TBD"), ticket-builder defaults to type=Task with an inline `Open: ticket type not inferable from PRD §12 — confirm with owner` line in the ticket body, and proceeds.
  new_string:
    ### Notes on the Double down chain
    The PRD is the source of truth for the chained ticket-builder calls — every Phase A inference must cite the PRD section it came from, never invent context. The user is asked exactly **one** question during this branch (the Gamble handoff itself), regardless of how many child tickets §12 contains. A PRD with 14 child tickets produces 14 Jira tickets + 1 epic + 1 Confluence page from a single user click. If the PRD §12 row is too thin for Phase A to infer a ticket type (e.g. just "Misc — TBD"), ticket-builder defaults to type=Task with an inline `Open: ticket type not inferable from PRD §12 — confirm with owner` line in the ticket body, and proceeds.

    **Hard cap: 25 child tickets per chain.** If §12 has 26+ rows, abort the chain BEFORE making any Jira call and present this AskUserQuestion:
    - Question: `This PRD has <N> child tickets in §12, which exceeds the Double-down chain cap of 25. How would you like to proceed?`
    - Header: `Chain too long?`
    - Options:
      - `Split the PRD` — Abort the chain; split §12 into multiple sub-PRDs and re-run Double-down per sub-PRD
      - `Bet on it instead` — Publish the Confluence page only and create the Jira tickets manually
      - `Cancel` — Stop the handoff entirely
```

- [ ] **Step 12: Verify the file**

Run: `Read /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/prd-writer/SKILL.md`
Expected: file is ~225 lines (up from 205). Verify the Phase A table has the Retention signal in Main problem and the sub-segment hints in Main user; Phase B Main problem has 4 options; the Notes on Double down chain ends with the new 25-cap question.

---

## Task 3: competitor-research/SKILL.md — all 7 CR-Δ edits

**Files:**
- Modify: `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/competitor-research/SKILL.md`

- [ ] **Step 1: Read the current CR SKILL.md to confirm line text matches the patches below**

Run: `Read /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/competitor-research/SKILL.md`
Expected: 248 lines, frontmatter on L1–L4, Phase A signal table at L66–L71, Handoff starts L221.

- [ ] **Step 2: CR-Δ-5 — Reorder frontmatter description**

```
Edit:
  old_string:
    description: Use when a PM wants structured competitor research for a PRD, roadmap decision, redesign, or strategic positioning. Reads competitor list from auto-memory, scans Jira/Confluence for company baseline, adaptively asks only the questions input doesn't answer, optionally uses Playwright for public-page browsing and screenshots, and returns a lean 7-section comparison report. Ends with a "Ready To Gamble On It?" handoff that publishes to Confluence (Product Knowledge Base space) or saves markdown only. This skill is research-only — it does NOT create Jira tickets. Use prd-writer or ticket-builder downstream if research findings should turn into work.
  new_string:
    description: Use when a PM wants a structured competitor research report — returns a lean 7-section comparison report for PRDs, roadmap decisions, redesigns, or strategic positioning. Reads competitor list from auto-memory, scans Jira/Confluence for company baseline, adaptively asks only the questions input doesn't answer, and optionally uses Playwright for public-page browsing and screenshots. Ends with a "Ready To Gamble On It?" handoff that publishes to Confluence (Product Knowledge Base space) or saves markdown only. This skill is research-only — it does NOT create Jira tickets. Use prd-writer or ticket-builder downstream if research findings should turn into work.
```

- [ ] **Step 3: CR-Δ-4 — Replace robots.txt enforcement claim**

```
Edit:
  old_string:
    - Respect robots.txt; if blocked, note "couldn't access <page>" in the report and skip
  new_string:
    - Public pages only. If a page returns HTTP 403/451 or shows a CAPTCHA / bot-detection wall, note `couldn't access <page> — <reason>` inline in §5 UX Flow Notes and skip. This skill does NOT perform robots.txt pre-flight (Playwright does not enforce robots.txt natively); rely on the page response.
```

- [ ] **Step 4: CR-Δ-6 — Add trust-signal keywords to Phase A Focus row**

```
Edit:
  old_string:
    | **Focus** | "signup", "registration", "onboarding" → Onboarding. "pricing", "tiers", "promo", "bonus" → Pricing. "homepage", "landing" → Homepage. "checkout", "deposit", "withdraw" → Checkout flow. Named feature surface (e.g. "game lobby", "VIP page") → Core feature experience. |
  new_string:
    | **Focus** | "signup", "registration", "onboarding" → Onboarding. "pricing", "tiers", "promo", "bonus" → Pricing. "homepage", "landing" → Homepage. "checkout", "deposit", "withdraw" → Checkout flow. "trust signals", "social proof", "reviews", "ratings", "badges" → Core feature experience (trust surface). Named feature surface (e.g. "game lobby", "VIP page") → Core feature experience. |
```

- [ ] **Step 5: CR-Δ-1 (part 1) — Resolve Phase A vs Phase B memory path conflict (Phase A side)**

```
Edit:
  old_string:
    | **Competitors** | If active product memory (`~/.claude/memory/<project-slug>.md`) has a `**Competitors:**` line → use it. If user named specific competitors in the prompt → use those. Otherwise ask. |
  new_string:
    | **Competitors** | If active product memory (`~/.claude/memory/<project-slug>.md`) has a `**Competitors:**` line → infer here and skip the Phase B Competitors question entirely. **This is the canonical reuse path** — when memory has a list, do NOT fall through to Phase B for Competitors. If user named specific competitors in the prompt (and memory is empty) → use those. Otherwise ask in Phase B. |
```

- [ ] **Step 6: CR-Δ-1 (part 2) — Mark Phase B memory-substitution as fallback (Phase B side)**

```
Edit:
  old_string:
    - **Competitors** — header: `Targets` — "Which competitors should be included?"
      - Memory default — Use the competitor list from active product memory (substitute the real names from memory into this label at runtime)
      - Memory + best-in-class — Memory list plus 2–3 indirect / aspirational references
      - Custom list — I'll provide URLs at runtime
  new_string:
    - **Competitors** — header: `Targets` — "Which competitors should be included?"
      - Memory default — Use the competitor list from active product memory (substitute the real names from memory into this label at runtime)
      - Memory + best-in-class — Memory list plus 2–3 indirect / aspirational references
      - Custom list — I'll provide URLs at runtime

    > **Note:** The memory-substitution label above is a **fallback path** — it only applies when Phase A could not infer Competitors (memory empty AND user did not name competitors in the prompt). The primary memory-reuse path is Phase A; when memory has a `**Competitors:**` line, Phase A infers Competitors and this Phase B question is skipped entirely.
```

- [ ] **Step 7: CR-Δ-2 — Fix screenshot path co-location bug (Handoff step 1)**

```
Edit:
  old_string:
    1. **Save the markdown.** Write the full report markdown to `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md`. Create the directory if it does not exist. Screenshots already live in the `screenshots/` subdir from Playwright.
  new_string:
    1. **Save the markdown.** Write the full report markdown to `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. Create the `<focus-slug>` directory if it does not exist. Screenshots already live in `<focus-slug>/screenshots/` from Playwright (same parent directory as the markdown — the relative `screenshots/<file>.png` references in §5 resolve correctly).
```

- [ ] **Step 8: CR-Δ-7 — Confluence-attachment offer for screenshots**

```
Edit:
  old_string:
          After the call, surface a one-line note: `Screenshots are local-only at ~/Downloads/competitor-research/<slug>/screenshots/; the Confluence page's inline image references will render as broken — open the local .md to see them rendered.` Return the new page URL.
  new_string:
          After the call, surface a one-line note: `Screenshots are local-only at ~/Downloads/competitor-research/<slug>/screenshots/; the Confluence page's inline image references will render as broken — open the local .md to see them rendered.` Return the new page URL.

          **Then, if N ≥ 1 screenshots exist in the `screenshots/` subdir,** present one bonus AskUserQuestion:
          - Question: `Upload <N> screenshots to the Confluence page as attachments? (fixes the inline image references)`
          - Header: `Attach screenshots?`
          - Options:
            - `Upload all` — Iterate the screenshots/ directory and attach each via the Atlassian MCP's create-attachment tool; rewrite the inline `![desc](screenshots/<file>.png)` references in the published page to point at the Confluence attachment URLs
            - `Upload none` — Skip attachment upload; the local .md remains the canonical screenshot bundle
```

- [ ] **Step 9: CR-Δ-3 — Specify memory-differs confirmation**

```
Edit:
  old_string:
    ### Notes on memory caching
    When the PM provides a competitor list at runtime (because memory had none, or chose `Custom list` in Phase B), append it to `~/.claude/memory/<project-slug>.md` so the next invocation reuses it without asking. Create the `~/.claude/memory/` directory and the file if they do not exist. Format: a `**Competitors:**` line listing names + URLs. Do not overwrite existing competitor lists silently — confirm with one inline message if the existing memory list differs from the runtime input.
  new_string:
    ### Notes on memory caching
    When the PM provides a competitor list at runtime (because memory had none, or chose `Custom list` in Phase B), append it to `~/.claude/memory/<project-slug>.md` so the next invocation reuses it without asking. Create the `~/.claude/memory/` directory and the file if they do not exist. Format: a `**Competitors:**` line listing names + URLs.

    **When runtime input differs from the cached list, do NOT silently overwrite memory.** Present this AskUserQuestion:
    - Question: `The cached competitor list differs from your runtime input. Which set should drive this run?`
    - Header: `Competitors?`
    - Options:
      - `Use cached` — Use the cached competitors (`<list-from-memory>`) and ignore runtime input
      - `Use runtime + update memory` — Use runtime input (`<list-from-input>`) and overwrite the memory cache
      - `Use runtime, keep memory` — Use runtime input just for this run; leave the memory cache untouched
```

- [ ] **Step 10: Verify the file**

Run: `Read /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills/competitor-research/SKILL.md`
Expected: file is ~270 lines (up from 248). Verify the Phase A Focus row has trust-signal keywords; Phase A Competitors row says "infer here and skip the Phase B Competitors question"; the Handoff save-markdown path includes the `<focus-slug>/` subdir; the memory-differs AskUserQuestion is spec'd with 3 options.

---

## Task 4: Plugin metadata bump + CHANGELOG.md

**Files:**
- Modify: `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/.claude-plugin/plugin.json`
- Create: `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/CHANGELOG.md`

- [ ] **Step 1: Bump plugin.json version 1.0.0 → 1.1.0**

```
Edit:
  old_string:
      "version": "1.0.0",
  new_string:
      "version": "1.1.0",
```

- [ ] **Step 2: Create CHANGELOG.md at plugin root**

Write `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/CHANGELOG.md`:

```markdown
# Changelog

All notable changes to the CasinoSkilo plugin follow the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format and adhere to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] — 2026-05-23

### Added
- **prd-writer:** `Retention / re-engagement` as a 4th value for the `Main problem` core question. Triggered by keywords "retention", "lapsed", "re-engage", "win-back", "reactivation". (PRD-Δ-3)
- **prd-writer:** Sub-segment hints on the `Main user` Phase A row — VIP / high-roller signals add a `vip` tag in the User Story; CRM operator / lifecycle signals add a `crm` tag. (PRD-Δ-2)
- **prd-writer:** Hard cap of 25 child tickets per Double-down chain, with an explicit AskUserQuestion when §12 has 26+ rows. (PRD-Δ-8)
- **ticket-builder:** New `## PRD-driven mode` section mirrors the cross-skill contract that previously lived only in `prd-writer/SKILL.md`. (TB-Δ-8)
- **competitor-research:** Bonus AskUserQuestion after Confluence publish offering to upload screenshots as Confluence attachments. (CR-Δ-7)
- **competitor-research:** Trust-signal keywords ("trust signals", "social proof", "reviews", "ratings", "badges") in the Phase A Focus row. (CR-Δ-6)

### Changed
- **ticket-builder:** `## User Flow` is now optional. Added a 5th Phase A inferred field `Needs flow diagram` (auto-skips for bugs/copy/config; required for new features and multi-step admin). Ambiguous cases trigger a Phase C `Flow?` question. (TB-Δ-1)
- **ticket-builder:** Definition of Done now has a hard cap of 3–5 items (never 6+). (TB-Δ-2)
- **ticket-builder:** `Inferred (not asked)` block now has a hard cap of 4 bullets; if Phase A inferred 5+ fields, the 4 most-actionable are shown with a `_(+N more inferred)_` overflow line. (TB-Δ-3)
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
```

- [ ] **Step 3: Verify both files**

Run:
```bash
cat /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/.claude-plugin/plugin.json
ls -la /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/CHANGELOG.md
```
Expected: plugin.json shows `"version": "1.1.0"`; CHANGELOG.md exists at ~50 lines.

---

## Task 5: Mirror plugin cache → GitHub repo

**Files:**
- Copy from: `/Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/`
- Copy to: `/Users/talshani/Documents/GitHub/CasinoSkilo/`

- [ ] **Step 1: Confirm what the repo currently has**

Run: `ls -la /Users/talshani/Documents/GitHub/CasinoSkilo/`
Expected: only `.git/`, `docs/`, `reports/`, `tests/`, `.claude/` are present. No production plugin files yet.

- [ ] **Step 2: Copy plugin contents into the repo**

Run:
```bash
cp -r /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/.claude-plugin /Users/talshani/Documents/GitHub/CasinoSkilo/
cp -r /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills /Users/talshani/Documents/GitHub/CasinoSkilo/
cp -r /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/skills-deferred /Users/talshani/Documents/GitHub/CasinoSkilo/
cp /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/LICENSE /Users/talshani/Documents/GitHub/CasinoSkilo/
cp /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/README.md /Users/talshani/Documents/GitHub/CasinoSkilo/
cp /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/CONTRIBUTING.md /Users/talshani/Documents/GitHub/CasinoSkilo/
cp /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/CHANGELOG.md /Users/talshani/Documents/GitHub/CasinoSkilo/
```

- [ ] **Step 3: Verify the copy**

Run: `ls -la /Users/talshani/Documents/GitHub/CasinoSkilo/`
Expected: shows `.claude-plugin/`, `skills/`, `skills-deferred/`, `LICENSE`, `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, plus the pre-existing `.git/`, `docs/`, `reports/`, `tests/`, `.claude/`.

Then verify one file's contents to confirm v1.1.0 edits propagated:
```bash
grep "Needs flow diagram" /Users/talshani/Documents/GitHub/CasinoSkilo/skills/ticket-builder/SKILL.md
grep '"version": "1.1.0"' /Users/talshani/Documents/GitHub/CasinoSkilo/.claude-plugin/plugin.json
```
Both should print a matching line.

- [ ] **Step 4: Also copy the `.in_use` and `.gitignore` if present**

Run:
```bash
ls /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/.gitignore 2>/dev/null && cp /Users/talshani/.claude/plugins/cache/CasinoSkilo/casino-skilo/1.0.0/.gitignore /Users/talshani/Documents/GitHub/CasinoSkilo/
```
Note: do NOT copy `.in_use/` (that's a Claude Code runtime marker, not part of the published plugin).

---

## Task 6: Commit 1 — production plugin

**Files staged:** `.claude-plugin/`, `skills/`, `skills-deferred/`, `LICENSE`, `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, `.gitignore`

- [ ] **Step 1: Check status**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo status`
Expected: shows all the production-plugin files as untracked, plus the existing `docs/`, `reports/`, `tests/` as untracked (those go in Commit 2).

- [ ] **Step 2: Stage production-plugin files only**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo add .claude-plugin skills skills-deferred LICENSE README.md CONTRIBUTING.md CHANGELOG.md .gitignore
```

- [ ] **Step 3: Verify nothing extra got staged**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo status --short`
Expected: only the production-plugin files appear under "Changes to be committed". `docs/`, `reports/`, `tests/` should still appear as untracked under "Untracked files".

- [ ] **Step 4: Create the commit**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo commit -m "$(cat <<'EOF'
feat(skills): apply v1.1.0 test-driven fixes + brevity redesign

- ticket-builder: 8 edits — User Flow optional via Phase A heuristic, DoD hard cap, Inferred block hard cap, "assume + flag" syntax defined, Inferred placement clarified, Phase A conflict-resolution rule, PRD-driven mode section added (mirrors prd-writer chain contract).
- prd-writer: 9 edits — cross-link to ticket-builder PRD-driven mode, Main user sub-segment hints, Retention added as 4th Main problem value, Phase A conflict-resolution rule, "Double down" verbatim in frontmatter, GGR sub-tag for Success signal, Confluence parentId fallback, 25-child cap on Double-down chain, 7-question cap scope clarified.
- competitor-research: 7 edits — frontmatter description reordered, robots.txt enforcement claim dropped, trust-signal keywords added to Focus row, Phase A vs Phase B memory-substitution conflict resolved, screenshot path co-location bug fixed, memory-differs confirmation spec'd as 3-option AskUserQuestion, Confluence-attachment offer for screenshots.
- Plugin metadata: bump to 1.1.0; CHANGELOG.md added at repo root.

Resolves all 4 P0 + 5 P1 actionable items from the 120-case test audit. See CHANGELOG.md for details. Test catalog re-run pending.
EOF
)"
```

- [ ] **Step 5: Verify the commit**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo log --oneline -1`
Expected: shows the commit hash + "feat(skills): apply v1.1.0 test-driven fixes + brevity redesign".

---

## Task 7: Commit 2 — tests + reports + docs

**Files staged:** `tests/`, `reports/`, `docs/`

- [ ] **Step 1: Stage the test harness, reports, and design/plan docs**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo add tests reports docs
```

- [ ] **Step 2: Verify what's staged**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo status --short`
Expected: all `tests/`, `reports/`, `docs/` files appear under "Changes to be committed". Nothing untracked should remain (except possibly `.claude/` which is the user's IDE-extension state and should be ignored — verify it's in `.gitignore` or doesn't show up).

If `.claude/` shows as untracked, decide: either add it to `.gitignore` first, or skip it. The repo should NOT commit user-specific IDE state.

- [ ] **Step 3: Create the commit**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo commit -m "$(cat <<'EOF'
test: add 120-case behavioral test catalog + v1.0.0 audit reports + v1.1.0 design/plan

- tests/: 120 YAML test cases (40 per skill) + rubric (schema, vocabulary, runner-prompt, judge-prompt) + per-skill coverage maps + README.
- reports/: per-skill v1.0.0 audit reports (ticket-builder Green, prd-writer Yellow, competitor-research Yellow), cross-skill summary with top-10 actionable items, raw runner+judge transcripts.
- docs/superpowers/specs/: v1.1.0 design doc covering all 24 SKILL.md edits + plugin metadata + redeploy.
- docs/superpowers/plans/: v1.1.0 implementation plan (this work).

Test harness is sub-agent-dispatched (no external runtime). See tests/README.md for how to re-run.
EOF
)"
```

- [ ] **Step 4: Verify both commits are present**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo log --oneline -2`
Expected: shows 2 commits — the test+docs commit on top, the production-plugin commit below.

---

## Task 8: Push to GitHub remote

- [ ] **Step 1: Confirm remote**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo remote -v`
Expected: `origin  https://github.com/talshani8499-netizen/CasinoSkilo.git (fetch)` and same for push.

- [ ] **Step 2: Confirm current branch**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo branch --show-current`
Expected: `main` (or whatever the user's default is — adjust the next step accordingly).

- [ ] **Step 3: Push both commits to remote**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo push -u origin main`
Expected: pushes 2 commits. If the remote already has a different `main` history (unlikely for the user's empty repo), STOP and ask the user before force-pushing.

- [ ] **Step 4: Verify push landed**

Run: `git -C /Users/talshani/Documents/GitHub/CasinoSkilo log origin/main --oneline -2`
Expected: same 2 commits visible on the remote.

---

## Task 9: Re-run the test catalog against v1.1.0

The plugin cache already has the v1.1.0 edits (we made them there first). No `/plugin update` needed — the active spec is already v1.1.0. We re-run the catalog directly.

Dispatch 3 parallel sub-agents (one per skill), using the same execution prompts as the v1.0.0 run.

- [ ] **Step 1: Dispatch the 3 re-run sub-agents in parallel**

Each sub-agent reads the (now-v1.1.0) SKILL.md, the 40 case YAMLs for its skill, and produces a runner trace + judge verdict for each case. Output goes to `reports/raw/<skill>/full-run-v1.1.0.md` (do not overwrite the v1.0.0 raw runs — keep both for comparison).

Dispatch via `Agent` tool with `subagent_type: general-purpose`, `run_in_background: true`, using the same prompts the v1.0.0 run used (see `tests/rubric/runner-prompt-template.md` + `tests/rubric/judge-prompt-template.md`), with these adjustments:
- Output file path: `reports/raw/<skill>/full-run-v1.1.0.md` instead of `full-run.md`
- Inline the v1.1.0 SKILL.md content into the prompt (the PRD-writer v1.0.0 run was blocked by plugin-cache permissions; inlining avoids that)
- Specifically test that the v1.0.0 PARTIAL/FAIL cases now PASS: TB-029 (Inferred placement), CR-016 (memory path conflict), CR-038 (screenshot path), CR-040 sub-criteria, and all 8 PRD PARTIALs

- [ ] **Step 2: Wait for all 3 completions**

Each sub-agent takes ~5–10 minutes. Run all 3 in parallel (single message, 3 Agent tool calls). Do not poll — the harness notifies on completion.

- [ ] **Step 3: Confirm raw runs landed**

Run:
```bash
ls -la /Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/*/full-run-v1.1.0.md
wc -l /Users/talshani/Documents/GitHub/CasinoSkilo/reports/raw/*/full-run-v1.1.0.md
```
Expected: 3 files, each 2000+ lines.

- [ ] **Step 4: Compare against v1.0.0 baseline**

For each skill, extract the v1.1.0 PASS/PARTIAL/FAIL counts from the file header `## Summary` block and compare to the v1.0.0 baseline:

| Skill | v1.0.0 baseline | v1.1.0 expected | v1.1.0 actual |
|---|---|---|---|
| ticket-builder | 39 / 1 / 0 | ≥ 40 / 0 / 0 (Green) | _record after run_ |
| prd-writer | 32 / 8 / 0 | ≥ 38 / 2 / 0 (Green) | _record after run_ |
| competitor-research | 34 / 4 / 2 | ≥ 38 / 2 / 0 (Green) | _record after run_ |

If any skill regressed (e.g. a previously-PASSing case is now FAIL), stop and investigate before tagging the release.

---

## Task 10: Aggregate v1.1.0 reports + release decision

- [ ] **Step 1: Dispatch 3 parallel aggregator sub-agents**

Same pattern as the v1.0.0 aggregation (Tasks already done in the v1.0.0 run). Each aggregator reads `reports/raw/<skill>/full-run-v1.1.0.md` + the coverage map and produces `reports/<skill>-test-report-v1.1.0.md`.

- [ ] **Step 2: Write cross-skill summary for v1.1.0**

Create `reports/summary-v1.1.0.md` mirroring the structure of `reports/summary.md` but for the post-fix run. Include a "Delta vs v1.0.0" section showing which cases flipped (PARTIAL→PASS, FAIL→PASS) and which (if any) regressed.

- [ ] **Step 3: Decide on release tagging**

Decision tree:
- **All 3 skills Green ≥ 95% with zero regressions** → tag v1.1.0 release on GitHub.
- **Yellow (80–95%) but zero regressions** → release as v1.1.0 with a known-issues note in the release body listing remaining PARTIALs.
- **Any regressions OR any Red** → DO NOT tag. Open a follow-up issue, hotfix locally, re-run Tasks 9–10 before tagging.

- [ ] **Step 4: If tagging, push tag**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo tag -a v1.1.0 -m "v1.1.0 — test-driven fixes + brevity redesign"
git -C /Users/talshani/Documents/GitHub/CasinoSkilo push origin v1.1.0
```

Then create the GitHub release via `gh`:
```bash
gh release create v1.1.0 \
  --repo talshani8499-netizen/CasinoSkilo \
  --title "v1.1.0 — Test-Driven Fixes + Brevity Redesign" \
  --notes-file /Users/talshani/Documents/GitHub/CasinoSkilo/CHANGELOG.md
```

Note: if `--notes-file CHANGELOG.md` includes the v1.0.0 section, you may want to extract only the v1.1.0 entry into a temp file first.

- [ ] **Step 5: Commit the v1.1.0 reports**

Run:
```bash
git -C /Users/talshani/Documents/GitHub/CasinoSkilo add reports
git -C /Users/talshani/Documents/GitHub/CasinoSkilo commit -m "test: add v1.1.0 post-fix test reports + summary"
git -C /Users/talshani/Documents/GitHub/CasinoSkilo push origin main
```

- [ ] **Step 6: Confirm `/plugin update` works for downstream users**

Run `/plugin update CasinoSkilo` in this Claude Code session. Expected: the plugin cache refreshes from GitHub and shows v1.1.0. (Local cache should already be v1.1.0 from our edits; this confirms the GitHub copy is consistent.)

If `/plugin update` reports any error or version mismatch, investigate before considering the redeploy complete.

---

## Done criteria

- All 3 SKILL.md files in the plugin cache have v1.1.0 edits applied.
- GitHub repo has 2 (or 3, if v1.1.0 reports were committed) commits + v1.1.0 tag + GitHub release.
- v1.1.0 test catalog re-run shows: TB Green, PRD Green, CR Green; zero regressions.
- `/plugin update CasinoSkilo` pulls v1.1.0 successfully.
- `reports/summary-v1.1.0.md` documents the delta vs v1.0.0 (which cases flipped) and confirms zero regressions.

## Out of scope (per design)

- No migration of old competitor-research outputs at the legacy path.
- No live Atlassian MCP testing — re-run continues to stub MCP behavior.
- No new test cases for v1.1.0 additions (new Phase A field, new Retention option, etc.) — defer to v1.2.0.
- No automated CI gate.
