---
name: security-scan
version: 0.1
status: stable
tags: [security, red-teaming, owasp, pre-merge]
description: "Varredura de segurança no PR antes do merge: credenciais expostas, injeção de prompt, SQL injection, endpoints sem auth. Finding crítico = bloqueante."
disable-model-invocation: true
user-invocable: true
origin: OdooiA Sprint 1
---

# security-scan — Varredura de Segurança Pré-Merge

Protege o sistema contra vulnerabilidades comuns antes do merge do PR.

## Verificações obrigatórias

### 1. Credenciais expostas

```bash
# Chaves de API, tokens, senhas hardcoded
grep -r "api_key\s*=\|sk_live\|sk_test\|password\s*=\s*['\"]" <src_path>/ \
  --include="*.py" --include="*.js" --include="*.ts" | grep -v "test_\|\.pyc\|example"
```

### 2. Injeção de prompt (se LLM no caminho crítico)

```bash
# Verificar que inputs do usuário são sanitizados antes de chegar ao LLM
grep -rn "user_input\|request\.data\|params\[" <src_path>/ | grep -i "prompt\|message\|query"
# Confirmar que há sanitização/validação antes do uso
```

### 3. SQL / query injection

```bash
# Queries raw sem sanitização (adaptar para o ORM do projeto)
grep -rn "raw_query\|execute(\|query(" <src_path>/ | grep -v "#\|test_"
```

### 4. Endpoints internos de IA sem autenticação

```bash
# Verificar que endpoints de LLM/banco vetorial não estão expostos externamente
# Para projetos Docker: confirmar que serviços de IA ficam na rede interna
docker network ls
# Confirmar que portas de LLM/VectorDB não estão em 0.0.0.0
```

### 5. Dependências com vulnerabilidades conhecidas (Trivy)

```bash
# Se Trivy disponível
trivy fs . --severity HIGH,CRITICAL --exit-code 1
```

## Critério de aprovação

- Zero credenciais hardcoded no diff do PR
- Zero injeção de prompt: inputs do usuário sanitizados antes do LLM
- Zero raw SQL sem sanitização em código novo
- Endpoints de IA isolados na rede interna
- Trivy: zero findings CRITICAL (HIGH: registrar mas não bloquear)

**Finding crítico = bloqueante. Ciclo não avança para QA.**

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA Sprint 1 — generalizado (sem refs Giskard/TEF) |
