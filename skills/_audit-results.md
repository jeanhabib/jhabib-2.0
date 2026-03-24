# Audit Results - Skills Jhabib 2.0

Data: 2026-03-24

## Frontmatter de cada Skill

| # | Skill | Frontmatter |
|---|-------|-------------|
| 1 | check-drift | name, version:0.1, status:stable, tags:[ml,drift,monitoring], origin:OdooiA FASE 11 |
| 2 | env-doctor | name, version:0.1, status:stable, tags:[infra,health-check,pre-dev], disable-model-invocation:true, user-invocable:true, origin:OdooiA Sprint 1 |
| 3 | eval-rag | name, version:0.1, status:stable, tags:[rag,quality,deepeval], origin:OdooiA FASE 11 |
| 4 | llm-benchmark | name, version:0.1, status:stable, tags:[llm,benchmark,ollama,model-selection], origin:OdooiA retrospectiva FASE 11 |
| 5 | nist-audit | name, version:0.1, status:stable, tags:[security,governance,nist,ai-rmf,compliance], disable-model-invocation:true, user-invocable:true, argument-hint, origin:OdooiA Sprint 1 |
| 6 | orchestrator | name, version:2.0, status:stable, tags:[meta,orchestration,sdd,cycle], origin:OdooiA Sprint 1 |
| 7 | phoenix-trace | name, version:0.1, status:stable, tags:[observability,otel,tracing,debugging], origin:OdooiA FASE 11 |
| 8 | retrospective | name, version:0.1, status:stable, tags:[learning,meta,knowledge-capture,jhabib-2.0], origin:OdooiA FASE 11 + Sprint 1 |
| 9 | security-scan | name, version:0.1, status:stable, tags:[security,pre-merge,scan], origin:OdooiA Sprint 1 |
| 10 | smoke-test | name, version:0.1, status:stable, tags:[qa,smoke,validation], origin:OdooiA Sprint 1 |
| 11 | _anti-patterns.md | Sem frontmatter (documento de referencia, nao eh skill) |

## Deficit comum a TODAS as skills

- **Nenhuma skill possui campos `id`, `primitive`, ou `runtime`** no frontmatter. Usam: name, version, status, tags, description, origin.
- **Nenhuma skill declara `runtime: agnostic`** explicitamente.
- **Nenhuma skill conecta a uma metrica Q canonica** mensuravel.
- **Nenhuma skill tem "Evidence" com dados quantitativos** — todas sao procedurais/checklists.
- **Nenhuma skill documenta user pain** explicitamente ou referencia ISO 25010.
- **Nenhuma skill define human override** para features de IA.
- **Nenhuma skill estima horas de manutencao recorrente** ou mapeia PDCA explicitamente.
- **Nenhuma skill identifica riscos financeiros** ou planos de mitigacao de custos.

## Tabela de Auditoria

| Arquivo | Tipo | Status | C-Level | Motivo | Destino |
|---------|------|--------|---------|--------|---------|
| `skills/check-drift/SKILL.md` | Skill generica ML | ⚠️ REVISAO | CTO: falta id/primitive/runtime/evidence; CFO: sem custo estimado | Util mas sem metricas mensuráveis; depende de ambiente ML configurado | Adicionar frontmatter canonico + threshold mensuravel |
| `skills/env-doctor/SKILL.md` | Skill generica infra | ⚠️ REVISAO | CTO: falta id/primitive/runtime; COO: ~0.5h/sprint manutencao, roda sem Jean | Checklist solido, mais proxima de aprovacao; sem evidence quantitativa | Adicionar id/primitive/runtime, vincular a Q metric |
| `skills/eval-rag/SKILL.md` | Skill generica RAG | ⚠️ REVISAO | CTO: falta id/primitive/runtime; CFO: DeepEval e gratuito (OSS) mas sem mitigacao documentada | Depende de DeepEval (OSS); criterios de aprovacao sao thresholds numericos (bom) mas sem evidence real | Documentar custo zero + adicionar frontmatter canonico |
| `skills/llm-benchmark/SKILL.md` | Skill generica LLM | ⚠️ REVISAO | CTO: falta id/primitive/runtime; tem criterios mensuráveis (>=80% em 5 exemplos) | Melhor evidence entre todas (criterio quantitativo claro); previne AP-003 | Mais proxima de aprovacao — adicionar frontmatter canonico |
| `skills/nist-audit/SKILL.md` | Skill generica compliance | ⚠️ REVISAO | CTO: falta id/primitive/runtime; CPO: sem ISO 25010 explicito; COO: ~1h/sprint, roda sem Jean | Checklist de auditoria NIST solido; sem evidence de execucao real | Adicionar frontmatter canonico + log de execucoes |
| `skills/orchestrator/SKILL.md` | Meta-skill (orquestracao) | ⚠️ REVISAO | CTO: falta id/primitive/runtime; COO: 0h manutencao (e um script); CPO: sem human override definido | Skill mestra do ciclo SDD; bem estruturada mas sem override humano para decisoes de IA | Adicionar human override + frontmatter canonico |
| `skills/phoenix-trace/SKILL.md` | Skill generica observability | ⚠️ REVISAO | CTO: falta id/primitive/runtime; CFO: Arize Phoenix OSS (gratis) mas sem mitigacao documentada | Depende de Phoenix rodando localmente; sem evidence quantitativa | Documentar custo + adicionar frontmatter canonico |
| `skills/retrospective/SKILL.md` | Meta-skill (learning) | ⚠️ REVISAO | CTO: falta id/primitive/runtime; COO: ~1h/sprint, roda sem Jean; mapeia parcialmente PDCA | Skill de captura de conhecimento; estrutura boa mas sem metricas | Adicionar frontmatter canonico + retro_score como Q metric |
| `skills/security-scan/SKILL.md` | Skill generica security | ⚠️ REVISAO | CTO: falta id/primitive/runtime; CFO: Trivy e OSS (gratis); CPO: criterio de aprovacao claro | Checklist de seguranca pre-merge; depende de Trivy (OSS) | Adicionar frontmatter canonico + evidence de execucao |
| `skills/smoke-test/SKILL.md` | Skill generica QA | ⚠️ REVISAO | CTO: falta id/primitive/runtime; COO: ~0.5h/sprint; CPO: isencoes bem documentadas | Checklist de smoke test com isencoes claras; depende de Playwright para QA UI | Adicionar frontmatter canonico + vincular a Q metric |
| `skills/_anti-patterns.md` | Documento referencia | ⚠️ REVISAO | CTO: sem frontmatter (aceitavel para doc); COO: 0h manutencao | 10 anti-patterns bem documentados com regra clara; nao e skill | Manter como esta, nao precisa de frontmatter canonico |

## Resumo

- **0 APROVADO** — nenhuma skill passa nos 4 criterios C-Level simultaneamente
- **11 REVISAO** — todas precisam de ajustes no frontmatter (id, primitive, runtime) e evidence mensuravel
- **0 DESCARTADO** — todas tem valor funcional real

### Acoes prioritarias
1. Definir schema canonico de frontmatter com campos: `id`, `primitive`, `runtime`, `q_metric`
2. Adicionar `runtime: agnostic` a todas as skills (ja sao agnosticas de fato)
3. Documentar evidence mensuravel (logs de execucao real) em cada skill
4. Adicionar `human_override` no orchestrator para decisoes de IA
5. Documentar custo de dependencias (todas OSS/gratis) no frontmatter
