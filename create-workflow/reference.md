# Reference: Create Workflow

## When to use Rule vs Skill only

- **Rule required** when the workflow skill is in the project (`.cursor/skills/` or `.agents/skills/`): ensures the agent reads the skill on every prompt.
- **No rule** when the skill is global (`~/.cursor/skills/`): the agent loads it based on prompt relevance.

## Example Rule for repo-specific workflow

```yaml
---
description: >
  Follow the project's workflow skill when working in this repository.
  Read .cursor/skills/my-project-workflow/SKILL.md before planning or executing tasks.
alwaysApply: true
---
```

## Difference from gin-workflow

**gin-workflow** is a *ready-made* workflow skill for the GIN project. **create-workflow** helps *create* new workflow skills for other projects or teams, following the same pattern.

## Source

From [my-agent-skills](https://github.com/mariocosttaa/my-agent-skills) — gin-workflow: [tree/gin-workflow](https://github.com/mariocosttaa/my-agent-skills/tree/gin-workflow).
