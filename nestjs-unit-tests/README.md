# nestjs-unit-tests

Cursor skill for **unit tests** in NestJS with Jest — co-location, mocks, services, controllers.

## What this skill does

- **Placement** — Co-located with code; `*.spec.ts` (e.g. `users.service.spec.ts`).
- **Syntax** — `Test.createTestingModule()`, `useValue`, `jest.fn()`, `afterEach(() => jest.resetAllMocks())`.
- **Scope** — Services, Controllers (mocked), Guards, Pipes, Interceptors; not Modules or private methods.
- **Comments** — English, 1–2 lines, objective.

## When to use

- Unit tests in NestJS, `*.spec.ts`, Jest.

**Not for:** integration tests (nestjs-integration-tests) or browser E2E (nestjs-e2e-tests).

## Files

| File | Use |
|------|-----|
| `SKILL.md` | Agent instructions |
| `reference.md` | Examples (service, controller, guard) with comments |

## Install

```bash
git clone -b nestjs-unit-tests https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/nestjs-unit-tests ~/.cursor/skills/
```

---

→ [See all skills on main](https://github.com/mariocosttaa/my-agent-skills)
