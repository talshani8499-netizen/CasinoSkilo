---
name: competitor-research
description: Use when a PM wants a structured competitor research report — returns a lean 7-section comparison report for PRDs, roadmap decisions, redesigns, or strategic positioning. Reads competitor list from auto-memory, scans Jira/Confluence for company baseline, adaptively asks only the questions input doesn't answer, and optionally uses Playwright for public-page browsing and screenshots. Ends with a "Ready To Gamble On It?" handoff that publishes to Confluence (Product Knowledge Base space) or saves markdown only. This skill is research-only — it does NOT create Jira tickets. Use prd-writer or ticket-builder downstream if research findings should turn into work.
---

# Competitor Research

## Purpose
Run structured competitor research against a known competitor list and produce consistent competitive insights for PRDs, roadmap decisions, redesigns, or strategic positioning. The advanced mode uses Playwright to browse public competitor pages and capture screenshots. Output adapts to the depth the PM picks at runtime, and to the company's existing research format when one is found in Confluence.

## When to use
- Competitor feature comparison
- Onboarding flow research
- Pricing and packaging research
- Landing page research
- Checkout flow research
- Signup flow comparison
- Messaging and positioning research
- UX pattern research
- Trust signal research
- Product gap analysis
- Market standard analysis
- Pre-PRD competitor input
- Strategic positioning research

## Inputs the skill expects
Three sources, used in this priority order:

### 1. Competitor list (memory-driven)
Read the active product's memory file at `~/.claude/memory/<project-slug>.md` (e.g. `~/.claude/memory/21com.md`) and pick up the competitor list. The project slug is the active product (read from prior memory, from the working directory, or from the PM if unknown). If memory has no list yet, fall back to PM input at runtime, then cache the answer back to memory so the next run reuses it. **Do NOT require a `competitors.json` file** — memory is the source of truth.

### 2. Research focus
Specified by the PM at runtime (homepage, signup flow, pricing, checkout, onboarding, named feature surface, etc.). Phase A attempts to infer this from the prompt before asking.

### 3. Company baseline
The "Our Product" column in the comparison table. Source from Confluence PRDs, strategy pages, the PM's prior PRD outputs (e.g. `~/Downloads/prds/<slug>.md`), or PM-provided description.

## Context to gather (before questions)
Search whatever Jira/Confluence MCP tools are available. Look for:

**Jira:**
- Existing competitor-related tickets
- Product gap tickets
- Roadmap items inspired by competitors
- Feature requests mentioning competitors
- Sales objections translated into product work
- Past research tasks

**Confluence:**
- Competitor research pages
- Positioning, GTM, and pricing docs
- Product strategy
- Market research
- Existing feature comparison tables
- Previous screenshots
- Past decision logs

Classify findings as **Facts** (with source link), **Assumptions** (clearly marked), or **Missing** (called out). If no MCP tools are connected, skip silently and proceed.

## Adaptive questions
The skill is an **adaptive interview**, not a fixed form. Run the four phases below in order. All questions are asked via **AskUserQuestion** (the in-terminal interactive chooser, one question at a time). The tool auto-adds an "Other" option, so provide exactly 3 concrete option labels per question. Total questions asked across all phases must never exceed 7 (any combination of core + adaptive).

### Phase A — Infer answers from input + context
Before asking anything, attempt to infer each of the 4 core answers from the user's input, the Jira/Confluence context scan, and active product memory. Mark an answer **inferred** only if the signal is unambiguous; otherwise fall through to Phase B for that question.

| Core question | Inference signals |
|---|---|
| **Focus** | "signup", "registration", "onboarding" → Onboarding. "pricing", "tiers", "promo", "bonus" → Pricing. "homepage", "landing" → Homepage. "checkout", "deposit", "withdraw" → Checkout flow. "trust signals", "social proof", "reviews", "ratings", "badges" → Core feature experience (trust surface). Named feature surface (e.g. "game lobby", "VIP page") → Core feature experience. |
| **Competitors** | If active product memory (`~/.claude/memory/<project-slug>.md`) has a `**Competitors:**` line → infer here and skip the Phase B Competitors question entirely. **This is the canonical reuse path** — when memory has a list, do NOT fall through to Phase B for Competitors. If user named specific competitors in the prompt (and memory is empty) → use those. Otherwise ask in Phase B. |
| **Output emphasis** | "leadership update", "exec summary", "one-pager" → Strategic recommendations. "screenshots", "visual", "annotated" → Screenshots + UX notes. Otherwise → Comparison + opportunities. |
| **Depth** | "quick", "fast", "scan", "30 min" → Quick scan. "deep", "step-by-step", "every screen" → Deep UX flow. Otherwise → Detailed comparison. |

