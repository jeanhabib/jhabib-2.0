---
tags: [product, qaai-augment, platform]
vetor: plataforma
status: draft
created: 2026-03-24
---

# QAi Augment — Plataforma de Orquestração

## O que é

Dashboard + toolkit de quality assurance via IA.
**Não é um produto vertical** — é a plataforma que sustenta V1 (OdooiA), V2 (réplicas) e V3 (metodologia licenciada).

## Papel no Ecossistema

```
QAi Augment (plataforma)
    ├── orquestra SKILLs do SDD
    ├── dashboard de métricas Q (ISO 25010)
    ├── gestão de Evidence e retros
    └── suporta múltiplos produtos verticais
```

## Protótipos Gerados (browser, 2026-03-23)

| Artefato | Descrição |
|----------|-----------|
| `jhab20-boardroom.jsx` | 5 C-Levels com ISO expertise |
| `jhab20-financial-dashboard.jsx` | SAC snowball + P&L + ISO 31000 |
| `jhab20-sdd-launcher.jsx` | Agentes por fase: SPEC/SKILL/EVIDENCE/RETRO |
| `jhab20-iso-map.jsx` | Mapa ISO interativo por C-Level |

Status: gerados no claude.ai, **não estão no repo ainda** (ver L6).

## Roadmap CPO (Lena Park)

- [ ] Definir MVP mínimo da plataforma (o que precisa existir para V1 funcionar?)
- [ ] Separar features "plataforma" de features "OdooiA-specific"
- [ ] Métrica Q canônica (ISO 25010) — critério de qualidade unificado
