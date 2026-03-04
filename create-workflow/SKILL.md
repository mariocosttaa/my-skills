---
name: create-workflow
description: >
  Guides creation of Cursor workflow skills (like gin-workflow). Use when the user wants to define
  a development workflow for a project or team, create a workflow skill, or document conventions
  (branches, requisitos, implementation, Jira, etc.). Supports generic workflows (global) and
  repo-specific workflows. When repo-specific and installed in the project, creates a rule that
  obliges the agent to read the workflow skill.
---

# Create Workflow Skill

Guide to create workflow skills in Cursor — per-requirement workflows, branch conventions, implementation documentation, Jira/Linear integration, etc. Inspired by **gin-workflow**; can be generic (global) or repository-specific.

---

## Required: questions before starting

**Do not create files** until you clarify the context and present an overview to the user.

### Questions to ask

1. **Type** — Generic workflow (any repo) or specific to this repository?
2. **Scope** — Where to install: global (`~/.cursor/skills/`) or in the project (`.cursor/skills/` or `.agents/skills/`)?
3. **Integration** — Is there an external system? (e.g. Jira, Linear, Trello) and what is the identifier format (e.g. GIN-AZ-42, PROJ-123)?
4. **File structure** — What files and folders define the workflow? (e.g. `/<code>/requisitos.md`, `/<code>/plan.md`, branch = code)
5. **Language** — Portuguese (pt-PT), English, or other?
6. **Name** — Skill name (lowercase, hyphens; e.g. `gin-workflow`, `my-team-workflow`).

### Overview before implementing

Show the user:

- **Type:** generic or repo-specific
- **Location:** path where the skill will be created
- **Skill name:** `workflow-name`
- **Main content:** workflow steps, files, conventions
- **Rule (if repo-specific and not global):** a rule will be created in `.cursor/rules/` with `alwaysApply: true` to oblige reading the workflow skill

Only proceed after confirmation.

---

## Workflow types

| Type | Where to install | Rule |
|------|------------------|------|
| **Generic** | `~/.cursor/skills/<workflow-name>/` | No rule — agent loads the skill when relevant |
| **Repo-specific** (global) | `~/.cursor/skills/<workflow-name>/` | No rule — user activates manually or by context |
| **Repo-specific** (in project) | `.cursor/skills/<workflow-name>/` or `.agents/skills/<workflow-name>/` | **Create rule** in `.cursor/rules/` that obliges reading and following the workflow skill |

---

## When repo-specific and installed in the project

If the workflow is repository-specific and is created in `.cursor/skills/` or `.agents/skills/` (not global), it is **required** to create a rule that forces the agent to consult the skill.

### Required rule

Create file `.cursor/rules/project-workflow.mdc` (or appropriate name) with:

```markdown
---
description: >
  Follow the project's workflow skill when working in this repository. The workflow defines
  conventions for branches, requisitos, implementation, and documentation. Read the skill at
  .cursor/skills/<workflow-name>/SKILL.md (or .agents/skills/<workflow-name>/SKILL.md) before
  planning or executing tasks.
alwaysApply: true
---

# Project workflow (required)

When working in this repository, **you must read and follow the project's workflow skill**.

- The skill is in `.cursor/skills/<workflow-name>/` (or `.agents/skills/<workflow-name>/`).
- Consult the `SKILL.md` file before planning or executing tasks.
- Follow the defined conventions: branch, directories, `requisitos.md`, `plan.md`, etc.
```

Replace `<workflow-name>` with the actual skill name (e.g. `gin-workflow`, `my-project-workflow`).

---

## Workflow skill structure

The skill follows the standard structure; `SKILL.md` should include:

1. **Lifecycle** — table or list of workflow steps (e.g. Jira → branch → requisitos → implementation → PR)
2. **Agent behaviour** — what to do when the user provides a requirement, during implementation, on completion
3. **Templates** — minimal structures for `requisitos.md`, `plan.md`, etc.
4. **Quick rules** — language, file locations, branch convention

See [gin-workflow](https://github.com/mariocosttaa/my-agent-skills/tree/gin-workflow) as reference.

---

## Summary: what to create

| Component | Generic (global) | Repo-specific (global) | Repo-specific (project) |
|-----------|------------------|------------------------|-------------------------|
| Skill folder | `~/.cursor/skills/<name>/` | `~/.cursor/skills/<name>/` | `.cursor/skills/<name>/` or `.agents/skills/<name>/` |
| SKILL.md | ✅ | ✅ | ✅ |
| reference.md | optional | optional | optional |
| Rule `.cursor/rules/` | ❌ | ❌ | ✅ required |

The rule ensures that when the agent works in the repo, it **reads and applies** the workflow skill automatically.
