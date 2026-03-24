---
tags: [vault, home]
---

# JHabib 2.0 — Home

> "Brasil valida o método, US é o destino"

## Navegação

- [[CLAUDE]] — Regras do agente e contexto completo
- [[VAULT]] — Convenções do vault

## Áreas

| Pasta | Conteúdo |
|-------|----------|
| [[00-strategy/]] | Visão, metas financeiras, AI Policy |
| [[01-methodology/]] | SDD, SKILLs, ADRs, anti-patterns |
| [[02-products/]] | QAi Augment + protótipos |
| [[03-clients/]] | Felipe (restaurante) |
| [[04-learning/]] | Retrospectivas |
| [[05-sessions/]] | Logs de sessão |
| [[06-us-market/]] | Pesquisa mercado US |

## Lacunas Abertas

```dataview
TABLE status, tags
FROM "" WHERE contains(tags, "lacuna")
SORT priority ASC
```

## Sessões Recentes

```dataview
TABLE date, lacunas-resolvidas
FROM "05-sessions"
SORT date DESC
LIMIT 5
```
