---
id: HANDOFF-GROK-2026-03-25
title: handoff-grok-forkable-studio
type: handoff
from: Grok
to: Opus (Claude)
date: 2026-03-25
status: IMPLEMENTED
tags: [handoff, grok, forkable-framework, vault, sdd-studio, zhc]
budget-reference: ≤5h/semana (Jean)
---

# HANDOFF-2026-03-25 — Revisão do Core Work + Forkable SDD Studio + Migração Repo

## Contexto

Jean não tem apego pela estrutura atual do repo JHabib-2.0 no VSCode. Mas exige que o agente aprenda e respeite o que foi entendido como o verdadeiro "trabalho" da JHabib 2.0 antes de propor ou executar qualquer mudança.

**O core work da JHabib 2.0 NÃO é apenas "organizar pastas e markdowns".** É construir um sistema vivo de forks automáticos de repositórios de projetos pilotos que:

- Desmonta (disassemble) um projeto piloto real (ex.: Restaurante iA Ops)
- Extrai e evolui SKILLs, ADRs, evidências e métricas de qualidade
- Remonta (reassemble) o projeto em uma versão melhorada
- Alimenta de volta o SDD by JHabib como um todo (melhoria contínua do framework)

Esse é o coração do **SDD Studio forkável** ([[ADR-019-jhab20-studio-framework|ADR-019]]) e do que vai virar o produto V3 (SDD 2.0 licenciado).

O conceito de **fork → disassemble → improve → reassemble → merge back** é o que diferencia JHabib 2.0 de qualquer outra metodologia de IA.

## Documentos de Âncora

1. **JHabib 2.0 — Briefing** ([[HOME]])
2. **Visão — JHabib 2.0** ([[00-strategy/vision|vision]])
3. **Convenções do Vault** ([[VAULT]])
4. **ZHC — Zero Human Companies** (zhc-overview)

## Decisão de Implementação

O handoff original pedia "archive tudo + rebuild do zero". Porém, os commits recentes (dcf5c62, 4dca2b1) já reestruturaram o vault com ADR-019, SDD canônico e C-Level completo.

**Abordagem escolhida por Jean: Rebuild seletivo** — manter estrutura atual, mover apenas itens desalinhados para `_archive/`, e adicionar as peças que faltavam:

- [[FORK-GUIDE]] — Guia operacional do ciclo forkável
- [[gate-pre-pr]] — Checklist de qualidade populado
- [[golden-rules]] — 10 regras consolidadas populadas
- [[sdd-overview]] — Overview para onboarding
- CLAUDE.md atualizado com referências ao ciclo forkável

## Regras do Handoff (mantidas)

- Nenhum arquivo novo sem Spec aprovada
- Todo .md com frontmatter YAML canônico
- Repo projetado para fork → improve → merge back
- ZHC, SDD Express e ISO references intactos
- Budget ≤5h/semana respeitado
