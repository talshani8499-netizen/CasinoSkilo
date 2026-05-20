---
name: prd-writer
description: Use when a PM wants to turn an idea, initiative, or discovery outcome into a full PRD. Scans Jira/Confluence for related context, adaptively asks only the questions input doesn't already answer, adds up to 3 context-derived follow-ups for real unknowns, and returns a maturity-adapted PRD. Ends with a "Ready To Gamble On It?" handoff that can push to Confluence (Product Knowledge Base space) and optionally chain the ticket-builder skill to create the Jira epic + child tickets, or save markdown only.
---

# PRD Writer

## Purpose
Turn an idea, feature request, stakeholder ask, or discovery outcome into a structured Product Requirements Document. Force the right product thinking up front, surface missing pieces, and produce a PRD that engineering, design, and stakeholders can use directly. The output adapts to how mature the idea is and to the company's existing PRD format when one is found.

## When to use
- New feature PRDs
- Product improvement / iteration PRDs
- MVP definition
- Internal tool or admin panel PRDs
- User flow redesign PRDs
- Monetization / pricing PRDs
- Compliance-related PRDs
- Experiment-to-feature PRDs
- Technical product PRDs
- Cross-team initiative PRDs

## Context to gather (before questions)
Search whatever Jira/Confluence MCP tools are available. Look for:

**Jira:**
- Related epics and their child tickets
- Similar feature tickets
- Bugs related to the feature
- Past implementation work and decisions
- Current roadmap tickets in this area
- Known dependencies, components, and owners

