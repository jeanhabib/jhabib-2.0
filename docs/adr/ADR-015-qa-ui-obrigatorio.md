# ADR-015 — QA UI Obrigatório Antes de Fechar Card de Feature

**Status:** Aceito
**Data:** 2026-03-16
**Origem:** OdooiA — generalizado para Jhabib 2.0

## Decisão

Nenhum card de feature pode ser fechado como Done sem validação visual na UI. A skill `smoke-test` é obrigatória e deve incluir screenshot ou descrição explícita do que foi visto na tela.

## Contexto

Incidente no OdooiA (2026-03-16): o ciclo foi declarado encerrado sem validação visual. A view foi entregue mas nunca validada com dados reais. O erro foi declarar Done baseado apenas em QA de terminal (smoke ✅ via CLI) sem abrir a interface.

O padrão "CI verde = feature pronta" é falso para sistemas com interface. A UI pode ter erros de renderização, dados ausentes, ou comportamentos incorretos que só aparecem visualmente.

## Regra

- `smoke-test` deve incluir etapa: "Abrir a UI → navegar até a view entregue → confirmar que dados aparecem"
- Cards com LLM no caminho crítico: obrigatório registrar **o que foi visto na UI** no card antes de mover para Review
- CI verde + testes passando **não substituem** validação visual
- O orchestrator deve perguntar ao dev: **"Você abriu a UI e viu o resultado?"** antes de emitir `✅ Ciclo encerrado`

## Isenções

Cards de `chore`, `infra`, `docs` ou `backend-only` podem declarar isenção explícita:
```
QA UI: N/A — isenção declarada (chore/tooling: sem interface)
```

## Consequências

- Skill `smoke-test` inclui etapa de validação UI explícita
- Template de card inclui campo: "QA UI: screenshot ou descrição"
- Orchestrator pergunta sobre QA UI antes de fechar o ciclo
