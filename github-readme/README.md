# Skill: github-readme

Cursor skill to create and improve GitHub repository READMEs.

## What it does

- Structures READMEs with: badges (shields.io), project name, description, Mermaid (if needed), preview (image/GIF), objective, quick start, examples.
- **Build mode:** the agent asks first (name, stack, objective, quick start, Mermaid, preview, etc.) and only then generates the README.
- Always reminds the user they can change the content.

## When to use

- "Create a README for this repo"
- "Improve the GitHub README"
- "Add badges to the README"
- "Document the project in the README"

## Files

| File | Use |
|------|-----|
| `SKILL.md` | Main instructions for the agent. |
| `reference.md` | Detailed structure, badge and section examples. |
| `README.md` | This file — documentation for humans. |

## Install

```bash
git clone -b github-readme https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/github-readme ~/.cursor/skills/
```
