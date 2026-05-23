# Test Catalog YAML Schema

Every case under `tests/<skill>/cases/` follows this schema. Keep cases short and focused on **one rule** at a time.

## Top-level keys

```yaml
id: TB-007                       # required: <SKILL_PREFIX>-<NNN>, zero-padded
category: phase-a-inference      # required: one of the categories below
title: "Bug ticket-type inferred from 'broken'"   # required: one short line
references:                      # required: where in SKILL.md the rule lives
  - skill: ticket-builder        #   skill name (matches folder)
  - skill_md_lines: [57, 62]     #   inclusive line range of rule under test

preconditions:                   # required: what the runner sees
  user_input: "..."              #   the raw PM input (the "prompt to the skill")
  jira_context: null | "..."     #   simulated Jira/MCP search results, or null
  confluence_context: null | "..." #  simulated Confluence pages, or null
  active_memory: null | "..."    #   contents of ~/.claude/memory/<slug>.md, or null
  mcp_state: none                #   none | atlassian | playwright | atlassian+playwright | multiple-atlassian
  prior_artifacts: null | "..."  #   e.g. a PRD body when testing PRD-driven mode in ticket-builder
  invoking_skill: null | "..."   #   e.g. "prd-writer:double-down" when ticket-builder is chained
  parent_jira_epic: null | "..." #   when ticket-builder is in PRD-driven mode

pass_criteria:                   # required: list of assertion objects
  - id: <assertion-id>           #   ID from pass-criteria-vocabulary.md
    ...assertion-specific fields...

notes: "free-form explanation of intent"   # optional
```

## Allowed `category` values

| Value | Meaning |
|---|---|
| `frontmatter` | YAML frontmatter and description text |
| `phase-a-inference` | Phase A signal table behavior |
| `phase-b-core-questions` | Phase B core-question bank |
| `phase-c-followups` | Phase C 6 hard rules + priority order |
| `output-structure` | Required/banned sections, ASCII flow, internal shape |
| `maturity-adaptation` | PRD-writer only: Initial idea / Clear direction / Existing feature |
| `depth-adaptation` | competitor-research only: Quick scan / Detailed / Deep UX |
| `handoff` | "Ready To Gamble On It?" branching, MCP tool lookup, file save |
| `quality` | Specific-not-generic, facts/assumptions/missing, no meta-commentary |
| `edge-case` | Vague input, too-large request, missing memory, MCP failures, robots.txt etc. |

## Allowed `mcp_state` values

| Value | Meaning |
|---|---|
| `none` | No MCP servers connected |
| `atlassian` | Single Atlassian MCP connected (Jira + Confluence) |
| `playwright` | Playwright MCP connected (competitor-research only) |
| `atlassian+playwright` | Both connected |
| `multiple-atlassian` | More than one Atlassian MCP — skill should ask which to use |

## Assertion-object shape

Each `pass_criteria` entry has an `id` (from `pass-criteria-vocabulary.md`) and zero-or-more assertion-specific fields. Example:

```yaml
pass_criteria:
  - id: inferred-block-present
    must: true
  - id: inferred-includes-field
    field: "Ticket type"
    expected_value: "Bug"
    must_cite_phrase: "broken"
  - id: phase-b-skips
    questions: ["Ticket type"]
  - id: total-questions-asked-max
    max: 3
```

The judge sub-agent grades each entry independently as **PASS / FAIL / PARTIAL**, then the case's overall verdict is:

- **PASS** = all criteria PASS
- **PARTIAL** = at least one PASS and at least one PARTIAL (no FAIL)
- **FAIL** = at least one criterion FAIL

## File naming

`<SKILL_PREFIX>-<NNN>.yaml` where:
- `SKILL_PREFIX` is `TB` (ticket-builder), `PRD` (prd-writer), or `CR` (competitor-research)
- `NNN` is the 3-digit zero-padded case number (001–040)

Example: `TB-007.yaml`, `PRD-018.yaml`, `CR-040.yaml`.

## Conventions

1. **One rule per case.** If you need to verify three rules at once, split into three cases.
2. **`user_input` should read like a real PM message.** No instruction-tuning artifacts ("Please test that…"). The runner should never know it's being tested.
3. **`pass_criteria` should be unambiguous.** Avoid subjective terms like "good", "appropriate", "reasonable". Use concrete checks the judge can grade.
4. **`references` always cite the SKILL.md line(s)** where the rule under test lives. This is how the judge looks up ground truth.
5. **Don't duplicate scenario fixtures inline.** Heavy Jira/Confluence blobs go under `tests/<skill>/fixtures/` and are referenced by relative path:
   ```yaml
   preconditions:
     jira_context: !include ../fixtures/vip-progress-bar-jira-search.md
   ```
   (The harness expands `!include` when dispatching the runner.)

## Example case file

```yaml
id: TB-018
category: phase-c-followups
title: "Phase C rejects generic placeholder option 'Use the existing system'"
references:
  - skill: ticket-builder
  - skill_md_lines: [94]

preconditions:
  user_input: "Add a VIP progress bar to the casino home"
  jira_context: |
    PR-470 / closed / "Casino home redesign" / component: home
    PR-481 / open / "Smartico loyalty event wiring" / component: integrations
  confluence_context: null
  active_memory: null
  mcp_state: atlassian

pass_criteria:
  - id: phase-c-no-banned-placeholders
    banned_phrases:
      - "Use the existing system"
      - "Option A"
      - "TBD"
      - "I'll specify later"
  - id: phase-c-options-are-concrete
    must_reference: ["file path", "API name", "event name", "system", "component", "project key"]

notes: "Hard rule #2 in Phase C — every option label must be concrete, never a placeholder."
```
