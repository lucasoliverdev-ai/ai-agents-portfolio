# 🚀 Agent 04 — Pré Qualificação · Prospecção Ativa (ExactForce)

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Ativo · **Cliente:** ExactForce

---

## Objetivo

Receber leads de campanhas de prospecção ativa via WhatsApp, conduzir o processo de pré-qualificação autônoma e encaminhar para o subagente correto conforme resultado — agendando reunião para qualificados ou encerrando com lead desqualificado.

---

## Contexto do Funil

Este agente é parte de um sistema de prospecção ativa estruturado em sequências de disparos:

```
Fluxo de Automação de Disparos (Prospecção Ativa)
  │
  ├── Sequências de disparo por lote (abr26-1 a abr26-10)
  │   Volumes: 19, 20, 20, 20, 20, 20, 37, 62, 43, 45 leads
  │
  └── Lead responde ao disparo demonstrando interesse
          │
          ▼
   Agente Master 04 (WhatsApp)
   Pré-qualificação completa
          │
     ┌────┴────┐
     │         │
Qualificado  Desqualificado
     │              │
Subagente 4.1   Subagente 4.2
(Agendamento)  (Encerramento)
```

### Fluxo de Automação de Disparos
- **Estratégia:** Sequências de mensagens por lotes diários de leads
- **Tags de entrada:** `prospec-conectado` (interesse confirmado) ou `leadqualificado-prospeccaoativa` (desqualificado)
- **Lotes rastreados:** 10 sequências identificadas (abr26-1 a abr26-10) com métricas por lote

---

## Fluxo do Agente Master

```
Início
  │
  ▼
Decisão por Tags (tag: lead-prospeccaoativa)
  │                         │
  ▼                         ▼
Add Tags               Finalizar Atendimento
  │
  ▼
Remover Tags (reset)
  │
  ▼
Agente IA (Perfil Autônomo)
  │
  ├── Chats de Atendimentos Antigos
  ├── Transferir para outra Estratégia de Agente (x2)
  ├── RAG (x3)
  ├── Transferir para outra Estratégia de Agente (x2 — com RAG)
  ├── Add Tags (x2)
  └── Extrair dados da conversa (x3)
  │
  ▼
Enviar mensagem de Texto
```

### Tools do Agente IA
| Tool | Função |
|---|---|
| Chats de Atendimentos Antigos | Histórico de interações anteriores do lead |
| Transferir para outra Estratégia (x4) | Roteamento para subagentes conforme decisão |
| RAG (x3) | Base de conhecimento: produto, empresa e argumentos de prospecção |
| Add Tags (x2) | Atualização de status no CRM |
| Extrair dados da conversa (x3) | Captura dados relevantes durante a qualificação |

---

## Integração CRM

- Tags adicionadas na entrada para identificar origem (prospecção ativa)
- Tags removidas e resetadas ao iniciar qualificação
- Pipeline atualizado conforme avanço do lead
- Rastreabilidade por lote de disparo (abr26-N)

---

## Subagentes

| Subagente | Condição de Ativação | Arquivo |
|---|---|---|
| Qualificado - ExactForce | Lead aprovado na pré-qualificação | [→ ver subagente](./subagents/sub-01-qualificado/) |
| Desqualificado - ExactForce | Lead reprovado na pré-qualificação | [→ ver subagente](./subagents/sub-02-desqualificado/) |
