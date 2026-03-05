# QA Plan — [Código Jira]

Context for the test team. Use when passing a new feature, fix, or removal to QA.

**Regra:** Nunca assumir URL, credenciais ou perspectiva de teste. Pedir ao utilizador toda a informação em falta antes de preencher.

---

## Resumo

**Tipo de alteração:** [Nova funcionalidade | Correção | Remoção]

[Resumo conciso do que foi implementado, corrigido ou removido. Em português de Portugal.]

---

## Perspectiva de teste

**Perguntar ao utilizador:** "O teste é mais na óptica de utilizador (UI, fluxos, experiência) ou técnica/interna (API, integração, logs)?"

| Perspectiva | Descrição |
|-------------|-----------|
| **Utilizador** | Foco em fluxos de UI, experiência do utilizador, cenários de uso reais |
| **Técnica/Interna** | Foco em API, integração, payloads, logs, validações técnicas |

*Preencher conforme resposta do utilizador. Se não souber, perguntar.*

---

## URL(s) e ambiente

**Perguntar ao utilizador:** "Qual a URL para testar?"

- **URL principal:** [ex: http://localhost:3000/login — **não assumir**; pedir se em falta]
- **URL API (se aplicável):** [ex: http://localhost:4444]
- **Ambiente:** [local | staging | outro]

---

## Contexto técnico

- **Branch:** `[Jira-code]`
- **Ficheiros principais alterados:** [lista ou caminhos relevantes]
- **Áreas afectadas:** [módulos, endpoints, UI, etc.]
- **Dependências:** [APIs externas, serviços, base de dados]

---

## Ambiente de testes

- **Variáveis de ambiente:** [lista se necessário; não incluir segredos]
- **Como correr localmente:** [comandos, pré-requisitos]
- **Dados de seed ou fixtures:** [se aplicável]

---

## Contas e credenciais de teste

**Perguntar ao utilizador:** "Que conta(s) de teste deve o QA usar? (email, password, role)"

*Nunca assumir ou inventar credenciais. Nunca incluir credenciais de produção.*

| Uso | Tipo | Credenciais |
|-----|------|-------------|
| [ex: Login básico] | [ex: Utilizador normal] | [email/username — pedir ao utilizador; password — pedir ao utilizador] |
| [ex: Admin] | [ex: Administrador] | [idem] |

*Ou:* "Credenciais a fornecer separadamente pelo utilizador."

---

## Cenários sugeridos para teste

1. [Cenário principal 1]
2. [Cenário principal 2]
3. [Cenário de edge case]
4. [Regressão: área que pode ter sido afectada]

---

## Casos de aceitação

- [ ] [Critério 1]
- [ ] [Critério 2]
- [ ] [Critério 3]

---

## Notas adicionais

[Configurações especiais, fluxos complexos, dados de exemplo, ou avisos para QA.]
