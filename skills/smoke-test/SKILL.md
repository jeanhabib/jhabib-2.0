---
id: SKILL-010
title: smoke-test
primitive: Tools
status: draft
runtime: agnostic
iso-ref: ISO/IEC 25010 — Functional Suitability
tags: [skill]
audited: false
audited-by:
created: 2026-03-17
---

# smoke-test — Validação Rápida do Sistema

Primeira barreira do QA. Valida que o sistema básico funciona antes de rodar testes mais pesados.

## Checklist de Smoke

```bash
# 1. Containers saudáveis
docker ps --format "table {{.Names}}\t{{.Status}}"

# 2. App responde (adaptar para o projeto)
curl -s -o /dev/null -w "%{http_code}" http://localhost:PORT/health
# Esperado: 200

# 3. Autenticação funciona (adaptar para o projeto)
# Testar login com credenciais de teste

# 4. QA UI (ver seção abaixo — obrigatória salvo isenção declarada)

# 5. Sem erros críticos nos logs
docker logs <container> --tail=50 2>&1 | grep -i "error\|traceback"
```

## Etapa QA UI (obrigatória para cards com interface)

Todo card que toque em qualquer view de UI **deve** passar pela etapa de QA UI antes de avançar.

### Roteiro mínimo (Playwright)

```bash
npx playwright install chromium
npx playwright test tests/smoke/ui_smoke.spec.ts --reporter=line
```

O script deve cobrir:
1. Login com credenciais de teste
2. Navegação para o módulo/view modificado
3. Ausência de erros no console (`page.on('console', ...)`)
4. Ausência de erros de rede (status >= 400) para recursos do módulo
5. Screenshot salvo como artefato

### Critério de aprovação QA UI

- Zero erros `console.error` originados do módulo modificado
- Zero requests com status 4xx/5xx para assets do módulo
- Screenshot registrado (evidência para o PR)

---

## Isenções documentadas

A etapa QA UI pode ser declarada **N/A** apenas nos seguintes casos. A isenção deve ser registrada explicitamente no output do ciclo.

| Motivo de isenção | Condição obrigatória |
|---|---|
| `chore/tooling` | Card não modifica nenhuma view ou arquivo de UI |
| `docs` | Card altera apenas arquivos `.md`, `.rst`, ou comentários |
| `backend-only` | Card altera apenas lógica de backend sem view nova ou alterada |
| `infra` | Card altera apenas `docker-compose.yml`, `Dockerfile`, `CI/CD workflows` |
| `docker-offline` | Ambiente Docker não disponível (registrar motivo) |

**Formato obrigatório de isenção no output:**
```
QA UI: N/A — isenção declarada (<motivo>: <justificativa>)
```

---

## Critério de aprovação geral

Todos os checks obrigatórios passando (QA UI obrigatório salvo isenção documentada). Qualquer falha = parar ciclo e retornar relatório para desenvolvimento com o output exato do erro.

## Integração no ciclo SDD

Roda após `nist-audit`. Se passar → `eval-rag`. Se falhar → volta para Fase 3 (máx. 2 retentativas).

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.2 | 2026-03-17 | Transferido do OdooiA — generalizado (sem refs Odoo/OWL) |
| 0.1 | 2026-03-13 | Criação no OdooiA Sprint 1 |
