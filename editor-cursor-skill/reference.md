# Reference: Editor Cursor Skill

## Paths and environment

On macOS/Linux:

- **my-skills repo**: `/Users/mario/Documents/dev-projects/others/my-skills/`
- **Global skills**: `~/.cursor/skills/` or `/Users/mario/.cursor/skills/`

On Windows, `~` resolves to `%USERPROFILE%`.

---

## Sync commands (reference)

### Replace entire skill folder in global

```bash
SKILL=gin-workflow
REPO=/Users/mario/Documents/dev-projects/others/my-skills
GLOBAL=~/.cursor/skills

rm -rf "$GLOBAL/$SKILL"
cp -r "$REPO/$SKILL" "$GLOBAL/"
```

### Merge contents (overwrite files, keep extra files in global)

```bash
cp -r "$REPO/$SKILL"/* "$GLOBAL/$SKILL"/
```

Use "replace entire folder" when structure might have changed (e.g. removed files). Use "merge" when only content changes.

---

## Skills known to exist in both locations

- gin-workflow
- qa-agent
- nestjs-unit-tests
- nestjs-integration-tests
- nestjs-e2e-tests
- github-readme
- git-commits
- docker
- create-workflow
- create-cursor-skill

## Skills known to be global-only (not in my-skills)

- docs-editor
