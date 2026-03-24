---
tags: [vault, conventions]
---

# Convenções do Vault

## Estrutura de Pastas

| Pasta | Propósito |
|-------|-----------|
| `00-strategy/` | Visão, metas, AI Policy |
| `01-methodology/` | SDD, SKILLs auditadas, ADRs, anti-patterns |
| `02-products/` | QAi Augment — overview + protótipos |
| `03-clients/` | Fichas de clientes |
| `04-learning/` | Retrospectivas |
| `05-sessions/` | Logs de sessão (1 por dia) |
| `06-us-market/` | Pesquisa go-to-market US |
| `templates/` | Templates para SKILLs, ADRs, APs, retros, sessões |

## Naming

- Pastas: `NN-nome-kebab/`
- SKILLs: `SKILL-NNN-nome.md`
- ADRs: `ADR-NNN-nome.md`
- Anti-patterns: `AP-NNN-nome.md`
- Sessões: `SESSION-YYYY-MM-DD.md`
- Retrospectivas: `RETRO-YYYY-MM-DD.md`

## Frontmatter

Todo `.md` deve ter frontmatter YAML. Ver templates em `templates/`.

## Tags Canônicas

`skill`, `adr`, `anti-pattern`, `strategy`, `product`, `client`, `retro`, `session`, `lacuna`

## Regra de Ouro

**Nenhum arquivo é criado sem Spec aprovada.**
Ver [[CLAUDE]] para regras completas.
