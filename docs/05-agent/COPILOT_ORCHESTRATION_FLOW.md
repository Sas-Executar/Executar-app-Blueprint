---
id: AGENT-FLOW-001
type: agent_workflow
title: Copiloto — Sync, Plan, Pre-Approve, Execute, Reconcile
status: pre_approved
version: 0.9.0
owner: null
---

# AGENT-FLOW-001

## Capability order

1. `SYNC`
2. `UNDERSTAND`
3. `STRUCTURE`
4. `VISUALIZE`
5. `PRE_APPROVE`
6. `DECOMPOSE`
7. `EXECUTE / MANAGE`
8. `RECONCILE`
9. `REPORT`
10. `REPLAN`

## SYNC

Quando fontes autorizadas estiverem disponíveis:
- tarefas/tracker;
- email;
- chat/WhatsApp;
- calendário;
- documentos;
- sistemas externos via MCP.

Não inventar dados ausentes.

## UNDERSTAND

Construir contexto de usuário, projetos, processos, tarefas, compromissos, restrições e documentos.

## STRUCTURE

Aplicar metodologia pertinente e organizar primeiro por:
- outcome;
- entregáveis;
- critérios;
- dependências macro;
- capacidade;
- riscos.

## VISUALIZE

Gerar:
1. Mermaid do plano/replanejamento.
2. Preview/lista de entregáveis esperados.

## PRE_APPROVE

Não decompor detalhadamente um novo plano relevante antes de apresentar a estrutura orientada a entregáveis para pré-aprovação.

## DECOMPOSE

Após gate:
`Project/Process → Deliverable → Flow/Task → Action → Evidence`.

## EXECUTE / MANAGE

Usar capabilities operacionais para:
- task management;
- capacity;
- process structuring;
- process optimization;
- runbook;
- status reporting;
- routines;
- Mapa-OS;
- Scanner.

## RECONCILE

Toda ação externa deve:
- validar actor/channel;
- resolver objeto canônico;
- aplicar policy;
- persistir uma vez;
- atualizar projeções;
- emitir audit record.

## REPORT

Entregáveis principais:
- onboarding;
- status report;
- Mapa-OS.

## REPLAN

Replanejar preservando:
- evidências;
- estados não equivalentes;
- prazo original;
- dependências;
- decisões;
- histórico.

Antes da nova decomposição, retornar ao gate `VISUALIZE → PRE_APPROVE`.
