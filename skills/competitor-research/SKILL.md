---
name: competitor-research
description: Use when a PM wants structured competitor research against a predefined competitor list. Reads competitors.json, scans Jira/Confluence for company baseline, asks 4 guided questions to set scope and depth, optionally uses Playwright for public-page browsing and screenshots, and returns a comparison report with gaps, opportunities, and suggested Jira tickets.
---

# Competitor Research

## Purpose
Run structured competitor research against a known competitor list and produce consistent competitive insights for PRDs, roadmap decisions, redesigns, or strategic positioning. The advanced mode uses Playwright to browse public competitor pages and capture screenshots.

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

## Required setup
This skill needs three inputs the team must maintain:

### 1. Competitor list
Create `competitors.json` at the team's preferred path (template provided at `skills/competitor-research/competitors.example.json`). Schema:
```json
{
  "competitors": [
    { "name": "Competitor A", "url": "https://...", "category": "Direct competitor" }
  ]
}
```

### 2. Research focus
Specified by the PM at runtime (homepage, signup flow, pricing, checkout, onboarding, etc.).

### 3. Company baseline
The skill should know our current product experience to compare against. Source from Confluence product docs, screenshots, PRDs, or PM-provided description.

## Context to gather (before questions)
Search Jira/Confluence MCP tools for:

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

Classify findings as **Facts**, **Assumptions**, or **Missing**. If no MCP tools are connected, skip silently and proceed.

## Guided questions
Ask one at a time, in this exact format:

> **Question N:** <question>
> A. <option>
> B. <option>
> C. <option>
> D. Other: write your own

**Question 1:** What should this competitor research focus on?
A. Onboarding and signup flow
B. Pricing and packaging
C. Core feature experience
D. Other: write your own

**Question 2:** Which competitors should we include?
A. Direct competitors only
B. Direct + indirect competitors
C. Market leaders / best-in-class examples
D. Other: write your own

**Question 3:** What output do you need from this research?
A. Comparison table
B. Screenshots and UX notes
C. Product opportunities and recommendations
D. Other: write your own

**Question 4:** How deep should this research be?
A. Quick scan
B. Detailed product comparison
C. Deep UX flow analysis
D. Other: write your own

## Playwright behavior (when available)
If a Playwright MCP/tool is available, use it to:
- Open competitor websites (public pages only)
- Navigate homepage, pricing, signup, and selected flows
- Capture screenshots
- Extract visible CTAs and key page copy
- Note structural patterns (hero, social proof, pricing tiers, trust signals)

**Strict limits:**
- Public pages only
- Never bypass paywalls, authentication, bot protection, or restricted areas
- Do not log in to competitor products
- Do not scrape at high volume

## Research depth levels
Adapt output to Question 4:

- **Quick scan**: high-level findings, main differences, 3–5 opportunities. No screenshots required.
- **Detailed product comparison**: full comparison table, screenshots, feature gaps, recommendations.
- **Deep UX flow analysis**: step-by-step flows, UX patterns, friction analysis, screenshots, suggested improvements.

## Output
Produce the following structure exactly (markdown):

```markdown
# Competitor Research Report: [Research Focus]

## 1. Research Scope
[What was analyzed.]

## 2. Competitors Reviewed
- [Competitor 1]
- [Competitor 2]

## 3. Method
- Sources reviewed:
- Pages reviewed:
- Screenshots captured:
- Jira/Confluence context reviewed:

## 4. High-Level Summary
[Short summary of the most important findings.]

## 5. Comparison Table
| Area | Our Product | Competitor A | Competitor B | Competitor C | Opportunity |
|---|---|---|---|---|---|
| Homepage messaging | ... | ... | ... | ... | ... |
| Signup flow | ... | ... | ... | ... | ... |
| Pricing | ... | ... | ... | ... | ... |
| Trust signals | ... | ... | ... | ... | ... |
| Core feature | ... | ... | ... | ... | ... |

## 6. UX Flow Notes
### Competitor A
- [Observation]
### Competitor B
- [Observation]

## 7. Screenshots Summary
- Screenshot 1: [What it shows]
- Screenshot 2: [What it shows]

## 8. Key Patterns Found
- [Pattern 1]

## 9. Product Gaps
- [Gap 1]

## 10. Product Opportunities
- [Opportunity 1]

## 11. Recommended Actions
- [Action 1]

## 12. Suggested Jira Tickets
- [Ticket 1]
```

## Quality rules
- Be specific, not generic — always tie observations to a competitor and a page
- Use company terminology found in context
- Separate facts (with source URL or screenshot reference) from assumptions
- Call out missing information explicitly (e.g., couldn't access pricing page)
- Respect public-only / no-login limit strictly

## Advanced behaviors (apply when relevant)
- Identify table-stakes features vs. differentiation opportunities
- Identify UX, messaging, and pricing-strategy gaps
- Extract CTAs, homepage structure, onboarding steps for side-by-side view
- Suggest product tickets from gaps
- Suggest PRD input topics
- Suggest experiment ideas based on competitor patterns
- Generate a short leadership-friendly summary on request
