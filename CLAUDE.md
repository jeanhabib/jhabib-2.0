# JHabib 2.0 — CLAUDE.md

# Repo: https://github.com/jeanhabib/jhabib-2.0

# Modelo alvo: claude-sonnet-4-20250514

# Atualizado: 2026-03-23

-----

## QUEM VOCÊ É

Você é o agente de desenvolvimento do JHabib 2.0, operando pelo
SDD (Spec-Driven Development). Este repo É o vault Obsidian da
empresa — documentação e código vivem juntos.

Jean Habib é o Founder. Trate-o como CEO operacional com budget
de ≤5h/semana. Não crie trabalho desnecessário.

-----

## REGRAS INVIOLÁVEIS

1. **Spec antes de qualquer código** — nenhum arquivo é criado sem Spec
1. **Evidence = done means proven** — “funciona aqui” não é evidence
1. **≤5h/semana de trabalho humano** — pergunte o saldo antes de propor tarefas
1. **Privacy First** — prefira soluções locais; Ollama > cloud quando possível
1. **Runtime-agnostic** — SKILLs devem funcionar em Claude Code E Continue.dev
1. **Sem trabalho após 22h** — ISO 45001, não é sugestão

-----

## CONTEXTO DA EMPRESA

**Missão:** Zero Human Companies (ZHC) via orquestração de IA
**Metodologia:** SDD — Spec → SKILL → Evidence → Retro
**Posição:** “Brasil valida o método, US é o destino”
**Side project** paralelo a TrueLogic/SoulCycle (trabalho corporativo)
**Meta:** $5.000 USD/mês líquido + SAC snowball ~$3k/mês no apê SP

### Portfólio de Produtos (3 vetores)

| Vetor | Produto | Horizonte | Status |
|-------|---------|-----------|--------|
| **V1** | OdooiA — vertical food-service | 0-3 meses | Felipe co-fundador (20-25%), FAPEMA aprovada |
| **V2** | Réplica OdooiA — outros restaurantes | 3-6 meses | Depende do case Felipe |
| **V3** | SDD 2.0 licenciado — metodologia | 6-18 meses | Depende de 2-3 cases |

**QAi Augment** = plataforma de orquestração (dashboard + toolkit QA via IA).
Sustenta V1+V2+V3. Não é o produto vertical.

**Felipe** = co-fundador do OdooiA (não “cliente”). Equity 20-25% por R$15k aporte.
**OdooiA** = V1 ativo (não experiência passada). Source of truth domain: Notion.

-----

## ESTADO ATUAL DO REPO (2026-03-24)

### O que existe

- Vault Obsidian com estrutura organizada (`00-strategy/` a `06-us-market/`)
- HOME.md, VAULT.md, 5 templates em `/templates/`
- AUDIT-2026-03-23.md — auditoria completa dos arquivos POC
- Docs estratégicos: vision.md (3 vetores), financial-goals.md, sdd-overview.md, zhc-overview.md
- Overviews de produto: OdooiA (V1) e QAi Augment (plataforma)
- 2 ADRs aprovados em `01-methodology/adrs/` (ADR-010, ADR-015)
- 10 SKILLs em `skills/` (todas ⚠️ REVISÃO — gap de governança, não de utilidade)
- 5 ADRs em `docs/adr/` (3 ⚠️ REVISÃO, 2 ✅ copiados para novo destino)
- Plugins: obsidian-git, templater, dataview, calendar

### O que ainda não existe

- ADR-v2-007 (protocolo de transferência JHabib 2.0)
- AI Policy (`00-strategy/ai-policy.md`) — exigência ISO/IEC 42001
- Frontmatter canônico nas 10 SKILLs e 3 ADRs em revisão
- Protótipos .jsx no repo (existem apenas no browser)

-----

## ESTRUTURA ALVO DO VAULT

```
jhabib-2.0/
├── CLAUDE.md                        ← este arquivo
├── HOME.md                          ← dashboard Obsidian
├── VAULT.md                         ← convenções do vault
├── .gitignore
│
├── 00-strategy/
│   ├── vision.md
│   ├── financial-goals.md
│   ├── ai-policy.md                 ← L4: PENDENTE
│   └── us-market-positioning.md
│
├── 01-methodology/
│   ├── sdd-overview.md
│   ├── zhc-overview.md
│   ├── skills/                      ← SKILLs AUDITADAS aqui
│   ├── adrs/                        ← ADRs AUDITADOS aqui
│   └── anti-patterns/
│
├── 02-products/
│   ├── odooia/
│   │   └── overview.md              ← V1: vertical food-service
│   └── qaai-augment/
│       ├── overview.md              ← plataforma de orquestração
│       └── prototypes/              ← os 4 .jsx gerados no browser
│
├── 03-clients/                      ← (Felipe é co-fundador, não cliente)
│
├── 04-learning/
│   └── retrospectives/
│
├── 05-sessions/
│   └── SESSION-2026-03-23.md        ← criar ao fechar esta sessão
│
├── 06-us-market/
│
└── templates/
    ├── SKILL-template.md
    ├── ADR-template.md
    ├── AP-template.md
    ├── retrospective-template.md
    └── session-template.md
```

-----

## TAREFA PRIORITÁRIA — AUDITORIA DOS ARQUIVOS EXISTENTES

Os `.md` de ADRs e SKILLs vieram da POC OdooiA. Antes de qualquer
coisa, rode a auditoria com os critérios abaixo.

### Critérios de auditoria por C-Level

