# 🤖 Portfólio de Agentes IA Conversacional — WhatsApp

> Ecossistema de agentes de inteligência artificial para atendimento, qualificação e prospecção de leads via WhatsApp, com integração a CRM, Google Agenda e APIs externas.

---

## 👨‍💻 Sobre

Este portfólio reúne 4 sistemas de agentes IA autônomos desenvolvidos para automatizar jornadas completas de relacionamento com leads no WhatsApp — desde a captação e qualificação até o agendamento de reuniões e atendimento farmacêutico especializado.

Cada sistema é composto por um **agente master** (responsável pela triagem e qualificação) e **subagentes** (responsáveis por ações específicas após a decisão do master). Todos os agentes possuem **integração nativa com CRM**, movendo os leads automaticamente entre etapas via sistema de tags.

---

## 🏗️ Arquitetura Geral

```
Lead entra (WhatsApp)
       │
       ▼
  Agente Master
  (Qualificação / Triagem)
       │
   ┌───┴───┐
   │       │
Qualificado  Desqualificado
   │             │
Subagente A   Subagente B
(Agendamento) (Fallback / Nutrição)
       │
   CRM atualizado via Tags automáticas
```

---

## 📦 Agentes do Portfólio

| # | Agente Master | Subagentes | Status | Cliente |
|---|---|---|---|---|
| 01 | [Lead ICP - Tráfego Pago](./agent-01-lead-icp-trafego-pago/) | 1 | Worker | Venda+ |
| 02 | [Atendimento Farmacêutico](./agent-02-atendimento-farmaceutico/) | — | Ativo | Venda+ |
| 03 | [Qualificação Leads - IA de Ligação](./agent-03-qualificacao-leads-ligacao/) | 2 | Worker | Venda+ |
| 04 | [Pré Qualificação - Prospecção Ativa](./agent-04-prospeccao-ativa-exactforce/) | 2 | Ativo | ExactForce |

---

## 🧰 Stack Tecnológica

| Tecnologia | Uso |
|---|---|
| **N8N** | Plataforma de automação e orquestração dos agentes |
| **WhatsApp** | Canal de comunicação principal |
| **LLM (Perfil Autônomo/Subautônomo)** | Motor de linguagem dos agentes IA |
| **RAG** | Base de conhecimento vetorial para respostas contextuais |
| **Google Agenda** | Agendamento automático de reuniões comerciais |
| **CRM Interno** | Gestão de pipeline com movimentação automática por tags |
| **API REST** | Consulta de estoque em tempo real (Farmácia) |
| **Sistema de Tags** | Gatilho de transição entre etapas e agentes |

---

## 🔁 Padrão de Design dos Agentes

Todos os agentes seguem um padrão arquitetural consistente:

1. **Entrada por Tag** — Lead é identificado e roteado via decisão por tags
2. **Agente IA Master** — Conduz a conversa de qualificação com perfil autônomo
3. **Tools disponíveis** — RAG, Extração de dados, Chats Antigos, CRM, Agenda
4. **Decisão** — Lead qualificado ou desqualificado
5. **Subagente ativado** — Cada resultado aciona um subagente especializado
6. **CRM atualizado** — Tags adicionadas/removidas automaticamente movem o lead no pipeline

---

## 📁 Estrutura do Repositório

```
ai-agents-portfolio/
├── README.md
├── agent-01-lead-icp-trafego-pago/
│   ├── README.md
│   ├── flow-master.png
│   ├── flow-config.json
│   └── subagents/
│       ├── sub-01-lead-qualificado/
│       │   ├── README.md
│       │   ├── flow.png
│       │   └── flow-config.json
├── agent-02-atendimento-farmaceutico/
│   ├── README.md
│   ├── flow-master.png
│   └── flow-config.json
├── agent-03-qualificacao-leads-ligacao/
│   ├── README.md
│   ├── flow-master.png
│   ├── flow-config.json
│   └── subagents/
│       ├── sub-01-lead-qualificado/
│       └── sub-02-lead-desqualificado/
└── agent-04-prospeccao-ativa-exactforce/
    ├── README.md
    ├── flow-master.png
    ├── flow-automacao-disparos.png
    ├── flow-config.json
    └── subagents/
        ├── sub-01-qualificado/
        └── sub-02-desqualificado/
```

---

## 📬 Contato

**Lucas Oliveira**
- Email: `lucassoliveira070@gmail.com`
- GitHub: lucasoliverdev-ai
