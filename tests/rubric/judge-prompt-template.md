# Judge Sub-Agent Prompt Template

This prompt is dispatched to a `general-purpose` (or `code-reviewer`) sub-agent after the runner produces traces. The judge grades each case against its `pass_criteria` and emits a structured verdict block per case.

---

## Prompt

You are grading the CasinoSkilo **`<SKILL_NAME>`** skill against {N} test cases. You will read the runner's traces and grade each case's `pass_criteria` independently.

You are NOT the runner. Do not re-simulate the skill. Only grade what the trace shows against the spec and the case's criteria.

### Ground truth

The spec is `<SKILL_MD_PATH>`, included in full below.

```
<INSERT FULL SKILL.md CONTENT HERE>
```

### Runner traces

The runner produced traces for these {N} cases (one `## TRACE: <CASE_ID>` block per case). All traces are concatenated below.

```
<INSERT RUNNER OUTPUT HERE>
```

### Cases under test (with pass_criteria)

The {N} YAML case files are included below in full. Use each case's `id`, `references`, and `pass_criteria` to look up the right rule and assertion.

```
<INSERT N CASE YAML FILES HERE>
```

### Your task

For each case, emit exactly one verdict block in this format:

````
## VERDICT: <CASE_ID>

**Title:** <case title>
**SKILL.md ref:** <skill>:L<start>-L<end>
**Trace section consulted:** <Phase A / Phase B / Phase C / Phase D / Handoff>
**Overall:** PASS | PARTIAL | FAIL

### Criteria

| # | Criterion ID | Verdict | Evidence | Cause (if not PASS) |
|---|---|---|---|---|
| 1 | <assertion-id> | PASS \| PARTIAL \| FAIL | <one-line excerpt from trace> | <one-sentence cause> |
| 2 | … | … | … | … |

### Notes
<one paragraph max — any nuance the table can't capture>

### Suggested SKILL.md edit (only if FAIL or PARTIAL)
Priority: P0 | P1 | P2
Location: `skills/<skill>/SKILL.md:L<n>`
Symptom: <one sentence>
Proposed edit:
```
<exact replacement text, surgical>
```
````

After all {N} verdict blocks, end with a single `## END OF JUDGEMENT` line.

### How to grade each criterion

Use the **`tests/rubric/pass-criteria-vocabulary.md`** definitions (included below) as the canonical interpretation.

```
<INSERT pass-criteria-vocabulary.md CONTENT HERE>
```

**PASS** — The trace clearly demonstrates the rule. Cite a one-line excerpt from the trace as evidence.

**PARTIAL** — The trace shows the rule was *attempted* but is degraded:
- Right shape, wrong field/header text
- Right behavior, missing one expected element
- Spec ambiguity that the runner resolved in a defensible way but not the canonical way

**FAIL** — The trace contradicts the rule:
- Banned section appears in output
- Phase C exceeds 3 follow-ups
- MCP tool-lookup pattern doesn't match the spec'd regex
- `Inferred (not asked)` block missing when Phase A inferred ≥1 field
- Banned generic placeholder ("Use the existing system", "Option A", "TBD", etc.) appears in a Phase C option label

### Priority for the Suggested Edit

- **P0** — Skill produces wrong output that a PM would have to manually fix. Examples: wrong section appears, MCP fallback message text differs, Phase C exceeds cap, Double-down chain produces wrong artifact count.
- **P1** — Skill degrades output quality. Examples: missing inferred-block citation, generic option label slipped past Phase C rule 2, missing kebab-case slug.
- **P2** — Polish. Examples: header wording drift, missing optional element, ASCII flow arrow style inconsistency.

The proposed edit MUST be surgical (a small, targeted change to the SKILL.md text). Do NOT propose redesigning the skill.

### Hard rules for the judge

1. **No grading from prior knowledge.** Only use the SKILL.md + the trace + the case YAML. If the spec is silent on a criterion, return PARTIAL with note `spec silent — defaulted in trace; consider clarifying SKILL.md`.
2. **Don't punish defensible spec ambiguity.** If the runner picked one of two reasonable readings, return PARTIAL (not FAIL) and suggest a P2 clarification edit.
3. **Cite trace evidence verbatim.** Quote ≤1 line. The reader of the report needs to see the exact substring.
4. **One verdict per case. No commentary between verdicts.** The aggregator parses on `## VERDICT:`.

Start with case <FIRST_CASE_ID> and emit verdicts in order.
