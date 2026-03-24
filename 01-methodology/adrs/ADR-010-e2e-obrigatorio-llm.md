---
id: ADR-010
title: e2e-obrigatorio-llm
status: ACCEPTED
superseded-by: ~
date: 2026-03-15
iso-ref: ~
tags: [adr]
audited: false
---

# ADR-010 — Teste E2E Obrigatório em Toda Story com LLM

**Origem:** OdooiA — generalizado para Jhabib 2.0

## Decisão

Toda story que tenha um LLM no caminho crítico exige teste E2E como critério de aceite, além de unit tests.

## Contexto

Na OdooiA FASE 11, o AgentRouter passou em 30 unit tests e falhou em produção porque o modelo `gemma:2b` não roteava intenções corretamente com 7 skills em simultâneo. Unit tests isolam componentes — quando um deles é um LLM local, o comportamento real só aparece com o modelo rodando no ambiente real.

Este padrão é recorrente: unit tests validam lógica determinística; LLMs são não-determinísticos e dependem do modelo específico, do prompt exato e do contexto de execução real.

## Critério de aceite obrigatório para stories com LLM

> "Smoke-test E2E com caso de uso demo executado e resultado registrado no card."

## Alternativas consideradas

- Apenas unit tests — rejeitado: não cobre qualidade de resposta do modelo no ambiente real
- Apenas E2E — rejeitado: unit tests ainda são necessários para isolar bugs determinísticos
- Mocks do LLM — rejeitado: mock não representa comportamento real do modelo

## Consequências

- Skill `llm-benchmark` é obrigatória antes de fechar qualquer story com novo modelo LLM
- Skill `smoke-test` deve incluir check E2E quando LLM está no caminho crítico
- Template de card deve incluir campo: "Teste E2E: descrição do resultado ou N/A"
- CI verde + unit tests passando **não substituem** validação E2E com o LLM real
