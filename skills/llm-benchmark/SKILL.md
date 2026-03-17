---
name: llm-benchmark
version: 0.1
status: stable
tags: [llm, benchmark, ollama, model-selection]
description: "Benchmarks a local LLM model against representative task examples before committing it to a component — prevents AP-003 (wrong model chosen by availability not fitness)."
origin: OdooiA retrospectiva FASE 11
---

# llm-benchmark — Validar Modelo LLM Antes de Commitar

> **Em uma frase:** Antes de usar um modelo LLM num componente crítico, executa 5 exemplos representativos da tarefa real e só avança se taxa de acerto ≥ 80%.

---

## Quando usar

- ✅ Ao escolher ou trocar o modelo LLM de um componente
- ✅ Ao receber bug report de "modelo responde errado"
- ✅ Antes de fechar story que envolve nova integração LLM
- ❌ Não usar para modelos de embedding (testar similaridade, não geração)

## Inputs

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|:-----------:|-----------|
| `task` | string | ✅ | Descrição da tarefa (ex: "intent routing com 7 opções") |
| `models` | string[] | ✅ | Modelos a comparar |
| `examples` | list | ✅ | 5 pares `{input, expected_output}` representativos |
| `success_criteria` | string | ❌ | Default: ≥ 4/5 corretos (80%) |

## Outputs

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `winner` | string | Modelo recomendado |
| `scores` | dict | `{modelo: N/5}` para cada modelo testado |
| `latencies_p50` | dict | Latência mediana por modelo em ms |
| `recommendation` | string | Usar / Trocar / Investigar |

## Critérios de Sucesso

- [ ] Mínimo 5 exemplos reais (não inventados) da tarefa
- [ ] Cada exemplo tem expected_output claro (não ambíguo)
- [ ] Latência medida no ambiente de runtime (não local do dev)
- [ ] Resultado registrado no card antes de fechar a story

---

## Implementação

### PASSO 1 — Montar 5 exemplos representativos

Para cada tarefa, cobrir os casos principais:
- Caso nominal (deveria funcionar claramente)
- Caso limite (input ambíguo ou edge)
- Caso negativo (input que NÃO deve acionar a feature)

### PASSO 2 — Executar benchmark

```python
import time

models = ["model-a", "model-b"]
examples = [
    {"input": "...", "expected": "..."},
    # ... 4 mais
]

for model in models:
    correct = 0
    latencies = []
    for ex in examples:
        start = time.time()
        # chamar o componente com o modelo
        elapsed = (time.time() - start) * 1000
        latencies.append(elapsed)
        # verificar se output bate com expected
    print(f"{model}: {correct}/5 | p50={sorted(latencies)[2]:.0f}ms")
```

### PASSO 3 — Registrar no card

Formato padrão:
```
LLM Benchmark — [tarefa]
model-a : 2/5 | p50=8.200ms  ❌
model-b : 4/5 | p50=4.100ms  ✅
→ Recomendado: model-b
```

### Anti-pattern que esta SKILL previne

→ AP-003: Modelo escolhido por disponibilidade, não por benchmark

---

## Changelog

| Versão | Data | Mudança |
|--------|------|---------|
| 0.1 | 2026-03-17 | Transferido do OdooiA — generalizado (sem refs Ollama-específicas) |
