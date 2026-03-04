# my-skills

Colecção de **Cursor Agent Skills** — capacidades específicas para o editor [Cursor](https://cursor.com) que guiam o AI a seguir boas práticas e workflows em tarefas concretas (commits, Docker, NestJS, README, etc.).

---

## O que são Skills e Rules?

| | Skills | Rules |
|---|--------|--------|
| **O que é** | Pacotes com instruções detalhadas que o agente usa *quando relevante* para o prompt | Regras curtas que correm *em cada prompt* (ou por ficheiro) |
| **Carregamento** | Só são carregadas se o prompt indicar que são úteis | Sempre aplicadas (ou conforme `globs` / ficheiro em uso) |
| **Estrutura** | Pasta com `SKILL.md` + opcional `reference.md`, `scripts/`, `assets/` | Ficheiro `.mdc` ou `.md` em `.cursor/rules/` |
| **Exemplo** | `git-commits` — ajuda com commits e branching | `.cursor/rules/inline-comments.mdc` — comentários em inglês |

Estas skills são **específicas para o Cursor** e seguem o formato [agentskills.io](https://agentskills.io).

---

## Onde colocar Skills

| Âmbito | Directório |
|--------|------------|
| **Global** (todos os projectos) | `~/.cursor/skills/<nome-skill>/` |
| **Projecto** (só este repo) | `.cursor/skills/<nome-skill>/` ou `.agents/skills/<nome-skill>/` |

Exemplo para a pasta `git-commits`:

- Global: `~/.cursor/skills/git-commits/`
- Projecto: `.cursor/skills/git-commits/` (na raiz do repo)

---

## Como fazer download de uma skill

Cada skill está numa **branch própria**, para poderes descarregar só o que precisas.

### Exemplo: skill `git-commits`

```bash
# Clonar o repo já na branch git-commits (só traz essa pasta)
git clone -b git-commits https://github.com/mariocosttaa/my-skills.git
cd my-skills
```

Ficas com:
```
my-skills/
├── README.md
└── git-commits/
    ├── SKILL.md
    ├── README.md
    └── reference.md
```

### Instalar no Cursor (exemplo: git-commits)

```bash
# Instalar globalmente
cp -r git-commits ~/.cursor/skills/

# Ou, para um projecto específico:
mkdir -p .cursor/skills
cp -r git-commits .cursor/skills/
```

---

### Branches disponíveis

A versão começa em **1.0** e incrementa com cada commit. Cada skill tem a sua branch; o comando de instalação copia a pasta para `~/.cursor/skills/`.

| Branch | Skill | v. inicial | v. actual | Instalar (copiar) |
|--------|-------|------------|-----------|-------------------|
| `main` | Todas as skills | 1.0 | 1.6 | `git clone https://github.com/mariocosttaa/my-skills.git && cd my-skills && cp -r create-* docker gin-workflow git-* github-readme nestjs-* ~/.cursor/skills/` |
| `create-cursor-skill` | Criar novas skills no Cursor | 1.0 | 1.5 | `git clone -b create-cursor-skill https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/create-cursor-skill ~/.cursor/skills/` |
| `create-workflow` | Criar skills de workflow (genérico ou repo-specific) | 1.0 | 1.6 | `git clone -b create-workflow https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/create-workflow ~/.cursor/skills/` |
| `docker` | Docker, Dockerfile, docker-compose | 1.0 | 1.5 | `git clone -b docker https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/docker ~/.cursor/skills/` |
| `gin-workflow` | Workflow GIN (Jira + repositório) | 1.0 | 1.3 | `git clone -b gin-workflow https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/gin-workflow ~/.cursor/skills/` |
| `git-commits` | Mensagens de commit e branching | 1.0 | 1.3 | `git clone -b git-commits https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/git-commits ~/.cursor/skills/` |
| `github-readme` | README do GitHub | 1.0 | 1.3 | `git clone -b github-readme https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/github-readme ~/.cursor/skills/` |
| `nestjs-e2e-tests` | E2E com Playwright (NestJS) | 1.0 | 1.3 | `git clone -b nestjs-e2e-tests https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/nestjs-e2e-tests ~/.cursor/skills/` |
| `nestjs-integration-tests` | Testes de integração NestJS | 1.0 | 1.3 | `git clone -b nestjs-integration-tests https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/nestjs-integration-tests ~/.cursor/skills/` |
| `nestjs-unit-tests` | Testes unitários NestJS | 1.0 | 1.3 | `git clone -b nestjs-unit-tests https://github.com/mariocosttaa/my-skills.git && cp -r my-skills/nestjs-unit-tests ~/.cursor/skills/` |

Para instalar **por projecto** em vez de global, troca `~/.cursor/skills/` por `.cursor/skills/` (na raiz do repo).

---

## Repositório

[https://github.com/mariocosttaa/my-skills](https://github.com/mariocosttaa/my-skills)
