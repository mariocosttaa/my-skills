# editor-cursor-skill

Edits Cursor Agent Skills in the my-skills repo and/or global `~/.cursor/skills`. Keeps the repo as source of truth: edit once in the repo, then sync to global.

## Install (global)

```bash
git clone https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/editor-cursor-skill ~/.cursor/skills/
```

Or from this repo:

```bash
cp -r editor-cursor-skill ~/.cursor/skills/
```

## Usage

Ask the agent to edit a skill, e.g.:

- "Edit the gin-workflow skill: add a section about cleanup"
- "Update the docker skill description"
- "Fix the typo in step 2 of git-commits"
- "Sync the qa-agent skill to global after my edits"

The skill will determine where the skill exists (repo, global, or both) and follow the edit-once-then-sync workflow.
