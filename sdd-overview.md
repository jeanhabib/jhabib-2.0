---
id: SDD-OVERVIEW
title: sdd-overview
status: active
tags: [methodology, sdd, onboarding]
created: 2026-03-25
---

# SDD — Spec-Driven Development (Overview)

> Documento completo: [[SDD]]
> Framework: JHabib 2.0 — SDD Studio

---

## O que é

SDD (Spec-Driven Development) é a metodologia de desenvolvimento do JHabib 2.0. Nada é executado sem especificação prévia. O ciclo garante rastreabilidade end-to-end alinhada com ISO 9001 e PDCA.

## Dois Modos

| | SDD Full | SDD Express ([[ADR-018-sdd-express-pre-receita|ADR-018]]) |
|---|---|---|
| **Quando** | Governança, plataforma, ADRs, SKILLs novas | V1 features, ativação comercial, onboarding |
| **Ciclo** | Spec → SKILL → Evidence → Retro | Spec-lite → Execute → Ship → Retro express |
| **Evidence** | Mensurável, ISO 25010 | "Felipe confirmou" ou "está em produção" |

**ADR-018 expira quando:** 2 meses consecutivos de MRR confirmado.

## Ciclo Completo (Full)

```
Spec → SKILL → Evidence → Retro
 │       │        │         │
Plan    Do      Check      Act    (PDCA)
 │       │        │         │
7.5    8.1      9.1       10.1   (ISO 9001)
```

## Modelo Studio + Forks ([[ADR-019-jhab20-studio-framework|ADR-019]])

JHabib 2.0 é o framework mestre. Cada cliente recebe um fork:

```
jhabib-2.0 (mestre)
    ├── fork → disassemble → improve → reassemble → merge back
    └── learning loop mensal → SKILLs/ADRs universais voltam ao mestre
```

Detalhes operacionais: [[FORK-GUIDE]]

## Hierarquia de Prioridades

```
Revenue > Produto > Método > Admin
```

Budget: ≤5h/semana (Jean) · 3h Revenue · 1h Método · 1h Admin

## Links Rápidos

- [[SDD]] — Metodologia completa + templates
- [[FORK-GUIDE]] — Guia do ciclo forkável
- [[gate-pre-pr|Gate Pre-PR]] — Checklist inviolável
- [[golden-rules|Golden Rules]] — 10 regras consolidadas
- [[AGORA]] — Estado real-time dos forks
- [[00-strategy/org-chart|Org Chart]] — C-Level Board