For each inferred answer, record the exact phrase that revealed it — that phrase later appears in the report's "Inferred (not asked)" block so the user can audit.

### Phase B — Ask only the core questions Phase A couldn't infer
Use the 4 core questions below but ONLY for the ones Phase A left unanswered. Skip the rest.

**Core question bank:**

- **Focus** — header: `Focus` — "What is this research focused on?"
  - Onboarding / signup flow — Landing through first deposit
  - Pricing & packaging — Tiers, promotions, bonus structure
  - Core feature experience — A specific surface (game lobby, profile, search, etc.)

- **Competitors** — header: `Targets` — "Which competitors should be included?"
  - Memory default — Use the competitor list from active product memory (substitute the real names from memory into this label at runtime)
  - Memory + best-in-class — Memory list plus 2–3 indirect / aspirational references
  - Custom list — I'll provide URLs at runtime

  > **Note:** The memory-substitution label above is a **fallback path** — it only applies when Phase A could not infer Competitors (memory empty AND user did not name competitors in the prompt). The primary memory-reuse path is Phase A; when memory has a `**Competitors:**` line, Phase A infers Competitors and this Phase B question is skipped entirely.

- **Output emphasis** — header: `Output` — "What should the report emphasize?"
  - Comparison + opportunities — Side-by-side matrix + gap analysis
  - Screenshots + UX notes — Annotated screenshots + step-by-step observations
  - Strategic recommendations — Positioning, market patterns, leadership-friendly summary

- **Depth** — header: `Depth` — "How deep should the research go?"
  - Quick scan — Public homepage + main flow, ~30 min equivalent of findings
  - Detailed comparison — Full matrix + screenshots of key surfaces, ~2-hour equivalent
  - Deep UX flow — Step-by-step per competitor with friction analysis + screenshots of every screen

### Phase C — Adaptive follow-ups (up to 3)
After core is settled, scan the input + Jira/Confluence + memory for **material unknowns** — decisions that meaningfully change the report output. For each unknown that survives the rules below, generate one AskUserQuestion call.

**Hard rules for adaptive follow-ups:**
1. **Maximum 3 follow-ups.** Stop sooner when no material unknowns remain.
2. **Each option label must be concrete.** Reference a real competitor name, market, source, or finding from the context scan. **Banned:** "Use the existing source", "Option A", "TBD", "I'll specify later", or any other generic placeholder.
3. **Skip the question entirely if input or context already answers it.** Convert that answer into an inline assumption in the report instead.
4. **Only ask about decisions that change the output.** NOT exact phrasing of observations, exact screenshot names, exact ticket titles.
5. **Priority order when picking which unknowns to ask about:**
   1. **Region / market scope** — global vs. a specific jurisdiction (e.g. Curacao/MGA only) vs. a specific market (LATAM, Africa, Turkey)
   2. **Source mix** — public competitor sites only vs. also third-party reviews (Trustpilot, AskGamblers, CasinoMeister)
   3. **Time horizon** — one-time snapshot vs. recurring (re-run quarterly, track diffs)
   4. **Authentication boundary** — strict public-pages-only (default) vs. include logged-in screenshots from PRDs/Confluence if available (never sign up to a competitor)
6. **If you cannot write 3 concrete option labels for a given unknown, the unknown is not material — assume + flag in the report, do not ask.**

