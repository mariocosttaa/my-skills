# gin-workflow

Cursor skill for the **GIN project workflow** — Jira + repo, per-requirement planning and execution.

## What this skill does

- **Branch & folder** — From Jira code (e.g. `GIN-AZ-42`) → branch + directory.
- **Docs** — `requisitos.md`, `plan.md`, `tasks.md`, `overview.md`, `suggestions.md` with templates.
- **Linkage** — Implementation ↔ README Feature section ↔ commit messages.
- **Language** — pt-PT for requirement documents; Jira naming conventions.

## When to use

- Jira requirement (e.g. GIN-AZ-42), feature branch, requisitos, plan, tasks.
- Updating README with feature references.

## Files

| File | Use |
|------|-----|
| `SKILL.md` | Agent instructions |
| `reference.md` | Conventions, templates, phases |
| `assets/` | Templates (requisitos, plan, tasks, overview, suggestions, qa-plan) |

## Install

```bash
git clone -b gin-workflow https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/gin-workflow ~/.cursor/skills/
```

---

→ [See all skills on main](https://github.com/mariocosttaa/my-agent-skills)
