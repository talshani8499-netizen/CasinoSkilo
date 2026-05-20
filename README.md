# CasinoSkilo

**AI Product Skills Kit — context-aware Claude Code skills for Product Managers.**

CasinoSkilo is a Claude Code plugin containing product-management workflows. Each skill scans internal company context (Jira/Confluence via MCP), asks guided multiple-choice questions, and returns a structured artifact that can be pasted directly into Jira, Confluence, or Slack.

> These are not prompts. They are reusable product workflows that turn company knowledge into better product execution.

---

## MVP — 4 skills

| Skill | Output | Best for |
|---|---|---|
| `ticket-builder` | Jira-ready ticket (user story, scope, flow, edge cases, DoD, analytics) | Turning a request into a ticket engineering can pick up |
| `prd-writer` | Full PRD adapted to idea maturity | Initial ideas, clear directions, or existing-feature iterations |
| `product-discovery` | Discovery brief ending in Proceed / Research More / Park | Pre-commit thinking on raw ideas and stakeholder requests |
| `competitor-research` | Comparison report with gaps, opportunities, suggested tickets | Pre-PRD market input, redesigns, positioning |

## Deferred (`skills-deferred/`)

Not loaded at runtime — kept in the repo for future activation.

| Skill | Status |
|---|---|
| `experiment-planner` | Deferred from MVP. Move back to `skills/` to enable. |
| `ux-copy` | Deferred from MVP. Move back to `skills/` to enable. |

---

## Install

### From a private GitHub repo (recommended)
```
/plugin marketplace add <your-org>/CasinoSkilo
/plugin install casino-skilo@CasinoSkilo
```

### From a local checkout (for refinement / testing)
```
/plugin marketplace add /path/to/CasinoSkilo
/plugin install casino-skilo@CasinoSkilo
```

Verify with `/skill` — six skills should be listed.

---

## How each skill behaves

Every skill follows the same operating logic:

1. **Context-first.** Searches Jira/Confluence MCP tools for related material before asking anything. Separates findings into Facts (cited), Assumptions (marked), and Missing (called out). If no MCP is connected, skips silently.
2. **Guided questions.** Asks 4–7 questions in `A / B / C / D. Other: write your own` format. Reduces cognitive load and avoids blank-page syndrome.
3. **Structured output.** Returns a copy-pasteable markdown artifact in the format the spec defines for that skill type.
4. **Company format adaptation.** Adapts to the company's existing Jira ticket / Confluence PRD format when found in scanned context.

---

## Requirements

- **Claude Code** (any recent version).
- **Optional MCP servers** for context scanning:
  - Atlassian / Jira MCP — for ticket and epic context
  - Confluence MCP — for PRD, strategy, and brand-voice context
  - Playwright MCP — for the `competitor-research` skill's browsing mode
- **Competitor list** (`competitors.json`) — only for `competitor-research`. See `skills/competitor-research/competitors.example.json`.

Skills work without MCP — they'll just skip the context-gathering step and ask the PM directly.

---

## Status

**v0.1.0 — lean scaffold.** Each skill ships with the structure, guided questions, output template, and quality rules from the spec. The kit is intentionally lean so each skill can be **hand-refined** with company-specific tone, terminology, and examples before going live. See [`CONTRIBUTING.md`](./CONTRIBUTING.md) for the refinement workflow.

---

## License

See [LICENSE](./LICENSE).
