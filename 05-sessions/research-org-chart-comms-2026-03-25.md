# Research: Org Chart & Internal Communication for AI-First Companies

**Date:** 2026-03-25
**Type:** Research (no action items)
**Context:** JHabib 2.0 — 1-person company with AI C-Level agents

---

## 1. Best Org Chart Models for a 1-Person + AI Agents Company

### The "Hub & Spoke" Model (Recommended for JHabib 2.0)
- **Human founder** at the center as the single decision authority and orchestrator
- **AI C-Level agents** as specialized spokes, each owning a domain (CTO, CFO, CPO, etc.)
- This mirrors what CIO.com calls the **"AI Agent Orchestrator"** role — the person who manages the fleet of AI agents, ensures they work in concert, and designs escalation paths when agents hit impasses

### Task-Based / Work-Based Model
- Per CIO.com (Sep 2025): "Rigid departmental silos are expected to break down. Instead of a fixed hierarchy, organizations may adopt more of a task-based or work-based model"
- Traditional fixed org charts are giving way to **dynamic, AI-enhanced versions** that provide "real-time guidance that adapts to changing conditions" (Functionly)
- AI-native startups can achieve $10M ARR with 15-20 people vs. 50-70 in traditional SaaS — a 1-person + AI model is the extreme version of this

### Holacracy-Inspired Circles (Hybrid Approach)
- Holacracy differentiates **roles from people** — one person can fill multiple roles
- Governance is distributed into **circles** (teams with specific functions)
- HBR's "Beyond the Holacracy Hype": self-management works best in fast-paced environments where quick adaptation is needed
- Leaner structures with fewer management layers drive **25% higher operational efficiency**
- **For JHabib 2.0:** Jean fills the "Founder/Orchestrator" role; each AI agent fills a C-Level role within its circle of competence. Decision authority flows through governance meetings (session logs)

### Recommended Structure for JHabib 2.0

```
                    ┌─────────────┐
                    │ Jean Habib  │
                    │  Founder /  │
                    │ Orchestrator│
                    └──────┬──────┘
                           │
        ┌──────┬───────┬───┴───┬───────┬──────┬──────┐
        │      │       │       │       │      │      │
      ┌─┴─┐ ┌─┴─┐  ┌──┴──┐ ┌─┴─┐  ┌──┴─┐ ┌─┴─┐ ┌─┴──┐
      │CTO│ │CPO│  │CMO  │ │CFO│  │COO │ │CRO│ │CISO│
      │AI │ │AI │  │AI   │ │AI │  │AI  │ │AI │ │AI  │
      └───┘ └───┘  └─────┘ └───┘  └────┘ └───┘ └────┘

      Each AI agent = autonomous within domain
      Escalation = always to Jean (single human authority)
```

---

## 2. Communication Flow Patterns

### From Sociis RH (Brazilian HR Best Practices)
- Internal communication includes ALL formal and informal information exchanges
- In small companies, communication responsibility falls on the administrator informally
- Key tools: async (Trello/Kanban, Conceptboard) + sync (Zoom/Google Meet)
- Two-way communication is critical — not just top-down broadcasts

### For AI-Agent Teams (Synthesis)
- **Decision flow:** AI agents analyze and recommend -> Jean approves/rejects -> AI agents execute
- **Escalation rule:** Any decision with financial impact, client-facing impact, or irreversibility escalates to Jean
- **Session logs** (05-sessions/) serve as the communication record — equivalent to meeting minutes
- **CLAUDE.md** serves as the standing operating procedure — equivalent to an employee handbook
- **AGORA.md** serves as real-time status dashboard — equivalent to a daily standup board

### Communication Channels Map

| Channel | Purpose | Direction | Frequency |
|---------|---------|-----------|-----------|
| CLAUDE.md | Strategy, rules, context | Jean -> Agents | Updated per session |
| AGORA.md | Real-time state | Bidirectional | Every session |
| Session logs | Decisions, retros | Agent -> Jean (review) | Per work session |
| Handoff docs | Cross-repo coordination | Jean <-> Fork agents | Per task |
| ADRs | Architectural decisions | Collaborative | As needed |
| C-Level consult | Domain expertise | Jean -> specific agent | On demand |

---

## 3. Documenting Roles, Responsibilities, and Decision Authority

### ISO 9001:2015 Clause 5.3 Requirements
- Organizations must develop and make available a **list of key personnel with job descriptions and responsibilities**
- An **organizational chart** of key employees as they relate to the QMS is required
- Each person must know who is responsible for each element of the management system
- Responsibilities and authorities must be **assigned and communicated** at all levels

### ISO 45001:2018 Clause 5.3 (Stricter)
- Same as ISO 9001 PLUS: responsibilities must be **maintained as documented information** (not just communicated)
- Top management remains **ultimately accountable** even when responsibility is delegated
- Communication methods: induction/training, position descriptions, organizational charts

### How JHabib 2.0 Already Complies
- **CLAUDE.md** = documented roles (C-Level Board table with ISO references)
- **ADRs** = documented decisions with authority
- **Session logs** = evidence of communication
- **Gap:** No formal "decision authority matrix" — see RACI/GRACI section below

---

## 4. Accountability Frameworks: RACI and GRACI

### Traditional RACI
- **R**esponsible — does the work
- **A**ccountable — ultimately answerable (only ONE person per task)
- **C**onsulted — provides input before work is done
- **I**nformed — kept in the loop

Per Yields.io: RACI is indispensable for AI governance — it defines ownership across the AI lifecycle (development, validation, deployment, audit). Key roles in AI RACI: AI Owner, Validator, Compliance Officer.

### GRACI Framework (Recommended for AI-First Orgs)
CIPH Lab's GRACI extends RACI with AI-specific dimensions:

