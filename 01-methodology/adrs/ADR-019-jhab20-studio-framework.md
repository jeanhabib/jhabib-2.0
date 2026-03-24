---
id: ADR-019
title: jhab20-como-sdd-studio-framework
status: ACCEPTED
superseded-by: ~
date: 2026-03-24
iso-ref: ISO 9001, ISO/IEC 42001, ISO 56001
tags: [adr, strategy, studio, framework]
audited: 2026-03-24
audited-by: c-level-board
---

# ADR-019 — JHabib 2.0 como SDD Studio Framework

## Status

ACCEPTED — 2026-03-24

## Contexto

Dois gaps identificados na operação atual:

1. **A2 delegada sem protocolo formal:** Tarefas de clientes/forks (ex: OdooiA) foram executadas diretamente a partir do contexto do JHabib 2.0, sem handoff estruturado. Isso gerou conflito de contexto entre repo mestre e repos de cliente — a violação de boundary aconteceu ao menos uma vez.

2. **Vault como metodologia sem visibilidade dos forks:** JHabib 2.0 acumulou metodologia, ADRs e SKILLs sem um modelo explícito de como essa metodologia se propaga para projetos externos. Não havia rastreamento dos forks ativos nem protocolo de learning loop.

O reposicionamento de JHabib 2.0 de "vault pessoal" para **SDD Studio Framework** resolve ambos os gaps ao tornar o modelo Studio + Forks explícito e operável.

## Decisão

**JHabib 2.0 é o framework mestre forkável do SDD Studio.**

- Cada cliente recebe um fork novo com seu próprio CLAUDE.md
- O repo mestre nunca executa código ou edita arquivos em repos de forks
- Learnings universais dos forks fluem de volta ao mestre via learning loop mensal
- O estado dos forks ativos é rastreado em `AGORA.md` (gitignored — estado volátil)

## Modelo Operacional: Studio + Forks

```
jhabib-2.0 (framework mestre)
    ├── food-service-ai-ops-v2  ← Fork 1 / V1 / OdooiA
    ├── <restaurante-2>         ← Fork 2..N / V2
    └── <cliente-sdd>           ← Fork SDD licenciado / V3
```

### Ciclo de vida de um cliente

```
prospect → fork criado → pilot → ativo → case study → learning loop
```

### Learning loop (ritual mensal)

1. Revisar AGORA.md e sessões recentes de cada fork ativo
2. ADRs e SKILLs que se mostraram universais → PR para `01-methodology/`
3. Atualizar `AGORA.md` com data do último sync

## Protocolo de Handoff (JHabib 2.0 → fork)

Quando JHabib 2.0 precisar solicitar trabalho em um fork:

1. Criar `05-sessions/handoffs/HANDOFF-<fork>-<YYYY-MM-DD>.md` com:
   - Contexto da tarefa (o quê, pra quem, done quando)
   - ADRs e SKILLs relevantes do mestre
   - Evidence esperada
2. Abrir sessão no repo destino (terminal separado)
3. O agente do fork executa com o SDD interno do fork
4. Resultado (Evidence ou blocker) é registrado de volta em AGORA.md do mestre

**JHabib 2.0 NUNCA executa código ou edita arquivos em repos de forks.**

### Template de handoff

```markdown
## HANDOFF-<fork>-<data>
- **Fork:** <nome-do-repo>
- **Tarefa:** [1 frase]
- **Pra quem:** [usuário final / stakeholder]
- **Done quando:** [critério observável]
- **ADRs relevantes:** [lista]
- **SKILLs sugeridas:** [lista]
- **Evidence esperada:** [formato]
```

## Regra de Boundary

| Permitido em JHabib 2.0 | Proibido em JHabib 2.0 |
|-------------------------|------------------------|
| Criar HANDOFF-*.md | Editar arquivos do fork |
| Atualizar AGORA.md | Executar código do fork |
| Propagar SKILLs/ADRs via PR | Fazer deploy no fork |
| Learning loop (leitura) | Commits em repos de cliente |

## Alinhamento com Portfólio

| Vetor | Fork | Papel |
|-------|------|-------|
| V1 — OdooiA food-service | `food-service-ai-ops-v2` | Fork 1 / proof-of-concept |
| V2 — Réplica restaurantes | Fork 2..N via template | Escala do modelo Studio |
| V3 — SDD licenciado | JHabib 2.0 como produto | Framework é o deliverable |

V3 é o estado em que JHabib 2.0 se torna vendável: o framework mestre **é** o produto.

## ADRs Relacionados

- **ADR-018** (SDD Express): define modo de execução vigente para V1. Não é substituído — Studio + Forks é o modelo de repo, Express é o modo de processo.

## Consequências

### Positivas

- **Separação de contexto clara:** agente do fork opera com contexto do cliente; agente mestre opera com contexto de metodologia
- **Escalabilidade:** V2 = clonar template de fork, não reinventar processo
- **Rastreabilidade:** AGORA.md e handoffs criam audit trail dos clientes ativos
- **V3 viabilizado:** quando o framework for estável e tiver 2-3 cases, torna-se produto licenciável

### Negativas / Riscos

- **Overhead de handoff:** cada delegação exige criação de HANDOFF-*.md — custo ~15min por tarefa
- **Risco de deriva:** se o learning loop não acontecer mensalmente, mestre e forks divergem
- **Curva de adoção:** Jean precisa internalizar o boundary rule antes de contratar mais forks

### Mitigação

- Template de handoff reduz overhead para ~5min após primeira vez
- AGORA.md como check semanal (não mensal) nos primeiros 2 meses
- Boundary rule adicionada como Regra Inviolável #8 no CLAUDE.md

## Evidence de Sucesso

| Marco | Critério | Prazo |
|-------|----------|-------|
| M1 | Primeiro HANDOFF-*.md criado e executado com sucesso | Sprint corrente |
| M2 | AGORA.md populado com pelo menos 1 fork ativo | Sprint corrente |
| M3 | Fork 2 criado via template (V2) | Após case Felipe confirmado |
| M4 | PR de learning loop aceito no mestre | 30 dias após M1 |

## Decisão Tomada Por

C-Level Board (CTO Alex Chen, CPO Lena Park, COO Daniel Santos, CFO Marcus Lima, CMO Sofia Reyes) — 2026-03-24
