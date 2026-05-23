# CasinoSkilo Skill Test Harness

Behavioral test suite for the three CasinoSkilo skills:

- [`ticket-builder`](../tests/ticket-builder/) — 40 cases
- [`prd-writer`](../tests/prd-writer/) — 40 cases
- [`competitor-research`](../tests/competitor-research/) — 40 cases

**120 cases total.** Each case is a self-contained YAML file under `tests/<skill>/cases/`. Cases live in-repo so they ship next to the kit and can be re-run after any SKILL.md change.

## Why a separate harness?

These skills are LLM-prompted behaviors, not deterministic code. There is no `pytest` to run. Instead, this harness uses a two-stage sub-agent dispatch to grade behavior against the spec:

1. **Runner** sub-agent reads the SKILL.md + the case `preconditions` and simulates what the skill would do — Phase A inferences, every `AskUserQuestion` it would emit, the final artifact markdown, and any tool calls it would make at handoff. **No real tools are called.**
2. **Judge** sub-agent reads the runner's output, the case `pass_criteria`, and the SKILL.md as ground truth, and grades each criterion **PASS / FAIL / PARTIAL** with line-level evidence.

The harness then aggregates the verdicts into per-skill reports in [`../reports/`](../reports/).

## Layout

```
tests/
├── README.md                       (this file)
├── rubric/
│   ├── test-catalog-schema.md      YAML schema every case follows
│   ├── pass-criteria-vocabulary.md Shared assertion IDs + meaning
│   ├── runner-prompt-template.md   Prompt used to dispatch the runner
│   └── judge-prompt-template.md    Prompt used to dispatch the judge
├── ticket-builder/
│   ├── cases/TB-001.yaml … TB-040.yaml
│   └── fixtures/                   Reusable input/context blobs
├── prd-writer/
│   ├── cases/PRD-001.yaml … PRD-040.yaml
│   └── fixtures/
└── competitor-research/
    ├── cases/CR-001.yaml … CR-040.yaml
    └── fixtures/
```

## Test ID conventions

- `TB-XXX` = ticket-builder
- `PRD-XXX` = prd-writer
- `CR-XXX` = competitor-research

Within each skill, IDs are grouped by category:

| Category | TB range | PRD range | CR range | Count/skill |
|---|---|---|---|---|
| A. Frontmatter & metadata | 001–003 | 001–003 | 001–003 | 3 |
| B. Phase A inference | 004–011 | 004–011 | 004–011 | 8 |
| C. Phase B core questions | 012–016 | 012–016 | 012–016 | 5 |
| D. Phase C follow-up rules | 017–024 | 017–024 | 017–024 | 8 |
| E. Output structure | 025–031 | 025–031 | 025–031 | 7 |
| F. Maturity / Depth adaptation | n/a (×3 reallocated) | 032–034 | 032–034 | 3 |
| G. Handoff & MCP integration | 032–036 | 035–039 | 035–039 | 5 |
| H. Quality & specificity | 037–038 | 040 | 040 | 2 |
| I. Edge cases & failure modes | 039–040 | (folded into G/H) | (folded into G/H) | 2 |

> **Note on ticket-builder:** it has no Maturity/Depth adaptation, so those 3 slots are reallocated — 1 extra to Output, 1 extra to Handoff, 1 extra to Edge cases. See the actual case files for definitive coverage.

## How to add a case

1. Pick the next free ID in your skill's category range.
2. Copy [`rubric/test-catalog-schema.md`](rubric/test-catalog-schema.md) as a template.
3. Fill in `preconditions` (the simulated user input + Jira/Confluence/memory state + MCP state) and `pass_criteria` (assertion IDs from [`rubric/pass-criteria-vocabulary.md`](rubric/pass-criteria-vocabulary.md)).
4. If your assertion isn't in the vocabulary, add it there first so other cases can reuse it.

Keep each case **focused on one rule**. Composite cases hide which rule failed.

## How to run

Dispatch is by sub-agent, batched 5 cases per runner / judge round, 3 batches in parallel:

```
For each skill:
  For each category batch (8 batches × 5 cases):
    Dispatch runner sub-agent with:
      - tests/rubric/runner-prompt-template.md
      - SKILL.md (full)
      - Cases in the batch (YAML)
    Capture structured output to reports/raw/<skill>/runner-<batch>.md
    Dispatch judge sub-agent with:
      - tests/rubric/judge-prompt-template.md
      - SKILL.md (full)
      - Runner output
      - Cases pass_criteria
    Capture verdicts to reports/raw/<skill>/judge-<batch>.md
  Aggregate into reports/<skill>-test-report.md
```

The aggregator produces `reports/<skill>-test-report.md` with:

- Executive header (pass/fail/partial counts, Green/Yellow/Red verdict)
- Per-category summary table
- Detailed per-case results
- **Actionable items** (P0/P1/P2 with exact SKILL.md edits)

…plus a cross-skill [`../reports/summary.md`](../reports/summary.md).

## Interpreting the report

- **PASS**: behavior matches the spec line referenced by the case.
- **PARTIAL**: behavior is close but degraded (e.g., right phase but wrong header text).
- **FAIL**: behavior contradicts the spec.

The **Actionable items** section is the punch list. Each item lists the exact SKILL.md line, the symptom, and a proposed surgical edit. Apply them in priority order:

- **P0** — Skill produces wrong output (e.g., banned section appears, wrong MCP tool called, Phase C exceeds 3 follow-ups)
- **P1** — Skill degrades output quality (e.g., generic placeholder option slipped past rule 2, missing "Inferred (not asked)" block)
- **P2** — Polish (e.g., header wording drift, missing kebab-case enforcement on slug)

## What the harness does NOT do

- Does not call real Jira / Confluence / Playwright MCPs. All MCP state is stubbed in case preconditions.
- Does not modify any SKILL.md. Reports recommend edits; you decide whether to apply.
- Does not test the deferred skills (`skills-deferred/`).
- Does not enforce a CI gate — runs are on-demand via sub-agent dispatch.

## Source of truth

The 3 SKILL.md files in the plugin cache are the spec. When updating, also bump the relevant pass_criteria in the cases if a rule changes.
