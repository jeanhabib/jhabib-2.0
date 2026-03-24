---
tags: [methodology, zhc]
iso-ref: ISO 56001
created: 2026-03-23
---

# ZHC — Zero Human Companies

## Conceito

Empresas que operam com **zero intervenção humana recorrente** no dia-a-dia.
O humano define estratégia, aprova Specs e valida Evidence.
A IA executa SKILLs, coleta dados e gera retros.

## Papel do Humano no ZHC

| Fase | Humano | IA |
|------|--------|-----|
| Spec | Aprova | Pode sugerir, não aprova sozinha |
| SKILL | Monitora | Executa |
| Evidence | Valida | Coleta e apresenta |
| Retro | Decide ação | Gera análise |

## Por que ISO 56001?

A ISO 56001 (Gestão da Inovação) enquadra ZHC como **inovação sistêmica**:
- Não é automação pontual — é redesign organizacional
- Requer governança (ISO 42001 para IA)
- Requer medição contínua (ISO 25010 para qualidade)
- Requer gestão de risco (ISO 31000)

## Pré-requisitos para ZHC

1. **SDD maduro** — ciclo Spec→SKILL→Evidence→Retro funcionando
2. **SKILLs auditadas** — todas com frontmatter, evidence, runtime-agnostic
3. **Orquestrador confiável** — orchestrator SKILL validada
4. **Override humano** — mecanismo claro para retomar controle (ISO 42001)
5. **Métricas canônicas** — Q metric definida e monitorada (ISO 25010)

## Estado Atual

- SDD: operacional, em refinamento
- SKILLs: 10 transferidas da POC, todas em revisão (ver [[AUDIT-2026-03-23]])
- Orquestrador: existe como SKILL, precisa de human override
- ZHC: conceito validado na POC OdooiA, não implementado
