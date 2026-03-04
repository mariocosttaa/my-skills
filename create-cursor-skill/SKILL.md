---
name: create-cursor-skill
description: >
  Guides users through creating Cursor Agent Skills from scratch. Use when the user wants to create
  a new skill, asks "how do I create a skill", "skill structure", "SKILL.md format", "where to put
  skills", or needs the full file structure, directory layout, frontmatter rules, optional .mdc rules
  context, README for skills, and best practices. Requires gathering requirements via questions and
  overview before implementing. Covers .agents/skills, .cursor/skills, SKILL.md frontmatter,
  references/, scripts/, assets/, and when to use skills vs .cursor/rules (.mdc).
---

# Create Cursor Skill

Guide to create Agent Skills in Cursor following the official pattern (agentskills.io) and best practices.

---

## Required: questions before starting

**Do not create any file** until you answer these questions and present an overview to the user. Ask in natural language (not a dry list); if context is missing, ask for clarification before proceeding.

### Questions to ask

1. **Purpose** — What specific task or workflow will this skill cover? What does the user expect the agent to know how to do?
2. **Scope** — Where will it be used: this project only (`.cursor/skills/` or `.agents/skills/`) or globally (`~/.cursor/skills/`)?
3. **Activation** — In which situations should the agent load this skill? (e.g. "when the user mentions Excel, PDF, deploy, etc.")
4. **Knowledge** — What information does the agent not know by default and needs in the skill?
5. **Format** — Are there templates, conventions or existing examples to follow?
6. **Name** — Suggested name for the skill (lowercase, hyphens; e.g. `excel-reports`, `docker-deploy`).

### Overview before implementing

After gathering answers, **show the user** a summary of what will be created, e.g.:

- **Skill name:** `example-skill`
- **Location:** `~/.cursor/skills/example-skill/` (or project path)
- **Files to create:** SKILL.md, reference.md (optional), README.md (optional)
- **Main content:** brief description of what the instructions will cover
- **Activation terms:** e.g. "Use when the user mentions X, Y, Z"

Only proceed to create files **after confirmation** from the user (explicit or implicit, e.g. "yes, go ahead").

---

## Quick decision: Skill vs Rule (.mdc)

| Goal | Use | Location |
|----------|------|----------|
| Reusable capability, loaded on demand | **Skill** | `.agents/skills/` or `.cursor/skills/` or `~/.cursor/skills/` |
| Per-project instructions, globs, always apply | **Rule** | `.cursor/rules/*.mdc` or `.cursor/rules/*.md` |

Skills are packages with `SKILL.md`; Rules are `.mdc`/`.md` files in `.cursor/rules/` with `description`, `globs`, `alwaysApply`. See [reference.md](reference.md) for details on both.

---

## Required skill structure

Each skill is a **folder** with a **SKILL.md** file:

```
skill-name/
├── SKILL.md              # Required — frontmatter YAML + instructions
├── reference.md          # Optional — detailed documentation
├── examples.md           # Optional — usage examples
├── README.md             # Optional — for humans (not injected into the agent)
├── scripts/              # Optional — executable scripts
├── references/           # Optional — reference files (progressive disclosure)
└── assets/               # Optional — templates, configs, images
```

**Rule:** The folder name must match the `name` field in the frontmatter (lowercase, hyphens, max 64 characters).

---

## Where to store the skill

| Scope | Path |
|--------|------|
| Project (repository) | `.agents/skills/skill-name/` or `.cursor/skills/skill-name/` |
| User (global) | `~/.cursor/skills/skill-name/` |

**Never** create skills in `~/.cursor/skills-cursor/` — reserved for Cursor internal skills.

---

## SKILL.md — minimum format

```markdown
---
name: my-skill-name
description: Short description of what the skill does and when the agent should use it (max 1024 chars).
---

# Skill Name

## Instructions
Step-by-step for the agent.
```

### Required frontmatter

| Field | Rules |
|-------|-------|
| `name` | Required. Lowercase, letters/numbers/hyphens, max 64 characters. Must match folder name. |
| `description` | Required. What it does + when to activate. Max 1024 characters. Third person (e.g. "Processes Excel files..." not "I process..."). |

### Optional frontmatter

| Field | Use |
|-------|-----|
| `license` | SPDX or reference to license file |
| `compatibility` | Compatible agents/environment |
| `metadata` | author, version, tags |
| `disable-model-invocation` | If `true`, the skill is only applied when explicitly invoked with `/skill-name` |

---

## Effective description

The description determines when the agent applies the skill. Include:

1. **What** — concrete capabilities.
2. **When** — activation terms (e.g. "Use when the user mentions PDF, Excel, deploy...").

Example:

```yaml
description: >
  Analyzes Excel spreadsheets, creates pivot tables, generates charts.
  Use when working with .xlsx files, spreadsheets, or when the user asks for data analysis.
```

---

## Principles for writing the skill

1. **Agent instructions in English** — Keep all instructions, comments and documentation in the skill in English. Outputs or generated content (e.g. requisitos.md, user-facing text) may be in another language if the skill explicitly states it (e.g. "output in pt-PT").
2. **Be concise** — only include what the agent does not know. Keep SKILL.md under ~500 lines.
3. **Progressive disclosure** — essentials in SKILL.md; details in `reference.md` or `references/` and link to them.
4. **Single-level references** — link from SKILL.md directly to files (e.g. `[reference.md](reference.md)`). Avoid deep trees.
5. **No Windows paths** — use `scripts/helper.py`, never `scripts\helper.py`.

---

## Pre-publish checklist

- [ ] Required questions asked; overview shown to the user; confirmation before implementing
- [ ] `name` in lowercase with hyphens, folder with the same name
- [ ] `description` in third person, with activation terms
- [ ] SKILL.md with clear instructions and concrete steps
- [ ] Extra documentation in reference(s) if needed
- [ ] README.md optional for humans browsing the folder
- [ ] No references to `~/.cursor/skills-cursor/`

For full structure, .mdc vs skills, and examples, see [reference.md](reference.md) and [examples.md](examples.md).
