# LEGACY_DOMAIN_COMPATIBILITY

Status: `ANALYZED`
Source: `SRC-LEGACY-DOMAIN-DESKOS-001`

## Objetivo

Reaproveitar capacidades maduras do modelo anterior sem substituir a hierarquia proprietária atual do EXECUTAR por equivalência falsa.

## Hierarquias

### Produto atual

`Project → ValueStream → Deliverable → Task → Action → Evidence`

### Desk-OS anterior

`WorkNode` genérico com tipos como:

`portfolio | project | phase | workflow | week | day | block | deliverable | action | synthesis`

## Compatibilidade

| Conceito atual | Desk-OS anterior | Ação |
|---|---|---|
| Project | project | `REUSE/ADAPT` |
| ValueStream | não há equivalente 1:1 | `GAP/MAP DECISION` |
| Deliverable | deliverable | `REUSE/ADAPT` |
| Task | workflow/block podem cumprir papéis próximos, mas não equivalentes | `CONFLICT/MAP DECISION` |
| Action | action | `REUSE/ADAPT` |
| Evidence | completion rule + evidence event, sem entidade equivalente clara | `ADAPT` |
| Dependency | `dependencies: WorkNodeId[]` | `REUSE` |
| Done criteria | `done_criteria[]` | `REUSE` |
| Completion rule | NONE/MANUAL/ALL_CHILDREN/THRESHOLD + requires_evidence | `REUSE` |
| Risk | LOW/MEDIUM/HIGH/CRITICAL | `REUSE/OPTIONAL` |
| Source trace | source_refs | `REUSE` |
| Plan version | PlanVersion | `REUSE` |
| Event envelope | DomainEvent | `REUSE` |

## Lifecycle reutilizável

### NodeStatus anterior

`DRAFT | READY | TODO | IN_PROGRESS | BLOCKED | DONE | CANCELLED | ARCHIVED`

### Execução atual

`BACKLOG | READY | FOCUS | BLOCKED | DONE`

Não são a mesma state machine.

Mapeamento provisório de interoperabilidade:

- BACKLOG ↔ DRAFT/TODO, conforme contexto;
- READY ↔ READY;
- FOCUS ↔ IN_PROGRESS;
- BLOCKED ↔ BLOCKED;
- DONE ↔ DONE;
- CANCELLED/ARCHIVED permanecem lifecycle auxiliar, ainda não exposto na máquina simplificada de execução.

### PlanLifecycle reutilizável

`GENERATED → IN_REVIEW → APPROVED → ACTIVE → COMPLETED/ARCHIVED`

com ramificações `BLOCKED`, `REJECTED`, `SUPERSEDED`.

Esse lifecycle é útil para versão de plano, mas não substitui lifecycle de Project/ValueStream/Deliverable.

## Conflitos registrados

- `CONFLICT-DOM-STRUCT-001`: ValueStream/Task não possuem equivalência 1:1 no NodeType anterior.
- `CONFLICT-DOM-STATE-001`: estado UX `FOCUS/BACKLOG` e NodeStatus técnico anterior usam vocabulários diferentes.

## Decisão de governança

Não criar um segundo domínio paralelo e não importar o modelo antigo inteiro por conveniência.

Reusar mecanismos compatíveis; adaptar tipos somente depois de contrato explícito no WF-05 e mapping para next-forge.