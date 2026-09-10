# WF-02 — Produto & Core Domain Status

Data: `2026-09-09`
Estado: `CANONICALIZATION_IN_PROGRESS`
Gate: `CORE_DOMAIN_SPEC_READY = NOT_READY`

## Fontes processadas

- `SRC-PRODUCT-MANIFESTO-001` — manifesto primário.
- `SRC-PRODUCT-BLUEPRINT-001` — blueprint/briefing composto.
- `SRC-SCANNER-RUNTIME-FOLLOWUP-001` — fonte operacional Scanner, corretamente roteada fora de Product Vision.
- referências observadas do produto atual (`AGENTS.md` + legado funcional) para preservar fila elegível, ciclos 72h, dependências, evidências e offline.

## PROD-001 a PROD-010

| ID | Tópico | Estado | Autoridade/saída | Gaps principais |
|---|---|---|---|---|
| `PROD-001` | Visão do produto | `INGESTED` | `vision/PRODUCT_VISION.md`, `PRODUCT_BRIEF.md` | aprovação formal/ICP detalhado |
| `PROD-002` | Estrutura do produto | `INGESTED` | `feature-specs/PRODUCT_STRUCTURE.md`, entity model | cardinalidades/lifecycle final |
| `PROD-003` | Regras centrais | `INGESTED_WITH_GAPS` | `20-DOMAIN/rules/CORE_BUSINESS_RULES.md` | fórmula capacidade, algoritmo BNA, detalhes ciclo |
| `PROD-004` | Estados e state machine | `INGESTED_WITH_GAPS` | `states/EXECUTION_STATES.md`, state machine | lifecycle de agregados, reopen/cancel/archive |
| `PROD-005` | Jornadas | `INGESTED_WITH_GAPS` | `journeys/CORE_JOURNEYS.md` | onboarding, erros, permissões detalhadas |
| `PROD-006` | Capability Map | `INGESTED` | `00-MANIFEST/CAPABILITY_MAP.md` | targets técnicos e DoR completa |
| `PROD-007` | Modelo funcional de dados | `INGESTED_WITH_GAPS` | `entities/CORE_ENTITY_MODEL.md`, glossary | schema/ERD/cardinalidades/IDs |
| `PROD-008` | Requisitos + AC | `INGESTED_WITH_GAPS` | `CORE_REQUIREMENTS.md`, `CORE_ACCEPTANCE_CRITERIA.md`, NFR | NFRs transversais e DoD específicos |
| `PROD-009` | Permissões e tenancy | `INGESTED_WITH_GAPS` | `permissions/CORE_PERMISSIONS.md` | roles e matriz final |
| `PROD-010` | Eventos / commands / queries | `INGESTED_WITH_GAPS` | `DOMAIN_EVENT_CATALOG.md`, `COMMAND_QUERY_CATALOG.md` | schemas/versionamento/idempotência |

## Artefatos canônicos criados neste WF

### Product
- `vision/PRODUCT_VISION.md`
- `vision/PRODUCT_BRIEF.md`
- `vision/ICP_JTBD.md`
- `feature-specs/PRODUCT_STRUCTURE.md`
- `feature-specs/EDGE_CASES_OFFLINE_SYNC.md`
- `capabilities/CORE_CAPABILITIES.md`
- `requirements/CORE_REQUIREMENTS.md`
- `requirements/NON_FUNCTIONAL_REQUIREMENTS.md`
- `acceptance-criteria/CORE_ACCEPTANCE_CRITERIA.md`
- `journeys/CORE_JOURNEYS.md`

### Domain
- `entities/CORE_ENTITY_MODEL.md`
- `rules/CORE_BUSINESS_RULES.md`
- `states/EXECUTION_STATES.md`
- `state-machines/EXECUTION_STATE_MACHINE.md`
- `events/DOMAIN_EVENT_CATALOG.md`
- `permissions/CORE_PERMISSIONS.md`
- `COMMAND_QUERY_CATALOG.md`
- `GLOSSARY.md`

## Gates parciais

- `PRODUCT_VISION_INGESTED = PASS`
- `CORE_STRUCTURE_INGESTED = PASS`
- `CORE_RULES_INGESTED = PASS_WITH_GAPS`
- `CORE_STATE_MODEL_INGESTED = PASS_WITH_GAPS`
- `CORE_JOURNEYS_INGESTED = PASS_WITH_GAPS`
- `CAPABILITY_MAP_POPULATED = PASS`
- `CORE_REQUIREMENTS_INGESTED = PASS_WITH_GAPS`
- `CORE_PERMISSIONS_INGESTED = PASS_WITH_GAPS`
- `CORE_EVENT_CATALOG_INGESTED = PASS_WITH_GAPS`
- `CORE_DOMAIN_SPEC_READY = NOT_READY`

## O que falta para fechar WF-02

1. aprovar/fechar ICP e JTBD prioritários;
2. decisão da fórmula de capacidade e granularidade operacional do ciclo de 72h;
3. lifecycle agregado de Project/ValueStream/Deliverable;
4. data model/ERD e cardinalidades finais;
5. roles + matriz de permissões;
6. política de offline/sync e conflitos;
7. schemas finais de commands/events/queries — encaminhados ao WF-05;
8. NFRs transversais — encaminhados ao WF-07/integração;
9. targets técnicos `95-INTEGRATION` para capabilities prontas.

## Regra

`INGESTED` ou `PARTIAL_SPECIFIED` não significa `READY`, `IMPLEMENTED` ou `VERIFIED`. Nenhum status foi promovido além da evidência disponível.