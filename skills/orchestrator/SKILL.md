---
name: orchestrator
version: 2.0
status: stable
tags: [meta, orchestration, sdd, cycle]
description: "Skill mestra do ciclo SDD 2.0. Lê o Kanban, elege o próximo card, orquestra todas as skills em sequência e fecha o ciclo. Único ponto de entrada para o fluxo automático."
origin: OdooiA Sprint 1 — versão genérica sem refs de projeto
---

# Orchestrator — SDD 2.0

Skill mestra. Porta o Handoff Context entre todas as skills. Não executa código — delega, rastreia e decide.

## Modo de Operação

- **Semi-auto (padrão):** Pausa antes de cada fase para aprovação.
- **Full-auto:** Roda até QA falhar ou bloqueante aparecer.

## Handoff Context (estrutura padrão)

```
card_id:      [id do card no Kanban]
card_title:   [título do card]
modulo:       [módulo ou área do sistema afetada]
prd:          [gerado na Fase 0]
spec_visual:  [gerado na Fase 1 — N/A se sem UI]
infra_status: [OK / FALHA]
pr_link:      [link do PR]
qa_results:   {smoke: ✅/❌, rag: ✅/❌, phoenix: ✅/❌}
drift:        ✅/❌
observacoes:  [desvios encontrados]
```

---

## PRÉ-CICLO: Leitura do Kanban

1. Buscar card com `Status = In Progress` no Kanban.
2. Se nenhum `In Progress`: pegar topo de `To Do` por Prioridade (P1 > P2 > P3) e mover para `In Progress`.
3. Montar Handoff Context inicial com dados do card.

---

## FASE 0 — product-owner

**Input:** Handoff Context com card selecionado.
**Output:** PRD compacto + tasks para cada skill downstream.
- Decompor em tasks atômicas ordenadas
- Identificar módulo, dependências de IA, critérios de aceitação
- Atualizar `prd` no Handoff Context
- **Pode abreviar:** se HANDOFF completo foi fornecido pelo usuário

## FASE 1 — ui-ux-specialist (spec visual)

**Input:** Handoff Context com `prd`.
**Output:** `spec_visual`.
- Capturar telas existentes, propor layout
- Criar artboard/wireframe com containers compatíveis com o framework de UI
- **Pode pular:** se o card não tem interface nova

## FASE 2 — env-doctor (infra health)

**Input:** Handoff Context com `modulo`.
**Output:** `infra_status`.
- Verificar todos os serviços da stack
- Se offline/instável: **PARAR**, criar card de débito técnico
- **Pode pular:** se infra já verificada no mesmo ciclo

## FASE 3 — implementação (frontend + backend)

**Input:** Handoff Context completo (prd + spec_visual + infra_status).
**Output:** código commitado + `pr_link`.
- Implementar fiel ao Handoff Context
- Commit: `feat(modulo): descrição — ref: #card`
- **Nunca pular**

## FASE 4 — security-scan + nist-audit

**Input:** Handoff Context com `pr_link`.
**Output:** relatório de segurança + checklist NIST.
- `security-scan`: varrer PR por vulnerabilidades
- `nist-audit`: verificar transparência, governança, privacidade
- **Bloqueante:** qualquer finding crítico
- **Nunca pular**

## FASE 5 — smoke-test + eval-rag + phoenix-trace

**Input:** Handoff Context com `pr_link` + infra OK.
**Output:** `qa_results`.
- `smoke-test`: validação rápida no ambiente
- `eval-rag`: se card envolver RAG, testar com DeepEval (Faithfulness ≥ 98%)
- `phoenix-trace`: capturar traces, verificar latência e erros
- **Shift-left:** falha → volta para FASE 3. Máx. 2 retentativas
- **Pode pular:** se ambiente offline ou isenção declarada

## FASE 6 — check-drift

**Input:** Handoff Context pós-QA.
**Output:** `drift` status.
- `check-drift`: verificar drift nos modelos ML
- Se drift: criar card de re-treinamento (P1)
- **Pode pular:** se nenhum modelo ML foi alterado

## FASE 7 — sprint-cycle (fechamento)

**Input:** Handoff Context completo.
**Output:** Kanban fechado + sinalização do próximo card.
- Fechar o card (Status → Done) **após PR mergeado**
- Registrar métricas de velocidade
- Preparar contexto do próximo card
- **Nunca pular**

---

## Regras de Ouro

1. Nenhum código antes do card estar no estado "In Progress".
2. Nenhum código chega ao QA sem security-scan + nist-audit.
3. Falha no QA volta para dev, nunca para o usuário.
4. O Kanban é a fonte de verdade — todo estado é registrado lá.
5. GitHub é o entregável — ciclo só fecha com PR mergeado.
6. `security-scan` usa `disable-model-invocation: true` — ler output de arquivo.
7. A skill de implementação não busca contexto sozinha — recebe tudo via Handoff Context.
8. `sprint-cycle` é apenas fechamento — não orquestra.

---

## Configuração por projeto

Ao usar este orchestrator num novo projeto, adaptar:
- `modulo` → nome do módulo/área do seu sistema
- FASE 1 → skill de UI do seu projeto (ou pular se não tem UI)
- FASE 3 → skills de implementação do seu stack
- Kanban → URL/ID do seu Kanban

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 2.0 | 2026-03-17 | Versão genérica — removidas refs OdooiA, Odoo, OWL, Figma |
| 1.0 | 2026-03-13 | Criação no OdooiA Sprint 1 |
