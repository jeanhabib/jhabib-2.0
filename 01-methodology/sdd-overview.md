---
tags: [methodology, sdd]
created: 2026-03-23
---

# SDD — Spec-Driven Development

## O que é

Metodologia proprietária do JHabib 2.0 para desenvolvimento orientado
a especificação. Toda feature, decisão ou artefato nasce de uma Spec
e só é considerado "done" com Evidence comprovada.

## Ciclo

```
Spec → SKILL → Evidence → Retro
```

Mapeia diretamente ao PDCA (ISO 9001):

| SDD | PDCA | ISO 9001 |
|-----|------|----------|
| **Spec** | Plan | Controle de documentos (7.5) |
| **SKILL** | Do | Operação (8.1) |
| **Evidence** | Check | Evidência de conformidade (9.1) |
| **Retro** | Act | Melhoria contínua (10.1) |

## SDD ↔ ISO Mapping Completo

| Conceito SDD | ISO de Referência | C-Level Responsável |
|-------------|-------------------|---------------------|
| Spec | ISO 9001 — controle de documentos | CTO Alex Chen |
| Evidence | ISO 9001 — evidência de conformidade | CTO Alex Chen |
| Métrica Q | ISO/IEC 25010 — qualidade de produto | CPO Lena Park |
| Anti-burnout ≤5h | ISO 45001 — saúde ocupacional | COO Daniel Santos |
| ZHC | ISO 56001 — inovação sistêmica | CMO Sofia Reyes |
| Privacy First | ISO/IEC 27001 — segurança da informação | CTO Alex Chen |
| Risk Assessment | ISO 31000 — gestão de riscos | CFO Marcus Lima |
| AI Governance | ISO/IEC 42001 — IA responsável | CTO Alex Chen |
| User-Centered | ISO 9241-210 — design centrado no humano | CPO Lena Park |

## Regras Invioláveis

1. **Spec antes de qualquer código** — nenhum arquivo é criado sem Spec
2. **Evidence = done means proven** — "funciona aqui" não é evidence
3. **≤5h/semana de trabalho humano** — COO monitora (ISO 45001)
4. **Privacy First** — preferir soluções locais; Ollama > cloud
5. **Runtime-agnostic** — SKILLs devem funcionar em qualquer agente

## Primitivas de SKILL

Cada SKILL pertence a uma primitiva:

| Primitiva | Descrição |
|-----------|-----------|
| **Intelligence** | Raciocínio, análise, decisão |
| **Engine** | Execução, pipeline, automação |
| **Agents** | Orquestração multi-agente |
| **Tools** | Ferramentas auxiliares |
| **Memory** | Persistência, contexto |
| **Learning** | Retro, métricas, melhoria |

## Referências

- [[golden-rules]] — 10 Regras de Ouro do SDD
- [[gate-pre-pr]] — Gate Pre-PR inviolável
- [[org-chart]] — Organograma e GRACI
- [[zhc-overview]] — Zero Human Companies
- [[ADR-018-sdd-express-pre-receita|ADR-018]] — SDD Express
- [[01-methodology/anti-patterns/anti-patterns|Anti-Patterns]]
