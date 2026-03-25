# Anti-Patterns — Jhabib 2.0

Padrões que causaram problemas reais em projetos. Cada entrada tem regra clara de evitar.

Origem: transferência de knowhow OdooiA → Jhabib 2.0 (Sprint 2, 2026-03).
Para anti-patterns com contexto Odoo-específico, ver repositório OdooiA.

---

## AP-001 — Unit Tests Sem E2E Criam Falsa Segurança de QA

**Detectado em:** OdooiA FASE 11 (AI Skills Registry)
**Impacto:** Crítico — bugs de integração descobertos pós-entrega; intent routing quebrado descoberto semanas depois

**Problema:**
30 unit tests passavam para o AgentRouter. O teste E2E com a pergunta demo real ("Qual o prato mais vendido?") só foi executado no Sprint 1. O modelo nunca foi testado com o prompt real + todas as skills + pergunta demo em conjunto.

**Regra:**
> Toda story que implementa um componente de IA (Agent Router, RAG, Skill) deve incluir obrigatoriamente um teste E2E com o caso de uso real antes de fechar a story. Unit tests são condição necessária mas não suficiente.

**Como aplicar:**
- Na Definição de Done: "Smoke-test com caso de uso real executado e resultado registrado no card"
- Se o ambiente não estiver disponível: registrar explicitamente como dívida técnica, não silenciar

---

## AP-002 — Dependência de Infraestrutura Implícita Sem Critério de Aceite

**Detectado em:** OdooiA FASE 11 (ChromaDB ausente do docker-compose)
**Impacto:** Alto — serviço crítico offline desde o início; descoberto em demo ao vivo

**Problema:**
A decisão arquitetural documentava "ChromaDB precisa estar no docker-compose" mas nenhuma story tinha como critério de aceite "o serviço X sobe com docker compose up". Foi adicionado só depois de uma demo falhar.

**Regra:**
> Se uma feature depende de um serviço externo (banco vetorial, LLM, cache, MQ), o critério de aceite deve incluir: "O serviço X é declarado no docker-compose e verificado pelo env-doctor antes do merge."

**Como aplicar:**
- Ao criar stories com novos serviços: adicionar critério explícito no card
- env-doctor deve listar todos os serviços *esperados* pela feature, não apenas os existentes

---

## AP-003 — Modelo LLM Escolhido Por Disponibilidade, Não Por Benchmark

**Detectado em:** OdooiA FASE 11 → Sprint 1
**Impacto:** Alto — modelo padrão falhou em tarefa crítica; descoberto em demo

**Problema:**
`gemma:2b` foi usado como LLM padrão porque estava disponível. Nunca foi benchmarked para a tarefa específica. Sprint 1 revelou falha sistemática na tarefa de classificação de intenção.

**Regra:**
> Antes de commitar um modelo LLM para um componente crítico, executar benchmark mínimo com 5 exemplos representativos. Registrar resultado no card. Se falhar em > 20% dos casos: trocar o modelo antes de fechar a story.

**Como aplicar:**
- Usar skill `llm-benchmark` antes de qualquer story com novo modelo LLM
- Critério de aceitação de modelo: > 80% de acerto nos 5 exemplos representativos

---

## AP-004 — Dados de Demo Não São Parte Do Módulo

**Detectado em:** OdooiA Sprint 1
**Impacto:** Médio — demo falhou em ambiente fresh por falta de dados transacionais

**Problema:**
O módulo foi entregue sem demo data. A demonstração dependia de dados reais no banco. Em ambiente fresh (novo cliente, UAT, CI), não há dados — resultado: resposta vazia ou "não tenho informações".

**Regra:**
> Todo módulo que depende de dados transacionais para demonstrar valor deve incluir dados de demo mínimos para que a feature principal funcione num ambiente fresh sem configuração manual.

**Como aplicar:**
- Na Definição de Done: "Feature funciona em ambiente limpo com apenas `docker compose up && instalar módulo`"
- Scripts de seed externos são para desenvolvimento — demo data é para produção/UAT

---

## AP-005 — Ciclo SDD Rodado Depois Do Código, Não Antes

**Detectado em:** OdooiA Sprint 1 (bugs demo cycle)
**Impacto:** Crítico — FASE 4 e FASE 7 executadas retroativamente; normalizou comportamento errado

**Problema:**
Bugfixes foram implementados diretamente sem invocar o orchestrator. Fases de segurança e fechamento de Kanban foram feitas retroativamente. Se não questionado, teria ficado sem fechar.

**Regra:**
> "Próximo ciclo" é a única entrada para implementação. Nenhuma linha de código é escrita sem o card no estado "In Progress". Se a urgência parecer justificar pular o processo, é sinal de que o card foi mal estimado — não de que o processo deve ser ignorado.

