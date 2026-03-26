---
id: SDD
title: sdd-spec-driven-development
status: active
tags: [methodology, sdd, canonical]
updated: 2026-03-25
---

# SDD — Spec-Driven Development

> Fonte de verdade única. Tudo mais linka para cá.
> [[org-chart]] · [[AGORA]] · [[ADR-018-sdd-express-pre-receita|ADR-018]] · [[ADR-019-jhab20-studio-framework|ADR-019]]

---

## Modos

| | SDD Full | SDD Express (ADR-018 ativo) |
|---|---|---|
| **Quando** | Governança, plataforma, ADRs, SKILLs novas | V1 features, ativação comercial, onboarding |
| **Spec** | Completa: frontmatter, ISO refs, critérios de aceite | Spec-lite: 1 parágrafo (o quê / pra quem / done quando) |
| **SKILL** | Com primitiva, runtime, evidence plan | Opcional — só se reutilizável |
| **Evidence** | Mensurável, vinculada à ISO 25010 | "Felipe confirmou" ou "está em produção" |
| **Retro** | Formal com retro_score | 3 bullets: funcionou / não funcionou / próximo |

**Ciclo Full:** `Spec → SKILL → Evidence → Retro`
**Ciclo Express:** `Spec-lite → Execute → Ship → Retro express`

**ADR-018 expira quando:** Felipe completar 2 meses consecutivos de pagamento SaaS (MRR confirmado). Todo trabalho volta para SDD Full.

---

## Hierarquia de Prioridades

```
Revenue > Produto > Método > Admin
```

**Alocação semanal (5h):** 3h Revenue · 1h Método · 1h Admin

---

## Templates

### Spec-lite (Express)

```markdown
## [Nome da entrega]
- **O quê:** [1 frase]
- **Pra quem:** [Felipe / usuário final / interno]
- **Done quando:** [critério observável]
```

### Spec Completa (Full)

```markdown
---
id: SPEC-NNN
title: [nome-kebab]
primitive: [Intelligence|Engine|Agents|Tools|Memory|Learning]
iso-ref: [ISO/IEC 25010 | outro]
created: YYYY-MM-DD
---

## Contexto
## O quê (escopo)
## Pra quem (usuário/sistema)
## Critérios de aceite (ISO 25010 — observáveis)
## Evidence plan
## Riscos (ISO 31000)
```

### Retro Express

```markdown
- **Funcionou:** [o quê]
- **Não funcionou:** [o quê]
- **Próximo:** [1 ação]
```

### Retro Full

```markdown
- **Funcionou:** [o quê e por quê]
- **Não funcionou:** [root cause]
- **Próximo:** [ação + owner + deadline]
- **retro_score:** [0-10] — [justificativa]
```

---

## 10 Regras (consolidadas — sem duplicação)

1. **Revenue > Produto > Método > Admin** — hierarquia de prioridade inviolável
2. **Spec antes de código** — sem spec, nenhuma ação. Express conta.
3. **Evidence = done means proven** — "parece funcionar" não é evidence
4. **≤5h/semana + sem trabalho após 22h** — ISO 45001, COO monitora
5. **Privacy First** — Ollama > cloud quando possível (ISO/IEC 27001)
6. **Runtime-agnostic** — SKILLs funcionam em qualquer agente (Claude Code, Continue.dev, etc.)
7. **Boundary rule** — JHabib 2.0 nunca executa código em repos de forks. Handoffs via `05-sessions/handoffs/` (ADR-019)
8. **Spike antes de setup** — prove que funciona antes de montar infra
9. **Código é fonte de verdade** — se não está no GitHub, não existe
10. **Nunca vibe coding** — sem "experimentos rápidos" em produção

---

## Gate Pre-PR (inviolável)

```
Lint → Migrate (do zero) → Seed → Tests → Smoke → QA UI → Review
```

**Falha em qualquer etapa = volta para dev. Sem exceções, sem "merge com ressalva".**

| Etapa | O que valida |
|-------|-------------|
| Lint | Código formatado, sem warnings |
| Migrate (do zero) | Schema reproduzível do zero |
| Seed | Dados de teste carregam |
| Tests | Unit + integration passam |
| Smoke | Happy path funciona E2E |
| QA UI | Interface acessível, responsiva |
| Review | Code review humano ou C-Level |

---

## Primitivas de SKILL

| Primitiva | Descrição |
|-----------|-----------|
| **Intelligence** | Raciocínio, análise, decisão |
| **Engine** | Execução, pipeline, automação |
| **Agents** | Orquestração multi-agente |
| **Tools** | Ferramentas auxiliares |
| **Memory** | Persistência, contexto |
| **Learning** | Retro, métricas, melhoria |

---

## SDD ↔ PDCA ↔ ISO

| SDD | PDCA | ISO 9001 | C-Level |
|-----|------|----------|---------|
| Spec | Plan | 7.5 — controle de documentos | CTO Alex Chen |
| SKILL | Do | 8.1 — operação | CTO Alex Chen |
| Evidence | Check | 9.1 — evidência de conformidade | CPO Lena Park |
| Retro | Act | 10.1 — melhoria contínua | COO Daniel Santos |

**ISO base comum:** ISO 9000 · ISO 9001 · ISO 9004

| Conceito | ISO | C-Level |
|----------|-----|---------|
| Métrica Q | ISO/IEC 25010 | CPO Lena Park |
| Anti-burnout ≤5h | ISO 45001 | COO Daniel Santos |
| ZHC / Inovação | ISO 56001 | CMO Sofia Reyes |
| Privacy First | ISO/IEC 27001 | CISO Priya Nair |
| Risk | ISO 31000 | CFO Marcus Lima |
| AI Governance | ISO/IEC 42001 | CTO Alex Chen |
| User-Centered | ISO 9241-210 | CPO Lena Park |

---

## ADRs Vigentes

| ID | Decisão | Status |
|----|---------|--------|
| ADR-001 | Autoresearch FROZEN até Métrica Q (Sprint 4) | ACCEPTED |
| ADR-010 | E2E obrigatório para LLM stories | ACCEPTED |
| ADR-011 | gemma:2b inválido para intent routing | ACCEPTED |
| ADR-017 | Fluxo unidirecional — sem divergência de métricas | ACCEPTED |
| ADR-018 | SDD Express para fase pré-receita (expira com 2 meses MRR) | ACCEPTED |
| ADR-019 | JHabib 2.0 como SDD Studio Framework forkável | ACCEPTED |

---

## Frontmatter Canônico

### SKILL

```yaml
---
id: SKILL-NNN
title: nome-kebab-case
primitive: Intelligence | Engine | Agents | Tools | Memory | Learning
status: draft | active | deprecated
runtime: agnostic | claude-code | continue-dev
iso-ref: ISO/IEC 25010 | outro
tags: [skill]
audited: false | YYYY-MM-DD
audited-by: cto | cpo | coo
created: YYYY-MM-DD
---
```

### ADR

```yaml
---
id: ADR-NNN
title: titulo-kebab-case
status: PROPOSED | ACCEPTED | DEPRECATED | SUPERSEDED
superseded-by: ~
date: YYYY-MM-DD
iso-ref: ~
tags: [adr]
audited: false | YYYY-MM-DD
---
```

### Anti-Pattern

```yaml
---
id: AP-NNN
title: nome-do-problema
severity: low | medium | high | critical
detected-in: restaurante-ia-ops | jhab20
tags: [anti-pattern]
date: YYYY-MM-DD
---
```