**Confluence:**
- Existing PRDs (to learn the company's PRD format)
- Product strategy documents
- Previous decision docs
- Research summaries and discovery docs
- UX guidelines and brand voice
- Analytics documentation and event taxonomies
- Technical architecture notes
- Release notes
- Known limitations and constraints

Classify findings as **Facts** (with source link), **Assumptions** (clearly marked), or **Missing** (called out). If no MCP tools are connected, skip silently and proceed.

## Adaptive questions
The skill is an **adaptive interview**, not a fixed form. Run the four phases below in order. All questions are asked via **AskUserQuestion** (the in-terminal interactive chooser, one question at a time). The tool auto-adds an "Other" option, so provide exactly 3 concrete option labels per question. Total questions asked across all phases must never exceed 7 (any combination of core + adaptive).

### Phase A — Infer answers from input + context
Before asking anything, attempt to infer each of the 4 core answers from the user's input and the Jira/Confluence context scan. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question.

| Core question | Inference signals |
|---|---|
| **Maturity** | "we already have", "v2 of", existing PRD found, live Jira epic → Existing feature. "from scratch", "thinking about", "not sure", "exploring" → Initial idea. "spec out", "ready to build", "write the requirements", "we're committing to" → Clear direction. |
| **Main user** | "player", "user", "customer" → End user. "admin", "back office", "BO", "CMS" → Admin. "CS", "support", "ops", "VIP team", "agent" → Support/ops. |
| **Main problem** | "blocked", "can't", "confused", "stuck" → Blocked/confused. "drop", "abandon", "churn", "not converting" → Drop-off. "manual", "slow", "tedious", "spreadsheets", "no tool for" → Internal workflow. |
| **Success signal** | "convert", "activate", "sign up", "deposit", "GGR" → Conversion. "fewer tickets", "support load", "complaints" → Reduced friction. "DAU", "retention", "sessions", "engagement", "stickiness" → Engagement. |

For each inferred answer, record the exact phrase that revealed it — that phrase later appears in the PRD's "Inferred (not asked)" block so the user can audit.

### Phase B — Ask only the core questions Phase A couldn't infer
Use the 4 core questions below but ONLY for the ones Phase A left unanswered. Skip the rest.

**Core question bank:**

- **Maturity** — header: `Maturity` — "How mature is this feature idea?"
  - Initial idea — Needs product thinking and structure
  - Clear direction — Needs full PRD and requirements
  - Existing feature — Needs improvement or iteration

- **Main user** — header: `Main user` — "Who is the main user affected?"
  - End user — Players / customers using the product
  - Admin / internal — Internal users in the CMS or back office
  - Support / ops — CS, VIP, or operations teams

- **Main problem** — header: `Main problem` — "What is the main problem this should solve?"
  - Blocked / confused — Users can't complete or understand the flow
  - Drop-off — Users not converting or churning
  - Internal workflow — Internal teams need a better tool or process

- **Success signal** — header: `Success` — "What is the main success signal?"
  - Conversion — Higher activation / conversion / deposit rate
  - Reduced friction — Fewer support tickets / less drop-off
  - Engagement — More sessions / retention / usage

### Phase C — Adaptive follow-ups (up to 3)
After core is settled, scan the input + Jira/Confluence context for **material unknowns** — decisions that meaningfully change the PRD output. For each unknown that survives the rules below, generate one AskUserQuestion call.

**Hard rules for adaptive follow-ups:**
1. **Maximum 3 follow-ups.** Stop sooner when no material unknowns remain.
2. **Each option label must be concrete.** Reference a real file path, API name, event name, system, component, person, project key, or finding from the context scan. **Banned:** "Use the existing system", "Option A", "TBD", "I'll specify later", or any other generic placeholder.
3. **Skip the question entirely if input or context already answers it.** Convert that answer into an inline assumption in the PRD instead.
4. **Only ask about decisions that change the output.** NOT styling, color, exact copy, exact analytics property names — those default + flag, never ask.
5. **Priority order when picking which unknowns to ask about:**
   1. **Scope edges** — MVP vs full vision, one platform vs all, one segment vs all
   2. **System / data ownership** — which platform owns the data or logic (e.g., Smartico vs Pragmatic Solutions vs in-house vs Sidekick engine)
   3. **Rollout strategy** — feature-flag-gated, gradual %, segment-by-segment, full launch
   4. **Cross-feature dependencies** — sits on top of feature X, requires feature Y first
   5. **Monetization / business model** — free vs paid, gated by VIP tier, no monetization
6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the PRD, do not ask.**

**Worked example (Community Chat PRD on 21.com — these are the kind of follow-ups the skill should generate, not generic templates):**
- *"What's the MVP cut?"* — A: Chat rooms + S0/S1/S2 gates only, defer cards/leaderboard / B: Chat + Big Win + Pinned, no leaderboard or tipping / C: Full v3.0 scope as in Epic PR-266.
- *"Who owns moderation tooling?"* — A: PS Admin Panel native / B: Smartico campaign console / C: Custom CMS module under PR-280.
- *"Casino home only, or sportsbook home too at launch?"* — A: Casino only at launch / B: Casino + sports in parallel / C: Casino now, sports as a follow-up epic.

**Bad follow-ups (do NOT generate):**
- "What color should the chat header be?" (defer to design)
- "What should the analytics event be called?" (default + flag in PRD)
- "How should it look?" (vague, no concrete options possible)

### Phase D — Output
Proceed to the Output section below. If anything was inferred in Phase A, surface it in the "Inferred (not asked)" block at the top of the PRD so the user can audit and correct.

## Maturity-driven adaptation
Adapt emphasis in the output based on the Maturity answer:

- **Initial idea**: emphasize Problem Statement, User Pain, Assumptions, Validation Plan, MVP Suggestion. De-emphasize detailed requirements. Surface unresolved decisions inline within the relevant section (Scope, Requirements, etc.) — do NOT add a separate Open Questions section.
- **Clear direction**: emphasize Full Requirements, User Flows, Edge Cases, Analytics, Jira Breakdown. Fold team handoffs into the relevant Requirements bullets — do NOT add a separate Dependencies section.
- **Existing feature iteration**: emphasize Current Behavior, Proposed Change, Why Current Flow Isn't Enough, Migration Impact, Existing Users, Analytics Comparison. Call out regression risk inline within the Proposed Change section — do NOT add a separate Risks section.

If the company has its own PRD format in Confluence, match that instead of the template below.

## Output
Default structure (adapt to company format when found):

    # PRD: [Feature Name]

    > **Inferred (not asked):** _(include this block only if Phase A inferred at least one core answer; one bullet per inference, citing the exact phrase from input or context that revealed it)_
    > - Maturity: Existing feature — from "we're on v2 of raffles"
    > - Main user: End user — from "players who deposit"

    ## 1. Overview
    ## 2. Problem Statement
    ## 3. Target Users
    ## 4. Goals
       ### User Goals / ### Business Goals / ### Product Goals
    ## 5. Scope (In Scope / Out of Scope)
    ## 6. User Stories
       [For each story: ASCII workflow diagram (happy path) + an Edge Cases table (Case | Expected behavior | Notes). Do NOT use Gherkin.]
    ## 7. User Flow
       [End-to-end ASCII flowchart in a fenced code block, box-drawing characters ┌─┐│└┘├┤┬┴ and arrows ▼ → ─▶.]
    ## 8. Requirements
       ### Functional / ### Non-Functional (Performance, Security,
            Permissions, Accessibility, Localization, Compliance)
    ## 9. UX / UI Considerations (screens, empty/error states, mobile)
    ## 10. Analytics & Success Metrics
       ### Primary Metric / ### Secondary Metrics / ### Tracking Events
    ## 11. Edge Cases
    ## 12. Suggested Jira Breakdown (Epic + child tickets)

## Quality rules
- Be specific, not generic
- Use company terminology found in the context scan
- Separate facts (cite source) from assumptions (mark clearly)
- Call out missing information explicitly
- Match the company's existing PRD format when found in Confluence
- Output must be copy-pasteable into Confluence

