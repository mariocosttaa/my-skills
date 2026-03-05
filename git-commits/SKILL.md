---
name: git-commits
description: >
  Guides Git commit messages and workflow: grouping changes, conventional commit format,
  branching (checkout, carry changes to feature branch, push). Use when the user wants to
  commit, write commit messages, follow commit rules, switch branches with uncommitted
  changes, or push to a feature branch. Always ask preferred commit language (English or
  other) and when in doubt ask before acting unless explicitly told to just do it.
---

# Git Commits & Branching

Skill for consistent commit messages, file grouping and branch flow (checkout with changes, push to feature branch). Based on Conventional Commits and branching best practices.

---

## Before acting: ask

1. **Commit language** — Always ask: "Do you want commit messages in English or another language?" before drafting or suggesting messages. Do not assume English by default.
2. **When in doubt** — If unsure (e.g. how to group files, which type to use, one or several commits), **ask the user** instead of proceeding. Only proceed without asking if the user explicitly says to "do it" or "apply" without further details.

---

## Change grouping (guideline, not strict)

### Focus per commit
- **Group related files** that form a complete logical change.
- **Keep each commit focused** on a single change (atomic commits).
- **Do not mix** unrelated changes in the same commit.

**Number of files:** There is no fixed maximum. A reference value is ~5 files per commit when it makes sense (e.g. Model + Resource + Controller + Request + Component for the same feature). The limit is **subjective** and depends on the diff: many small related changes can justify a single commit; few files with very different changes should be separate commits.

### Group in the same commit when:
- Same feature (e.g. Model + Resource + Controller + Request + Component).
- Related bug fixes in several files.
- Refactor affecting several related components.

### Separate commits when:
- Isolated bug fix.
- Documentation updates.
- Style changes.
- Unrelated features or fixes.

---

## Commit message format

### Structure (Conventional Commits + bullet body)

```
type[(scope)]: brief description

- bullet point for each file/change
- keep it concise and clear
```

- **type** (required): see list below.
- **scope** (optional): part of the codebase affected, e.g. `feat(auth):`, `fix(api):`.
- **description**: short summary in imperative mood ("add" not "added"); language as agreed with the user (EN or other).
- **body** (optional): bullets or paragraphs with detail; use bullets per file/change when useful.

### Types (Conventional Commits)
- `feat:` New feature (MINOR in SemVer).
- `fix:` Bug fix (PATCH in SemVer).
- `docs:` Documentation.
- `style:` Formatting/style (no logic change).
- `refactor:` Refactoring.
- `perf:` Performance.
- `test:` Tests.
- `ci:` CI/CD configuration.
- `build:` Build or dependencies.
- `chore:` Maintenance, configs, general tasks.

### Breaking changes
- In **footer**: `BREAKING CHANGE: description`.
- Or in prefix: `feat(api)!: description` (the `!` before the `:`).

### Mandatory: no Made-with trailer
- **Never** add `Made-with: Cursor` or similar trailers/footers to commit messages.
- This is mandatory. Strip them if the IDE pre-fills them before committing.

---

## Message examples

### Good — related files
```
feat: implement user management CRUD

- Add UserModel with relationships
- Create UserResource with ID hashing
- Add UserCreateRequest validation
- Implement UserCreateModal component
- Update PanelUsersController
```

### Good — single file
```
fix: resolve date parsing in booking calendar

- Fix timezone handling in DateSelectionCalendar.tsx
```

### Good — with scope and breaking change
```
feat(api)!: require auth for all endpoints

- Add middleware to protect routes
- Update OpenAPI spec

BREAKING CHANGE: unauthenticated requests now return 401
```

### Bad — many unrelated topics in one commit
```
feat: various improvements

- Add user management
- Fix booking calendar
- Update documentation
- Refactor modal components
```

### Bad — vague description
```
fix: stuff
```

---

## Workflow before committing

1. See which files changed: `git status` (and optionally `git diff`).
2. Group related files (following the focus guideline).
3. Write a clear message in the format above (in the agreed language).
4. Test changes before committing.

### Useful commands
```bash
git status
git add file1.php file2.php file3.php
git commit -m "type: description

- change 1
- change 2"
git push origin <branch-name>
```

---

## Branching: carry changes to another branch and push

When the user wants to **switch branch but take changes** (uncommitted) to a feature branch and push:

### Option A — changes already committed
- Checkout the target branch (e.g. feature/xyz).
- If changes were made on another branch: merge or rebase that branch into feature/xyz, then `git push origin feature/xyz`.

### Option B — changes not yet committed (stash)
1. Save changes: `git stash push -u -m "brief description"` (includes untracked with `-u`).
2. Switch branch: `git checkout feature/feature-name` (or `git switch feature/feature-name`).
3. Apply stash: `git stash pop` (or `git stash apply` to keep the stash).
4. Resolve conflicts if any.
5. Commit and push: `git add ...`, `git commit -m "..."`, `git push origin feature/feature-name`.

### Branch names (best practices)
- `feature/description` — new feature.
- `bugfix/description` or `fix/description` — bug fix.
- `docs/description` — documentation.
- Avoid direct commits to `main`/`master`; use feature branches and merge/PR.

### Before push
- Update branch with remote if needed: `git pull origin <branch> --rebase` (or `git pull` per project flow).
- Avoid `git commit --amend` on already pushed commits (breaks shared history).

---

## Best practices

### Do
- Atomic commits (one logical change per commit).
- Descriptive messages in type: description (+ body) format.
- Test before committing.
- Use the agreed language for messages.
- Branch per feature/fix; push to the correct branch.

### Avoid
- Many unrelated files in the same commit.
- Vague messages ("fix", "update").
- Mixing features and fixes in the same commit.
- Committing without testing.
- Amend on already pushed commits without team agreement.

---

## Quick checklist before committing

- [ ] Are these files related? (focus per commit)
- [ ] Is the message clear and in type: description format?
- [ ] Did I use the agreed language (EN or other)?
- [ ] Did I test the changes?
- [ ] Does the commit correspond to a single logical change?

When in doubt: ask the user. For more detail (Conventional Commits, SemVer, revert), see [reference.md](reference.md).
