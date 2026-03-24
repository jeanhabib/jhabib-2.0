---
fork: food-service-ai-ops-v2
data: 2026-03-24
card: A2 — Modo demo EPI Vision
status: pending
---

# HANDOFF — food-service-ai-ops-v2 — 2026-03-24

## FORK

`food-service-ai-ops-v2`

## DATA

2026-03-24

## CARD / TAREFA

A2 — Modo demo EPI Vision

---

## CONTEXTO

O RTSP está bloqueado: Felipe ainda não forneceu as credenciais de acesso às câmeras do Jakaru Food Park. Sem o stream real, o pipeline EPI Vision não pode ser demonstrado em produção.

A call com Felipe (A3) está agendada para esta semana. Precisamos de um **modo demo** que mostre o dashboard EPI funcionando com dados simulados, permitindo que Jean conduza a demo sem depender do RTSP.

---

## O QUE FOI FEITO AQUI (jhabib-2.0)

- Agente analisou o código do fork e identificou que o pipeline EPI Vision já tem suporte a mock embutido:
  - `api/app/services/epi_pipeline.py` contém o método `_mock_detect()` pronto para uso
  - A API é image-based: `POST /api/epi/detect` (não depende de streaming RTSP)
  - Dashboard está em `frontend/app/epi/`
- Decisão: criar script de seed que popula dados via API existente, sem modificar o fluxo de produção

---

## O QUE PRECISA FAZER LÁ (fork)

1. Criar `scripts/demo_epi.py`:
   - Registrar 3 câmeras demo (nomes sugestivos: "Caixa", "Entrada", "Cozinha")
   - Gerar 20 detecções via `POST /api/epi/detect` usando imagens mock ou base64 placeholder
   - Usar `_mock_detect()` do pipeline — não criar nova lógica de detecção

2. Adicionar target no `Makefile`:
   ```makefile
   demo-epi:
       @echo "Populando dados demo EPI Vision..."
       python scripts/demo_epi.py
       @echo "Demo pronto. Acesse: http://localhost:3000/epi"
   ```

3. Verificar que `make demo-epi` funciona do zero (sem estado anterior)

---

## CRITÉRIO DE DONE

- [ ] `make demo-epi` executa sem erros
- [ ] Dashboard `http://localhost:3000/epi` exibe 3 câmeras e ≥20 detecções
- [ ] Fluxo de produção (RTSP real) não foi modificado
- [ ] Jean consegue abrir o dashboard e conduzir a demo sem explicações técnicas adicionais

---

## RETORNO ESPERADO

Quando concluído, atualizar `AGORA.md` do mestre:

```
food-service-ai-ops-v2 | A2 concluído — demo disponível via make demo-epi
```
