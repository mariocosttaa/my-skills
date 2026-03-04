# Referência: Create Workflow

## Quando usar Rule vs só Skill

- **Rule obrigatória** quando a skill de workflow está no projeto (`.cursor/skills/` ou `.agents/skills/`): garante que o agente lê a skill em cada prompt.
- **Sem rule** quando a skill está global (`~/.cursor/skills/`): o agente carrega conforme relevância do prompt.

## Exemplo de Rule para repo-specific

```yaml
---
description: >
  Follow the project's workflow skill when working in this repository.
  Read .cursor/skills/my-project-workflow/SKILL.md before planning or executing tasks.
alwaysApply: true
---
```

## Diferença para gin-workflow

O **gin-workflow** é uma skill de workflow *já pronta* para o projeto GIN. A **create-workflow** ajuda a *criar* novas skills de workflow para outros projetos ou equipas, seguindo o mesmo padrão.