## Advanced behaviors (apply when relevant)
- Identify missing product thinking
- Suggest MVP vs later phases and split into phases
- Detect unclear user value or unclear business value
- Suggest success metrics and analytics events
- Generate a Jira ticket breakdown from the PRD
- Generate alternate audiences of the same PRD on request: stakeholder summary, engineering handoff version, leadership one-pager, shorter Confluence-friendly version

## Handoff — "Ready To Gamble On It?"
After the PRD is rendered, save it to disk and ask the user for the final call. Steps in order:

1. **Save the markdown.** Write the full PRD markdown to `~/Downloads/prds/<prd-slug>.md`. Create the directory if it does not exist. The slug is a kebab-cased version of the PRD title.
2. **Ask the user using AskUserQuestion.**
    - Question: `Ready To Gamble On It?`
    - Header: `Gamble?`
    - Options:
      - `Bet on it` — Publish to the Confluence **Product Knowledge Base** space via Atlassian MCP
      - `Hold the chip` — Save the .md file only, no Confluence page
      - `Double down` — Publish to Confluence AND build the Jira epic + child tickets by chaining the `ticket-builder` skill (one ticket per row in §12 Suggested Jira Breakdown)
3. **Branch on the answer.**
    - **`Bet on it` + Atlassian MCP connected:** Find the connected Atlassian MCP's create-Confluence-page tool (look for a tool name matching `mcp__*atlassian*` or `mcp__*confluence*` with `createConfluencePage` or `create_page` in it; if multiple Atlassian MCPs are connected, ask the user which one to use). Call it with:
      - `cloudId` = the active fastglobal cloud ID (look it up via the Atlassian MCP's accessible-resources tool — typically `getAccessibleAtlassianResources` or `get_accessible_atlassian_resources`)
      - `spaceId` = `772571142` (**Product Knowledge Base**, key `PKB`)
      - `parentId` = `772571521` (the PKB overview homepage — required; PKB rejects top-level creates with 404)
      - `contentFormat` = `markdown`
      - `title` = the PRD title (e.g. `PRD: Login with Telegram`)
      - `body` = the full PRD markdown verbatim
      Return the new page URL. If the create fails, report the error and confirm the markdown file is still saved.
    - **`Bet on it` + Atlassian MCP NOT connected:** Report `Atlassian MCP not connected — saved markdown only at <path>` and stop.
    - **`Hold the chip`:** Confirm `Saved at <path>. No Confluence page created.`
    - **`Double down` + Atlassian MCP connected:**
      1. Create the Confluence page first (same parameters as `Bet on it`).
      2. Create the parent Jira sub-epic by calling the Atlassian/Jira MCP's create-issue tool (look for a tool name matching `mcp__*atlassian*` or `mcp__*jira*` with `createJiraIssue`, `createIssue`, or `create_issue` in it; same lookup pattern as ticket-builder) using the PRD's §12 sub-epic title and a description that links to the new Confluence page. Capture the new epic's key.
      3. Iterate the §12 Suggested Jira Breakdown. For **each** row, invoke the `ticket-builder` skill in **PRD-driven mode** with this contract:
         - Input: the row's title + type + owner area.
         - Upstream context: the full PRD body, supplied as if it were the Jira/Confluence scan output (treat the PRD as Facts).
         - Parent: the sub-epic key created in step 2 — ticket-builder pushes children under this epic.
         - **Hard instruction to ticket-builder:** "PRD-driven mode — skip Phase B (no core questions) and Phase C (no adaptive follow-ups). Phase A infers all four core answers from the PRD body; surface them in the ticket's `Inferred (not asked)` block citing the PRD section (e.g. `from PRD §10 FR-2`). If a material unknown is unanswered by the PRD, follow your own rule: assume + flag inline. Do NOT call AskUserQuestion for any ticket in this batch. At the handoff, auto-choose `Bet on it` to push to Jira under the supplied parent epic — do NOT ask the user."
      4. Return the Confluence URL, the parent sub-epic key, and the full list of created child ticket keys.
    - **`Double down` + Atlassian MCP NOT connected:** Same fallback as `Bet on it`.
4. **Always** end by printing the absolute path to the saved markdown file so the user can copy/paste it anywhere.

### Notes on the Double down chain
The PRD is the source of truth for the chained ticket-builder calls — every Phase A inference must cite the PRD section it came from, never invent context. The user is asked exactly **one** question during this branch (the Gamble handoff itself), regardless of how many child tickets §12 contains. A PRD with 14 child tickets produces 14 Jira tickets + 1 epic + 1 Confluence page from a single user click. If the PRD §12 row is too thin for Phase A to infer a ticket type (e.g. just "Misc — TBD"), ticket-builder defaults to type=Task with an inline `Open: ticket type not inferable from PRD §12 — confirm with owner` line in the ticket body, and proceeds.
