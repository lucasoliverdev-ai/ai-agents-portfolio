# 📞 Agent 03 — Qualificação de Leads · IA de Ligação

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Ativo · **ID:** `30794`

---

## Objetivo

Receber leads que demonstraram interesse durante uma ligação telefônica com IA e solicitaram mais informações via WhatsApp. O agente conduz a qualificação textual completa e encaminha o lead para o subagente adequado conforme o resultado.

---

## Contexto do Funil

Este agente é parte de um funil multicanal:

```
IA de Ligação Telefônica
  │
  └── Lead solicita mais info no WhatsApp
          │
          ▼
   Agente Master 03 (WhatsApp)
   Qualificação completa via texto
          │
     ┌────┴────┐
     │         │
Qualificado  Desqualificado
     │              │
Subagente 3.1   Subagente 3.2
(Agendamento)  (Última tentativa
               de conversão)
```

---

## Fluxo do Agente Master

```
Início
  │
  ▼
Decisão por Tags (tag: leadpitchyes)
  │                        │
  ▼                        ▼
Remover Tags          Finalizar Atendimento
  │
  ▼
Agente IA (Perfil Autônomo)
  │
  ├── RAG (x4) — Conhecimento do produto/empresa
  ├── Transferir para Estratégia (x2) → Subagentes
  ├── Acessar Links
  ├── Chats Antigos
  ├── Criar Registro CRM (Tool)
  ├── Add Tag (Tool)
  ├── Políticas e Regras
  └── Adicionar tag (x2)
  │
  ▼
Digitando → Mensagem de Texto
```

### Tools do Agente IA
| Tool | Função |
|---|---|
| RAG (x4) | Base de conhecimento: produto, empresa, objeções e argumentos |
| Acessar Links | Acesso a links externos relevantes para a conversa |
| Criar Registro CRM | Registra lead no CRM automaticamente |
| Add Tag | Adiciona tags de qualificação ao lead |
| Políticas e Regras | Diretrizes de atendimento e compliance |
| Chats Antigos | Histórico de interações anteriores |
| Transferir para Estratégia | Roteamento para subagente correto |

---

## Integração CRM

- Tags removidas ao entrada para reset do estado do lead
- CRM atualizado com registro criado automaticamente
- Lead movido no pipeline conforme resultado da qualificação

---

## Subagentes

| Subagente | Condição de Ativação | Arquivo |
|---|---|---|
| Lead Qualificado IA de Ligação | Lead aprovado na qualificação | [→ ver subagente](./subagents/sub-01-lead-qualificado/) |
| Lead Desqualificado IA de Ligação | Lead reprovado na qualificação | [→ ver subagente](./subagents/sub-02-lead-desqualificado/) |
