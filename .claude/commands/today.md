Você é o agente do JHabib 2.0 executando o SKILL-011 (/today).

## Passo 1 — Ler os arquivos de estado

Leia estes 9 arquivos em paralelo (vault base: `/Users/jeanhabib/Library/Mobile Documents/iCloud~md~obsidian/Documents/jhabib-2.0`):

1. `00-strategy/ops-state.md`
2. `00-strategy/financial-state.md`
3. `00-strategy/compliance-state.md`
4. `01-methodology/tech-state.md`
5. `02-products/product-state.md`
6. `03-clients/pipeline.md`
7. `06-us-market/gtm-state.md`
8. `AGORA.md`
9. O arquivo mais recente em `05-sessions/SESSION-*.md` (use Glob para encontrar)

## Passo 2 — Coletar horas

Pergunte: "Jean, quantas horas do budget semanal já foram usadas esta semana?"

Aguarde a resposta antes de continuar.

## Passo 3 — Imprimir o Terminal Briefing

Com base nos `## Top Blockers` e `## Ações desta semana` de cada state file, aplique o filtro:

**Revenue > Produto > Método > Admin**

- Revenue = qualquer item que mova R1→R4 ou MRR (Felipe, invoice, deploy)
- Produto = features que Felipe pediu ou precisa para a demo
- Método = ADRs, SKILLs, SDD (só se necessário para Revenue ou Produto)
- Admin = vault, docs (mínimo viável)

Imprima o briefing neste formato exato (≤10 linhas):

```
=== TODAY — {DATA_HOJE} === [{horas_usadas}h usadas / 5h budget]

REVENUE (prioridade máxima)
  {item_revenue} → Owner: Jean | Deadline: {prazo}

PRODUTO
  {item_produto} → Owner: Agente/Jean

BLOCKER CRÍTICO
  {blocker_principal} — {quem_desbloqueia}

TOP 3 AÇÕES
  1. {ação_jean} (≤30min para Jean)
  2. {ação_agente_1} (agente executa)
  3. {ação_agente_2} (agente executa)

Budget restante: {5 - horas_usadas}h | Próxima sessão recomendada: {sugestão}
```

## Passo 4 — Criar arquivo TODAY

Crie o arquivo `05-sessions/TODAY-{DATA_HOJE}.md` usando o template em `templates/TODAY-template.md`.

Preencha cada seção do C-Level com os dados extraídos dos state files (Estado Atual, Blocker, Ação).

Confirme ao final: "TODAY-{DATA_HOJE}.md criado no vault."