**Como aplicar:**
- Criar o card primeiro (30 segundos), depois implementar
- CLAUDE.md ou equivalente deve documentar esta regra

---

## AP-NEW-001 — `pip install` Solto no Host Viola Runtime Canônico

**Detectado em:** OdooiA múltiplos ciclos
**Impacto:** Alto — dependências no host não replicáveis em CI, container ou outros devs

**Problema:**
Dependências instaladas com `pip install` diretamente no host (fora do container) funcionam localmente mas quebram no CI e na máquina de outros colaboradores. O container é o ambiente canônico — fora dele, nada é garantido.

**Regra:**
> Nunca instalar dependências Python diretamente no host. Toda dependência nova vai para `requirements.txt` → `requirements.lock` via `uv pip compile`. CI usa o lock file.

**Como aplicar:**
- Se precisar testar uma lib nova: adicionar ao `requirements.txt`, rodar `uv pip compile`, instalar no container
- Lock file é gerado automaticamente — nunca editar manualmente

---

## AP-NEW-002 — `docker exec` no CI Sem Container em Execução

**Detectado em:** OdooiA múltiplos ciclos de CI
**Impacto:** Alto — CI falha com "container not found" de forma não-óbvia

**Problema:**
Comandos `docker exec <container>` no CI assumem que o container já está rodando. Em runners limpos de CI (GitHub Actions), os containers não sobem automaticamente — o script de CI precisa fazer `docker compose up` explicitamente antes do `exec`.

**Regra:**
> Todo `docker exec` no CI deve ser precedido de um `docker compose up -d <serviço>` no mesmo job. Nunca assumir que containers estão rodando num runner limpo.

**Como aplicar:**
- Verificar todo `docker exec` no `ci.yml` — cada um deve ter `docker compose up` correspondente no job
- Alternativa: usar comandos que não dependem de container ativo (ex: `python3` direto no runner)

---

## AP-NEW-003 — Fechar Card no Notion Antes do Merge Confirmado

**Detectado em:** OdooiA múltiplos ciclos
**Impacto:** Médio — Kanban desincronizado com realidade; métricas de velocity infladas

**Problema:**
Card movido para "Done" no Notion antes do PR ser mergeado. Se o PR for rejeitado ou revertido, o Kanban fica incorreto e as métricas de velocity ficam infladas.

**Regra:**
> O card só vai para "Done" após o merge confirmado no GitHub. A sequência correta é: PR aberto → CI verde → aprovado → mergeado → **então** card fechado.

**Como aplicar:**
- `sprint-cycle` deve verificar merge antes de mover o card
- Nunca usar "update properties Done" como gatilho de "abri o PR"

---

## AP-NEW-004 — Gerar Handoff Sem Ler a Skill Primeiro (Vibe Coding)

**Detectado em:** OdooiA múltiplos ciclos
**Impacto:** Alto — handoff incorreto, skill rodada com contexto errado, retrabalho

**Problema:**
Handoff gerado "de cabeça" sem ler o SKILL.md correspondente. A skill pode ter pré-condições, inputs obrigatórios e restrições que não são óbvias. Gerar handoff sem lê-la cria handoffs incompletos ou incorretos.

**Regra:**
> Antes de gerar o Handoff Context para uma skill, ler o SKILL.md completo. Nunca assumir que você sabe o que a skill faz — leia sempre.

**Como aplicar:**
- Orchestrator: antes de passar contexto para uma skill, ler o SKILL.md dela
- Se a skill não tem SKILL.md: criar antes de invocar

---

## AP-NEW-005 — Assumir Path de Arquivo Dentro do Container Sem Verificar Volumes

**Detectado em:** OdooiA múltiplos ciclos
**Impacto:** Médio — scripts que "funcionam localmente" falham no container por path incorreto

**Problema:**
Código assume que `/path/to/file` no host mapeia para o mesmo path dentro do container. Volumes Docker podem mapear caminhos diferentes. Um arquivo em `./tests/evals/` no host pode ser `/mnt/tests/evals/` dentro do container — ou não estar montado.

**Regra:**
> Antes de usar um path dentro de um container (via `docker exec`), verificar o `docker-compose.yml` para confirmar o mapeamento de volumes. Nunca assumir que host path == container path.

**Como aplicar:**
- Documentar paths de volume no SKILL.md de cada skill que usa `docker exec`
- Ao escrever scripts: parametrizar paths, não hardcodar

---

*Última atualização: 2026-03-17 — Transferência OdooiA → Jhabib 2.0 (Sprint 2)*