| Letter | Meaning |
|--------|---------|
| R | Responsible — does the work |
| A | Accountable — ultimately answerable |
| C | Consulted — provides input |
| I | Informed — kept in the loop |
| **G** | **Governance — approves which AI tools can be used** |
| **V** | **Verification — validates AI output before approval** |
| **A2** | **AI-Assisted — human does task with AI support** |
| **A0** | **AI-Only — fully automated, no human intervention** |

### Why GRACI Matters
Without it:
- AI tools proliferate without clear governance ownership
- No verification step for AI outputs creates compliance risk
- Confusion about when human oversight is required vs. optional
- Accountability dissolves when things go wrong

### GRACI Applied to JHabib 2.0 (Example)

| Task | Jean (Founder) | AI CTO | AI CFO | AI CPO | Mode |
|------|---------------|--------|--------|--------|------|
| ADR creation | A, G, V | R | C | C | A2 |
| Financial projection | A, V | I | R | C | A2 |
| Product roadmap | A, G | C | C | R | A2 |
| Code in fork repos | A, G | I | I | I | Handoff |
| Session log | A | R | I | I | A2 |
| Client communication | R, A | I | I | C | Human-only |
| SKILL authoring | A, G, V | R | I | C | A2 |
| Risk assessment | A, V | C | R | I | A2 |

**Key insight:** Jean is ALWAYS Accountable (A) — AI agents are Responsible (R) within their domains. Jean holds Governance (G) and Verification (V) for all AI-generated outputs.

---

## 5. ISO Standards on Organizational Structure

### ISO 9001:2015 (Quality Management)
- **Clause 5.3:** Top management shall ensure roles, responsibilities and authorities are assigned, communicated, and understood
- Requires organizational chart + job descriptions
- Does NOT require documented information for roles (just communication)

### ISO 45001:2018 (Occupational Health & Safety)
- **Clause 5.3:** Same as ISO 9001 BUT requires **documented information** for roles
- Top management is ultimately accountable even with delegation
- Relevant for JHabib 2.0's anti-burnout rules (<=5h/week)

### ISO/IEC 42001 (AI Management System)
- Requires AI governance roles to be defined
- Risk management for AI systems must have clear ownership
- Human oversight requirements for AI decision-making

### ISO 56001 (Innovation Management)
- Supports flexible organizational structures for innovation
- Compatible with holacracy-style circles for R&D functions

### Compliance Summary for JHabib 2.0

| Requirement | Current State | Gap |
|-------------|--------------|-----|
| Roles documented | CLAUDE.md C-Level table | OK |
| Responsibilities assigned | CLAUDE.md + ADRs | OK |
| Org chart | Implicit in C-Level table | Formalize (see diagram above) |
| Decision authority matrix | Not explicit | Add GRACI matrix |
| Documented information (45001) | Session logs + ADRs | OK |
| AI governance roles (42001) | CTO + CISO defined | OK |
| Human oversight (42001) | Jean = always Accountable | OK |
| Anti-burnout (45001) | COO Daniel Santos monitors | OK |

---

## 6. Key AI-Native Roles from CIO.com (Reference)

Five new roles for the agentic era:

1. **AI Agent Orchestrator** — manages the fleet of AI agents, designs escalation paths, manages the "agent stack" (Jean's current role)
2. **Human-Agent Collaboration Designer** — designs workflows between humans and AI, ensures adoption and productivity (relevant for SDD methodology)
3. **AI Ethics & Governance Specialist** — establishes guardrails for agent behavior, audits decisions, ensures compliance (CISO Priya Nair's domain)
4. **AI Quality Assurance Engineer** — tests and validates AI agent behavior end-to-end (CTO Alex Chen's domain, per ADR-010)
5. **GTM Engineer** — replaces traditional sales/marketing ops with AI-driven automation (CMO Sofia Reyes + CRO Rafael Souza domain)

---

## Sources

- [Sociis RH — Guia Completo Comunicacao Interna](https://sociisrh.com.br/comunicacao-interna/)
- [CIO.com — The New Org Chart: AI-Native Roles in the Agentic Era](https://www.cio.com/article/4060162/the-new-org-chart-unlocking-value-with-ai-native-roles-in-the-agentic-era.html)
- [Yields.io — RACI Matrix: Defining Accountability in AI Governance](https://www.yields.io/blog/raci-matrix-ai-governance/)
- [CIPH Lab — GRACI: AI Governance Accountability Framework](https://www.ciph-lab.com/ai-governance-raci)
- [Holacracy.org — Holacracy vs Hierarchy vs Flat Orgs](https://www.holacracy.org/blog/holacracy-vs-hierarchy-vs-flat-orgs/)
- [ISO 9001 Checklist — Clause 5.3 Organizational Roles](https://www.iso-9001-checklist.co.uk/5.3-organizational-roles-responsibilities-and-authorities.htm)
- [ISO 45001 Checklist — Clause 5.3 Organizational Roles](https://www.iso-9001-checklist.co.uk/iso-45001/5.3-organizational-roles-responsibilities-and-authorities-iso-45001.htm)
- [Elevate Consult — AI Governance Operating Model & RACI](https://elevateconsult.com/insights/designing-the-ai-governance-operating-model-raci/)
- [Workvivo — Internal Comms for Scaling Tech Companies](https://www.workvivo.com/blog/internal-comms-for-scaling-tech-companies-guide/)
- [Slack — How to Build Internal Communications Strategy](https://slack.com/blog/collaboration/internal-communications-strategy)
- [MasterClass — Holacracy: Pros and Cons](https://www.masterclass.com/articles/holacracy)
- [Wrike — What is Holacracy?](https://www.wrike.com/blog/what-is-holacracy-and-will-it-work-in-my-company/)
