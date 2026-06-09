# 🔄 Subagente 03.2 — Lead Desqualificado · IA de Ligação

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Worker
**Ativado por:** Agente Master `30794` quando lead não é qualificado

---

## Objetivo

Receber o lead desqualificado e fazer uma última tentativa de conversão apresentando o valor do produto. Se o lead demonstrar interesse mesmo após a desqualificação inicial, agenda reunião. Caso contrário, encerra o atendimento direcionando para conteúdo de nutrição (grupo externo de marketing).

---

## Fluxo do Subagente

```
Início
  │
  ▼
Remover Tags
  │
  ▼
Decisão por Tags (tag: lead-seminteresse)
  │                         │
  ▼                         ▼
Agente IA (Autônomo)    Finalizar Atendimento
  │
  ├── Agenda (Google Agenda)
  ├── Chats de Atendimentos Antigos
  ├── Criar Registro CRM (Tool)
  ├── RAG (base de conhecimento produto)
  └── Adicionar tag (x2)
  │
  ▼
Decisão por Tags
  ├── lead-agendado → Confirmação de Reunião
  ├── lead-desqualificado → Encerramento com Nutrição
  └── ELSE (Padrão)

Rota lead-agendado:
  Split → Mensagem Predefinida (confirmação) → Delay → Remover Tags → Finalizar
       → Delay → Remover Tags → Finalizar

Rota lead-desqualificado:
  Split → Delay → Digitando → Mensagem de Texto (link grupo marketing) → Finalizar
```

### Mensagens Predefinidas
**Confirmação de agendamento:**
> *"Perfeito! Agendado! Vou passar para o Guilherme um resumo do que você me contou para a conversa já começar mais objetiva. Agendado então {{primeiro_nome}}, até lá!"*

**Encerramento com nutrição:**
> *"Super entendido. Nesse caso, talvez o melhor caminho agora seja acompanhar o Moviman to Anti-Cantoso. É um conteúdo gratuito do..."*

### Tools do Agente IA
| Tool | Função |
|---|---|
| Agenda | Agendamento de reunião para leads reconvertidos |
| Chats de Atendimentos Antigos | Contexto de interações anteriores |
| Criar Registro CRM | Registra interação final no CRM |
| RAG | Argumentos de valor do produto para última tentativa |
| Adicionar tag (x2) | Tags de resultado: agendado ou desqualificado definitivo |

---

## Integração CRM

- Tags limpas ao entrar no subagente
- Resultado final tagueado: `lead-agendado` ou `lead-desqualificado`
- Pipeline atualizado conforme desfecho

---

## Resultado esperado

| Cenário | Resultado |
|---|---|
| Lead reconvertido | Reunião agendada no Google Agenda + confirmação via WhatsApp |
| Lead mantém desqualificação | Direcionado para grupo de marketing + atendimento finalizado |
