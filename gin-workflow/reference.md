# Referência: GIN Workflow

## Convenções rápidas

| Elemento | Formato |
|----------|---------|
| Código Jira | `GIN-AZ-42` (maiúsculas, hífen) |
| Branch | Igual ao código Jira |
| Directório | `/<código-jira>/` |
| requisitos.md | pt-PT, descrição do requisito |
| plan.md | pt-PT, plano de execução (preencher durante) |
| tasks.md | pt-PT, checklist `[ ]` / `[x]` |
| overview.md | pt-PT, resumo final (preencher ao concluir) |
| suggestions.md | pt-PT, opcional; erros e sugestões com referência/local |

## Formato de tasks.md

- `[ ]` — tarefa por fazer
- `[x]` — tarefa concluída
- Linha em branco entre cada tarefa
- Opcional: descrição curta abaixo da tarefa (uma ou mais linhas), antes da próxima

## Integração com Jira

- O código Jira vem do identificador da issue (ex.: GIN-AZ-42). O utilizador gere o Kanban e o PR.
- Ao criar a branch e o directório, usar o código exato da issue.
- Referenciar o código em commits quando útil: `feat(GIN-AZ-42): adicionar validação de email`.

## Relação com outras skills

- **github-readme**: Usar ao actualizar o README; incluir referência aos ficheiros da feature.
- **git-commits**: Commits granulares e mensagens descritivas.

## Formato de suggestions.md

Secções: **Erros encontrados**, **Sugestões de melhoria**, **Outras notas**. Tabela com colunas:

| Local | Descrição | Objectivo |
|-------|-----------|-----------|
| `path/ficheiro:linha` ou `path/ficheiro` | O que foi observado | O que corrigir ou melhorar |

## Fases

- **Início (setup)**: branch, directório, requisitos, estrutura, README.
- **Durante (preenchimento)**: plan, tasks, suggestions (opcional), overview ao concluir.

## Templates

Ver `assets/requisitos.template.md`, `assets/plan.template.md`, `assets/tasks.template.md`, `assets/overview.template.md`, `assets/suggestions.template.md`.
