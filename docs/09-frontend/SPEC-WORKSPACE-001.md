---
id: SPEC-WORKSPACE-001
type: technical_product_spec
title: Workspace, Routes and Task Visualization
status: draft
version: 0.9.0
owner: null
---

# SPEC-WORKSPACE-001

## 1. Route Model

```text
/projects
/projects/:projectId
/projects/:projectId/documents
/calendar
/overview
/roadmap
/sprint
/now
/today
/tomorrow
/yesterday
/copilot
/mapa-os
/scanner
/reports
/automations
/workflows
```

A nomenclatura de URL é indicativa; rotas técnicas finais dependem da arquitetura frontend.

## 2. Navigation Objects

| Área | Objeto principal | Regra |
|---|---|---|
| Projeto(s) | Project | individual ou agregação |
| Documentos | Attachment/Document | anexado a entregável/objeto |
| Calendário | Time Projection | não altera estado sozinho |
| Overview | Project/Portfolio Projection | leitura agregada |
| Roadmap | Deliverables/Milestones | horizonte |
| Sprint | Execution Window | planejamento operacional |
| Agora | Action | próxima ação elegível |
| Hoje/Amanhã/Ontem | Temporal Projection | projeção |
| Copiloto | Agent Interaction | comando/contexto |
| Mapa-OS | Analog Projection | artefato imprimível |
| Scanner | Visual Command Surface | reconhece e despacha |
| Reports | StatusReport | histórico canônico |
| Automações | RoutineConfig | automação governada |
| Workflows | WorkflowDefinition | processo configurado |

## 3. View Modes

### WIP 1:1
Mostra uma unidade operacional ativa dominante.

### Lista
Mostra objetos ordenados sem alterar estado.

### Kanban
Agrupa objetos por estado/estágio.

## 4. Scope Modes

### Single Project
A view é filtrada por um `project_id`.

### Remix Multi-project
Agrega referências a objetos de múltiplos projetos em uma projeção comum. Não duplica tarefas nem cria projeto sintético por padrão.

## 5. Object Separation

A UI deve diferenciar visual e semanticamente:
- `StandaloneTask`
- `ProjectTask`
- `ProcessStep/Task`
- `Deliverable`
- `Action`

`StandaloneTask` não requer `project_id` nem `process_id` quando a regra de domínio permitir.

## 6. Documents

Documentos são anexos ou recursos ligados a objetos de trabalho, preferencialmente entregáveis. O documento não define sozinho o estado do projeto.

## 7. Cross-channel state

Qualquer mudança deve retornar um `DomainMutationResult` e disparar refresh/reconciliation para as projeções afetadas.

## 8. Pending technical decisions

- estrutura final das rotas Next.js;
- modelo de portfolio/remix;
- auth/tenant propagation entre adapters;
- conflito de updates concorrentes;
- ordenação de eventos;
- cache e realtime.
