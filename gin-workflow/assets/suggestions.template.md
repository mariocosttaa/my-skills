# Sugestões — [Código Jira]

Coisas observadas durante a implementação que **não fazem parte do requisito atual**. Cada entrada deve ter **referência/local** (ficheiro, path, linha) e **objectivo** (o que corrigir ou melhorar). Útil para backlog ou tarefas futuras.

---

## Erros encontrados

Problemas, bugs ou inconsistências vistas no código; não resolvidas porque estão fora do âmbito do requisito.

| Local | Descrição | Objectivo |
|-------|-----------|-----------|
| `src/auth/validators/email.ts:12` | Validação não considera domínios internacionais | Corrigir regex para suportar IDN |
| `src/users/repository.ts` | Query N+1 na listagem de utilizadores | Adicionar eager loading ou batch |

---

## Sugestões de melhoria

Refactors, melhorias de UX, comentários, technical debt; propostas para trabalho futuro.

| Local | Descrição | Objectivo |
|-------|-----------|-----------|
| `src/users/controller.ts` | Lógica de paginação repetida em vários endpoints | Extrair para decorator ou interceptor reutilizável |
| `frontend/Login.tsx` | Sem feedback visual durante loading | Adicionar spinner ou skeleton |
| `docker-compose.yml` | Healthcheck do Postgres pode ser mais robusto | Aumentar interval e timeout |

---

## Outras notas

[Opcional: observações gerais, dependências, dívida técnica, etc.]
