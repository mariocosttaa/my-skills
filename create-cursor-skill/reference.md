# Reference: Skills vs Rules, Structure and Formats

## 1. Workflow when creating a skill — Plan mode (Build) first

Before implementing any skill file, use **Plan mode** in Cursor (or equivalent "Build") to gather everything needed:

- **How to activate:** `Cmd+.` / `Ctrl+.` → choose Plan; or `Shift+Tab` to switch modes.
- **Goal:** search the codebase, clarification questions to the user, and definition of a reviewed plan before writing code.
- **What to gather:** purpose, scope, location (project vs user), triggers, domain knowledge, output format, existing examples.
- **Rule:** do not create SKILL.md or other files until the discovery phase is complete. Only then switch to Agent mode to implement.

---

## 2. Where Skills and Rules live

### Skills (SKILL.md)

| Scope | Path |
|--------|------|
| Project | `.agents/skills/<skill-name>/` |
| Project | `.cursor/skills/<skill-name>/` |
| User (global) | `~/.cursor/skills/<skill-name>/` |

Compatibility: Cursor also loads from `.claude/skills/` and `.codex/skills/` (and equivalents in `~`).

Each skill is a **folder** with a required **SKILL.md** file.

### Rules (project rules)

| Type | Location |
|------|----------|
| Project Rules | `.cursor/rules/` |

Files: **.mdc** (with frontmatter) or **.md**. Can be in subfolders (e.g. `.cursor/rules/frontend/components.mdc`).

---

## 3. Full Skill structure

```
skill-name/
├── SKILL.md                 # Required
├── reference.md             # Optional — detailed reference
├── examples.md              # Optional — examples
├── README.md                # Optional — documentation for humans
├── scripts/                 # Optional — executable scripts
│   ├── deploy.sh
│   └── validate.py
├── references/              # Optional — multiple .md (progressive disclosure)
│   └── REFERENCE.md
└── assets/                  # Optional — templates, configs, images
    └── config-template.json
```

- **SKILL.md**: main instructions; keep focused and < ~500 lines.
- **reference(s)** and **examples**: loaded on demand when the agent follows links.
- **scripts/**: reference in SKILL.md with relative paths (e.g. `scripts/deploy.sh`).
- **README.md**: not injected into the agent; serves humans browsing the folder.

---

## 4. SKILL.md format — frontmatter

### Required fields

```yaml
---
name: my-skill-name
description: What the skill does and when the agent should use it (max 1024 chars).
---
```

- **name**: unique identifier; lowercase letters, numbers, hyphens only; max 64 characters; must match folder name.
- **description**: third person; include activation terms (e.g. "Use when the user mentions X, Y, Z").

### Optional fields

| Field | Description |
|-------|-------------|
| `license` | License (SPDX or file reference) |
| `compatibility` | Environment / compatible agents |
| `metadata` | author, version, tags, etc. |
| `disable-model-invocation` | If `true`, the skill is only applied when invoked with `/skill-name` |

---

## 5. .mdc format (Rules)

Rules live in `.cursor/rules/` and control when they are applied via frontmatter.

### .mdc structure

```markdown
---
description: Description for the agent to decide when to apply (Apply Intelligently).
globs: "*.ts"              # Optional — apply when file matches
alwaysApply: false         # true = apply for the whole session
---

# Rule content in Markdown
- Instruction 1
- Instruction 2
```

### Activation types (via UI / properties)

| Type | Behaviour |
|------|-----------|
| Always Apply | `alwaysApply: true` — for the whole session |
| Apply Intelligently | Good description; agent decides by relevance |
| Apply to Specific Files | `globs` set (e.g. `*.ts`, `src/**/*.tsx`) |
| Apply Manually | Applied when @-mentioned in chat (e.g. `@my-rule`) |

### .mdc best practices

- Names in kebab-case (e.g. `typescript-standards.mdc`).
- Always use `.mdc` extension for rules with frontmatter.
- Focused, actionable rules; avoid duplicating what is already in the code.
- Keep under ~500 lines; reference files with `@file` instead of pasting content.

---

## 6. Practical difference: Skill vs Rule

| Aspect | Skill | Rule (.mdc) |
|--------|-------|-------------|
| Main file | SKILL.md inside folder | .mdc or .md in .cursor/rules/ |
| Structure | Folder with SKILL.md + optional scripts/references/assets | Single file (or folder with several .mdc) |
| Discovery | By name/description; or `/skill-name` | By description/globs/alwaysApply or @rule |
| Typical use | Workflows, domains, reusable scripts | Code patterns, per-project conventions |
| Scope | Project or user (per folder) | Project (`.cursor/rules/`) |

---

## 7. Progressive disclosure

- **Discovery**: agent sees only `name` and `description` (~100 tokens).
- **Activation**: when relevant, loads full SKILL.md.
- **Execution**: follows instructions and opens referenced files (reference.md, examples, scripts) only when needed.

Hence: keep SKILL.md lean; detail in `reference.md` or `references/*.md` and link with single-level links.

---

## 8. Scripts in skills

- Place in `scripts/` and reference with relative paths: `scripts/deploy.sh`, `python scripts/validate.py`.
- Scripts should be self-contained, with useful error messages.
- Document dependencies (packages, environment) in SKILL.md or reference.

---

## 9. README.md in the skill folder

- **Not** injected into the agent context.
- Serves humans: explain purpose, folder structure, when to use each file.
- Useful in repositories and in `~/.cursor/skills/` for local documentation.
