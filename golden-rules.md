---
id: GOLDEN-RULES
title: golden-rules
status: active
tags: [methodology, rules, canonical]
iso-ref: ISO 9001, ISO 45001, ISO/IEC 27001, ISO/IEC 42001
created: 2026-03-25
---

# 10 Golden Rules — SDD by JHabib

> Fonte canônica: [[SDD]] § 10 Regras
> Governança: C-Level Board

Regras consolidadas e invioláveis. Aplicam-se ao repo mestre **e** a todos os forks.

---

## As 10 Regras

### 1. Revenue > Produto > Método > Admin
Hierarquia de prioridade inviolável. Alocação semanal: 3h Revenue · 1h Método · 1h Admin.

### 2. Spec antes de código
Sem spec, nenhuma ação. SDD Express conta como spec (spec-lite). → [[SDD]]

### 3. Evidence = done means proven
"Parece funcionar" não é evidence. Critério observável, mensurável. → ISO/IEC 25010

### 4. ≤5h/semana + sem trabalho após 22h
Anti-burnout inviolável. COO Daniel Santos monitora. → ISO 45001

### 5. Privacy First
Ollama > cloud quando possível. Dados sensíveis nunca em LLMs cloud sem DPA. → ISO/IEC 27001

### 6. Runtime-agnostic
SKILLs funcionam em qualquer agente (Claude Code, Continue.dev, Cursor, etc.). Sem vendor lock-in.

### 7. Boundary rule
JHabib 2.0 nunca executa código em repos de forks. Handoffs via `05-sessions/handoffs/`. → [[ADR-019-jhab20-studio-framework|ADR-019]]

### 8. Spike antes de setup
Prove que funciona antes de montar infra. POC > Architecture Astronaut.

### 9. Código é fonte de verdade
Se não está no GitHub, não existe. Git > Obsidian > Notion > conversa.

### 10. Nunca vibe coding
Sem "experimentos rápidos" em produção. Spec → execute → evidence → retro.

---

## Enforcement

| Regra | Quem monitora | Quando |
|-------|--------------|--------|
| 1 (Revenue) | CFO Marcus Lima | Alocação semanal |
| 2-3 (Spec/Evidence) | CTO Alex Chen | Toda PR |
| 4 (Anti-burnout) | COO Daniel Santos | Toda sessão |
| 5 (Privacy) | CISO Priya Nair | Toda integração LLM |
| 6 (Runtime) | CTO Alex Chen | Toda SKILL nova |
| 7 (Boundary) | COO Daniel Santos | Todo handoff |
| 8-10 (Dev) | CTO Alex Chen | Todo commit |
