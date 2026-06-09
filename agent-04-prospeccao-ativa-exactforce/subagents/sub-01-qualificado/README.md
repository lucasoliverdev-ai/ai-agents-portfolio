# 📅 Subagente 04.1 — Qualificado · ExactForce

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Worker
**Ativado por:** Agente Master quando lead é qualificado na prospecção ativa

---

## Objetivo

Receber o lead qualificado e conduzir o agendamento de reunião diretamente no Google Agenda da área comercial, com confirmação e briefing automático via WhatsApp.

---

## Fluxo do Subagente

```
Início
  │
  ▼
Agente IA (Perfil Autônomo)
  │
  ├── Agenda (Google Agenda)
  ├── Tansferir para Fila de Atendimento
  ├── RAG
  ├── Chats de Atendimentos Antigos
  └── Extrair dados da conversa
  │
  ▼
Roteador (6 - Roteador)
  ├── Condição: Após validar se o lead enviou...
  │     │
  │     ▼
  │   Delay → Enviar mensagem de Texto → Finalizar Atendimento
  │
  └── ELSE (Padrão)
        │
        ▼
      Remover Tags → Add Tags → Finalizar Atendimento
```

### Tools do Agente IA
| Tool | Função |
|---|---|
| Agenda | Cria evento no Google Agenda da área comercial |
| Transferir para Fila de Atendimento | Escalada para atendente humano se necessário |
| RAG | Base de conhecimento para dúvidas finais do lead |
| Chats de Atendimentos Antigos | Histórico de interações anteriores |
| Extrair dados da conversa | Captura dados finais e preferência de horário |

---

## Integração CRM

- Tags removidas e readicionadas conforme resultado do agendamento
- Lead movido para coluna "Reunião Agendada" no pipeline do CRM
- Briefing da conversa encaminhado automaticamente para o comercial

---

## Resultado esperado

- Reunião agendada no Google Agenda com dados do lead
- Lead notificado com confirmação via WhatsApp
- Equipe comercial notificada com contexto da conversa
- CRM atualizado automaticamente
