# Jhabib 2.0 — Metodologia de Desenvolvimento com IA

Repositório central da metodologia **Jhabib 2.0**: skills genéricas, ADRs e anti-patterns reutilizáveis entre projetos.

## O que é o Jhabib 2.0

Jhabib 2.0 é a **metodologia mestra** de desenvolvimento orientado por IA (SDD — Spec-Driven Development). Cada projeto que a aplica valida e evolui o método. O conhecimento gerado retorna aqui como skills, decisões arquiteturais e lições aprendidas.

Fluxo unidirecional: `Projeto → aprende → Jhabib 2.0`. O Jhabib 2.0 nunca injeta código de volta nos projetos — apenas define metodologia.

## Estrutura

```
skills/                  # Skills genéricas reutilizáveis em qualquer projeto
  _anti-patterns.md      # Padrões que causaram problemas — não repetir
  env-doctor/SKILL.md
  smoke-test/SKILL.md
  eval-rag/SKILL.md
  llm-benchmark/SKILL.md
  check-drift/SKILL.md
  phoenix-trace/SKILL.md
  nist-audit/SKILL.md
  retrospective/SKILL.md
  security-scan/SKILL.md
  orchestrator/SKILL.md

docs/adr/                # Architecture Decision Records genéricos
  ADR-006-sdd-pipeline.md
  ADR-008-dois-planos-dev-produto.md
  ADR-010-e2e-obrigatorio-llm.md
  ADR-015-qa-ui-obrigatorio.md
  ADR-016-dois-contextos-runtime-evals.md
```

## Origem

Primeira transferência de knowhow: **OdooiA → Jhabib 2.0** (Sprint 2, 2026-03).
ADR-017 formaliza o protocolo de transferência.
