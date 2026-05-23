# Pass Criteria Vocabulary

Shared assertion IDs used across all 120 cases. Each ID has a fixed shape, a fixed meaning, and (where relevant) a fixed mapping to a SKILL.md line. Reusing IDs is what keeps the harness consistent — if a rule changes, you update it here once and every case picks it up.

When you need a new assertion, add it here first.

---

## A — Frontmatter & metadata

### `frontmatter-yaml-valid`
The skill's `SKILL.md` has a YAML frontmatter block (between `---` lines) that parses as valid YAML and contains at least `name` and `description`.
```yaml
- id: frontmatter-yaml-valid
```

### `frontmatter-description-trigger`
`description` begins with the literal phrase `Use when` (the standard trigger).
```yaml
- id: frontmatter-description-trigger
```

### `frontmatter-description-names-output`
`description` names the output type so Claude can match user intent (e.g. "returns a lean ticket", "returns a maturity-adapted PRD", "returns a lean 7-section comparison report").
```yaml
- id: frontmatter-description-names-output
  expected_output_type: "Jira-ready ticket"   # or "PRD", "comparison report"
```

---

## B — Phase A inference

### `phase-a-infers-field`
Given the case's `user_input` (and optional context), Phase A correctly infers the named core field to the expected value, citing the exact phrase that triggered it.
```yaml
- id: phase-a-infers-field
  field: "Ticket type"               # one of the 4 core fields for this skill
  expected_value: "Bug"
  must_cite_phrase: "broken"         # exact substring of user_input that triggered
```

### `phase-a-does-not-infer-field`
Given the case's input (which is intentionally ambiguous), Phase A should leave the named field uninferred and let Phase B ask it.
```yaml
- id: phase-a-does-not-infer-field
  field: "Main user"
```

### `phase-a-resolves-conflict`
Given conflicting signals in the input (e.g. "fix the new feature"), Phase A resolves to the named field using documented signal priority OR explicitly does not infer.
```yaml
- id: phase-a-resolves-conflict
  field: "Ticket type"
  acceptable_outcomes: ["Bug", "<not inferred>"]
```

### `inferred-block-present`
The output artifact contains the `> **Inferred (not asked):**` block at the top (just after frontmatter/metadata lines, before the first section).
```yaml
- id: inferred-block-present
  must: true                          # set false to assert block is ABSENT
```

### `inferred-block-omitted-when-empty`
When Phase A inferred zero fields, the `Inferred (not asked)` block is omitted (not rendered as an empty block).
```yaml
- id: inferred-block-omitted-when-empty
```

### `inferred-includes-field`
The `Inferred (not asked)` block contains a bullet for the named field with the expected value and a phrase citation.
```yaml
- id: inferred-includes-field
  field: "Ticket type"
  expected_value: "Bug"
  must_cite_phrase: "broken"
```

---

## C — Phase B core questions

### `phase-b-skips`
Phase B does NOT ask the named questions (because Phase A inferred them).
```yaml
- id: phase-b-skips
  questions: ["Ticket type", "Main user"]
```

