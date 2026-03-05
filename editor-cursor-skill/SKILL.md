---
name: editor-cursor-skill
description: >
  Edits Cursor Agent Skills in global ~/.cursor/skills and/or my-skills repo. Use when the user
  wants to edit a skill, change a skill, update skill instructions, sync a skill between repo and
  global, or modify any SKILL.md. **Always edits in global first**, then copies to my-skills if it
  exists there, so both stay in sync.
---

# Editor Cursor Skill

Edits Cursor Agent Skills. **Rule:** Always edit in global (`~/.cursor/skills`) first. If the skill also exists in my-skills, copy from global to my-skills to keep both updated. This avoids edits in only one location and ensures consistency.

---

## Paths (macOS/Linux)

| Location | Path |
|----------|------|
| my-skills repo (sync target) | `/Users/mario/Documents/dev-projects/others/my-skills/<skill-name>/` |
| Global Cursor | `~/.cursor/skills/<skill-name>/` → `/Users/mario/.cursor/skills/<skill-name>/` |

---

## Before editing: gather

1. **Skill name** — e.g. `gin-workflow`, `docker`, `git-commits`. Ask if not given.
2. **What to change** — From the user prompt. E.g. "add a section about X", "update the description", "fix typo in step 3".
3. **Location** — Infer by checking both paths; if unclear, ask:
   - **repo-only**: Only in my-skills (e.g. new skill, not yet installed globally)
   - **global-only**: Only in `~/.cursor/skills` (e.g. `docs-editor`, not in my-skills)
   - **both**: Exists in both — **edit in global first**, then copy global → my-skills

---

## Workflow: edit global first, sync to my-skills after

### Rule: Always edit in global first

**Edit in `~/.cursor/skills/<skill-name>/` first.** Global is the location Cursor uses. If the skill also exists in my-skills, **copy from global to my-skills** after editing, so both stay updated. Never edit in only one place when both exist.

### Step 1: Check where the skill exists

```
global: /Users/mario/.cursor/skills/<skill-name>/
repo:   /Users/mario/Documents/dev-projects/others/my-skills/<skill-name>/
```

- If in **global** → edit in global. Then, if my-skills has this skill, copy global → my-skills.
- If **global-only** (no my-skills) → edit in global only.
- If **repo-only** (no global) → copy from my-skills to global, edit in global, then copy global → my-skills.

### Step 2: Apply edits in global

Based on the user’s request, edit the relevant files (SKILL.md, reference.md, assets/, etc.) **in global** `~/.cursor/skills/<skill-name>/`. Create the folder there if it does not exist.

### Step 3: Copy from global to my-skills (when my-skills has the skill)

If the skill folder exists in my-skills, copy from global to keep both in sync:

```bash
# Copy from global to my-skills (overwrites)
cp -r /Users/mario/.cursor/skills/<skill-name>/* /Users/mario/Documents/dev-projects/others/my-skills/<skill-name>/
```

Or, to replace the entire folder in my-skills:

```bash
rm -rf /Users/mario/Documents/dev-projects/others/my-skills/<skill-name>
cp -r /Users/mario/.cursor/skills/<skill-name> /Users/mario/Documents/dev-projects/others/my-skills/
```

Use `cp -r` to preserve subfolders (assets/, scripts/, references/). **Do not skip this step** when my-skills has the skill — both locations must stay in sync.

---

## Location decision matrix

| Skill in global? | Skill in my-skills? | Action |
|------------------|---------------------|--------|
| ✅ Yes | ✅ Yes | **Edit global** → **copy global → my-skills** |
| ✅ Yes | ❌ No | Edit global only |
| ❌ No | ✅ Yes | Create in global (or copy from my-skills), edit in global, then copy global → my-skills |
| ❌ No | ❌ No | Create in global first (use create-cursor-skill), then optionally create in my-skills and sync |

---

## Skill structure to preserve

Each skill folder can contain:

- `SKILL.md` (required)
- `reference.md`, `examples.md`, `README.md`
- `assets/`, `scripts/`, `references/`

When syncing, copy the whole folder contents so nothing is lost.

---

## After editing

1. Confirm what was changed (files and edits).
2. If copied to my-skills, say so.
3. For my-skills: suggest committing (e.g. `git add <skill>/`, `git commit`). Do not commit automatically unless the user asks.
