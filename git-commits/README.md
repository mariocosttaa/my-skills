# git-commits

Cursor skill for **commit messages** and **branch flow**: Conventional Commits, file grouping, and stash/checkout workflow.

## What this skill does

- **Commit format** — `type[(scope)]: description` + optional bullet body (feat, fix, docs, refactor, etc.).
- **Grouping** — Focus per commit; related files together; avoid mixing unrelated changes.
- **Branch workflow** — Stash → checkout feature branch → pop → commit → push.
- **Rules** — Asks commit language (EN or other); never adds `Made-with: Cursor` or similar trailers (mandatory).

## When to use

- Writing or reviewing commit messages.
- Deciding how to group files into commits.
- Switching branch while carrying uncommitted changes.

## Files

| File | Use |
|------|-----|
| `SKILL.md` | Agent instructions |
| `reference.md` | Conventional Commits, SemVer, revert, branch strategies |
| `README.md` | This file (for humans) |

## Install

```bash
git clone -b git-commits https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/git-commits ~/.cursor/skills/
```

---

→ [See all skills on main](https://github.com/mariocosttaa/my-agent-skills)
