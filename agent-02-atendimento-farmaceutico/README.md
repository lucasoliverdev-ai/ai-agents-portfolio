# 💊 Agent 02 — Atendimento Farmacêutico

**Plataforma:** SellFlux · **Canal:** WhatsApp · **Status:** Desativado · **ID:** `29594`

---

## Objetivo

Atender automaticamente clientes no WhatsApp de uma farmácia, cobrindo três jornadas distintas: consulta de preço de produtos, recomendação de remédios por sintomas e verificação de disponibilidade de medicamentos prescritos em receita — finalizando com a conversão em venda.

---

## Fluxo do Agente Master

```
Início
  │
  ▼
Add Tags
  │
  ▼
Decisão por Tags (tag: lead-captado)
  │                        │
  ▼                        ▼
Delay                 Finalizar atendimento
  │
  ▼
Agente IA (Perfil Subautônomo)
  │
  ├── Add Tags (x2)
  ├── Chats de Atendimentos Antigos
  ├── Políticas e Regras da Empresa
  ├── Add Tags
  ├── Consulta API (Estoque/TAL)
  ├── Transferir para Fila de Atendimento
  ├── Produtos
  ├── RAG (x6) — Base de conhecimento de produtos e sintomas
  ├── Criar Registro CRM (Tool)
  ├── Atualizar Memória de Atendimento
  └── Extrair dados da conversa (x5)
  │
  ▼
Delay → Enviar mensagem de Texto
```

### As 3 Jornadas de Atendimento

| Jornada | Gatilho | Ação do Agente |
|---|---|---|
| **Consulta de Preço** | Cliente pergunta o preço de um produto | Consulta base RAG e responde com valor atualizado |
| **Recomendação por Sintoma** | Cliente descreve sintoma | IA sugere remédio com base em sintomas pré-definidos via RAG |
| **Receita Médica** | Cliente envia receita e pergunta disponibilidade | IA consulta API de estoque em tempo real e confirma disponibilidade |

### Tools do Agente IA
| Tool | Função |
|---|---|
| Consulta API (Estoque) | Verifica disponibilidade de medicamentos em tempo real |
| RAG (x6) | Base de conhecimento de produtos, sintomas e recomendações |
| Criar Registro CRM | Registra lead/cliente no CRM automaticamente |
| Atualizar Memória de Atendimento | Mantém contexto ao longo da conversa |
| Políticas e Regras da Empresa | Garante respostas dentro das diretrizes farmacêuticas |
| Chats de Atendimentos Antigos | Histórico de atendimentos anteriores do cliente |
| Transferir para Fila de Atendimento | Escala para atendente humano quando necessário |
| Extrair dados da conversa | Captura dados relevantes do cliente |
| Produtos | Catálogo de produtos disponíveis |

---

## Integração CRM

- Registro criado automaticamente a cada novo atendimento
- Memória de atendimento atualizada a cada interação
- Tags adicionadas conforme jornada do cliente

---

## Observações Técnicas

- **Perfil Subautônomo:** agente com maior controle e previsibilidade nas respostas, adequado para contexto regulado (farmácia)
- **Escalada humana:** disponível via nó "Transferir para Fila de Atendimento" quando o agente identifica necessidade
- **Status Desativado:** agente em fase de manutenção ou revisão de fluxo

---

## Subagentes

Este agente opera de forma standalone — sem subagentes. Todas as jornadas são tratadas pelo agente master.
