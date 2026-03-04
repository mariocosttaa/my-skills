---
name: nestjs-unit-tests
description: >
  Guides writing NestJS unit tests with Jest: file placement, naming (*.spec.ts), syntax, and
  commenting. Use when creating or editing unit tests for NestJS services, controllers, guards,
  pipes, or interceptors. Enforces comments in English (one or two lines, objective) and
  best practices: isolated tests, mocked dependencies, reset mocks. Does not cover integration
  or E2E tests.
---

# NestJS Unit Tests

Skill for writing NestJS unit tests following best practices: file placement and naming, Jest and `TestingModule` syntax, and **comments in English** (one or two lines, objective) for readability.

---

## When creating or editing tests: ask before running and fixing

1. **Run and fix tests:** When creating or changing unit tests, **ask** the user if they want you to run the tests and, if they fail, fix them. Do not assume you should run and fix automatically.
2. **Only modify test files:** If making the tests pass requires changing **another file outside the test** (e.g. the service, controller, a module or config), **do not do it**. Instead, **ask** the user: explain what is failing and what change in production code (or another file) would be needed, and ask if they want you to apply that change or prefer to resolve it another way.

Summary: ask if you should run tests and fix; when fixing, only touch `*.spec.ts` files; any change in another file requires prior confirmation.

---

## File placement and naming

- **Placement:** The test file is **in the same directory** as the file it tests (co-location).
- **Name:** `{file-name}.spec.ts`
  - Examples: `users.service.spec.ts`, `users.controller.spec.ts`, `auth.guard.spec.ts`, `validate-payload.pipe.spec.ts`

Example structure:
```
src/
  users/
    users.service.ts
    users.service.spec.ts      ← unit test for service
    users.controller.ts
    users.controller.spec.ts   ← unit test for controller
```

Do not put unit tests in separate folders (e.g. `test/unit/`); keep them with the code.

---

## Comments (required by default)

- **Language:** Always **English**.
- **Style:** One line, or two if needed; objective and brief.
- **Where:** At points that help read the test: at the start of `describe`, in `beforeEach` (what is being prepared), at the start of each `it` (scenario), and inside `it` for non-obvious steps (e.g. why a specific mock is used, what is being asserted).
- **Avoid:** Commenting every line; commenting the obvious. The goal is to aid reading without clutter.

Example of adequate density:
```typescript
// Unit tests for UserService: creation and password hashing.
describe('UserService', () => {
  let service: UserService;
  let mockRepo: jest.Mocked<UserRepository>;

  // Build testing module with mocked repository before each test.
  beforeEach(async () => {
    const module = await Test.createTestingModule({
      providers: [
        UserService,
        { provide: UserRepository, useValue: { save: jest.fn() } },
      ],
    }).compile();

    service = module.get(UserService);
    mockRepo = module.get(UserRepository);
  });

  afterEach(() => jest.resetAllMocks());

  it('should hash the password before saving the user', async () => {
    mockRepo.save.mockResolvedValue({ id: 1, email: 'test@test.com' });

    await service.createUser({ email: 'test@test.com', password: '123456' });

    const savedUser = mockRepo.save.mock.calls[0][0];
    expect(savedUser.password).not.toBe('123456');
    expect(savedUser.password).toMatch(/^\$2b\$/); // bcrypt format
  });
});
```

---

## Syntax and structure

### Framework
- **Jest** (default in NestJS) with `@nestjs/testing`: `Test.createTestingModule()`.
- One `describe` per tested class/file; `it` per behavioural scenario.

### Setup and teardown
- **beforeEach:** Create the `TestingModule`, compile, get the service/controller instance and mocks. Do not share state between tests.
- **afterEach:** Call `jest.resetAllMocks()` to avoid mocks from one test affecting another.
- **beforeAll/afterAll:** Only if strictly necessary (e.g. high setup cost); prefer `beforeEach` for isolation.

### Mocking
- Dependencies (repositories, other services) via `providers` with `useValue: { method: jest.fn() }`.
- For types: `jest.Mocked<Repository>` or `jest.Mocked<SomeService>`.
- Avoid excess mocks: test the unit's real behaviour; mock only what is external.

### What to test (unit)
- **Services:** Business logic, transformations, validations (with mocked dependencies).
- **Controllers:** Service calls and response format (service mocked; do not test real HTTP here — that is integration).
- **Guards, Pipes, Interceptors:** Isolated behaviour with controlled inputs/outputs.
- **Do not test:** Modules (config only); private methods directly (test via public API).

### Test names
- `it('should ...')` with a verb that describes the expected behaviour: "should hash the password before saving", "should return 404 when user not found".
- Avoid vague names like "works" or "test create".

---

## Quick rules

| Rule | Detail |
|-------|--------|
| File | `*.spec.ts` next to the tested file |
| Comments | English, 1–2 lines, objective; present but not excessive |
| Dependencies | Mock with `useValue` and `jest.fn()` |
| Reset | `afterEach(() => jest.resetAllMocks())` |
| Isolation | Independent tests; do not depend on execution order |
| Assertions | Validate behaviour and relevant data (e.g. hashed password, returned value) |

---

## Minimal example (service)

See [reference.md](reference.md) for full examples with comments (service, controller, guard) and additional best practices. A starter template for a service is in `assets/service.spec.template.ts`.
