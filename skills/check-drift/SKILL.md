---
id: SKILL-001
title: check-drift
primitive: Intelligence
status: draft
runtime: agnostic
iso-ref: ISO/IEC 25010 — Reliability
tags: [skill]
audited: false
audited-by:
created: 2026-03-17
---

# check-drift — Detecta Data Drift em Modelos ML

> Compara distribuição atual dos dados de entrada com baseline e alerta quando drift supera threshold. Previne degradação silenciosa de modelos em produção.

## Quando usar

- Modelos de previsão, classificação ou recomendação em produção
- Agendado via cron após X semanas em produção
- Após mudança significativa de dados de entrada
- Não usar: LLMs generativos (sem baseline de distribuição definida)

## Inputs

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|:-----------:|-----------|
| `model_id` | string | ✅ | Identificador do modelo a verificar |
| `baseline_path` | string | ✅ | Path do dataset de baseline (quando modelo foi treinado) |
| `current_data` | string | ✅ | Path dos dados recentes de produção |
| `threshold` | float | ❌ | Default: 0.1 (PSI > 0.1 = drift moderado) |

## Outputs

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `drift_detected` | bool | True se drift acima do threshold |
| `psi_score` | float | Population Stability Index |
| `drifted_features` | list | Features com maior drift |
| `recommendation` | string | Monitorar / Re-treinar / Urgente |

## Critério de ação

| PSI | Status | Ação |
|-----|--------|------|
| < 0.1 | Estável | Monitorar normalmente |
| 0.1–0.25 | Drift moderado | Agendar re-treinamento |
| > 0.25 | Drift severo | Criar card P1 de re-treinamento imediato |

## Integração no ciclo SDD

Roda na FASE 6, após QA. Se nenhum modelo ML foi alterado no card, esta skill pode ser pulada (declarar explicitamente).

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA FASE 11 — generalizado |
