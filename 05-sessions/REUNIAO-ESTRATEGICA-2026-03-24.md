---
date: 2026-03-24
type: reuniao-estrategica
tags: [session, strategy, c-level, revenue]
participantes: [Jean Habib (Founder), Alex Chen (CTO), Sofia Reyes (CMO), Marcus Lima (CFO), Lena Park (CPO), Daniel Santos (COO)]
tema: Metodologia efetiva para gerar receita — parar de polir, começar a vender
---

# Reunião Estratégica C-Level — 2026-03-24

> [[HOME]] · [[SESSION-2026-03-24|Session]] · [[org-chart]] · [[ADR-018-sdd-express-pre-receita|ADR-018]]

> **Tema central:** O JHabib 2.0 tem método, tem produto, tem sócio — mas receita zero. Como encurtar o caminho até o primeiro R$ entrar?

---

## 1. Abertura — Jean Habib (Founder)

Estou gastando mais de 5h/semana estabilizando a estrutura do JHabib. Auditoria feita, vault organizado, ADRs e SKILLs mapeados. Mas nenhum centavo entrou. Precisamos de uma metodologia que priorize receita sobre perfeição. A pergunta para este board é: **o que cortamos, o que aceleramos, e o que muda no SDD para gerar dinheiro?**

---

## 2. Diagnóstico por C-Level

### CFO Marcus Lima (ISO 31000) — "O relógio está correndo"

> Vou ser direto. Temos custo zero de infraestrutura — ótimo. Mas temos custo de oportunidade brutal: cada hora do Jean que vai para governança é uma hora que não fecha receita.

**Números na mesa:**
- Receita atual: **R$ 0**
- Custo fixo: **~R$ 0** (stack OSS)
- Custo de oportunidade: **~R$ 200-400/hora** (valor hora senior market US)
- OdooiA modelo comercial: Setup R$15-25k + SaaS R$2.200-3.500/mês
- Felipe já tem equity e aporte de R$15k aprovado
- FAPEMA aprovada — dinheiro de pesquisa que pode ser alavancado

**Diagnóstico financeiro:** O primeiro R$ está a literalmente **uma conversa com Felipe** de distância. Não é um problema de produto — é um problema de ativação comercial.

**Riscos:**
1. Gastar horas em L2-L7 (governança) antes de ativar V1 = atraso de receita
2. SDD over-engineered para o estágio atual = barreira, não alavanca
3. Felipe esfriar se não ver progresso tangível

---

### CTO Alex Chen (ISO/IEC 42001) — "SDD precisa de um fast-track mode"

> O SDD como está é robusto para escala, mas pesado demais para estágio pré-receita. Proponho bifurcar o ciclo.

**Problema:** O ciclo `Spec → SKILL → Evidence → Retro` está sendo aplicado com o mesmo rigor para governança interna E para features de produto. Isso não escala quando o budget é 5h/semana.

**Proposta — SDD Fast-Track (para V1 revenue-critical):**

```
[SDD Full]     Spec → SKILL → Evidence → Retro     (governança, plataforma)
[SDD Express]  Spec-lite → Execute → Ship → Retro   (V1 features, comercial)
```

| | SDD Full | SDD Express |
|---|---|---|
| Spec | Completa, frontmatter, ISO refs | 1 parágrafo: o quê, pra quem, critério de done |
| SKILL | Com primitiva, runtime, evidence plan | Opcional — só se for reutilizável |
| Evidence | Mensurável, ISO 25010 | "Felipe confirmou que funciona" ou "está em produção" |
| Retro | Formal com retro_score | 3 bullets: funcionou, não funcionou, próximo |

**Condição:** SDD Express só vale para V1 (OdooiA) até o primeiro cliente pagante. Depois, tudo volta para SDD Full.

**ADR proposto:** ADR-018 — SDD Express para fase pré-receita.

---

### CMO Sofia Reyes (ISO 56001) — "Vocês estão construindo quando deveriam estar vendendo"

> O OdooiA tem 2 módulos entregues, um modelo comercial definido, e um co-fundador com restaurante real. O que falta não é tecnologia — é uma conversa de venda.

**Realidade do mercado:**
- Felipe = primeiro cliente E co-fundador. Ele já investiu R$15k. Ele **quer** que funcione.
- O blocker é técnico-operacional (IP + credenciais câmeras RTSP), não comercial
- A FAPEMA dá legitimidade acadêmica — use isso no pitch

**Plano comercial imediato (próximos 30 dias):**

1. **Semana 1:** Ligar para Felipe. Destravar o RTSP. Definir data de ativação.
2. **Semana 2:** Ativar módulos no Jakaru. Dashboard + EPI Vision rodando.
3. **Semana 3:** Felipe usando por 1 semana. Coletar feedback real.
4. **Semana 4:** Primeiro invoice: Setup + primeiro mês SaaS.

