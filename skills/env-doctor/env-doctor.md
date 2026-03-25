---
id: SKILL-002
title: env-doctor
primitive: Tools
status: draft
runtime: agnostic
iso-ref: ISO/IEC 25010 — Operability
tags: [skill]
audited: false
audited-by:
created: 2026-03-17
---

> **Pilar:** [[org-chart|Engenharia & SDD]] · **Owner:** CTO Alex Chen · [[cto-alex-chen]]
> **Metodologia:** [[sdd-overview]] · [[golden-rules]]

# env-doctor — Health Check da Stack

Verifica se todos os serviços estão online antes de qualquer ciclo de desenvolvimento.

## Como usar

Adapte o checklist abaixo para os serviços do seu projeto. A estrutura é sempre a mesma: porta, comando de verificação, resultado esperado.

## Checklist modelo

| Serviço | Porta | Comando de verificação |
|---------|-------|------------------------|
| App principal | :PORT | `curl -s -o /dev/null -w "%{http_code}" http://localhost:PORT/health` |
| Banco de dados | :PORT | `docker exec <container> <health-cmd>` |
| LLM local | :11434 | `curl -s http://localhost:11434/api/tags` |
| Banco vetorial | :PORT | `curl -s http://localhost:PORT/heartbeat` |
| Observabilidade | :6006 | `curl -s -o /dev/null -w "%{http_code}" http://localhost:6006` |

## Execução básica

```bash
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
```

## Resultado esperado

Todos os containers do projeto com status `healthy` ou `running`.

## Se algum falhar

Parar o ciclo. Criar card de débito técnico no Kanban com prioridade `P1`. Não avançar para desenvolvimento com infra degradada.

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA (Sprint 1) — generalizado |
