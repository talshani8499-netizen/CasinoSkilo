---
name: ticket-builder
description: Use when a PM wants to turn a raw feature idea, bug, improvement, or stakeholder request into a Jira-ready ticket. Scans Jira/Confluence for related context, adaptively asks only the questions your input doesn't already answer, adds up to 3 context-derived follow-ups for real unknowns, and returns a lean ticket with user story, description, ASCII user flow, and DoD. Ends with a "Ready To Gamble On It?" handoff that can push to Jira via MCP or save markdown only.
---

# Ticket Builder

## Purpose
Turn a raw product request into a Jira-ready ticket that design, engineering, QA, and stakeholders can act on without a back-and-forth. Reduce ambiguity, surface missing pieces (analytics, edge cases, permissions, mobile), and adapt to the company's existing ticket format.

## When to use
- New feature tickets
- Improvement tickets for existing features
- Bug tickets
- Technical enablement / internal tooling tickets
- UX improvement tickets
- Analytics / event-tracking tickets
- A/B test implementation tickets
- Admin panel tickets
- Compliance-related tickets
- Edge case handling tickets
- Follow-up tickets from a PRD
- Breaking a large epic into smaller tickets

## Context to gather (before questions)
Search whatever Jira/Confluence MCP tools are available for related material. Look for:

**Jira:**
- Similar existing tickets in the same product area
- Open and recently closed tickets touching the same flow
- Bugs connected to the same feature
- Existing epics and their child tickets
- Components, labels, squads, and owners
- The team's typical user-story format
- The team's typical Definition of Done structure
- QA notes and previous edge cases on related tickets
- Recurring or reopened tickets in this area

**Confluence:**
- PRDs related to the feature
- Technical documentation and product flow docs
- Design decision documents
- Known product constraints
- Product terminology and glossary
- Analytics tracking plans

Classify everything found as **Facts** (with source link), **Assumptions** (clearly marked), or **Missing** (called out). If no MCP tools are connected, skip silently and proceed.

## Adaptive questions
The skill is an **adaptive interview**, not a fixed form. Run the four phases below in order. All questions are asked via **AskUserQuestion** (the in-terminal interactive chooser, one question at a time). The tool auto-adds an "Other" option, so provide exactly 3 concrete option labels per question. Total questions asked across all phases must never exceed 7 (any combination of core + adaptive).

### Phase A — Infer answers from input + context
Before asking anything, attempt to infer each of the 4 core answers from the user's input and the Jira/Confluence context scan. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question.

| Core question | Inference signals |
|---|---|
| **Ticket type** | "fix", "broken", "regression", "bug" → Bug. "add", "new", "build" → Feature. "improve", "enhance", "redesign", "update" → Improvement. |
| **Main user** | "player", "user", "customer" → End user. "admin", "back office", "BO", "CMS" → Admin. "CS", "support", "ops", "VIP team", "agent" → Support/ops. |
| **Main goal** | "fix", "broken", "blocking", "regression" → Fix friction. "drive deposits", "retention", "GGR", "compliance", "legal" → Business need. otherwise → Improve UX. |
| **Connection** | reference to existing component/file/flow → Changes or Extends. "new flow", "from scratch", "doesn't exist today" → New flow. |

For each inferred answer, record the exact phrase that revealed it — that phrase later appears in the ticket's "Inferred (not asked)" block so the user can audit.

### Phase B — Ask only the core questions Phase A couldn't infer
Use the same 4 core questions (drawn from the bank below) but ONLY for the ones Phase A left unanswered. Skip the rest.

**Core question bank:**

- **Ticket type** — header: `Ticket type` — "What type of ticket is this?"
  - New feature — A wholly new capability that does not exist yet
  - Improvement — Enhancement to an existing feature or flow
  - Bug or issue — Something is broken or behaving incorrectly

- **Main user** — header: `Main user` — "Who is the main user affected?"
  - End user — Players / customers using the product
  - Admin / internal — Internal users in the admin panel or back office
  - Support / ops — CS, VIP, or operations teams

- **Main goal** — header: `Main goal` — "What is the main goal of this ticket?"
  - Improve UX — Make the experience better, clearer, or more engaging
  - Fix friction — Remove a problem, bug, or blocker
  - Business need — Support a business, revenue, or operational outcome

- **Connection** — header: `Connection` — "Is this connected to an existing flow or feature?"
  - Changes a flow — Modifies behavior of an existing flow
  - Extends a feature — Adds something on top of an existing feature
  - New flow — Brand-new flow or capability with no existing equivalent

### Phase C — Adaptive follow-ups (up to 3)
After core is settled, scan the input + Jira/Confluence context for **material unknowns** — decisions that meaningfully change the ticket output. For each unknown that survives the rules below, generate one AskUserQuestion call.

**Hard rules for adaptive follow-ups:**
1. **Maximum 3 follow-ups.** Stop sooner when no material unknowns remain.
2. **Each option label must be concrete.** Reference a real file path, API name, event name, system, component, person, project key, or finding from the context scan. **Banned:** "Use the existing system", "Option A", "I'll specify later", or any other generic placeholder.
3. **Skip the question entirely if input or context already answers it.** Convert that answer into an inline assumption in the ticket instead.
4. **Only ask about decisions that change the output.** NOT styling, color, exact copy, exact analytics property names — those default + flag, never ask.
5. **Priority order when picking which unknowns to ask about:**
   1. Data source ambiguity (multiple systems could provide the data)
   2. Scope edges (one platform vs all, one segment vs all)
   3. Behavioral choice (replace vs overlay, sync vs async)
   4. Trigger / cadence (every event vs first only, real-time vs polled)
   5. Permissions / segments (all users vs subset)
