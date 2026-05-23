# Runner Sub-Agent Prompt Template

This prompt is dispatched to a `general-purpose` sub-agent. The runner's job is to **simulate** the skill against a batch of test cases — it does NOT call any real tools.

---

## Prompt

You are simulating the **CasinoSkilo `<SKILL_NAME>`** skill against {N} test cases. You will produce a structured trace for each case so a judge can later grade behavior against the spec.

**IMPORTANT: Do not call any real tools.** Specifically:
- Do not call `AskUserQuestion` — instead, write out the exact question you would have asked, its header, and its 3 concrete options.
- Do not call any MCP tool — instead, write out the tool name pattern you would have searched for and the parameters you would have passed.
- Do not write any file — instead, write out the absolute path you would have written to.

The runner's deliverable is a single structured Markdown block per case, formatted exactly as shown below. Match the section headings verbatim so the judge can parse it.

### Ground truth

The skill spec is the file `<SKILL_MD_PATH>` (included in full below). When a case's behavior is ambiguous, follow the spec literally — do not improvise.

```
<INSERT FULL SKILL.md CONTENT HERE>
```

### Test cases in this batch

The {N} cases are listed below. For each one, produce one trace block with this exact structure:

````
## TRACE: <CASE_ID>

### Preconditions
<one-paragraph restatement of the case preconditions, including user_input, MCP state, and any context/memory>

### Phase A — Inferences
For each of the 4 core fields, output:
- **<Field name>:** Inferred to "<value>" — citation: "<exact phrase from input/context>"
  OR
- **<Field name>:** Not inferred (will fall through to Phase B)

If Phase A inferred zero fields, write `none — every core field will be asked in Phase B`.

### Phase B — Questions asked
List every Phase B question you would have emitted via AskUserQuestion. For each:
```
Q<n>: <question text>
  header: <header string>
  options:
    1) <option label>
    2) <option label>
    3) <option label>
  (the AskUserQuestion tool auto-adds an "Other" option)
```
If Phase B asks zero questions, write `none — all 4 core fields were inferred in Phase A`.

For each Phase B question, also list **what answer you assume the simulated PM gives** (pick the most plausible based on the user_input — this drives the rest of the simulation).

### Phase C — Follow-ups
List every Phase C follow-up question (max 3). For each, use the same format as Phase B questions, plus a one-line `rationale:` field explaining which "material unknown" it covers and why it survived the 6 hard rules.

If Phase C emits zero follow-ups, write `none — no material unknowns survived the rules` and list what unknowns were converted to inline assumptions in the artifact instead.

For each Phase C question, also list **what answer you assume the simulated PM gives**.

### Phase D — Artifact
Render the full final artifact markdown verbatim, exactly as the skill would output it. Include the `Inferred (not asked)` block at the top if Phase A inferred at least one field. Include every spec'd section. Do NOT include any banned sections.

Wrap the artifact in a fenced block tagged with the artifact type:
````
```markdown-artifact
# <Title>
... full artifact ...
```
````

### Handoff
1. **File save:** state the absolute path you would write to, e.g. `~/Downloads/tickets/add-a-vip-progress-bar-to-the-casino-home.md`. Confirm the directory creation step.
2. **Gamble question:** the exact question, header, and option labels you would emit via AskUserQuestion at the handoff.
3. **Simulated user choice:** pick the most plausible option based on the case's `mcp_state` (e.g. if `mcp_state: atlassian`, simulate the user picking "Bet on it").
4. **Tool call:** if the user choice triggers a tool call, write out:
   - the tool-name regex pattern you would have searched for (e.g. `mcp__*atlassian*` with `createIssue|createJiraIssue|create_issue`)
   - the exact parameters you would have passed (e.g. `projectKey`, `issueType`, `summary`, `description` for Jira; `cloudId`, `spaceId`, `parentId`, `contentFormat`, `title`, `body` for Confluence)
5. **Final message:** the exact message you would print to the user at the end (e.g. `Created PR-482 at https://….atlassian.net/browse/PR-482. Saved at /Users/.../Downloads/tickets/<slug>.md.`).

### Special-mode notes (if applicable)
If the case has `invoking_skill: prd-writer:double-down`, also state:
- That Phase B and Phase C were skipped (PRD-driven mode)
- Where each Phase A inference cites the PRD (e.g. `from PRD §10 FR-2`)
- That the handoff auto-chose "Bet on it" without asking the user
- The parent epic key supplied

If the case is for competitor-research with no memory list, state that memory was appended after Phase B with the `**Competitors:**` line.

If the case is for competitor-research with `mcp_state` including `playwright`, list the screenshot files you would have captured and their relative paths in §5 UX Flow Notes.

````

After all {N} traces, end with a single `## END OF BATCH` line.

### Rules

1. **Do not improvise behavior the spec doesn't define.** If the spec is silent, write `spec silent — defaulted to <X>` and continue.
2. **Stay deterministic per case.** Don't ask yourself "what should I do" — read the SKILL.md, match the case, and produce the trace.
3. **Be explicit about every banned thing avoided.** If Phase C had a tempting styling question, say so and explain why it was skipped (rule 4).
4. **One trace per case. No commentary between cases.** The judge parses on the `## TRACE:` heading.

Start with case <FIRST_CASE_ID> and produce traces in order.
