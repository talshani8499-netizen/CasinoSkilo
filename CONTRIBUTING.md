# Contributing to CasinoSkilo

This kit ships as a **lean v1 scaffold**. Each skill is structured the way it will be in production, but the prose, examples, and company-specific bits need to be hand-refined before going live. This guide covers how to refine an existing skill, add a new one, and ship a new version.

---

## Repo layout

```
CasinoSkilo/
├── .claude-plugin/
│   └── plugin.json          # bump version here when you ship changes
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md         # the skill (frontmatter + body)
│       └── <supporting>     # optional templates, configs, examples
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

---

## Refine an existing skill

1. **Open the skill's `SKILL.md`** in `skills/<skill-name>/SKILL.md`.
2. **Tighten the frontmatter `description`.** This is what Claude reads to decide when to invoke the skill. Lead with "Use when…" and name the output type. Example:
   > Use when a PM wants to turn a raw feature idea into a Jira-ready ticket.
3. **Edit the body section by section.** The template mirrors the spec — keep the section headings (`## Purpose`, `## When to use`, `## Context to gather`, `## Guided questions`, `## Output`, `## Quality rules`, `## Advanced behaviors`) so the skill stays consistent with the others.
4. **Add company-specific bits.** Real terminology, real Jira component names, real ticket-format examples, real Confluence templates. The skill gets dramatically better when it knows your team's conventions.
5. **Add an example output.** A worked example at the bottom of the SKILL.md (or in a sibling file like `examples/sample-output.md`) helps Claude produce on-brand output.
6. **Test locally** (see "Testing" below).
7. **Bump version** in `.claude-plugin/plugin.json` and commit.

### Refinement checklist

- [ ] `description` reads naturally as "Use when…"
- [ ] Guided questions use the exact `A / B / C / D. Other: write your own` format
- [ ] Output template uses real section names from your team's docs (not generic ones)
- [ ] Brand voice and terminology references are concrete, not "the company's preferred…"
- [ ] At least one real-world example output is included
- [ ] No placeholder text like `[Item 1]` left in non-template sections
- [ ] SKILL.md is under 500 lines (move supporting material to sibling files)

---

## Add a new skill

1. **Create the folder:**
   ```
   mkdir -p skills/<new-skill-name>
   ```
2. **Create `SKILL.md`** using this template:

   ```markdown
   ---
   name: <new-skill-name>
   description: Use when a PM wants to <do something>. Scans Jira/Confluence for related context, asks N guided questions, and returns <output type>.
   ---

   # <Skill Display Name>

   ## Purpose
   ## When to use
   ## Context to gather (before questions)
   ## Guided questions
   ## Output
   ## Quality rules
   ## Advanced behaviors (apply when relevant)
   ```

3. **Copy the structure** from an existing skill (start with `ticket-builder` — it's the most representative).
4. **Add supporting files** alongside `SKILL.md` if needed (templates, JSON configs, example outputs). Reference them from `SKILL.md` so Claude knows when to load them.
5. **List the skill** in `README.md`'s skill table.
6. **Bump version** and commit.

---

## Testing

### Smoke test
From the repo root:
```
claude
> /skill
```
Confirm all skills (including any new one) are listed.

### Invocation test
```
> /skill ticket-builder
```
Provide a sample raw request and walk through the guided questions. Verify the output matches the structure in `SKILL.md`.

### JSON validity
```
python3 -m json.tool .claude-plugin/plugin.json
```

### Edit-and-reload
Edit a `SKILL.md`, save, and re-invoke the skill in the same session. Claude Code picks up changes immediately, so iteration is fast.

---

## Versioning and release

- Use semantic versioning in `.claude-plugin/plugin.json`:
  - **patch** (`0.1.0 → 0.1.1`): typo, prose tweak, small clarification.
  - **minor** (`0.1.0 → 0.2.0`): new skill, new supporting file, meaningful behavior change.
  - **major** (`0.x.x → 1.0.0`): first official ship; breaking changes to skill names or invocation.
- Tag releases (`git tag v0.2.0 && git push --tags`) so teammates can pin to a known good version.
- Note user-visible changes in commit messages or a `CHANGELOG.md` (add one when needed).

---

## Style notes

- **Skill names** are folder names: lowercase, hyphenated, short (`ticket-builder`, not `Ticket Builder Skill`).
- **Guided questions** must use the exact lettered format. Consistency across skills is what makes the kit feel like a kit.
- **Output sections** should be production-ready markdown — assume the user pastes it into Jira/Confluence without editing.
- **Keep `SKILL.md` short.** Anything that doesn't need to be in Claude's context every invocation belongs in a sibling file.

---

## Asking questions

Open an issue or DM the kit's maintainers (set this in your forked README).
