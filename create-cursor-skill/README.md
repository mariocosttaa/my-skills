# create-cursor-skill

**Skill that guides creation of Agent Skills in Cursor** — folder structure, SKILL.md format, frontmatter, .mdc rules and best practices ([agentskills.io](https://agentskills.io/) standard).

---

## Structure of this skill

```
create-cursor-skill/
│
├── SKILL.md              ← Main entry for the agent
│                             Use Plan (Build) mode before implementing
│                             Skill vs Rule (.mdc) decision
│                             Required structure, where to store
│                             SKILL.md format and frontmatter
│                             Pre-publish checklist
│
├── reference.md          ← Detailed reference
│                             Skills vs Rules, directories
│                             Full structure, frontmatter, .mdc
│                             Progressive disclosure, scripts
│
├── examples.md           ← Practical examples
│                             Minimal skill, with references, with scripts
│                             Example .mdc Rule
│
└── README.md             ← This file (for humans)
```

---

## When to use

- You want to **create a new skill** from scratch (the agent should use **Plan/Build mode** first to gather requirements).
- You have doubts about **folder structure**, **SKILL.md**, **frontmatter** or **where to store** (project vs user).
- You need to distinguish **Skills** (SKILL.md in a folder) from **Rules** (.mdc files in `.cursor/rules/`).
- You want **examples** of minimal skills, with references or with scripts.

The agent uses this skill when it detects requests like "how to create a skill", "skill structure", "SKILL.md", ".mdc", etc.

---

## Where this skill is stored

- **In this project:** `.cursor/skills/create-cursor-skill/` — Cursor loads skills from this folder automatically.

To use in all your projects, copy to `~/.cursor/skills/create-cursor-skill/`.

---

## Source

From [my-agent-skills](https://github.com/mariocosttaa/my-agent-skills): `git clone -b create-cursor-skill https://github.com/mariocosttaa/my-agent-skills.git && cp -r my-agent-skills/create-cursor-skill ~/.cursor/skills/`

---

## Official references

- [Cursor Docs — Agent Skills](https://cursor.com/docs/context/skills)
- [Cursor Docs — Rules](https://cursor.com/docs/context/rules)
- [agentskills.io](https://agentskills.io/) — SKILL.md specification