**Worked example (matches Tal's 21.com competitors — these are the kind of follow-ups the skill should generate, not generic templates):**
- *"What region for this research?"* — A: 21.com licensed markets only (Curacao + MGA jurisdictions) / B: Global, no jurisdiction filter / C: LATAM + Africa (matches existing CS_Africa / CSO Confluence spaces).
- *"Include third-party reviews?"* — A: Trustpilot + AskGamblers (English) only / B: Add CasinoMeister threads for VIP-tier signal / C: Public competitor sites only — no third-party.

**Bad follow-ups (do NOT generate):**
- "What should the screenshot filenames be?" (mechanical detail)
- "How should observations be phrased?" (vague, no concrete options)
- "Use the existing competitors or different ones?" (already answered in Phase B)

### Phase D — Output
Proceed to the Output section below. If anything was inferred in Phase A, surface it in the "Inferred (not asked)" block at the top of the report.

## Playwright behavior (when available)
If Playwright MCP tools are available (`mcp__playwright__browser_navigate`, `mcp__playwright__browser_snapshot`, `mcp__playwright__browser_take_screenshot`, `mcp__playwright__browser_console_messages`), use them to:
- Open competitor websites (public pages only)
- Navigate homepage, pricing, signup, and selected flows
- Capture screenshots (saved to `~/Downloads/competitor-research/<focus-slug>/screenshots/<competitor>-<page>.png`)
- Extract visible CTAs and key page copy via the page snapshot
- Note structural patterns (hero, social proof, pricing tiers, trust signals)
- Reference each screenshot inline in the report markdown as `![desc](screenshots/<file>.png)` — relative path, so the saved .md + screenshots subdir form a self-contained bundle locally

**Strict limits:**
- Public pages only
- Never bypass paywalls, authentication, bot protection, or restricted areas
- Do not log in to competitor products
- Do not scrape at high volume — limit to ~5 pages per competitor per run
- Public pages only. If a page returns HTTP 403/451 or shows a CAPTCHA / bot-detection wall, note `couldn't access <page> — <reason>` inline in §5 UX Flow Notes and skip. This skill does NOT perform robots.txt pre-flight (Playwright does not enforce robots.txt natively); rely on the page response.

## Research depth levels
Adapt output to the Depth answer:

- **Quick scan**: high-level findings, main differences, 3–5 opportunities. Screenshots optional. ~30-min equivalent of digging.
- **Detailed product comparison**: full comparison table, screenshots of key surfaces, feature gaps, prioritized recommendations. ~2-hour equivalent.
- **Deep UX flow analysis**: step-by-step flows per competitor, UX pattern catalog, friction analysis, screenshots of every screen, side-by-side comparison, suggested experiments. ~4+ hour equivalent.

## Output
Default 7-section structure (adapt to company format when found in Confluence):

    # Competitor Research Report: [Focus]

    > **Inferred (not asked):** _(include this block only if Phase A inferred at least one core answer; one bullet per inference, citing the exact phrase from input or context that revealed it)_
    > - Focus: Onboarding — from "compare our signup to competitors"
    > - Competitors: Stake, 1Xbet, Rollbit, Bc.Game — from memory `~/.claude/memory/21com.md`

    | Field | Value |
    |---|---|
    | **Status** | Draft v1.0 |
    | **Author** | [PM name from memory] |
    | **Date** | [YYYY-MM-DD] |
    | **Depth** | [Quick scan / Detailed / Deep UX] |
    | **Region scope** | [from Phase C if asked, else "global"] |

    ## 1. Research Scope
    [What was analyzed; which competitors; which pages; method (sources reviewed, Playwright used or not, Jira/Confluence context reviewed). 2–4 bullet lines, not a separate Method section.]

    ## 2. Competitors Reviewed
    - [Competitor 1] — <URL>
    - [Competitor 2] — <URL>

    ## 3. Executive Summary
    [Tight summary of the most important findings — the leadership-friendly version. 3–6 sentences max.]

    ## 4. Comparison Table
    | Area | Our Product | <Comp A> | <Comp B> | <Comp C> | Opportunity |
    |---|---|---|---|---|---|
    | Homepage messaging | ... | ... | ... | ... | ... |
    | Signup flow | ... | ... | ... | ... | ... |
    | Pricing | ... | ... | ... | ... | ... |
    | Trust signals | ... | ... | ... | ... | ... |
    | Core feature | ... | ... | ... | ... | ... |

    ## 5. UX Flow Notes
    [Per-competitor observations. Screenshots referenced inline as `![desc](screenshots/<competitor>-<page>.png)` paths — no separate Screenshots section.]

    ### <Competitor A>
    - [Observation 1] — `![homepage hero](screenshots/competitorA-home.png)`
    - [Observation 2]

    ### <Competitor B>
    - [Observation 1]

    ## 6. Key Patterns
    [Cross-competitor patterns. Call out table-stakes (everyone does this) vs. differentiation (only one does this) explicitly.]

    ## 7. Gaps & Opportunities
    [Merged prioritized list. Each item: what's missing on our side, why it matters, suggested action. This is the final section — the report ends here. If findings should become work, feed this section into prd-writer or ticket-builder as a downstream step, but do NOT generate tickets from this skill.]

    - **<Gap 1 title>** — Missing: ... Why it matters: ... Action: ...
    - **<Gap 2 title>** — Missing: ... Why it matters: ... Action: ...

## Quality rules
- Be specific, not generic — always tie observations to a competitor and a page (or screenshot)
- Use company terminology found in the context scan
- Separate facts (cite source URL or screenshot reference) from assumptions (mark clearly)
- Call out missing information explicitly (e.g. "couldn't access pricing page — geo-blocked")
- Respect public-only / no-login limit strictly
- If memory has no competitor list yet, ask via Phase B then cache the answer back to memory before producing the report

## Advanced behaviors (apply when relevant)
- Identify table-stakes features vs. differentiation opportunities
- Identify UX, messaging, and pricing-strategy gaps
- Extract CTAs, homepage structure, onboarding steps for side-by-side view
- Suggest PRD input topics (can feed directly into `prd-writer` skill)
- Suggest experiment ideas based on competitor patterns
- Generate a short leadership-friendly summary on request

## Handoff — "Ready To Gamble On It?"
After the report is rendered, save it to disk and ask the user for the final call. Steps in order:

1. **Save the markdown.** Write the full report markdown to `~/Downloads/competitor-research/<focus-slug>/<focus-slug>-<YYYY-MM-DD>.md`. Create the `<focus-slug>` directory if it does not exist. Screenshots already live in `<focus-slug>/screenshots/` from Playwright (same parent directory as the markdown — the relative `screenshots/<file>.png` references in §5 resolve correctly).
2. **Ask the user using AskUserQuestion.**
    - Question: `Ready To Gamble On It?`
    - Header: `Gamble?`
    - Options:
      - `Bet on it` — Publish the full report to the Confluence **Product Knowledge Base** space via Atlassian MCP
      - `Hold the chip` — Save the .md (and screenshots subdir) only, no Confluence page
3. **Branch on the answer.**
    - **`Bet on it` + Atlassian MCP connected:** Find the connected Atlassian MCP's create-Confluence-page tool (look for a tool name matching `mcp__*atlassian*` or `mcp__*confluence*` with `createConfluencePage` or `create_page` in it; if multiple Atlassian MCPs are connected, ask the user which one to use). Call it with:
      - `cloudId` = the active fastglobal cloud ID (look it up via the Atlassian MCP's accessible-resources tool — typically `getAccessibleAtlassianResources` or `get_accessible_atlassian_resources`)
      - `spaceId` = `772571142` (**Product Knowledge Base**, key `PKB`)
      - `parentId` = `772571521` (the PKB overview homepage — required; PKB rejects top-level creates with 404)
      - `contentFormat` = `markdown`
      - `title` = the report title (e.g. `Competitor Research Report: Onboarding`)
      - `body` = the full report markdown verbatim
      After the call, surface a one-line note: `Screenshots are local-only at ~/Downloads/competitor-research/<slug>/screenshots/; the Confluence page's inline image references will render as broken — open the local .md to see them rendered.` Return the new page URL.

      **Then, if N ≥ 1 screenshots exist in the `screenshots/` subdir,** present one bonus AskUserQuestion:
      - Question: `Upload <N> screenshots to the Confluence page as attachments? (fixes the inline image references)`
      - Header: `Attach screenshots?`
      - Options:
        - `Upload all` — Iterate the screenshots/ directory and attach each via the Atlassian MCP's create-attachment tool; rewrite the inline `![desc](screenshots/<file>.png)` references in the published page to point at the Confluence attachment URLs
        - `Upload none` — Skip attachment upload; the local .md remains the canonical screenshot bundle
    - **`Bet on it` + Atlassian MCP NOT connected:** Report `Atlassian MCP not connected — saved markdown only at <path>` and stop.
    - **`Hold the chip`:** Confirm `Saved at <path>. No Confluence page created.`
4. **Always** end by printing the absolute path to the saved markdown file so the user can copy/paste it anywhere.

This skill is research-only. It does NOT create Jira tickets. If the findings should turn into work, hand the report's §7 Gaps & Opportunities to `prd-writer` (for a full PRD on a gap) or to `ticket-builder` (for a one-off ticket) as a separate, follow-up invocation — never inside this skill.

### Notes on memory caching
When the PM provides a competitor list at runtime (because memory had none, or chose `Custom list` in Phase B), append it to `~/.claude/memory/<project-slug>.md` so the next invocation reuses it without asking. Create the `~/.claude/memory/` directory and the file if they do not exist. Format: a `**Competitors:**` line listing names + URLs.

**When runtime input differs from the cached list, do NOT silently overwrite memory.** Present this AskUserQuestion:
- Question: `The cached competitor list differs from your runtime input. Which set should drive this run?`
- Header: `Competitors?`
- Options:
  - `Use cached` — Use the cached competitors (`<list-from-memory>`) and ignore runtime input
  - `Use runtime + update memory` — Use runtime input (`<list-from-input>`) and overwrite the memory cache
  - `Use runtime, keep memory` — Use runtime input just for this run; leave the memory cache untouched
