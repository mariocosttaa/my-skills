# Reference: Git Commits & Branching

Additional detail for the git-commits skill (Conventional Commits, SemVer, revert, branch strategies).

---

## Conventional Commits (summary)

Spec: [conventionalcommits.org](https://www.conventionalcommits.org/)

- **Structure:** `<type>[(scope)]: <description>` + optional body + optional footer.
- **Types** used in the skill: feat, fix, docs, style, refactor, perf, test, ci, build, chore.
- **Scope:** noun describing the area (e.g. `parser`, `api`, `auth`).
- **BREAKING CHANGE:** in footer or `!` after type/scope (e.g. `feat!:`).

---

## SemVer and types

- `fix` → PATCH (1.0.x)
- `feat` → MINOR (1.x.0)
- BREAKING CHANGE → MAJOR (x.0.0)

---

## Revert

To revert commits, use type `revert` and reference the SHAs in the footer:

```
revert: let us never again speak of the noodle incident

Refs: 676104e, a215868
```

---

## Branch strategies (reference)

- **Git Flow:** main (production), develop (integration), feature/*, bugfix/*, release/*.
- **GitHub Flow:** main + feature branches; deploy from main.
- **Trunk-based:** main always deployable; short-lived branches.

The skill does not enforce a strategy; adapt to the project (and ask if there is no convention).

---

## Useful stash commands

- `git stash list` — list stashes.
- `git stash drop` — remove last stash after pop.
- `git stash branch branch-name` — create branch and apply stash (useful to avoid mixing with other work).
