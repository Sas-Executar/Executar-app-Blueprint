# MASTER INDEX

Canonic index for the Executar App Blueprint. `status` indicates documentation state only; it does not imply implementation or verification.

| Domain | ID range | Path | Purpose | Initial priority |
|---|---|---|---|---|
| Governance | GOV-* | docs/00-governance | canonicality, precedence, traceability | P0 |
| Product | PROD-* | docs/01-product | vision, users, JTBD, journeys | P0 |
| Requirements | REQ-* | docs/02-requirements | PRD, requirements, AC, scope | P0 |
| Domain | DOM-* | docs/03-domain | vocabulary, rules, states, events | P0 |
| Architecture | ARCH-*/ADR-* | docs/04-architecture | system design and decisions | P0 |
| Agent | AGENT-* | docs/05-agent | runtime, tools, guardrails, memory | P0 |
| Skills | SKILL-* | skills | executable/imported skill packages and contracts | P0 |
| Deliverables | DELIV-* | deliverables | reusable placeholder output models | P0 |
| Prompts | PROMPT-* | docs/06-prompts | prompt contracts and failures | P0 |
| Data | DATA-* | docs/07-data | model, migrations, RLS, retention | P0 |
| API | API-* | docs/08-api-contracts | API/event/error contracts | P0 |
| Frontend | UI-* | docs/09-frontend | IA, routes, states, design system | P0/P1 |
| Backend | BE-* | docs/10-backend | boundaries, use cases, jobs | P0/P1 |
| Security | SEC-* | docs/11-security | threats, permissions, injection | P0 |
| Tests & Evals | TEST-* | docs/12-testing-evals | test strategy and agent quality gates | P0 |
| Observability | OBS-* | docs/13-observability | traces, logs, metrics, AI cost | P0/P1 |
| DevOps | DEVOPS-* | docs/14-devops | environments, CI/CD, deploy | P0 |
| Operations | OPS-* | docs/15-operations-release | runbook, incidents, releases | P0/P1 |
| Personalization | PERS-* | docs/16-personalization | profile, preferences, memory, context | P0 |

## Canonical artifact registry

| ID | Artifact | Path | Status | Version | Role |
|---|---|---|---|---|---|
| PROD-001 | EXECUTAR — Visão do Produto | `docs/01-product/PRODUCT_VISION.md` | pre_approved | 0.9.0 | semantic root for product derivation |
| AGENT-SKILL-REGISTRY-001 | Skill Registry | `docs/05-agent/SKILL_REGISTRY.md` | registered | 1.0.0 | inventory and authority boundaries for skills |
| AGENT-DELIV-REGISTRY-001 | Deliverable Registry | `docs/05-agent/DELIVERABLE_REGISTRY.md` | registered | 1.0.0 | maps skills to placeholder output models |
| SKILL-MAPA-OS-001 | executar-mapa-os | `skills/executar-mapa-os/SKILL.md` | registered | 1.0.0 | operational Mapa-OS skill package |
| SKILL-COP-001 | copiloto-executar | `skills/copiloto-executar/SKILL.md` | registered | source package | daily EXECUTAR copiloto skill package |

## Canonical flow
EVID → PROBLEM → ICP → JOURNEY → JTBD → VALUE → PRD → REQ → AC → ADR → SPEC → CODE → TEST → EVAL → RELEASE → KPI → LEARNING

## Agent read path
`AGENTS.md` → this index → affected domain docs → requirements/AC → ADR/contracts/schemas → registered skills/deliverable contracts → code → tests → implementation → verification → documentation update.

## State semantics
`draft ≠ review ≠ pre_approved ≠ approved ≠ implemented ≠ tested ≠ verified ≠ released`.

`registered` is an inventory/traceability state for imported packages and templates. It does not imply `approved`, `implemented`, `tested`, `verified` or `released`.
