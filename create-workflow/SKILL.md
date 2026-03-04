---
name: create-workflow
description: >
  Guides creation of Cursor workflow skills (like gin-workflow). Use when the user wants to define
  a development workflow for a project or team, create a workflow skill, or document conventions
  (branches, requisitos, implementação, Jira, etc.). Supports generic workflows (global) and
  repo-specific workflows. When repo-specific and installed in the project, creates a rule that
  obliges the agent to read the workflow skill.
---

# Create Workflow Skill

Guia para criar skills de workflow no Cursor — fluxos de trabalho por requisito, convenções de branch, documentação de implementação, integração com Jira/Linear, etc. Inspirado no **gin-workflow**; pode ser genérico (global) ou específico de repositório.

---

## Obrigatório: perguntas antes de começar

**Não criar ficheiros** até esclarecer o contexto e apresentar um overview ao utilizador.

### Perguntas a fazer

1. **Tipo** — Workflow genérico (qualquer repo) ou específico deste repositório?
2. **Âmbito** — Onde instalar: global (`~/.cursor/skills/`) ou no projeto (`.cursor/skills/` ou `.agents/skills/`)?
3. **Integração** — Há sistema externo? (ex.: Jira, Linear, Trello) e qual o formato de identificação (ex.: GIN-AZ-42, PROJ-123)?
4. **Estrutura de ficheiros** — Que ficheiros e pastas define o workflow? (ex.: `/<código>/requisitos.md`, `/<código>/implementacao.md`, branch = código)
5. **Idioma** — Português (pt-PT), inglês, outro?
6. **Nome** — Nome da skill (lowercase, hífens; ex.: `gin-workflow`, `my-team-workflow`).

### Overview antes de implementar

Mostrar ao utilizador:

- **Tipo:** genérico ou repo-specific
- **Localização:** path onde a skill será criada
- **Nome da skill:** `workflow-name`
- **Conteúdo principal:** passos do workflow, ficheiros, convenções
- **Rule (se repo-specific e não global):** será criada regra em `.cursor/rules/` com `alwaysApply: true` para obrigar a leitura da skill de workflow

Só avançar após confirmação.

---

## Tipos de workflow

| Tipo | Onde instalar | Rule |
|------|---------------|------|
| **Genérico** | `~/.cursor/skills/<workflow-name>/` | Não cria rule — o agente carrega a skill quando relevante |
| **Repo-specific** (global) | `~/.cursor/skills/<workflow-name>/` | Não cria rule — o utilizador activa manualmente ou por contexto |
| **Repo-specific** (no projeto) | `.cursor/skills/<workflow-name>/` ou `.agents/skills/<workflow-name>/` | **Criar rule** em `.cursor/rules/` que obriga a ler e seguir a skill de workflow |

---

## Quando repo-specific e instalado no projeto

Se o workflow for específico do repositório e for criado em `.cursor/skills/` ou `.agents/skills/` (não global), é **obrigatório** criar uma rule que force o agente a consultar a skill.

### Regra obrigatória

Criar ficheiro `.cursor/rules/project-workflow.mdc` (ou nome adequado, ex.: `project-workflow.mdc`) com:

```markdown
---
description: >
  Follow the project's workflow skill when working in this repository. The workflow defines
  conventions for branches, requisitos, implementação, and documentation. Read the skill at
  .cursor/skills/<workflow-name>/SKILL.md (or .agents/skills/<workflow-name>/SKILL.md) before
  planning or executing tasks.
alwaysApply: true
---

# Project workflow (obrigatório)

Ao trabalhar neste repositório, **deves ler e seguir a skill de workflow do projeto**.

- A skill está em `.cursor/skills/<workflow-name>/` (ou `.agents/skills/<workflow-name>/`).
- Consulta o ficheiro `SKILL.md` antes de planear ou executar tarefas.
- Segue as convenções definidas: branch, directórios, `requisitos.md`, `implementacao.md`, etc.
```

Substituir `<workflow-name>` pelo nome real da skill (ex.: `gin-workflow`, `my-project-workflow`).

---

## Estrutura da skill de workflow

A skill segue a estrutura padrão; o `SKILL.md` deve incluir:

1. **Ciclo de vida** — tabela ou lista dos passos do workflow (ex.: Jira → branch → requisitos → implementação → PR)
2. **Comportamento do agente** — o que fazer quando o utilizador indica um requisito, durante a implementação, ao concluir
3. **Templates** — estruturas mínimas para `requisitos.md`, `implementacao.md`, etc.
4. **Regras rápidas** — idioma, localização de ficheiros, convenção de branch

Ver [gin-workflow](https://github.com/mariocosttaa/my-skills/tree/gin-workflow) como referência.

---

## Resumo: o que criar

| Componente | Genérico (global) | Repo-specific (global) | Repo-specific (projeto) |
|------------|-------------------|------------------------|-------------------------|
| Pasta da skill | `~/.cursor/skills/<name>/` | `~/.cursor/skills/<name>/` | `.cursor/skills/<name>/` ou `.agents/skills/<name>/` |
| SKILL.md | ✅ | ✅ | ✅ |
| reference.md | opcional | opcional | opcional |
| Rule `.cursor/rules/` | ❌ | ❌ | ✅ obrigatório |

A rule garante que, quando o agente trabalha no repo, **lê e aplica** a skill de workflow automaticamente.
