---
title: gate-pre-pr
status: active
tags: [methodology, sdd, qa]
created: 2026-03-25
---

# Gate Pre-PR — Processo Inviolável

Todo PR em projetos SDD passa por este gate antes de merge. Sem exceções.

## Pipeline

```
Lint → Migrate (do zero) → Seed → Tests → Smoke → QA UI → Review
```

| Etapa | O que valida | Falha = |
|-------|-------------|---------|
| **Lint** | Código formatado, sem warnings | Volta pra dev |
| **Migrate (do zero)** | Schema reproduzível do zero | Volta pra dev |
| **Seed** | Dados de teste carregam | Volta pra dev |
| **Tests** | Unit + integration passam | Volta pra dev |
| **Smoke** | Happy path funciona E2E | Volta pra dev |
| **QA UI** | Interface acessível, responsiva | Volta pra dev |
| **Review** | Code review humano ou C-Level | Volta pra dev |

## Regra

**Falha em qualquer etapa = volta para dev.** Não existe "merge com ressalva".

## Referências

- [[ADR-010-e2e-obrigatorio-llm]] — E2E obrigatório para LLM stories
- [[ADR-015-qa-ui-obrigatorio]] — QA UI obrigatório
- [[golden-rules]] — Regra 4: "Falha no QA volta para dev"
