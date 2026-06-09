# 📅 Subagente 01.1 — Lead Qualificado ICP · Tráfego Pago

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Worker · **ID:** `27073`
**Ativado por:** Agente Master `27072` quando lead é qualificado

---

## Objetivo

Receber o lead qualificado pelo agente master e conduzir o processo de agendamento de reunião diretamente no Google Agenda da área comercial, confirmando o horário via WhatsApp.

---

## Fluxo do Subagente

```
Início
  │
  ▼
Agente IA (Autônomo)
  │
  ├── Agenda (Google Agenda)
  ├── Extrair dados da conversa
  ├── Chats de Atendimentos Antigos
  │
  ▼
Roteador (6 - Roteador)
  ├── Condição: Lead já escolheu o horário
  │     │
  │     ▼
  │   Delay → Enviar mensagem de Texto → Finalizar atendimento
  │
  └── ELSE (Padrão)
        │
        ▼
      Split
        ├── Delay → Mensagem predefinida (confirmação de agendamento) → Finalizar
        └── Delay → Add Tags → Remover Tags → Finalizar
```

### Mensagem Predefinida de Confirmação
> *"Perfeito! Vou agendar aqui. A reunião será com o Thauan, nosso especialista em varejo de ghai. Ele vai entrar em contato com você par... Nosso DDD é 71 então fica atento ao celurar... Agendado então {{primeiro_nome}}, até lá!"*

### Tools do Agente IA
| Tool | Função |
|---|---|
| Agenda | Cria evento diretamente no Google Agenda da área comercial |
| Extrair dados da conversa | Captura preferência de horário e dados do lead |
| Chats de Atendimentos Antigos | Contexto de interações anteriores |

---

## Integração CRM

- Tags atualizadas ao confirmar agendamento
- Lead movido para coluna "Reunião Agendada" no pipeline do CRM

---

## Resultado esperado

- Reunião criada automaticamente no Google Agenda da área comercial
- Lead notificado via WhatsApp com confirmação e informações do especialista
- CRM atualizado com status de agendamento
