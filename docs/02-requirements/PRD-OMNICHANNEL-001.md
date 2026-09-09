---
id: PRD-OMNI-001
type: prd
title: Gestão Omnicanal Autônoma e Interdependente
status: pre_approved
version: 0.9.0
owner: null
depends_on:
  - PROD-FLOW-001
  - PRD-ROUTINES-001
  - PRD-SCANNER-001
---

# PRD — Gestão Omnicanal Autônoma e Interdependente

## Problema

Ferramentas de produtividade normalmente obrigam o usuário a retornar à interface principal para consultar, atualizar e reorganizar o trabalho. Isso contradiz a proposta do EXECUTAR de reduzir carga executiva operacional.

## Objetivo

Permitir que o mesmo estado de trabalho seja consultado e administrado por múltiplos canais interoperáveis, mantendo uma única fonte de verdade e possibilitando uma experiência `planeje uma vez → imprima → continue executando sem depender do app`.

## Canais

| Canal | Leitura | Ação | Configuração | Observação |
|---|---|---|---|---|
| App | sim | sim | sim | superfície completa |
| MCP | sim | sim, conforme policy | sim, conforme capability | integração com outras AIs/plataformas |
| WhatsApp | sim | sim, conforme comandos/policy | limitada | adapter |
| Email | sim | sim, conforme comandos/policy | limitada | adapter assíncrono |
| Copiloto | sim | sim, conforme authority | sim | interface agentic |
| Mapa-OS + Scanner | sim | sim via Scanner | símbolos configuráveis | prioridade analógica |

## Requisitos

### REQ-OMNI-001 — Estado único
Todos os canais devem ler e escrever no mesmo estado canônico.

### REQ-OMNI-002 — Reconciliação
Ação aceita em um canal deve refletir-se nos demais após persistência/reconciliação.

### REQ-OMNI-003 — Canal não é fonte de verdade
Email, WhatsApp, MCP, Copiloto, Mapa-OS e Scanner não podem manter estado concorrente.

### REQ-OMNI-004 — Operação sem app
Depois de planejamento e emissão do Mapa-OS, o usuário deve conseguir executar o fluxo básico sem abrir novamente a interface principal, enquanto houver informações suficientes no artefato e ações suportadas pelo Scanner/canais.

### REQ-OMNI-005 — Pré-aprovação deliverable-first
Plano/replanejamento deve apresentar estrutura por entregáveis e visualização antes da decomposição fina.

### REQ-OMNI-006 — Mermaid
O agente deve conseguir produzir visualização Mermaid do plano/replanejamento para revisão.

### REQ-OMNI-007 — Onboarding
O agente deve gerar onboarding parametrizado contendo fluxo, comandos, uso do Mapa-OS e uso/configuração do Scanner.

### REQ-OMNI-008 — Views
A UI deve oferecer WIP 1:1, Lista e Kanban, aplicáveis a projeto individual ou remix multi-projeto.

### REQ-OMNI-009 — Separação semântica
Tarefa isolada, processo e projeto devem ter representações distintas, sem perder interoperabilidade.

### REQ-OMNI-010 — Documentos ligados a entregáveis
Arquivos de projeto devem poder ser anexados aos entregáveis/objetos correspondentes.

### REQ-OMNI-011 — Configuração do Scanner
Símbolos e ações devem ser configuráveis sob policy e contrato próprios.

### REQ-OMNI-012 — Auditabilidade
Toda mutação externa deve registrar canal, identidade/actor quando disponível, comando, objeto, resultado, timestamp e evidência/receipt quando aplicável.

## Acceptance Criteria

- Dado um update pelo WhatsApp, quando a ação for aceita, então o app deve refletir o mesmo estado canônico.
- Dada uma falha de entrega por Email, o estado da tarefa não deve ser revertido nem alterado.
- Dado um Mapa-OS impresso, quando o Scanner reconhecer um símbolo configurado, então deve resolver `VisualSymbolId → comando → ação` e reconciliar o resultado.
- Dado um novo plano, o agente deve apresentar entregáveis + Mermaid antes da decomposição detalhada.
- Dado um remix multi-projeto, a visualização pode agregar tarefas sem criar cópias dos objetos.
- Dada uma tarefa isolada, ela não deve ser automaticamente convertida em projeto ou processo.

## Fora de escopo deste documento

- provider específico de WhatsApp;
- provider específico de Email;
- implementação do servidor MCP;
- escolha final de modelo visual do Scanner;
- credenciais e autenticação por provider;
- implementação do runtime.

Esses itens pertencem a specs/ADRs próprios e gates de implementação.
