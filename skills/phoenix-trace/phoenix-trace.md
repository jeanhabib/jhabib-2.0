---
id: SKILL-007
title: phoenix-trace
primitive: Tools
status: draft
runtime: agnostic
iso-ref: ISO/IEC 25010 — Performance Efficiency
tags: [skill]
audited: false
audited-by:
created: 2026-03-17
---

> **Pilar:** [[org-chart|IA & Data Science]] · **Owner:** CTO Alex Chen · [[cto-alex-chen]]
> **Metodologia:** [[sdd-overview]] · [[golden-rules]]

# phoenix-trace — Analisa Traces OTEL via Arize Phoenix

> Consulta o Arize Phoenix local (:6006) e gera relatório de latência, erros e tokens por span. Identifica gargalos no pipeline de IA.

## Quando usar

- Latência alta reportada em produção ou demo
- Após mudança de modelo para comparar antes/depois
- Debugging de pipeline LLM com múltiplos steps
- Validação de que instrumentação OTEL está funcionando

## Pré-requisitos

- Arize Phoenix rodando em `localhost:6006`
- Endpoint gRPC OTEL em `localhost:4317`
- Pipeline instrumentado com `opentelemetry` SDK

## Verificação de pré-condições

```bash
# Phoenix ativo
curl -s -o /dev/null -w "%{http_code}" http://localhost:6006
# Esperado: 200

# gRPC endpoint
nc -z localhost 4317 && echo "PASS" || echo "FAIL"
```

## Outputs

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `top_slowest_spans` | list | 5 spans mais lentos com latência |
| `error_spans` | list | Spans com erro e stack trace |
| `token_consumption` | dict | Tokens por call por modelo |
| `recommendation` | string | Onde otimizar (modelo, chunk size, cache) |

## Integração no ciclo SDD

Roda na FASE 5, após `smoke-test`. Se pipeline de IA não está no card, esta skill pode ser pulada (declarar explicitamente).

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA FASE 11 — generalizado |
