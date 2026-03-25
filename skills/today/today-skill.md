---
id: SKILL-011
title: today
primitive: Intelligence
status: draft
runtime: claude-code
iso-ref: ISO 45001
tags: [skill]
audited: false
audited-by: ~
created: 2026-03-24
---

> **Pilar:** [[org-chart|PMO & Delivery]] · **Owner:** COO Daniel Santos · [[coo-daniel-santos]]
> **Metodologia:** [[sdd-overview]]

# today — Briefing Executivo Diário

> Lê os 7 state files do C-Level + AGORA.md + última SESSION. Aplica o filtro
> Revenue > Produto > Método > Admin. Produz terminal briefing (≤10 linhas) + cria
> `05-sessions/TODAY-YYYY-MM-DD.md`.

## Objetivo

Dar a Jean um resumo executivo acionável em ≤2 minutos sem abrir arquivos
manualmente. Respeita o budget de ≤5h/semana e o princípio anti-burnout (ISO 45001).

## Trigger

Jean digita `/today` no Claude Code.

## Inputs implícitos (lidos automaticamente)

| Arquivo | Owner |
|---------|-------|
| `00-strategy/ops-state.md` | COO Daniel Santos |
| `00-strategy/financial-state.md` | CFO Marcus Lima |
| `00-strategy/compliance-state.md` | CISO Priya Nair |
| `01-methodology/tech-state.md` | CTO Alex Chen |
| `02-products/product-state.md` | CPO Lena Park |
| `03-clients/pipeline.md` | CRO Rafael Souza |
| `06-us-market/gtm-state.md` | CMO Sofia Reyes |
| `AGORA.md` | Forks ativos |
| `05-sessions/SESSION-*.md` (mais recente) | Última sessão |

## Passos

1. Ler os 9 arquivos acima em paralelo.
2. Extrair seções `## Top Blockers` e `## Ações desta semana` de cada state file.
3. Extrair `## O que ficou aberto` da última SESSION (se existir).
4. Extrair tabela de forks e próximas ações de `AGORA.md`.
5. Se não houver `05-sessions/TODAY-YYYY-MM-DD.md` para hoje, perguntar:
   "Jean, quantas horas do budget semanal já foram usadas?"
6. Aplicar filtro de prioridade:
   - **Revenue** = qualquer item que mova R1→R4 ou MRR (Felipe, invoice, deploy)
   - **Produto** = features que Felipe pediu ou precisa para a demo
   - **Método** = ADRs, SKILLs, SDD (só se necessário para Revenue ou Produto)
   - **Admin** = vault, docs, organização (mínimo viável)
7. Imprimir TERMINAL BRIEFING no formato fixo abaixo.
8. Criar `05-sessions/TODAY-YYYY-MM-DD.md` usando o template `templates/TODAY-template.md`.

## Output: Terminal Briefing (formato fixo, ≤10 linhas)

```
=== TODAY — YYYY-MM-DD === [Xh usadas / 5h budget]

REVENUE (prioridade máxima)
  R? — [ação concreta] → Owner: Jean | Deadline: hoje/semana

PRODUTO
  A? — [ação concreta] → Owner: Agente/Jean

BLOCKER CRÍTICO
  [blocker] — [quem desbloqueia e como]

TOP 3 AÇÕES
  1. [ação ≤30min para Jean]
  2. [ação que o agente executa]
  3. [ação que o agente executa]

Budget restante: Xh | Próxima sessão recomendada: [data]
```

## Evidence

- Terminal briefing impresso em < 5 segundos após `/today`
- Arquivo `05-sessions/TODAY-YYYY-MM-DD.md` criado e abrível no Obsidian
- Top 3 ações são factíveis dentro do budget restante

## Override Humano

Jean pode ignorar o TOP 3 e definir prioridade manualmente. O skill apenas sugere
— a decisão final é sempre de Jean.

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-24 | Criação inicial — vault restructuring C-Level |
