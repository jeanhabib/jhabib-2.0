# ADR-008 — Dois Planos: Toolchain de Desenvolvimento vs Stack do Produto

**Status:** Aceito
**Data:** 2026-03-15
**Origem:** OdooiA — generalizado para Jhabib 2.0

## Decisão

Projetos Jhabib 2.0 operam com dois planos arquiteturais completamente separados que nunca se misturam em produção.

## Contexto

Existe confusão recorrente entre o stack usado para **construir** o produto e o stack que **roda** o produto em produção. São mundos distintos com requisitos distintos.

## Os Dois Planos

### Plano 1 — Toolchain de Desenvolvimento (AI-first)

- Desenvolvedor usa Claude Code / Continue.dev / Cursor para escrever código
- Skills e prompts ensinam a IA a gerar código correto para o projeto
- Este plano pode usar APIs cloud (Claude API, Notion MCP, etc.) — é a máquina do dev, não o produto
- Metodologia: SDD — Spec-Driven Development (Jhabib 2.0)

### Plano 2 — Stack do Produto (cliente-first)

- O que roda no ambiente do cliente: depende dos requisitos do projeto
- Definido pelo cliente, pelo ADR-001 do projeto e pelos requisitos de negócio
- Pode ser on-premise, cloud, híbrido — decide-se projeto a projeto
- Se dados sensíveis: verificar LGPD e requisitos de privacidade

## Consequências

- Nunca adicionar dependências da toolchain de dev no código do produto
- Skills do Claude são artefatos de desenvolvimento, não parte do produto
- Cada projeto define seu Plano 2 em ADR-001 (arquitetura do produto)
- A configuração do Plano 1 (`.claude/`, `continue/`, etc.) vai para o repositório de desenvolvimento
