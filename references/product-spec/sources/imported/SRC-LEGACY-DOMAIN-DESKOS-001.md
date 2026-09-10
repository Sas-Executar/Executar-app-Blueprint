# SRC-LEGACY-DOMAIN-DESKOS-001

| Campo | Valor |
|---|---|
| `SOURCE_ID` | `SRC-LEGACY-DOMAIN-DESKOS-001` |
| `source_name` | `corpus_canonico(1).json` → `desk-os-fractal-v1.1.0-source-built` |
| `date_ingested` | `2026-09-09` |
| `type` | Modelo de domínio/implementação anterior do ecossistema |
| `epistemic_classification` | `A · OBSERVED` / `D · INTERNAL` |
| `source_location` | ChatGPT Library `file_00000000a2e8820e81e6c8dba5cf3d0e` |
| `normalization_status` | `CLASSIFIED_FOR_REUSE_AND_CONFLICT_ANALYSIS` |

## Estruturas observadas

A fonte contém um modelo tipado com:

- `WorkNode` com `workspace_id`, `project_id`, `plan_version_id`, `parent_id`, `node_type`, `title`, `order`, `depth`, `status`, `completion_rule`, `done_criteria`, `owner`, `schedule`, `dependencies`, `risk`, `source_refs`, `metadata`;
- `NodeStatus = DRAFT | READY | TODO | IN_PROGRESS | BLOCKED | DONE | CANCELLED | ARCHIVED`;
- `CompletionRule = NONE | MANUAL | ALL_CHILDREN | THRESHOLD`, com `requires_evidence`;
- `PlanLifecycleState = GENERATED | IN_REVIEW | APPROVED | ACTIVE | BLOCKED | REJECTED | SUPERSEDED | COMPLETED | ARCHIVED`;
- `PlanVersion` versionada, com validation report e approval metadata;
- eventos de domínio tipados;
- envelope de evento com `stream_version`, `correlation_id`, `causation_id` e `idempotency_key`;
- fluxo de execução com command validation → authorization → expected version check → domain transition → event append → snapshot projection → response;
- offline baseado em remote snapshot → local cache → navegação offline read-only → queued safe commands opcional → reconnect reconciliation; comandos mutáveis offline podem permanecer bloqueados no MVP.

## Conflito estrutural explícito

O modelo anterior usa `NodeType` genérico (`project`, `phase`, `workflow`, `block`, `deliverable`, `action` etc.) e **não é idêntico** à hierarquia proprietária atual:

`Project → ValueStream → Deliverable → Task → Action → Evidence`.

Portanto ele não é promovido como domínio canônico atual por simples cópia.

Ele é fonte de REUSE para:

- versionamento;
- lifecycle de plano;
- completion rules;
- envelope de eventos;
- dependencies/source refs;
- optimistic concurrency / expected version;
- offline conservador.

A reconciliação de tipos está registrada em `20-DOMAIN/LEGACY_DOMAIN_COMPATIBILITY.md`.
