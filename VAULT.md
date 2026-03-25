---
tags: [vault, conventions]
---

# Convenções do Vault

## Estrutura de Pastas

| Pasta | Propósito |
|-------|-----------|
| `00-strategy/` | Visão, metas, AI Policy |
| `01-methodology/` | SDD, SKILLs auditadas, ADRs, anti-patterns |
| `02-products/` | Restaurante iA Ops (V1) + QAi Augment — overviews |
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
- Briefing diário: `TODAY-YYYY-MM-DD.md` (gerado por SKILL-011 /today — não criar manualmente)

## Frontmatter

Todo `.md` deve ter frontmatter YAML. Ver templates em `templates/`.

## Tags Canônicas

`skill`, `adr`, `anti-pattern`, `strategy`, `product`, `client`, `retro`, `session`, `lacuna`

## 3 Camadas do Ecossistema

| Camada | Ferramenta | Conteúdo |
|--------|-----------|----------|
| **Execução visual** | Notion | Boards, kanban, status, delegação |
| **Reflexão + Memória** | Obsidian (este vault) | Estratégia, metodologia, produtos, learning, memória do agente. Ver [[org-chart]] para estrutura organizacional |
| **Técnico + Agente** | Repo git | CLAUDE.md, skills, handoffs, ADRs, testes, código |

O Obsidian é a **memória permanente do agente**: briefing rápido de sessão (HOME.md) + base de conhecimento profunda consultável. Notion é fonte de verdade do domínio dos projetos. Repos git são fonte de verdade técnica.

## Regra de Ouro

**Nenhum arquivo é criado sem Spec aprovada.**
Ver [[CLAUDE]] para regras completas.
Ver [[golden-rules]] para as 10 regras universais do SDD.
