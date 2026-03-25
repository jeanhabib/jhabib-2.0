---
id: SKILL-008
title: retrospective
primitive: Learning
status: draft
runtime: agnostic
iso-ref: ISO/IEC 25010 — Maintainability
tags: [skill]
audited: false
audited-by:
created: 2026-03-17
---

> **Pilar:** [[org-chart|PMO & Delivery]] · **Owner:** COO Daniel Santos · [[coo-daniel-santos]]
> **Metodologia:** [[sdd-overview]] · [[golden-rules]]

# retrospective — Conduz Retrospectiva e Captura Conhecimento

> **Em uma frase:** Ao fechar uma fase ou sprint, transforma aprendizado em SKILLs reutilizáveis, anti-patterns e ADRs — alimentando o Learning Loop do Jhabib 2.0.

---

## ① Frente — Interface Pública

### Quando usar

- ✅ Ao fechar uma fase major ou sprint de qualquer projeto
- ✅ Quando identificar padrão recorrente que merece virar SKILL
- ✅ Antes de começar o próximo sprint — garante que o conhecimento não se perde
- ❌ Não usar no meio de um ciclo ativo — espere ponto de parada natural

### Inputs

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|:-----------:|-----------|
| `project_name` | string | ✅ | Nome do projeto |
| `phase` | string | ✅ | Fase ou sprint encerrado |
| `skills_dir` | string | ❌ | Path do diretório de skills. Default: `.claude/skills/` |
| `output_dir` | string | ❌ | Onde salvar outputs. Default: `skills/` do Jhabib 2.0 |

### Outputs

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `generic_skills` | string[] | SKILLs genéricas para migrar ao Jhabib 2.0 |
| `domain_skills` | string[] | SKILLs de domínio para documentar no Notion |
| `new_skills` | string[] | SKILLs novas a criar identificadas |
| `anti_patterns` | string[] | AP-XXX para `01-methodology/anti-patterns/anti-patterns.md` |
| `adrs` | string[] | ADRs novos propostos |
| `retro_score` | 1-5 | 1=método ajudou muito, 5=método atrapalhou |

---

## ② Corpo — Implementação

### Injeção de contexto

```bash
git log --oneline -20          # commits da fase
ls .claude/skills/             # inventário de skills do projeto
cat 01-methodology/anti-patterns/anti-patterns.md   # anti-patterns já documentados
```

### Plano

```
PASSO 1 — Inventário
  → Listar todas as SKILLs do projeto
  → Classificar cada uma: genérica / domínio / obsoleta
  → Genérica = resolve problema independente de stack/cliente

PASSO 2 — Cinco perguntas obrigatórias
  Q1. Qual SKILL criada aqui resolve problema genérico?
  Q2. O que teria acelerado o projeto se já existisse como SKILL?
  Q3. Qual decisão arquitetural merece virar ADR?
  Q4. O que não funcionou → deve ser anti-pattern com regra clara?
  Q5. O ciclo SDD foi seguido? O que quebrou o ciclo?

PASSO 3 — Redigir outputs
  → SKILL genérica: copiar para Jhabib 2.0 com frontmatter atualizado
  → Anti-pattern: formato AP-XXX: título / problema / regra
  → ADR: título + motivação de 2 linhas

PASSO 4 — Reportar
  → Listar todos os outputs classificados
  → Retro score com justificativa
  → Sugestão de 1 mudança no ciclo para o próximo sprint
```

### Validation Loop

```
Para cada SKILL classificada como genérica:
  SE contém referência ao cliente/stack específico →
    reescrever para remover acoplamento antes de migrar

SE retro_score >= 4 →
  adicionar issue: revisar ciclo SDD no próximo sprint
```

---

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA FASE 11 + Sprint 1 — generalizado |
