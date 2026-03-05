# nestjs-e2e-tests

Cursor skill for **browser E2E tests** with **Playwright** — POM, selectors, fixtures.

## What this skill does

- **Playwright** — Auto-waiting, multi-browser.
- **POM** — Page Object Model in `e2e/pages/`; selectors and actions encapsulated.
- **Selectors** — data-testid > getByRole/getByLabel > getByText; avoid CSS/XPath.
- **Fixtures** — Page Objects and `authenticatedPage` to avoid repeated login.
- **Structure** — `e2e/tests/`, `e2e/pages/`, `e2e/fixtures/`; `playwright.config.ts`.
- **Scope** — Critical happy paths (login, register, main flows); not edge cases.

## When to use

- Browser E2E tests, Playwright, Page Objects, Cypress, login/UI flows.

**Not for:** unit tests (nestjs-unit-tests) or API-only integration (nestjs-integration-tests).

## Files

| File | Use |
|------|-----|
| `SKILL.md` | Agent instructions |
| `reference.md` | POM, selectors, examples |

## Install

**Latest:**
```bash
git clone https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/nestjs-e2e-tests ~/.cursor/skills/
```

**Specific version:** clone repo → checkout `versions` → copy `nestjs-e2e-tests/versions/vX.Y/` to `~/.cursor/skills/nestjs-e2e-tests/`.

---

→ [See all skills](https://github.com/mariocosttaa/my-agent-skills)
