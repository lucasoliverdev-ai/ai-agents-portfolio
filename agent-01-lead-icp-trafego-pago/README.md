# 🎯 Agent 01 — Lead ICP · Tráfego Pago

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Worker · **ID:** `27072`

---

## Objetivo

Receber leads capturados via formulários de tráfego pago, conduzir um processo de qualificação autônomo via WhatsApp e tomar a decisão de qualificar ou desqualificar o lead — encaminhando leads qualificados para agendamento de reunião com a área comercial.

---

## Fluxo do Agente Master

```
Início
  │
  ▼
Decisão por Tags (tag: leadicp-leadforms)
  │                        │
  ▼                        ▼
Agente IA (Autônomo)    Finalizar atendimento
  │
  ├── Extrair dados da conversa (x4)
  ├── Chats de Atendimentos Antigos
  ├── Transferir para outra Estratégia de Agente (x2)
  ├── Add Tags
  │
  ▼
Delay → Enviar mensagem de Texto
  │
  ▼
Lead Qualificado → Subagente 01
```

### Tools do Agente IA
| Tool | Função |
|---|---|
| Extrair dados da conversa | Captura informações-chave do lead durante a conversa |
| Chats de Atendimentos Antigos | Contexto de interações anteriores do lead |
| Transferir para outra Estratégia | Roteamento para subagente correto |
| Add Tags | Atualiza status do lead no CRM automaticamente |

---

## Integração CRM

- Tags adicionadas automaticamente conforme avanço do lead
- Pipeline do CRM atualizado em tempo real sem intervenção humana

---

## Subagentes

| Subagente | Condição de Ativação | Arquivo |
|---|---|---|
| Lead Qualificado ICP | Lead aprovado na qualificação | [→ ver subagente](./subagents/sub-01-lead-qualificado/) |

---

## Resultado esperado

- Lead qualificado → reunião agendada automaticamente no Google Agenda
- Lead não qualificado → atendimento finalizado com tag de desqualificação
