# 📅 Subagente 03.1 — Lead Qualificado · IA de Ligação

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Worker
**Ativado por:** Agente Master `30794` quando lead é qualificado

---

## Objetivo

Receber o lead qualificado e conduzir o agendamento de reunião diretamente no Google Agenda da área comercial, com confirmação automática via WhatsApp.

---

## Fluxo do Subagente

```
Início
  │
  ▼
Remover Tags (reset de estado)
  │
  ▼
Decisão por Tags (tag: lead-qualificado)
  │                         │
  ▼                         ▼
Agente IA (Autônomo)    Finalizar Atendimento
  │
  ├── Agenda (Google Agenda)
  ├── Adicionar tag
  ├── Chats de Atendimentos Antigos
  └── Extrair Dados da conversa
  │
  ▼
Decisão por Tags (tag: lead-agendado)
  │                         │
  ▼                         ▼
Split                   ELSE (Padrão)
  │
  ├── Mensagem Predefinida (Confirmação) → Delay → Remover Tags → Finalizar
  └── Delay → Digitando → Mensagem de Texto → Finalizar
```

### Mensagem Predefinida de Confirmação
> *"Perfeito! Agendado! Vou passar para o Guilherme um resumo do que você me contou para a conversa já começar mais objetiva. Agendado então {{primeiro_nome}}, até lá!"*

### Tools do Agente IA
| Tool | Função |
|---|---|
| Agenda | Cria evento no Google Agenda da área comercial |
| Adicionar tag | Marca lead como `lead-agendado` |
| Chats de Atendimentos Antigos | Contexto de interações anteriores |
| Extrair Dados da conversa | Captura preferência de horário e dados finais |

---

## Integração CRM

- Tag `lead-agendado` adicionada ao confirmar reunião
- Lead movido para coluna "Reunião Agendada" no CRM
- Tags anteriores removidas ao iniciar subagente

---

## Resultado esperado

- Reunião criada no Google Agenda com briefing do lead
- Lead notificado com confirmação personalizada
- CRM atualizado automaticamente
