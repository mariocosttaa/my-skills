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

| Branch | Skill |
|--------|-------|
| `main` | Todas as skills |
| `create-cursor-skill` | Criar novas skills no Cursor |
| `docker` | Docker, Dockerfile, docker-compose |
| `gin-workflow` | Workflow GIN (Jira + repositório) |
| `git-commits` | Mensagens de commit e branching |
| `github-readme` | README do GitHub |
| `nestjs-e2e-tests` | E2E com Playwright (NestJS) |
| `nestjs-integration-tests` | Testes de integração NestJS |
| `nestjs-unit-tests` | Testes unitários NestJS |

Para outra skill, troca `git-commits` pelo nome da branch, ex.:

```bash
git clone -b docker https://github.com/mariocosttaa/my-skills.git
```

---

## Repositório

[https://github.com/mariocosttaa/my-skills](https://github.com/mariocosttaa/my-skills)
