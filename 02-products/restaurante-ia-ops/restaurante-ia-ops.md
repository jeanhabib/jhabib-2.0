---
tags: [product, restaurante-ia-ops, v1]
vetor: V1
status: active
repo: github.com/jeanhabib/food-service-ai-ops-v2
created: 2026-03-24
updated: 2026-03-25
---

# Restaurante iA Ops — Vertical Food-Service

## O que é

Plataforma SaaS white-label de gestão inteligente para food service. Combina ERP/PDV com módulos de IA (visão computacional, previsão de demanda, engenharia de cardápio, gamificação).

Primeiro produto vertical do JHabib 2.0. Valida o SDD em domínio real.

## Stack

FastAPI + PostgreSQL 16 + Next.js 15 + Ollama + Playwright

## Financiamento

FAPEMA/SECTI Edital 06/2025 — projeto aprovado.

## Cliente Piloto

**Jakaru Food Park** (Felipe Policarpo) — São Luís, MA

## Módulos

| # | Módulo | Status | Tela | Destaque |
|---|--------|--------|------|----------|
| M1 | PDV/ERP | 0% | — | Odoo headless (futuro) |
| M2 | Flow Analysis | 50% | `/flow` | Horários de pico |
| M3 | Supply Management | **100%** | `/supply` | Forecast mussarela |
| M4 | EPI Vision | 33% | `/epi` | YOLO detecção (spike) |
| M5 | Menu Engineering | 60% | `/menu` | BCG Matrix |
| M6 | LMS Gamificado | 60% | `/lms` | Mobile, XP, leaderboard |
| M7 | Dashboard BI | 60% | `/dashboard` | KPIs reais Jakaru |
| M8 | Telegram Gateway | **100%** | Telegram | Digest diário pro Felipe |

**Progresso: 23/43 requisitos implementados (53%) — 6/7 módulos IA com core funcional**

## Stakeholders

- **Felipe Policarpo** — co-fundador (20-25% equity por R$15k aporte). Jakaru Food Park, MA. Contato FAPEMA.
- **Fernando** — dev sênior, consultor por PR (R$300-1.500). Equity condicional 5-10%.
- **Jean** — 70-75% equity. IP 100% com JHabib 2.0.
- **Manu** — parceiro ERP. **Inativo — fora do critical path.** XLSX definitivo (ADR-005).

## Decisões Recentes (2026-03-24)

| Decisão | Impacto |
|---------|---------|
| Manu fora do critical path | XLSX definitivo (ADR-005) |
| Odoo headless como plano B | ERP backup + conector API real |
| Telegram como mobile | Corta responsivo, Felipe validou |
| Felipe é contato FAPEMA | Pagamento PF/PJ via JHabib pendente |
| FAPEMA deadline 30/03 | Vídeo + relatório + demo |

## Modelo Comercial

- Setup: R$15-25k (uma vez)
- SaaS base: R$2.200/mês
- SaaS premium: R$3.500/mês
- Diferencial: 100% on-premise, sem cloud, ideal para MA (internet instável)

## Automações Ativas

| Task | Frequência | Monitora |
|------|-----------|----------|
| `fapema-delivery-tracker` | Diário 9h17 | Entregas, PRs, deadlines |
| `cpo-weekly-review` | Segunda 9h29 | Roadmap, LMS, delegações |
| `cto-weekly-review` | Segunda 9h34 | Módulos técnicos, testes |
| `cmo-weekly-review` | Segunda 9h42 | Pipeline, FAPEMA, Felipe |

## Relação com JHabib 2.0

Restaurante iA Ops é o **V1 ativo** — não experiência passada:
- Valida o SDD em produção real
- Gera knowhow transferível (ADR-017)
- Felipe como primeiro case para vender réplicas (V2)

Source of truth domain-specific: **Notion** (hub Restaurante iA Ops).
Source of truth metodologia: **este vault** (jhabib-2.0).

## Referências

- [[org-chart]] — Posição no organograma: V1 ativo sob pilares CTO + CPO
- [[vision]] — Portfólio de produtos (V1)
- [[cro-rafael-souza]] — Estado do pipeline CRO
- [[03-clients/jakaru-restaurante-ia-ops/jakaru-felipe|Jakaru client profile]]
- [[golden-rules]] — Regras de desenvolvimento
- [[gate-pre-pr]] — Gate Pre-PR obrigatório

## Handoffs

- [[HANDOFF-food-service-ai-ops-v2-2026-03-24]]
