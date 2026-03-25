---
title: golden-rules-sdd
status: active
tags: [methodology, sdd]
created: 2026-03-25
---

# 10 Regras de Ouro — SDD Studio

Regras universais aplicáveis a qualquer projeto SDD. Extraídas do piloto Restaurante iA Ops e validadas como padrão do framework.

1. **Spike antes de setup** — prove que funciona antes de montar infra
2. **Design-first** — wireframe/spec antes de código
3. **FASE 4 (security) inviolável** — nenhum PR pula revisão de segurança
4. **Falha no QA volta para dev** — sem exceções, sem "depois a gente arruma"
5. **Código é fonte de verdade** — não docs, não slides, não Notion
6. **GitHub é o entregável** — se não está no repo, não existe
7. **Handoff incompleto = recusado** — critério de done explícito ou volta
8. **Nunca push direto para main** — sempre via PR com gate
9. **Nunca vibe coding** — sem "vou só experimentar aqui rapidinho" em prod
10. **Docker-only** — nunca rodar pip/python/npm no host

## Referências

- [[sdd-overview]]
- [[gate-pre-pr]]
- [[ADR-010-e2e-obrigatorio-llm]]