6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the ticket, do not ask.**

**Worked example (a VIP progress bar ticket on 21.com — these are the kind of follow-ups the skill should generate, not generic templates):**
- *"Where does points-to-next-tier come from?"* — A: Smartico `LOYALTY_POINTS_UPDATE` event / B: PS-native VIP API (currently being scoped) / C: Hybrid: Smartico now, abstract behind a service, swap to PS later.
- *"How does the module fit on the existing hero (`components/home/banner.tsx`)?"* — A: Replaces first carousel slide for logged-in users / B: Persistent strip below the carousel / C: Overlay on top of the first slide.
- *"Casino home only or sports home too?"* — A: Casino only, scoped to /home under PR-470 / B: Casino + sports parallel build / C: Casino now, sports as follow-up child ticket.

**Bad follow-ups (do NOT generate):**
- "What color should the progress bar be?" (defer to design)
- "What should the analytics event be called?" (default + flag in ticket)
- "How should it look?" (vague, no concrete options possible)

### Phase D — Output
Proceed to the Output section below. If anything was inferred in Phase A, surface it in the "Inferred (not asked)" block at the top of the ticket so the user can audit and correct.

## Output
Keep the ticket lean. Produce **only** the sections below — nothing else. Do not add Background, Context, Problem, Desired Outcome, Scope, Functional Requirements, Edge Cases, Analytics, Dependencies, Open Questions, or "Builder notes". Adapt to the company's existing ticket format if Jira context reveals a different convention.

    # [Ticket Title]

    **Ticket type:** [Feature / Improvement / Bug]
    **Parent epic (if any):** [link]
    **Component:** [file or product area]
    **Labels:** [suggested labels]

    > **Inferred (not asked):** _(include this block only if Phase A inferred at least one core answer; one bullet per inference, citing the exact phrase from input or context that revealed it)_
    > - Ticket type: Bug — from "fix the bug where..."
    > - Main user: End user — from "guest profiles"

    ## User Story
    As a [user type], I want to [action], so that [value].

    ## Description
    [2–4 sentences describing what we are building or fixing, in plain product language. For features/improvements: what the change is and the value it delivers. For bugs: what is broken, where, and what the correct behavior should be. No background, no history, no rationale beyond the value line — just a crisp statement of the work.]

    ## User Flow
    [ASCII flowchart of the happy-path flow inside a fenced code block. Keep it tight — one diagram, no prose steps before or after unless absolutely needed for clarity. Use box-drawing characters (┌─┐│└┘├┤┬┴) and arrows (▼ → ─▶). Branches/decisions render as ┌─────┐ with a `?` and labeled outgoing arrows.]

    ## Definition of Done
    - [DoD item 1]
    - [DoD item 2]

## Handoff — "Ready To Gamble On It?"
After the ticket is rendered, save it to disk and ask the user for the final call. Steps in order:

1. **Save the markdown.** Write the full ticket markdown to `~/Downloads/tickets/<ticket-slug>.md`. Create the directory if it does not exist. The slug is a kebab-cased version of the ticket title.
2. **Ask the user using AskUserQuestion.**
    - Question: `Ready To Gamble On It?`
    - Header: `Gamble?`
    - Options:
      - `Bet on it` — Push this ticket to Jira (uses the Atlassian MCP if connected; otherwise the markdown file is the deliverable)
      - `Hold the chip` — Just keep the markdown file, do not push to Jira
3. **Branch on the answer.**
    - **`Bet on it` + Atlassian MCP connected:** Find the connected Atlassian/Jira MCP's create-issue tool (look for a tool name matching `mcp__*atlassian*` or `mcp__*jira*` with `createIssue`, `createJiraIssue`, or `create_issue` in it; if multiple Jira MCPs are connected, ask the user which one to use). Call it with the project key, issue type, summary (ticket title), and description (ticket body in markdown). Confirm by returning the new issue key and URL. If the create fails, report the error and confirm the markdown file is still saved.
    - **`Bet on it` + Atlassian MCP NOT connected:** Report `Atlassian MCP not connected — saved markdown only at <path>` and stop.
    - **`Hold the chip`:** Confirm `Saved at <path>. No Jira ticket created.`
4. **Always** end by printing the absolute path to the saved markdown file so the user can copy/paste it anywhere.

## Quality rules
- Be specific, not generic
- Use company terminology found in scanned context
- Separate facts (cite source) from assumptions (mark clearly) — but only inline within the sections above; do not add a standalone facts/assumptions section
- Suggest a better ticket title if the input is vague (apply it directly in the title — do not add a separate "suggested title" note)
- If the request is too large, say so in one sentence above the ticket and propose splitting — do not bury this in a notes section
- Output must be copy-pasteable into Jira (markdown)
- Do NOT add any meta-commentary, "builder notes", or post-ticket reflections. The ticket ends at Definition of Done.
