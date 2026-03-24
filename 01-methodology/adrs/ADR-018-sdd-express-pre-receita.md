---
id: ADR-018
title: sdd-express-pre-receita
status: ACCEPTED
superseded-by: ~
date: 2026-03-24
iso-ref: ISO 9001, ISO 45001
tags: [adr, revenue, methodology]
audited: 2026-03-24
audited-by: c-level-board
---

# ADR-018 — SDD Express para Fase Pré-Receita

**Origem:** Reunião Estratégica C-Level 2026-03-24 — aprovação unânime.

## Contexto

O ciclo SDD completo (`Spec → SKILL → Evidence → Retro`) está sendo aplicado com rigor uniforme para governança interna E features de produto. Com budget de ≤5h/semana e receita zero, o overhead de Specs completas, frontmatter canônico e Evidence formal está consumindo horas que deveriam ir para ativação comercial.

O OdooiA (V1) tem 2 módulos entregues, modelo comercial definido (R$2.200/mês SaaS), co-fundador com restaurante real, e FAPEMA aprovada. O blocker não é tecnológico — é ativação.

Diagnóstico do CFO: "Cada hora em governança é uma hora que não fecha receita."

## Decisão

Bifurcar o ciclo SDD em dois modos:

| | SDD Full | SDD Express |
|---|---|---|
| **Quando usar** | Governança, plataforma, decisões arquiteturais | V1 features, ativação comercial, onboarding |
| **Spec** | Completa com frontmatter, ISO refs, critérios de aceite | 1 parágrafo: o quê, pra quem, critério de done |
| **SKILL** | Com primitiva, runtime, evidence plan | Opcional — só se for reutilizável |
| **Evidence** | Mensurável, vinculada a ISO 25010 | "Felipe confirmou que funciona" ou "está em produção" |
| **Retro** | Formal com retro_score | 3 bullets: funcionou / não funcionou / próximo |

### Regras do Express

1. **Só vale para V1 (OdooiA)** até a condição de expiração ser atingida
2. **Spec-lite é obrigatória** — não é "sem spec", é spec proporcional
3. **Retro express é obrigatória** — 3 bullets no final de cada entrega
4. **ADRs seguem SDD Full sempre** — decisões arquiteturais não têm atalho

### Template Spec-lite

```markdown
## [Nome da entrega]
- **O quê:** [1 frase]
- **Pra quem:** [Felipe / usuário final / interno]
- **Done quando:** [critério observável]
```

## Condição de Expiração

Este ADR expira automaticamente quando:

> **Felipe completar 2 meses consecutivos de pagamento SaaS (MRR confirmado).**

Após expiração, todo trabalho volta para SDD Full. O CTO deve criar ADR-019 formalizando a transição de volta.

## Decisões Vinculadas (mesma reunião)

1. **Freeze L2-L7** — lacunas de governança congeladas até primeiro pagamento. Frontmatter atualizado just-in-time se SKILL for usada em V1 (emenda CPO).
2. **Alocação semanal:** 3h revenue / 1h método / 1h admin.
3. **Hierarquia de prioridades:** Revenue > Produto > Método > Admin.

## Consequências

### Positivas

- Libera ~2h/semana do budget que estavam em overhead de governança
- Desbloqueia ativação do V1 sem sacrificar rastreabilidade (retro express mantém)
- Alinha o SDD ao estágio real da empresa (pré-receita)
- Reduz risco de burnout (COO: risco cai de 🟡 para 🟢)

### Negativas

- Dívida técnica de governança acumula (SKILLs sem frontmatter completo)
- Risco de o Express virar o "novo normal" se a condição de expiração não for monitorada
- Evidence menos rigorosa pode mascarar problemas de qualidade

### Mitigações

- Condição de expiração objetiva e mensurável (2 meses MRR)
- CPO monitora emenda just-in-time
- Retro express obrigatória mantém feedback loop mínimo
- COO monitora alocação de horas semanalmente

## Evidence

Esta decisão é validada quando:

1. **Curto prazo (30 dias):** Jean opera dentro de 5h/semana com V1 progredindo
2. **Médio prazo (60 dias):** Primeiro pagamento do Felipe confirmado
3. **Sucesso final:** ADR-018 expira naturalmente (2 meses de MRR = método funcionou)

## Alternativas Consideradas

- **Manter SDD Full para tudo** — rejeitado: overhead incompatível com 5h/semana e receita zero
- **Abandonar SDD temporariamente** — rejeitado: perder rastreabilidade cria problemas piores depois
- **SDD Express permanente** — rejeitado: o rigor do Full é necessário para V2/V3 e escala
