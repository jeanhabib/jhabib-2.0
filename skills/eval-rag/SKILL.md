---
id: SKILL-003
title: eval-rag
primitive: Intelligence
status: draft
runtime: agnostic
iso-ref: ISO/IEC 25010 — Functional Correctness
tags: [skill]
audited: false
audited-by:
created: 2026-03-17
---

# eval-rag — Avalia Pipeline RAG com DeepEval

> Roda métricas DeepEval sobre um pipeline RAG local. Gera score e identifica chunks problemáticos.

## Quando usar

- Ao implementar ou modificar um RAGService
- Antes de demo com cliente que usa RAG documental
- Após mudança de modelo de embedding
- Não usar: respostas que vêm diretamente do banco (não passam por RAG)

## Inputs

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|:-----------:|-----------|
| `rag_endpoint` | string | ✅ | URL do endpoint RAG a testar |
| `test_questions` | list | ✅ | Perguntas representativas com resposta esperada |
| `threshold` | float | ❌ | Default: 0.98 (Faithfulness ≥ 98%) |

## Outputs

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `faithfulness_score` | 0-1 | Fidelidade da resposta ao contexto recuperado |
| `answer_relevancy_score` | 0-1 | Relevância da resposta à pergunta |
| `contextual_precision_score` | 0-1 | Precisão dos chunks recuperados |
| `failed_chunks` | list | Chunks com score < 0.7 |
| `recommendation` | string | Ajuste de chunk_size ou modelo de embedding se scores baixos |

## Critério de aprovação

- Faithfulness ≥ 98%
- Answer Relevancy ≥ 0.8
- Contextual Precision ≥ 0.7

## Integração no ciclo SDD

Roda na FASE 5, após `smoke-test`. Se RAG não está no caminho crítico do card, esta skill é opcional.

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA FASE 11 — generalizado |