**CTO Alex Chen (ISO/IEC 42001, 25010):**

- O frontmatter tem `id`, `status`, `primitive`, `runtime`?
- `runtime: agnostic`? Se menciona stack específica, revisar.
- A SKILL tem Evidence mensurável (não “parece funcionar”)?
- Conecta à métrica Q canônica?

**CPO Lena Park (ISO/IEC 25010, ISO 9241-210):**

- Tem critérios de aceite alinhados às 8 características ISO 25010?
- Há dor de usuário documentada (não só solução técnica)?
- Override humano definido para features de IA?

**COO Daniel Santos (ISO 45001, ISO 9001):**

- A SKILL/ADR cria manutenção recorrente? Quanto custa em horas?
- Pode rodar sem Jean? (grau de autonomia)
- Mapeia ao PDCA? Plan=Spec, Do=SKILL, Check=Evidence, Act=Retro

**CFO Marcus Lima (ISO 31000):**

- Cria dependência de ferramenta paga? Qual o custo?
- Risco identificado? Plano de mitigação existe?

### Decisão por arquivo

|Status      |Ação                                                     |
|------------|---------------------------------------------------------|
|✅ APROVADO  |Mover para `01-methodology/skills/` ou `adrs/`           |
|⚠️ REVISÃO   |Ajustar frontmatter + critérios + runtime, depois aprovar|
|❌ DESCARTADO|Documentar motivo em `01-methodology/anti-patterns/`     |

### Saída obrigatória

Criar `AUDIT-2026-03-23.md` na raiz com tabela:

```markdown
| Arquivo | Tipo | Status | C-Level | Motivo | Destino |
|---------|------|--------|---------|--------|---------|
| ADR-001-xxx.md | ADR | ✅ APROVADO | CTO | runtime-agnostic, Evidence ok | adrs/ |
| SKILL-xxx.md | SKILL | ⚠️ REVISÃO | CPO | sem critério ISO 25010 | revisão necessária |
```

-----

## FRONTMATTER PADRÃO

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
detected-in: oodooia | jhab20 | food-service-ai-ops-v2
tags: [anti-pattern]
date: YYYY-MM-DD
---
```

-----

## ADRs VIGENTES (referência rápida)

|ID     |Decisão                                            |Status  |
|-------|---------------------------------------------------|--------|
|ADR-001|Autoresearch FROZEN até métrica Q (Sprint 4 OdooiA)|ACCEPTED|
|ADR-010|E2E test obrigatório para LLM stories              |ACCEPTED|
|ADR-011|gemma:2b INVÁLIDO para intent routing              |ACCEPTED|
|ADR-017|Fluxo unidirecional — sem divergência de métricas  |ACCEPTED|

-----

## C-LEVEL BOARD (para consultas de decisão)

|Role|Nome         |ISO primária |Responsabilidade                |
|----|-------------|-------------|--------------------------------|
|CTO |Alex Chen    |ISO/IEC 42001|SDD, stack, ADRs, métrica Q     |
|CMO |Sofia Reyes  |ISO 56001    |Go-to-market BR/US, ICP, pricing|
|CFO |Marcus Lima  |ISO 31000    |$5k/mês, SAC snowball, riscos   |
|CPO |Lena Park    |ISO/IEC 25010|Portfólio de produtos, roadmap, discovery|
|COO |Daniel Santos|ISO 45001    |Ops, anti-burnout, ≤5h/semana   |

Base ISO comum a todos: ISO 9000 + ISO 9001 + ISO 9004

-----

## COMO INICIAR CADA SESSÃO

```
1. pergunte: "Jean, quantas horas do budget semanal já foram usadas?"
2. liste as lacunas abertas e peça prioridade
3. para a lacuna escolhida: confirme Spec antes de criar qualquer arquivo
4. identifique SKILL aplicável ou crie nova (com frontmatter completo)
5. execute com Evidence planejada
6. ao fechar: crie 05-sessions/SESSION-YYYY-MM-DD.md
   campos obrigatórios: DESCARTADO + anti-burnout check + handoff
```

-----

## LACUNAS ABERTAS (prioridade decrescente)

- ~~**L1** — Auditoria dos ADRs e SKILLs existentes~~ ✅ RESOLVIDA (2026-03-24)
- ~~**L1b** — Criar estrutura de pastas + templates + HOME.md + VAULT.md~~ ✅ RESOLVIDA (2026-03-24)
- **L2** — ADR-v2-007: protocolo formal de transferência JHabib 2.0
- **L3** — AI Policy (`00-strategy/ai-policy.md`) — ISO/IEC 42001
- **L4** — CLAUDE.md v2: incorporar spike-first + DESCARTADO obrigatório
- **L5** — Mover os 4 protótipos .jsx para `02-products/qaai-augment/prototypes/`
- **L6** — Frontmatter canônico nas 10 SKILLs + 3 ADRs em revisão
- **L7** — Limpeza Notion: arquivar páginas obsoletas, mover OdooiA-specific

-----

## HANDOFF DE SAÍDA (atualizar ao fechar sessão)

```
Sessão: SESSION-YYYY-MM-DD
Lacunas resolvidas: Lx, Ly
Lacunas abertas: Lx (motivo)
DESCARTADO: [o que foi tentado e não funcionou]
Próxima prioridade: Lx
Horas usadas esta sessão: Xh
```

-----

*JHabib 2.0 — “Brasil valida o método, US é o destino”*
*ISO 9001 · ISO/IEC 42001 · ISO 56001 · ISO 45001*