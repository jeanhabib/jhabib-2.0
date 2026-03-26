---
id: GATE-PRE-PR
title: gate-pre-pr
status: active
tags: [methodology, gate, quality]
iso-ref: ISO 9001, ISO/IEC 25010
created: 2026-03-25
---

# Gate Pre-PR (Inviolável)

> Fonte canônica: [[SDD]] § Gate Pre-PR
> Owner: CTO Alex Chen

Falha em qualquer etapa = volta para dev. Sem exceções, sem "merge com ressalva".

## Pipeline

```
Lint → Migrate (do zero) → Seed → Tests → Smoke → QA UI → Review
```

## Etapas

| # | Etapa | O que valida | Evidence esperada |
|---|-------|-------------|-------------------|
| 1 | **Lint** | Código formatado, sem warnings | `0 errors, 0 warnings` |
| 2 | **Migrate (do zero)** | Schema reproduzível do zero | DB criado sem erros a partir de migrations |
| 3 | **Seed** | Dados de teste carregam | Seed script completa sem erros |
| 4 | **Tests** | Unit + integration passam | 100% pass rate no CI |
| 5 | **Smoke** | Happy path funciona E2E | Fluxo principal executado com sucesso |
| 6 | **QA UI** | Interface acessível, responsiva | Checklist visual aprovado |
| 7 | **Review** | Code review humano ou C-Level | Aprovação registrada no PR |

## Regras

- **Nenhuma etapa pode ser pulada** — mesmo em SDD Express
- **Falha = volta para dev** — não existe "merge com ressalva"
- **Evidence é obrigatória** — screenshots, logs, ou output do CI
- O gate se aplica a **todos os repos** (mestre e forks)

## Aplicação em Forks

Quando um fork executa via [[FORK-GUIDE|FORK-GUIDE]], o gate Pre-PR se aplica ao PR dentro do fork. O handoff de volta ao mestre deve incluir evidence de que o gate foi cumprido.
