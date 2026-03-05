# create-cursor-skill

Cursor skill for **creating Agent Skills** — folder structure, SKILL.md format, frontmatter, .mdc rules ([agentskills.io](https://agentskills.io/) standard).

## What this skill does

- **Plan mode** — Agent uses Plan/Build mode first to gather requirements.
- **Skill vs Rule** — SKILL.md (folder) vs .mdc (rules); where to store each.
- **Structure** — SKILL.md, reference.md, examples.md, assets/; frontmatter format.
- **Examples** — Minimal skill, with references, with scripts, example .mdc rule.

## When to use

- Create a new skill from scratch.
- Questions about folder structure, SKILL.md, frontmatter, where to store (project vs global).
- Distinguish Skills from Rules.

## Files

| File | Use |
|------|-----|
| `SKILL.md` | Agent instructions, pre-publish checklist |
| `reference.md` | Skills vs Rules, full structure, .mdc |
| `examples.md` | Minimal skill, with references, with scripts |

## Install

**Latest:**
```bash
git clone https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/create-cursor-skill ~/.cursor/skills/
```

**Specific version:** clone repo → checkout `versions` → copy `create-cursor-skill/versions/vX.Y/` to `~/.cursor/skills/create-cursor-skill/`.

**References:** [Cursor — Agent Skills](https://cursor.com/docs/context/skills) · [Cursor — Rules](https://cursor.com/docs/context/rules) · [agentskills.io](https://agentskills.io/)

---

→ [See all skills](https://github.com/mariocosttaa/my-agent-skills)
