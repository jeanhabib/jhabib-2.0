---
id: FORK-GUIDE
title: fork-guide
status: active
tags: [methodology, forks, studio, canonical]
iso-ref: ISO 9001, ISO 56001
created: 2026-03-25
see-also: ADR-019
---

# FORK-GUIDE — Ciclo Forkável do SDD Studio

> ADR de referência: [[ADR-019-jhab20-studio-framework|ADR-019]]
> Owner: CTO Alex Chen + COO Daniel Santos

---

## O que é o SDD Studio

JHabib 2.0 é um **framework mestre forkável**. Cada projeto piloto recebe um fork independente com seu próprio contexto. O repo mestre nunca executa código em forks — apenas orquestra via handoffs.

O diferencial é o ciclo **fork → disassemble → improve → reassemble → merge back**, que transforma cada projeto piloto em melhoria contínua do framework.

---

## Modelo Operacional

```
jhabib-2.0 (framework mestre)
    ├── food-service-ai-ops-v2  ← Fork 1 / V1
    ├── <restaurante-2>         ← Fork 2..N / V2
    └── <cliente-sdd>           ← Fork SDD licenciado / V3
```

### Ciclo de Vida de um Cliente

```
prospect → fork criado → pilot → ativo → case study → learning loop
```

---

## O Ciclo: Fork → Disassemble → Improve → Reassemble → Merge Back

### 1. Fork (criar projeto)

1. Criar repo novo a partir do template de fork
2. Configurar CLAUDE.md do fork com contexto do cliente
3. Copiar SKILLs e ADRs relevantes do mestre
4. Registrar fork em [[AGORA]] (`## Forks Ativos`)

### 2. Disassemble (desmontagem analítica)

Durante a operação do fork, o agente do mestre observa (read-only):
- Quais SKILLs foram usadas e como performaram
- Quais ADRs foram respeitados/violados
- Quais anti-patterns emergiram
- Quais métricas de qualidade (ISO 25010) foram atingidas

### 3. Improve (aprendizado)

Do disassemble, extrair:
- **SKILLs universais** — funcionaram no fork e são reutilizáveis
- **ADRs novos** — decisões que devem virar regra
- **Anti-patterns** — erros que devem ser documentados para evitar recorrência
- **Métricas** — benchmarks reais para calibrar o framework

### 4. Reassemble (remontagem melhorada)

Aplicar as melhorias de volta ao fork:
- Atualizar SKILLs do fork com versões melhoradas
- Adicionar ADRs novos ao fork
- Corrigir anti-patterns detectados

### 5. Merge Back (learning loop)

SKILLs e ADRs que se provaram universais voltam ao mestre via PR:
- PR para `01-methodology/skills/` ou `01-methodology/adrs/`
- Review pelo CTO (qualidade técnica) e COO (governança)
- Atualizar [[AGORA]] com data do último sync

---

## Protocolo de Handoff (Mestre → Fork)

Quando o mestre precisar solicitar trabalho em um fork:

1. Criar `05-sessions/handoffs/HANDOFF-<fork>-<YYYY-MM-DD>.md`
2. Abrir sessão no repo destino (terminal separado)
3. Agente do fork executa com SDD interno do fork
4. Resultado (evidence ou blocker) registrado em [[AGORA]]

### Template de Handoff

```markdown
---
type: handoff
fork: <nome-do-repo>
date: YYYY-MM-DD
tags: [handoff]
---

## HANDOFF-<fork>-<data>
- **Fork:** <nome-do-repo>
- **Tarefa:** [1 frase]
- **Pra quem:** [usuário final / stakeholder]
- **Done quando:** [critério observável]
- **ADRs relevantes:** [lista]
- **SKILLs sugeridas:** [lista]
- **Evidence esperada:** [formato]
```

---

## Boundary Rules

| Permitido em JHabib 2.0 | Proibido em JHabib 2.0 |
|-------------------------|------------------------|
| Criar HANDOFF-*.md | Editar arquivos do fork |
| Atualizar [[AGORA]] | Executar código do fork |
| Propagar SKILLs/ADRs via PR | Fazer deploy no fork |
| Learning loop (leitura) | Commits em repos de cliente |

**Regra absoluta:** JHabib 2.0 NUNCA executa código ou edita arquivos em repos de forks.

---

## Learning Loop (Ritual Mensal)

1. Revisar [[AGORA]] e sessões recentes de cada fork ativo
2. Identificar SKILLs e ADRs universais → PR para `01-methodology/`
3. Documentar anti-patterns novos → `01-methodology/anti-patterns/`
4. Atualizar [[AGORA]] com `last-sync: YYYY-MM-DD`
5. Retro express: funcionou / não funcionou / próximo

### Critérios para "Universal"

Uma SKILL ou ADR é universal quando:
- Funcionou em **2+ forks** diferentes, OU
- Resolve um problema **estrutural** (não específico do cliente)
- É **runtime-agnostic** (funciona em qualquer agente)

---

## V1 → V2 → V3

| Vetor | Fork | Papel |
|-------|------|-------|
| **V1** — Restaurante iA Ops | `food-service-ai-ops-v2` | Proof-of-concept |
| **V2** — Réplica restaurantes | Fork 2..N via template | Escala do modelo |
| **V3** — SDD licenciado | JHabib 2.0 como produto | Framework = deliverable |

V3 é o estado em que o framework mestre **é** o produto vendável.

---

## Links

- [[SDD]] — Metodologia completa
- [[ADR-019-jhab20-studio-framework|ADR-019]] — Decisão arquitetural
- [[gate-pre-pr|Gate Pre-PR]] — Checklist de qualidade
- [[AGORA]] — Estado real-time dos forks