### `phase-b-asks`
Phase B DOES ask the named questions (because Phase A didn't infer them).
```yaml
- id: phase-b-asks
  questions: ["Main goal", "Connection"]
```

### `phase-b-question-shape`
Each Phase B question has exactly **3 concrete options** (the AskUserQuestion tool auto-adds an "Other") and the spec'd `header` string.
```yaml
- id: phase-b-question-shape
  question: "Ticket type"
  expected_header: "Ticket type"
  expected_options_count: 3
```

### `phase-b-uses-ask-user-question`
All Phase B questions are emitted via `AskUserQuestion`, not free-form text prompts.
```yaml
- id: phase-b-uses-ask-user-question
```

### `phase-b-options-match-spec`
The 3 options for the named Phase B question match the labels in the skill's core question bank verbatim.
```yaml
- id: phase-b-options-match-spec
  question: "Ticket type"
  expected_options: ["New feature", "Improvement", "Bug or issue"]
```

---

## D — Phase C follow-ups

### `phase-c-max-3`
Phase C emits **at most 3** follow-up questions. Zero is allowed (when no material unknowns survive).
```yaml
- id: phase-c-max-3
```

### `phase-c-no-banned-placeholders`
None of the Phase C option labels contain any banned generic placeholder.
```yaml
- id: phase-c-no-banned-placeholders
  banned_phrases:
    - "Use the existing system"
    - "Use the existing source"
    - "Option A"
    - "TBD"
    - "I'll specify later"
```

### `phase-c-options-are-concrete`
Every Phase C option references at least one of: a real file path, API name, event name, system name, component, person, project key, market, region, or finding from the context scan.
```yaml
- id: phase-c-options-are-concrete
  must_reference_any_of: ["file path", "API name", "event name", "system", "component", "project key", "market", "region"]
```

### `phase-c-skips-when-context-answers`
Phase C does NOT ask about the named topic because the case's `jira_context`/`confluence_context`/`active_memory` already answers it. The skill must convert that answer to an inline assumption instead.
```yaml
- id: phase-c-skips-when-context-answers
  topic: "data source for points-to-next-tier"   # human-readable topic
  inline_assumption_expected: true                # the artifact should mention the assumption inline
```

### `phase-c-skips-styling-copy-questions`
Phase C does NOT ask about styling, color, exact copy, or exact analytics property names.
```yaml
- id: phase-c-skips-styling-copy-questions
```

### `phase-c-priority-order-respected`
When multiple material unknowns exist, the follow-ups picked are at the top of the skill's priority list (e.g. for ticket-builder: data source ambiguity > scope edges > behavioral > trigger > permissions).
```yaml
- id: phase-c-priority-order-respected
  skill: ticket-builder
  expected_top_topic: "data source ambiguity"
```

### `phase-c-fallback-to-assume-and-flag`
When the runner cannot write 3 concrete options for an unknown, it does NOT ask the question; the unknown is converted to an inline assumption + flag in the artifact.
```yaml
- id: phase-c-fallback-to-assume-and-flag
  topic: "preferred animation library"
```

### `total-questions-asked-max`
Total user-facing questions across Phase B + Phase C does not exceed the cap.
```yaml
- id: total-questions-asked-max
  max: 7
```

---

## E — Output structure

### `output-has-required-sections`
The artifact contains all required sections for this skill (in order, with the spec'd headings).
```yaml
- id: output-has-required-sections
  skill: ticket-builder
  required_sections:
    - "User Story"
    - "Description"
    - "User Flow"
    - "Definition of Done"
```

### `output-omits-banned-sections`
The artifact contains NONE of the named banned sections.
```yaml
- id: output-omits-banned-sections
  banned_sections:
    - "Background"
    - "Context"
    - "Problem"
    - "Desired Outcome"
    - "Scope"
    - "Functional Requirements"
    - "Edge Cases"
    - "Analytics"
    - "Dependencies"
    - "Open Questions"
    - "Builder notes"
```

### `ascii-flow-uses-box-drawing`
Any ASCII flow diagram uses the spec'd box-drawing characters `┌─┐│└┘├┤┬┴` and arrows `▼ → ─▶`, inside a fenced code block.
```yaml
- id: ascii-flow-uses-box-drawing
```

### `user-story-shape`
The User Story line follows the canonical `As a [user], I want to [action], so that [value].` shape.
```yaml
- id: user-story-shape
```

### `edge-cases-as-table-not-gherkin`
PRD §6 User Stories embed Edge Cases as a markdown table (columns: Case | Expected behavior | Notes). Not Gherkin (`Given/When/Then`).
```yaml
- id: edge-cases-as-table-not-gherkin
```

### `prd-has-12-sections`
PRD-writer output contains all 12 numbered sections (`## 1. Overview` through `## 12. Suggested Jira Breakdown`).
```yaml
- id: prd-has-12-sections
```

### `cr-has-7-sections`
competitor-research output contains all 7 numbered sections (`## 1. Research Scope` through `## 7. Gaps & Opportunities`).
```yaml
- id: cr-has-7-sections
```

### `no-meta-commentary-after-final-section`
The artifact ends at its last spec'd section. No "builder notes", reflections, or commentary follow.
```yaml
- id: no-meta-commentary-after-final-section
  final_section_heading: "Definition of Done"
```

---

## F — Maturity / Depth adaptation

### `prd-emphasis-matches-maturity`
The PRD's emphasis matches the maturity answer (Initial idea / Clear direction / Existing feature).
```yaml
- id: prd-emphasis-matches-maturity
  maturity: "Initial idea"
  expected_emphasis:
    - "Problem Statement"
    - "User Pain"
    - "Assumptions"
    - "Validation Plan"
    - "MVP Suggestion"
  forbidden_sections: ["Open Questions"]
```

### `cr-depth-matches-answer`
competitor-research output length/detail scales correctly with the Depth answer.
```yaml
- id: cr-depth-matches-answer
  depth: "Quick scan"
  expected_findings_min: 3
  expected_findings_max: 5
  screenshots_required: false
```

---

## G — Handoff & MCP integration

### `gamble-handoff-presented-once`
Exactly one "Ready To Gamble On It?" question is presented at the end (via AskUserQuestion).
```yaml
- id: gamble-handoff-presented-once
```

### `gamble-options-match-spec`
The options for the handoff question match the skill's spec'd set verbatim.
```yaml
- id: gamble-options-match-spec
  skill: ticket-builder
  expected_options: ["Bet on it", "Hold the chip"]   # PRD adds "Double down"; CR has only Bet on it + Hold
```

### `mcp-tool-lookup-pattern`
When the user chooses Bet on it and the right MCP is connected, the skill looks up the create tool with the correct name-regex pattern.
```yaml
- id: mcp-tool-lookup-pattern
  target: "jira-create-issue"                      # or "confluence-create-page"
  expected_regex: 'mcp__.*(atlassian|jira).*'
  expected_verbs: ["createIssue", "createJiraIssue", "create_issue"]
```

### `mcp-fallback-when-disconnected`
When the user chooses Bet on it but no Atlassian MCP is connected, the skill replies with the exact fallback `Atlassian MCP not connected — saved markdown only at <path>` and stops.
```yaml
- id: mcp-fallback-when-disconnected
  expected_message_substring: "Atlassian MCP not connected"
```

### `markdown-saved-with-absolute-path`
The artifact is saved to `~/Downloads/<folder>/<slug>.md` with the correct folder name and the absolute path is printed at the end.
```yaml
- id: markdown-saved-with-absolute-path
  folder: "tickets"     # or "prds", "competitor-research"
```

### `slug-is-kebab-case`
The slug of the saved file is the kebab-cased version of the artifact title.
```yaml
- id: slug-is-kebab-case
  title: "Add a VIP progress bar to the casino home"
  expected_slug: "add-a-vip-progress-bar-to-the-casino-home"
```

### `confluence-call-uses-pkb-params`
Confluence create-page call uses `spaceId=772571142`, `parentId=772571521`, `contentFormat=markdown`, and `title` matches the artifact title.
```yaml
- id: confluence-call-uses-pkb-params
```

### `double-down-creates-confluence-epic-and-children`
PRD-writer Double-down branch creates: 1 Confluence page + 1 Jira sub-epic + N child tickets (where N = number of rows in §12).
```yaml
- id: double-down-creates-confluence-epic-and-children
  expected_child_count: 6
```

### `double-down-child-tickets-no-questions`
Each chained ticket-builder call in Double-down mode emits ZERO user-facing questions (Phase B and Phase C skipped; auto Bet on it at handoff).
```yaml
- id: double-down-child-tickets-no-questions
```

### `double-down-child-tickets-cite-prd`
Each chained ticket's `Inferred (not asked)` block cites the PRD section (e.g. `from PRD §10 FR-2`) for every Phase A inference.
```yaml
- id: double-down-child-tickets-cite-prd
```

### `cr-confluence-screenshots-note`
After publishing a competitor-research report to Confluence, the skill surfaces the one-line note about screenshots being local-only.
```yaml
- id: cr-confluence-screenshots-note
  expected_message_substring: "Screenshots are local-only"
```

### `cr-multiple-atlassian-asks-which`
When more than one Atlassian MCP is connected, the skill asks the user which one to use before publishing.
```yaml
- id: cr-multiple-atlassian-asks-which
```

---

## H — Quality & specificity

### `uses-company-terminology`
When Jira/Confluence context is provided, the artifact uses the same terminology (component names, file paths, project keys) found in that context — not generic placeholders.
```yaml
- id: uses-company-terminology
  expected_terms: ["Smartico", "PR-470", "components/home/banner.tsx"]
```

### `facts-cite-source`
Facts in the artifact cite their source (link, page, ticket key, file path). Assumptions are explicitly marked. Missing information is called out.
```yaml
- id: facts-cite-source
```

### `output-copy-pasteable`
The artifact is pure markdown — no embedded shell prompts, no truncation markers, no `<<…>>` placeholders left unresolved.
```yaml
- id: output-copy-pasteable
```

---

## I — Edge cases & failure modes

### `vague-input-suggests-better-title`
When the user input is vague (e.g. "make it better"), the skill applies a sharper title directly in the artifact title line — does NOT add a separate "suggested title" note or section.
```yaml
- id: vague-input-suggests-better-title
```

### `too-large-request-proposes-split`
When the request is clearly too large for one ticket/PRD, the skill says so in one sentence ABOVE the artifact and proposes a split. Does NOT bury the note inside a "Builder notes" section.
```yaml
- id: too-large-request-proposes-split
```

### `prd-thin-row-defaults-to-task`
When a PRD §12 row is too thin for Phase A to infer a ticket type (e.g. "Misc — TBD"), the chained ticket defaults to type `Task` with an inline `Open: ticket type not inferable from PRD §12 — confirm with owner` line.
```yaml
- id: prd-thin-row-defaults-to-task
```

### `cr-memory-empty-caches-after-phase-b`
When `~/.claude/memory/<project-slug>.md` has no competitor list, Phase B asks for it, then the answer is appended to memory (`**Competitors:**` line) before the report is rendered.
```yaml
- id: cr-memory-empty-caches-after-phase-b
```

### `cr-memory-differs-confirms-inline`
When runtime input names competitors that differ from the memory list, the skill confirms inline with one message and does NOT overwrite memory silently.
```yaml
- id: cr-memory-differs-confirms-inline
```

### `cr-playwright-unavailable-degrades-gracefully`
When Playwright MCP is not connected, the skill still produces the report (without screenshots), and the §1 Research Scope notes "Playwright not available — no screenshots captured".
```yaml
- id: cr-playwright-unavailable-degrades-gracefully
```

### `cr-robots-txt-blocked-inline-note`
When a competitor page is blocked by robots.txt or geofence, the skill notes `couldn't access <page>` inline in the report and skips.
```yaml
- id: cr-robots-txt-blocked-inline-note
```

### `multiple-atlassian-asks-which`
When more than one Atlassian MCP is connected, the skill asks the user which one to use before calling the create tool. (Generic — applies to all three skills.)
```yaml
- id: multiple-atlassian-asks-which
```

### `mcp-create-failure-confirms-markdown-saved`
If the MCP create call fails (Jira or Confluence), the skill reports the error and confirms the markdown file is still saved.
```yaml
- id: mcp-create-failure-confirms-markdown-saved
```

---

## J — PRD-writer specific structure

### `prd-section-has-subsections`
A specific PRD section contains the spec'd subsection headings (e.g. §8 has Functional + Non-Functional with Performance/Security/Permissions/Accessibility/Localization/Compliance under Non-Functional; §10 has Primary/Secondary/Tracking).
```yaml
- id: prd-section-has-subsections
  section: "8. Requirements"
  required_subsections:
    - "Functional"
    - "Non-Functional"
    - "Performance"
    - "Security"
    - "Permissions"
    - "Accessibility"
    - "Localization"
    - "Compliance"
```

### `prd-section-12-has-sub-epic-and-children`
PRD §12 (Suggested Jira Breakdown) includes both a named sub-epic title AND a list/table of child ticket rows with at least 1 row.
```yaml
- id: prd-section-12-has-sub-epic-and-children
  min_child_rows: 1
```

### `frontmatter-description-names-chain-behavior`
The skill's `description` mentions the `Double down` chain behavior (so Claude can match user intent for the chained handoff).
```yaml
- id: frontmatter-description-names-chain-behavior
  expected_phrase: "Double down"
```

### `double-down-falls-back-when-no-mcp`
When the user picks Double down but no Atlassian MCP is connected, the skill emits the same fallback message as Bet on it (no chain executed).
```yaml
- id: double-down-falls-back-when-no-mcp
  expected_message_substring: "Atlassian MCP not connected"
```

---

## K — competitor-research specific structure

### `cr-output-has-metadata-table`
competitor-research output has a metadata table at the top with rows: `Status`, `Author`, `Date`, `Depth`, `Region scope`.
```yaml
- id: cr-output-has-metadata-table
  required_rows: ["Status", "Author", "Date", "Depth", "Region scope"]
```

### `cr-comparison-table-min-rows`
competitor-research §4 Comparison Table has at least N rows drawn from the canonical row labels (Homepage messaging / Signup flow / Pricing / Trust signals / Core feature).
```yaml
- id: cr-comparison-table-min-rows
  min_rows: 4
  required_row_labels_any_of: ["Homepage messaging", "Signup flow", "Pricing", "Trust signals", "Core feature"]
```

### `cr-screenshots-inline-not-separate-section`
§5 UX Flow Notes references screenshots inline via `![desc](screenshots/<file>.png)`. No separate `Screenshots` section exists.
```yaml
- id: cr-screenshots-inline-not-separate-section
  inline_pattern: "![*](screenshots/*.png)"
  banned_section: "Screenshots"
```

### `cr-section-6-distinguishes-table-stakes-vs-differentiation`
§6 Key Patterns explicitly groups findings into table-stakes (industry-standard) vs. differentiation (unique/contrarian).
```yaml
- id: cr-section-6-distinguishes-table-stakes-vs-differentiation
  expected_labels_any_of: ["Table stakes", "Differentiation", "table-stakes", "differentiation"]
```

### `cr-no-jira-tickets-generated`
competitor-research is research-only — output ends at §7 Gaps & Opportunities, and no Jira create-issue MCP call is made.
```yaml
- id: cr-no-jira-tickets-generated
  final_section_heading: "Gaps & Opportunities"
```

### `cr-markdown-save-path-pattern`
The markdown file is saved to `~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md`.
```yaml
- id: cr-markdown-save-path-pattern
  expected_pattern: "~/Downloads/competitor-research/<focus-slug>-<YYYY-MM-DD>.md"
```

### `cr-screenshots-subdir-co-located`
Captured screenshots are written to a `screenshots/` subdir co-located with the markdown file (`~/Downloads/competitor-research/<focus-slug>/screenshots/`).
```yaml
- id: cr-screenshots-subdir-co-located
```

### `cr-phase-b-competitor-question-uses-memory-names`
When memory has a `**Competitors:**` list, the Phase B Competitors question label substitutes those names verbatim (e.g. "Same as cached (Stake, 1Xbet, Rollbit, Bc.Game)").
```yaml
- id: cr-phase-b-competitor-question-uses-memory-names
  expected_names: ["Stake", "1Xbet", "Rollbit", "Bc.Game"]
```

### `cr-depth-quick-scan-shape`
When Depth = Quick scan, the output stays light: 3–5 opportunities, screenshots optional, ~30-min equivalent.
```yaml
- id: cr-depth-quick-scan-shape
  expected_findings_min: 3
  expected_findings_max: 5
  screenshots_required: false
```

### `cr-depth-detailed-shape`
When Depth = Detailed comparison, the output includes a full comparison matrix, key-surface screenshots, and a prioritized recommendations list.
```yaml
- id: cr-depth-detailed-shape
  matrix_required: true
  screenshots_required: true
  prioritized_recommendations_required: true
```

### `cr-depth-deep-ux-shape`
When Depth = Deep UX flow, the output includes step-by-step flow per competitor, friction analysis, every-screen screenshots, side-by-side comparison, and suggested experiments.
```yaml
- id: cr-depth-deep-ux-shape
  per_competitor_steps_required: true
  friction_analysis_required: true
  every_screen_screenshots_required: true
  side_by_side_required: true
  experiments_required: true
```

### `cr-phase-c-skip-screenshot-filenames`
Phase C does NOT ask the user to name screenshot filenames (rule 4 — skip exact phrasing/screenshot names/ticket titles).
```yaml
- id: cr-phase-c-skip-screenshot-filenames
```

### `cr-phase-c-skip-redundant-competitor-question`
Phase C does NOT ask "Use existing competitors or different ones?" because Phase B already resolved this.
```yaml
- id: cr-phase-c-skip-redundant-competitor-question
```

### `cr-phase-c-priority-order-respected`
When multiple material unknowns exist, Phase C picks them in CR-specific priority order: region/market scope > source mix > time horizon > authentication boundary.
```yaml
- id: cr-phase-c-priority-order-respected
  expected_priority_order: ["region/market scope", "source mix", "time horizon", "authentication boundary"]
```

### `cr-research-scope-notes-playwright-status`
§1 Research Scope explicitly states whether Playwright was available, and lists any inaccessible pages.
```yaml
- id: cr-research-scope-notes-playwright-status
  expected_substring_any_of: ["Playwright not available", "Playwright connected", "screenshots captured"]
```
