---
name: nist-audit
version: 0.1
status: stable
tags: [security, governance, nist, ai-rmf, compliance]
description: "Auditoria NIST AI RMF (Transparência, Segurança, Robustez, Governança) para sistemas de IA. Obrigatório para Edge AI e dados biométricos/sensíveis."
disable-model-invocation: true
user-invocable: true
argument-hint: "nome-do-modulo | all"
origin: OdooiA Sprint 1
---

# nist-audit — Auditoria NIST AI RMF

Guardião do framework de risco. Assegura que cada funcionalidade de IA nasce com os requisitos de confiança necessários.

## Critério 1 — Transparência (GOVERN-1): Rastreabilidade

Verificar que o sistema de IA possui instrumentação de observabilidade:

```bash
# Traces OTEL ativos
curl -s -o /dev/null -w "%{http_code}" http://localhost:6006      # Phoenix ativo → 200
nc -z localhost 4317 && echo "PASS" || echo "FAIL"                # gRPC endpoint

# Código instrumentado (adaptar para o projeto)
grep -r "opentelemetry\|tracer\|otel" <src_path>/
```

✅ PASS: Observabilidade ativa + código instrumentado
⚠️ WARN: Observabilidade ativa mas sem instrumentação no módulo
❌ FAIL: Sem observabilidade

## Critério 2 — Segurança (MAP-2): Proteção contra manipulação

```bash
# Verificar credenciais expostas no PR
grep -r "api_key\|password\s*=\s*['\"]" <src_path>/ --include="*.py" | grep -v "test_"

# Verificar injeção via queries sem sanitização (adaptar para stack)
grep -rn "raw_query\|execute(" <src_path>/

# Red teaming de prompts (se LLM no caminho crítico)
# Executar script de testes adversariais específico do projeto
```

## Critério 3 — Robustez (MEASURE-2): Cobertura de testes

```bash
# Cobertura de testes (adaptar para o projeto)
python -m pytest <test_path>/ -v --tb=short 2>&1 | tail -20
```

Meta: superar linha de base do projeto. Novos testes devem cobrir casos adversariais.

## Critério 4 — Governança de Dados (GOVERN-3): Privacidade e LGPD

Para módulos com Edge AI ou dados biométricos: verificar que dados sensíveis são anonimizados antes de persistir. **Obrigatório — sem exceção.**

```bash
# Verificar anonimização (adaptar para o projeto)
grep -rn "anonymize\|hash\|mask" <src_path>/ | grep -i "biometric\|face\|image"
```

## Relatório final

Gerar relatório `nist_audit_<modulo>_<data>.md` com:
- Resultado de cada critério (PASS / WARN / FAIL)
- Evidências (output dos comandos)
- Ação recomendada para cada FAIL

**Finding crítico = bloqueante. Ciclo não avança para QA.**

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA Sprint 1 — generalizado (sem refs módulos Odoo) |
