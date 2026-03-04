---
name: gin-workflow
description: >
  Planificação e execução do fluxo de trabalho por requisito no projeto GIN (Jira + repositório).
  Usar quando o utilizador indicar um requisito Jira (ex. GIN-AZ-42), pedir para criar/abrir uma
  feature, escrever requisitos.md, plan.md, tasks.md, suggestions.md ou overview.md, atualizar o
  README, ou seguir o workflow. A skill deve ser lida no início (setup) e durante (preenchimento).
  Ao trabalhar no README, usar a skill github-readme.
---

# GIN Workflow — Requisito → Plano → Tarefas → Overview

Fluxo de trabalho por requisito no repositório. *Contexto:* o requisito vem do Jira (ex.: GIN-AZ-42); o utilizador gere o Kanban e o PR. A skill deve ser **relida no início** (setup) e **durante** (preenchimento). Ficheiros: `requisitos.md`, `plan.md`, `tasks.md`, `overview.md`; `suggestions.md` é opcional.

---

## Fase 1: Início (setup)

Branch, directório, requisitos, estrutura e README.

| Passo | O que fazer |
|-------|-------------|
| 1 | Criar a feature branch: `git checkout -b GIN-AZ-42`. |
| 2 | Criar o directório da feature: `/<código-jira>/`. |
| 3 | Criar `requisitos.md` com a descrição do requisito (pt-PT). |
| 4 | Criar `plan.md`, `tasks.md`, `overview.md` (templates ou vazios); opcionalmente `suggestions.md`. |
| 5 | Actualizar o README com a secção da nova feature e links para os ficheiros. |

---

## Fase 2: Durante (preenchimento)

Plan, tasks, suggestions e overview ao longo da implementação.

| Ficheiro | Quando preencher |
|----------|------------------|
| `plan.md` | Durante: abordagem, decisões, ordem de trabalho. |
| `tasks.md` | Durante: marcar `[x]` conforme se avança; adicionar tarefas se necessário. |
| `suggestions.md` | Durante (opcional): melhorias ou correções vistas que não dependem do requisito. |
| `overview.md` | Ao concluir: resumo final do implementado. |

---

## Os ficheiros

| Ficheiro | Obrigatório | Propósito |
|----------|-------------|-----------|
| `requisitos.md` | ✅ | Descrição do requisito, critérios de aceitação. |
| `plan.md` | ✅ | Plano de execução; preencher durante a implementação. |
| `tasks.md` | ✅ | Checklist `[ ]` / `[x]`; actualizar durante. |
| `overview.md` | ✅ | Resumo final (preencher ao concluir). |
| `suggestions.md` | Opcional | Erros encontrados e sugestões que não dependem do requisito; com referência e local. |

### suggestions.md (opcional)

Regista **erros encontrados** e **sugestões** durante a implementação que **não fazem parte do requisito atual**. Secções: Erros encontrados, Sugestões de melhoria, Outras notas. Tabela com colunas *Local* (ficheiro/path/linha), *Descrição* e *Objectivo*. Ver [assets/suggestions.template.md](assets/suggestions.template.md).

---

## Formato de `tasks.md`

Cada tarefa é uma linha com `[ ]` (por fazer) ou `[x]` (concluída). Uma linha em branco entre tarefas. Opcionalmente, uma descrição curta abaixo da tarefa.

```markdown
[x] - Criar endpoint de validação de email

[ ] - Adicionar testes unitários

Implementar com Jest, mock do repositório.

[ ] - Actualizar documentação da API
```

**Regras:**
- `[ ]` = tarefa por fazer; `[x]` = tarefa concluída.
- Linha em branco entre cada tarefa.
- Abaixo da tarefa (opcional): descrição curta numa ou mais linhas, antes da próxima tarefa.
- Actualizar `tasks.md` à medida que se avança; marcar `[x]` quando a tarefa estiver feita.

---

## Comportamento do agente

### Fase 1: Início (setup) — quando o utilizador entrega o requisito

1. **Identificar o código Jira** (ex.: GIN-AZ-42). Se não for dado, perguntar.
2. **Criar a estrutura**:
   - Branch: `git checkout -b GIN-AZ-42`.
   - Directório: `/<código-jira>/` (ex.: `/GIN-AZ-42/`).
3. **Criar os ficheiros** dentro desse directório:
   - `requisitos.md` — descrição do requisito em pt-PT.
   - `plan.md` — template ou vazio (a preencher durante).
   - `tasks.md` — checklist inicial com `[ ]`; derivar do requisito.
   - `overview.md` — vazio ou com cabeçalho (a preencher ao concluir).
   - `suggestions.md` — opcional, vazio (a preencher durante).
4. **Actualizar o README** com a secção da nova feature.
5. Confirmar ao utilizador: directório criado, ficheiros criados, README actualizado.

### Fase 2: Durante (preenchimento) — durante a implementação

- **plan.md**: Preencher abordagem, decisões, ordem de trabalho; actualizar se o plano mudar.
- **tasks.md**: Marcar `[x]` quando concluída; adicionar descrições curtas abaixo das tarefas; adicionar novas tarefas se necessário.
- **suggestions.md** (opcional): Registar erros encontrados e sugestões; indicar sempre o local (ficheiro/path) e o objectivo.
- Commits granulares e mensagens descritivas na branch da feature.

### Ao concluir a implementação

- **Revisar `tasks.md`**: tarefas relevantes com `[x]`.
- **Preencher `overview.md`**: resumo conciso do implementado (pt-PT).
- **Actualizar o README** se necessário.

---

## README do repositório

- **Quando:** Ao criar uma nova feature ou ao concluir implementação.
- **Como:** Usar a skill **github-readme**; perguntar antes de reescrever o README inteiro.
- **Conteúdo obrigatório:** Secção que refira os ficheiros por feature:
  - `requisitos.md`, `plan.md`, `tasks.md`, `overview.md`; opcionalmente `suggestions.md`.

Exemplo: "Em cada pasta `<código-jira>/` existem `requisitos.md`, `plan.md`, `tasks.md`, `overview.md` e, opcionalmente, `suggestions.md`."

---

## Templates

- [assets/requisitos.template.md](assets/requisitos.template.md)
- [assets/plan.template.md](assets/plan.template.md)
- [assets/tasks.template.md](assets/tasks.template.md)
- [assets/overview.template.md](assets/overview.template.md)
- [assets/suggestions.template.md](assets/suggestions.template.md) (opcional)

Referência adicional em [reference.md](reference.md).

---

## Regras rápidas

- **Idioma**: todos os ficheiros sempre em **português de Portugal**.
- **Localização**: todos em `/<código-jira>/`, ex.: `GIN-AZ-42/requisitos.md`, `GIN-AZ-42/plan.md`, etc.
- **Branch**: nome igual ao código Jira (ex.: `GIN-AZ-42`).
- **tasks.md**: `[ ]` por fazer, `[x]` concluída; linha em branco entre tarefas; descrição curta opcional abaixo.
- **Commits**: granulares e descritivos na branch da feature.
- **README**: actualizar na fase início e ao concluir; incluir secção que ligue aos ficheiros da feature.
