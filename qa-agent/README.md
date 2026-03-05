# qa-agent

Cursor skill for **QA engineering** — browser testing, code review, UI/UX evaluation, structured reports.

> **Required: Browser MCP** — This skill needs **mario-playwright-mcp** or **browsermcp** in `.cursor/mcp.json`. Without MCP, the agent cannot run browser tests. Add the MCP server and restart Cursor before use.

---

## What it does

- Browser-based testing (navigate, snapshot, click, type, screenshot) via **Browser MCP**
- Code review (security, correctness, architecture)
- UI/UX evaluation and ratings
- Post-action analysis (inspect screen after submit/create/save)
- Console and network capture for debugging
- Reports in `QA-AGENT/<project>/test/<timestamp>/` with `report/` and `browser/` folders

## When to use

- User wants to **test a website**, test in browser, test a page
- QA, quality assurance, test cases, regression, inspect page, debug console

## Prerequisites

| Requirement | Details |
|-------------|---------|
| **Browser MCP** | `mario-playwright-mcp` (recommended) or `browsermcp` in `.cursor/mcp.json` |
| App reachable | Dev server or deployed URL |

## Files

| File | Use |
|------|-----|
| `SKILL.md` | Agent instructions |
| `STRUCTURE.md` | Output folder layout |
| `reference.md` | Best practices |
| `examples.md` | MCP workflow examples |

## Install

```bash
git clone -b qa-agent https://github.com/mariocosttaa/my-agent-skills.git
cp -r my-agent-skills/qa-agent ~/.cursor/skills/
```
