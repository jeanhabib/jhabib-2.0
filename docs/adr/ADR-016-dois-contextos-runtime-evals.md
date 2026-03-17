# ADR-016 — Runtime dos Evals: Dois Contextos Distintos

**Status:** Aceito
**Data:** 2026-03-16
**Origem:** OdooiA — generalizado para Jhabib 2.0

## Decisão

Os evals rodam em contextos diferentes dependendo do ambiente:

- **Local (dev):** `docker exec <container> python3 /mnt/tests/evals/` — dependências já instaladas no container
- **CI (GitHub Actions):** `python3 tests/evals/*.py` direto no runner — serviços live (LLM, VectorDB) fazem skip gracioso

## Contexto

O `make evals` original rodava `python3` no host. O host não tem as dependências necessárias instaladas. Os evals existem no container via volume montado. O CI é um runner limpo sem Docker Compose.

Tentar usar o mesmo comando em ambos os contextos resulta em erros silenciosos ou falsos positivos.

## Consequências

- `make evals` usa `docker exec <container>` localmente
- CI invoca `python3 tests/evals/*.py` direto no runner — sem `docker exec`
- Evals usam `main()` + `if __name__ == '__main__'` — não pytest
- Volume de tests é obrigatório no serviço principal do `docker-compose.yml`
- `make doctor` não checa dependências Python do host — container é o ambiente canônico

## Handoff obrigatório

Todo handoff que inclua execução de evals deve especificar:
> "Rodar localmente via `docker exec` — CI roda direto no runner sem docker exec."

## Alternativas consideradas

- Instalar dependências no host — rejeitado: viola AP-NEW-001 (pip no host)
- Usar sempre docker exec (inclusive no CI) — rejeitado: CI runners não têm containers rodando
- Pytest no container — rejeitado: overhead de setup, evals são scripts independentes
