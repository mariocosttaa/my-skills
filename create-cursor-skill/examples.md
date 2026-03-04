# Examples of well-structured Skills

## Example 1 — Minimal skill

Folder: `~/.cursor/skills/commit-helper/`

**SKILL.md:**

```markdown
---
name: commit-helper
description: Generates conventional commit messages by analyzing git diffs. Use when the user asks for help writing commit messages or reviewing staged changes.
---

# Commit Helper

1. Run `git diff --cached` (or `git status`) to see staged changes.
2. Summarize scope (e.g. feat, fix, docs) and short description.
3. Output in format: `type(scope): description` with optional body.
```

File structure:

```
commit-helper/
└── SKILL.md
```

---

## Example 2 — Skill with reference and README

Folder: `.cursor/skills/code-review/`

**SKILL.md:**

```markdown
---
name: code-review
description: Reviews code for quality, security, and maintainability. Use when reviewing pull requests, code changes, or when the user asks for a code review.
---

# Code Review

## Quick Start

1. Check correctness and edge cases.
2. Verify security (e.g. injection, XSS).
3. Assess readability and maintainability.
4. Ensure tests cover the changes.

## Feedback format

- 🔴 **Critical**: Must fix before merge
- 🟡 **Suggestion**: Consider improving
- 🟢 **Nice to have**: Optional

For detailed standards, see [STANDARDS.md](references/STANDARDS.md).
```

**references/STANDARDS.md** (summary content): security checklist, style conventions, etc.

**README.md:** skill description, when to use, folder structure (for humans).

Structure:

```
code-review/
├── SKILL.md
├── README.md
└── references/
    └── STANDARDS.md
```

---

## Example 3 — Skill with scripts

Folder: `.cursor/skills/deploy-app/`

**SKILL.md:**

```markdown
---
name: deploy-app
description: Deploys the application to staging or production. Use when the user mentions deployment, releases, or environments.
---

# Deploy App

## Usage

1. Run validation: `python scripts/validate.py`
2. Deploy: `./scripts/deploy.sh <environment>` (staging | production)
```

Structure:

```
deploy-app/
├── SKILL.md
├── scripts/
│   ├── validate.py
│   └── deploy.sh
└── README.md
```

---

## Example 4 — .mdc Rule (Rule, not Skill)

File: `.cursor/rules/typescript-standards.mdc`

```markdown
---
description: TypeScript and React conventions for this project. Use when editing .ts or .tsx files.
globs: "**/*.{ts,tsx}"
alwaysApply: false
---

# TypeScript Standards

- Use strict mode; avoid `any`.
- Prefer functional components and hooks in React.
- Export types from a dedicated types file per feature.
```

This is a **Rule**, not a Skill: lives in `.cursor/rules/`, uses `globs` and `alwaysApply`, and has no folder with SKILL.md.

---

## Summary

| Example | Content | When to use as template |
|---------|---------|-------------------------|
| 1 | SKILL.md only | Very simple skill, no extras |
| 2 | SKILL + references + README | Skill with detailed documentation |
| 3 | SKILL + scripts + README | Skill that runs scripts |
| 4 | .mdc in .cursor/rules/ | Project rules (not a skill) |
