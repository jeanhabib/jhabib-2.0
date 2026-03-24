---
id: ADR-006
title: sdd-pipeline
status: ACCEPTED
superseded-by: ~
date: 2026-03-17
iso-ref: ~
tags: [adr]
audited: false
---

# ADR-006 — Pipeline de Desenvolvimento com IA (SDD)

**Origem:** OdooiA — generalizado para Jhabib 2.0

## Decisão

Todo desenvolvimento segue o ciclo orquestrado por IA: Product Owner → Infra → Scaffold → Segurança → QA → Deploy.

## Contexto

Times pequenos (1-3 pessoas) precisam garantir qualidade e rastreabilidade por processo, não por tamanho de time. O ciclo SDD substitui Scrum clássico com overhead menor e automação mais profunda via Claude Code ou equivalente.

## Fases do Ciclo

| Fase | Responsável | Pode pular? |
|------|------------|-------------|
| 0 — product-owner | PRD + decomposição | ✅ Se HANDOFF completo |
| 1 — ui-ux-specialist | Spec visual | ✅ Se sem UI nova |
| 2 — env-doctor | Infra health | ✅ Se infra já verificada |
| 3 — implementação | Código | ❌ Sempre |
| 4 — security-scan + nist-audit | Segurança | ❌ Nunca |
| 5 — smoke-test + eval-rag + phoenix-trace | QA | ✅ Com isenção declarada |
| 6 — check-drift | ML | ✅ Se sem modelo alterado |
| 7 — sprint-cycle | Fechamento | ❌ Nunca |

## Alternativas consideradas

- Desenvolvimento ad-hoc — rejeitado: sem rastreabilidade, qualidade inconsistente
- Scrum tradicional — overhead excessivo para times pequenos
- Kanban puro sem automação — rejeitado: sem enforcement de segurança/QA

## Consequências

- Todo card vem do Kanban — nunca do `git log` ou intuição
- `main` protegida: todo código entra via PR com CI obrigatório
- O Kanban é a fonte de verdade — todo estado é registrado lá
- Ciclo só fecha com PR mergeado (nunca antes)