**Pricing V1 (recomendação):**
- Para Felipe (co-fundador): Setup R$0 (ele já investiu equity). SaaS base R$2.200/mês.
- Primeiro pagamento: **R$2.200 no mês 1**.
- MRR projetado V1: **R$2.200/mês** = ~US$440/mês (9% da meta de $5k).

> Não esperem o produto perfeito. Felipe é sócio, não vai cancelar por um bug. Ativem, cobrem, iterem.

---

### CPO Lena Park (ISO/IEC 25010) — "MVP means M-I-N-I-M-A-L"

> Estou vendo o roadmap do QAi Augment com items de plataforma que não precisam existir para V1 funcionar. Vamos separar radicalmente.

**O que V1 (OdooiA) precisa AGORA para Felipe pagar:**
1. ✅ EPI Vision funcionando (já entregue)
2. ✅ Dashboard KPIs funcionando (já entregue)
3. ❌ Integração RTSP com câmeras reais do Jakaru (bloqueado por Felipe)
4. ❌ Um onboarding mínimo (doc de 1 página: como usar)

**O que V1 NÃO precisa agora:**
- ❌ QAi Augment dashboard
- ❌ Métrica Q canônica unificada
- ❌ Frontmatter canônico nas 10 SKILLs
- ❌ AI Policy formal
- ❌ Protótipos .jsx no repo

**Proposta — Freeze de escopo:**

> Todas as lacunas L2-L7 ficam **CONGELADAS** até o primeiro pagamento do Felipe. Única exceção: L4 (CLAUDE.md v2) se o SDD Express for aprovado, porque afeta o fluxo de trabalho direto.

**Métrica de qualidade V1 (simplificada):**
- Felipe consegue ver o dashboard? ✅/❌
- EPI Vision detecta corretamente? % accuracy > 80%
- Sistema roda 24h sem crash? ✅/❌

Isso é a "métrica Q" para V1. Não precisa de ISO 25010 completa agora.

---

### COO Daniel Santos (ISO 45001) — "5h/semana não é aspiração, é sobrevivência"

> Jean está queimando mais que 5h/semana em governança. Isso é insustentável com TrueLogic/SoulCycle em paralelo. Meu trabalho é proteger o recurso mais escasso: o tempo do Jean.

**Alocação proposta (5h/semana, estrita):**

| Bloco | Horas | Atividade |
|-------|-------|-----------|
| **Revenue** | 3h | Comunicação com Felipe, deploy, fixes |
| **Método** | 1h | Uma retro express, um ADR se necessário |
| **Admin** | 1h | Sessão log, vault mínimo |

**Regras operacionais:**
1. **Zero hora em governança interna até o primeiro pagamento** — L2-L7 congeladas
2. **O agente (Claude) faz o trabalho pesado** — Jean decide e valida, não executa
3. **Timeboxing brutal:** se algo não cabe em 1 pomodoro (25min), quebrar ou delegar
4. **Sessões após 22h: proibidas** (ISO 45001, já está no CLAUDE.md)

**Burnout risk assessment:**
- Atual: 🟡 MODERADO (overhead de governança sugando energia criativa)
- Após SDD Express + freeze: 🟢 BAIXO (foco claro, escopo reduzido)

---

## 3. Debate e Decisões

### DEBATE 1: "SDD Express vai criar dívida técnica?"

**Alex (CTO):** Sim, mas dívida controlada. A retro express no final de cada sprint garante que documentamos o que ficou pendente. Quando o dinheiro entrar, pagamos a dívida.

**Marcus (CFO):** Dívida técnica com receita > perfeição sem receita. Simples.

**Lena (CPO):** Concordo, com uma condição: o ADR-018 precisa definir claramente quando o Express expira. Não quero que vire o novo normal.

**Daniel (COO):** O Express libera ~2h/semana do Jean que estavam indo para Specs completas. Essas 2h vão para revenue.

> **DECISÃO 1: APROVADA POR UNANIMIDADE**
> Criar ADR-018 — SDD Express para fase pré-receita.
> Expira quando: primeiro pagamento recorrente confirmado (mês 2 do Felipe).
> Owner: CTO Alex Chen.

---

### DEBATE 2: "Congelar L2-L7 não é arriscado?"

**Alex (CTO):** L6 (frontmatter) me incomoda — as SKILLs sem governança podem divergir. Mas Sofia tem razão: isso não gera receita.

**Sofia (CMO):** Exato. Governança perfeita com zero clientes é um hobby, não um negócio.

**Marcus (CFO):** Risco de não congelar > risco de congelar. O clock está correndo.

**Lena (CPO):** Proponho um compromisso: se durante o trabalho de V1 alguma SKILL for usada, atualizamos o frontmatter naquele momento (just-in-time). Não fazemos batch update.

