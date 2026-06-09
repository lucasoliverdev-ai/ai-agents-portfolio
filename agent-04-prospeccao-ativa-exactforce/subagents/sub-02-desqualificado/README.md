# 🔚 Subagente 04.2 — Desqualificado · ExactForce

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Worker
**Ativado por:** Agente Master quando lead não é qualificado na prospecção ativa

---

## Objetivo

Receber o lead desqualificado, agradecer o interesse de forma personalizada e encerrar o atendimento de maneira respeitosa — removendo o lead do fluxo ativo e atualizando o CRM.

---

## Fluxo do Subagente

```
Início
  │
  ▼
Agente IA (Perfil Autônomo)
  │
  └── Chats de Atendimentos Antigos
  │
  ▼
Split
  ├── Enviar mensagem de Texto (agradecimento)
  └── Delay → Remover Tags → Add Tags → Finalizar Atendimento
```

### Tools do Agente IA
| Tool | Função |
|---|---|
| Chats de Atendimentos Antigos | Contexto de interações anteriores para personalizar encerramento |

---

## Integração CRM

- Tags de prospecção ativa removidas
- Tags de desqualificação adicionadas
- Lead saí do funil ativo e é segmentado para nutrição futura

---

## Resultado esperado

- Lead encerrado com mensagem de agradecimento personalizada
- Lead removido do fluxo de prospecção ativa
- CRM atualizado com status de desqualificação
- Lead disponível para reengajamento futuro via outras campanhas
