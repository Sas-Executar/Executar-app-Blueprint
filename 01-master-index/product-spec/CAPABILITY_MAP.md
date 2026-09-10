# Capability Map

A **capability** é a unidade principal de organização deste repositório.
Cada capability pode referenciar PRD, requirement, acceptance criteria, domain rule, state, contract, page, component, agent tool, analytics event, test expectation e target técnico.

## Estados

`DISCOVERED → PARTIAL → SPECIFIED → READY → IMPLEMENTING → IMPLEMENTED → VERIFIED`

- `PARTIAL`: alguns elementos aplicáveis existem, mas a Definition of Ready ainda não está completa.
- `SPECIFIED`: elementos aplicáveis da Definition of Ready estão documentados.
- `READY`: spec revisada/aprovada para implementação.

## Capabilities WF-02

| CAPABILITY_ID | DOMAIN | NAME | STATUS | SOURCE | REQUIREMENTS | DEPENDENCIES | TARGET | READINESS | BLOCKERS |
|---|---|---|---|---|---|---|---|---|---|
| `CAP-EXEC-001` | Context | Context Understanding | `PARTIAL` | `SRC-PRODUCT-MANIFESTO-001` | REQ-EXEC-001 | canonical state | `TBD` | core behavior documented | contracts/NFR target |
| `CAP-EXEC-002` | Structure | Work Structuring | `PARTIAL` | manifesto | REQ-EXEC-002 | CAP-EXEC-001 | `TBD` | hierarchy documented | data contract |
| `CAP-EXEC-003` | Planning | Capacity Planning | `PARTIAL` | manifesto+blueprint | REQ-EXEC-006,007 | CAP-EXEC-002 | `TBD` | core rule documented | capacity algorithm/data |
| `CAP-EXEC-004` | Planning | Dependency & Eligibility | `PARTIAL` | manifesto+legacy | REQ-EXEC-003,011 | CAP-EXEC-002 | `TBD` | rules/state machine documented | contract/algorithm |
| `CAP-EXEC-005` | Execution | Best Next Action | `PARTIAL` | manifesto | REQ-EXEC-004,017 | CAP-EXEC-003,004 | `TBD` | behavior documented | dispatch algorithm |
| `CAP-EXEC-006` | Execution | WIP 1:1 Execution | `PARTIAL` | manifesto | REQ-EXEC-005 | CAP-EXEC-005 | `TBD` | invariant documented | concurrency contract |
| `CAP-EXEC-007` | Evidence | Evidence Capture | `PARTIAL` | manifesto | REQ-EXEC-010,011 | CAP-EXEC-006 | `TBD` | concept documented | evidence schema/policy |
| `CAP-EXEC-008` | Planning | Continuous Replanning | `PARTIAL` | manifesto | REQ-EXEC-008 | CAP-EXEC-003,004 | `TBD` | journey/rule documented | decision/algorithm |
| `CAP-EXEC-009` | Context | Check-in / Checkout / Resume | `PARTIAL` | manifesto | REQ-EXEC-001,009 | CAP-EXEC-001 | `TBD` | journey/rules documented | persistence contract |
| `CAP-EXEC-010` | Projection | Mapa-OS | `PARTIAL` | manifesto+blueprint | REQ-EXEC-012 | CAP-EXEC-003,004,005 | `TBD` | purpose documented | WF-04 page/assets/contracts |
| `CAP-EXEC-011` | Scanner | Visual Symbol Scanner | `PARTIAL` | scanner source | REQ-EXEC-013 | CAP-EXEC-015 | `TBD` | core intent + source recorded | WF-03/05 runtime contracts |
| `CAP-EXEC-012` | Agent | Copilot Orchestration | `PARTIAL` | manifesto | REQ-EXEC-014,018 | core domain | `TBD` | product mission documented | WF-03 agent/tool policies |
| `CAP-EXEC-013` | Reporting | Status Report Generation | `PARTIAL` | manifesto | REQ-EXEC-015 | CAP-EXEC-007,009 | `TBD` | output purpose documented | page/copy/report schema |
| `CAP-EXEC-014` | Automation | Routines & Workflows | `PARTIAL` | manifesto+blueprint | TBD | canonical state | `TBD` | capability identified | WF-03/05 detailed contracts |
| `CAP-EXEC-015` | Platform Product | Omnichannel State Continuity | `PARTIAL` | blueprint+manifesto | REQ-EXEC-016 | state/contracts | `TBD` | principle documented | sync/offline/permission contracts |

## Autoridades relacionadas

- descrição detalhada: `10-PRODUCT/capabilities/CORE_CAPABILITIES.md`
- requisitos: `10-PRODUCT/requirements/CORE_REQUIREMENTS.md`
- AC: `10-PRODUCT/acceptance-criteria/CORE_ACCEPTANCE_CRITERIA.md`
- regras: `20-DOMAIN/rules/CORE_BUSINESS_RULES.md`
- estados: `20-DOMAIN/states/EXECUTION_STATES.md`
- máquina: `20-DOMAIN/state-machines/EXECUTION_STATE_MACHINE.md`
- jornadas: `10-PRODUCT/journeys/CORE_JOURNEYS.md`

Nenhuma capability é `READY` neste WF porque ainda faltam contratos, targets técnicos e áreas transversais aplicáveis. `PARTIAL` não significa implementada.