> **DECISÃO 2: APROVADA COM EMENDA**
> L2-L7 congeladas até primeiro pagamento.
> Emenda Lena: frontmatter just-in-time se uma SKILL for usada em V1.
> Owner: CPO Lena Park monitora.

---

### DEBATE 3: "O blocker real é o Felipe?"

**Sofia (CMO):** Sim. RTSP está bloqueado por ele. Precisamos de uma data ou um workaround.

**Alex (CTO):** Podemos fazer um modo demo com vídeo gravado enquanto o RTSP não está disponível. Já temos o EPI Vision funcionando — só precisa de input. Felipe vê o dashboard com dados simulados, entende o valor, libera as credenciais.

**Lena (CPO):** Isso também serve como onboarding. Felipe vê o sistema rodando, mesmo que com dados demo.

**Daniel (COO):** Isso é 1-2h de trabalho do agente. Jean só precisa mandar o link pro Felipe.

> **DECISÃO 3: APROVADA**
> Alex prepara modo demo (vídeo/imagens) para EPI Vision.
> Jean agenda call com Felipe esta semana para mostrar demo e destravar RTSP.
> Owner: Jean (call) + CTO Alex (demo técnico).

---

### DEBATE 4: "Qual é a meta de 90 dias?"

**Marcus (CFO):**

| Marco | Prazo | Métrica |
|-------|-------|---------|
| **M1** — Felipe ativa OdooiA | Semana 2-3 (abril) | Sistema rodando no Jakaru |
| **M2** — Primeiro pagamento | Mês 1 (abril) | R$2.200 na conta |
| **M3** — MRR estável | Mês 3 (junho) | 3 meses consecutivos pagos |
| **M4** — Segundo restaurante (V2 pilot) | Mês 3 (junho) | 1 lead qualificado no Nordeste |

**Sofia (CMO):** M4 depende de M1 ser um sucesso documentado. Quando Felipe estiver rodando, usamos como case study para prospectar V2.

**Lena (CPO):** E o case study É a Evidence do SDD — mata dois coelhos.

> **DECISÃO 4: APROVADA**
> Meta 90 dias conforme tabela do CFO.
> CMO prepara template de case study (1 pager) quando M1 for atingido.
> Owner: CFO Marcus Lima (tracking), CMO Sofia Reyes (case study).

---

## 4. Plano de Ação Consolidado

| # | Ação | Owner | Prazo | Deps |
|---|------|-------|-------|------|
| **A1** | Criar ADR-018 (SDD Express) | CTO Alex | Esta semana | — |
| **A2** | Preparar modo demo EPI Vision | CTO Alex (agente) | 2 dias | — |
| **A3** | Call com Felipe: mostrar demo + destravar RTSP | Jean | Esta semana | A2 |
| **A4** | Ativar OdooiA no Jakaru | Jean + Alex (agente) | Semana 2 | A3 |
| **A5** | Criar onboarding 1-pager para Felipe | CPO Lena (agente) | Junto com A4 | A2 |
| **A6** | Emitir primeiro invoice | CFO Marcus | Após A4 | A4 |
| **A7** | Atualizar CLAUDE.md com SDD Express | CTO Alex (agente) | Junto com A1 | A1 |
| **A8** | Case study template | CMO Sofia | Quando M1 atingido | A4 |

---

## 5. O que muda no dia a dia

### Antes (pré-reunião)
```
Jean → organiza vault → audita SKILLs → spec completa → executa → evidence formal
Resultado: vault bonito, receita zero
```

### Depois (pós-reunião)
```
Jean → decide prioridade revenue → spec-lite → agente executa → ship → retro express
Resultado: produto na mão do Felipe, dinheiro entrando
```

### Nova hierarquia de prioridades

```
1. 🔴 REVENUE   — Tudo que coloca dinheiro na conta (V1 ativo)
2. 🟡 PRODUTO   — Features que Felipe pediu ou precisa
3. 🔵 MÉTODO    — SDD/governança (só se necessário para 1 ou 2)
4. ⚪ ADMIN     — Vault, docs, organização (mínimo viável)
```

---

## 6. Encerramento — Jean Habib (Founder)

**Decisões desta reunião:**
1. ✅ SDD Express aprovado (ADR-018) — rigor proporcional ao estágio
2. ✅ L2-L7 congeladas até primeiro pagamento (emenda just-in-time)
3. ✅ Modo demo como workaround para RTSP blocker
4. ✅ Meta 90 dias: M1→M2→M3→M4
5. ✅ Alocação 3h revenue / 1h método / 1h admin

**Próxima ação imediata:** Criar ADR-018 + modo demo, ligar para Felipe.

---

*"Brasil valida o método, US é o destino" — mas primeiro, o método precisa pagar as contas.*

*ISO 9001 · ISO/IEC 42001 · ISO 56001 · ISO 45001*
