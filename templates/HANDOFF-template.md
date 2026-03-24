---
fork: nome-do-repo-fork
data: YYYY-MM-DD
card: AX — Título do card
status: pending  # pending | done | blocked
---

# HANDOFF — nome-do-repo-fork — YYYY-MM-DD

## FORK

`nome-do-repo-fork`

## DATA

YYYY-MM-DD

## CARD / TAREFA

AX — Título do card/tarefa

---

## CONTEXTO

> Background necessário para o agente do fork entender a situação antes de executar.
> Inclua: por que este card existe, qual problema resolve, decisões já tomadas.

---

## O QUE FOI FEITO AQUI (jhabib-2.0)

> Análise, decisões e preparação feitas nesta sessão no repo mestre.
> O agente do fork não precisa refazer este trabalho.

- [ ] Item analisado 1
- [ ] Item analisado 2

---

## O QUE PRECISA FAZER LÁ (fork)

> Lista concreta de ações a executar no repo do fork.
> Seja específico: arquivos a criar, comandos a rodar, código a escrever.

1. Ação 1 — `caminho/do/arquivo.py`
2. Ação 2 — `Makefile` target `make xxx`
3. Ação 3 — verificar em `http://localhost:PORT/rota`

---

## CRITÉRIO DE DONE

> Como saber que o card está concluído. Verificável sem ambiguidade.

- [ ] Critério 1
- [ ] Critério 2

---

## RETORNO ESPERADO

> O que deve voltar para `AGORA.md` do mestre quando concluído.
> Copie este bloco para AGORA.md ao confirmar conclusão.

```
fork-nome | Card AX concluído — [descrição do resultado]
```
