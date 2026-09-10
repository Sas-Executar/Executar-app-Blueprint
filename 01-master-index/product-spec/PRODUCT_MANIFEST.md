# Product Manifest

| Campo | Valor |
|---|---|
| `product` | EXECUTAR |
| `repository purpose` | Fonte canônica da camada proprietária do produto EXECUTAR — produto, domínio, design, conteúdo, agentes, contratos, integrações, governança e medição. Não reproduz infraestrutura genérica já resolvida pela plataforma. |
| `architecture relationship` | `next-forge` = chassis técnico / plataforma / foundation. `EXECUTAR-Product-Spec` = especificação proprietária / customization layer. Integração futura = produto EXECUTAR executável. |
| `version` | 1.1 |
| `date` | 2026-09-09 |
| `phase` | WF-02 Produto & Core Domain em canonicalização |
| `canonical authorities` | Ver tabela abaixo |
| `main domains` | Context, Structure, Planning, Execution, Evidence, Mapa-OS, Scanner, Copilot, Reporting, Routines, Omnichannel State |
| `design authority` | `30-DESIGN/` — WF-01 concluído; `DESIGN_FOUNDATION_READY = PASS` |
| `product vision authority` | `10-PRODUCT/vision/PRODUCT_VISION.md` |
| `domain authority` | `20-DOMAIN/` |
| `capability authority` | `00-MANIFEST/CAPABILITY_MAP.md` + `10-PRODUCT/capabilities/CORE_CAPABILITIES.md` |
| `agent authority` | `50-AGENTS/` — ainda WF-03 / não canonizado |
| `contract authority` | `60-CONTRACTS/` — templates existentes; contratos executáveis ainda WF-05 |
| `integration target` | `Sas-Executar/next-forge` |

---

## Autoridades canônicas

| Tipo de conteúdo | Área canônica | Status |
|---|---|---|
| Visão de produto | `10-PRODUCT/vision/PRODUCT_VISION.md` | `PRE_APPROVED_FROM_PRIMARY_SOURCE` |
| Product brief | `10-PRODUCT/vision/PRODUCT_BRIEF.md` | `PRE_APPROVED_FROM_PRIMARY_SOURCE` |
| ICP / JTBD | `10-PRODUCT/vision/ICP_JTBD.md` | `PARTIAL` |
| Estrutura funcional | `10-PRODUCT/feature-specs/PRODUCT_STRUCTURE.md` | `PARTIAL_SPECIFIED` |
| Capabilities | `10-PRODUCT/capabilities/CORE_CAPABILITIES.md` + `00-MANIFEST/CAPABILITY_MAP.md` | `PARTIAL_SPECIFIED` |
| Requisitos | `10-PRODUCT/requirements/CORE_REQUIREMENTS.md` | `PARTIAL_SPECIFIED` |
| NFRs | `10-PRODUCT/requirements/NON_FUNCTIONAL_REQUIREMENTS.md` | `PARTIAL` |
| Acceptance Criteria | `10-PRODUCT/acceptance-criteria/CORE_ACCEPTANCE_CRITERIA.md` | `PARTIAL_SPECIFIED` |
| Jornadas | `10-PRODUCT/journeys/CORE_JOURNEYS.md` | `PARTIAL_SPECIFIED` |
| Entidades | `20-DOMAIN/entities/CORE_ENTITY_MODEL.md` | `PARTIAL_SPECIFIED` |
| Regras de domínio | `20-DOMAIN/rules/CORE_BUSINESS_RULES.md` | `PARTIAL_SPECIFIED` |
| Estados | `20-DOMAIN/states/EXECUTION_STATES.md` | `PARTIAL_SPECIFIED` |
| State machine | `20-DOMAIN/state-machines/EXECUTION_STATE_MACHINE.md` | `PARTIAL_SPECIFIED` |
| Eventos | `20-DOMAIN/events/DOMAIN_EVENT_CATALOG.md` | `PARTIAL_SPECIFIED` |
| Commands/Queries | `20-DOMAIN/COMMAND_QUERY_CATALOG.md` | `PARTIAL_SPECIFIED` |
| Permissões | `20-DOMAIN/permissions/CORE_PERMISSIONS.md` | `PARTIAL` |
| Glossário | `20-DOMAIN/GLOSSARY.md` | `PARTIAL_SPECIFIED` |
| Edge cases / offline / sync | `10-PRODUCT/feature-specs/EDGE_CASES_OFFLINE_SYNC.md` | `PARTIAL` |
| Design tokens | `30-DESIGN/` | `PASS / WF-01 DONE` |
| Páginas/rotas | `40-CONTENT/` | `GAP` — WF-04 |
| Agentes | `50-AGENTS/` | `GAP` — WF-03 |
| Contratos executáveis | `60-CONTRACTS/` | `GAP/PARTIAL` — WF-05 |
| Integrações externas | `70-INTEGRATIONS/` | `GAP` — WF-06 |
| Analytics/KPIs | `90-MEASUREMENT/` | `GAP` — WF-07 |
| Mapeamento para next-forge | `95-INTEGRATION/` | `PARTIAL` — só fecha após specs suficientes |

---

## Fontes principais do WF-02

- `SRC-PRODUCT-MANIFESTO-001` — fonte primária da tese, visão, princípios e capabilities.
- `SRC-PRODUCT-BLUEPRINT-001` — fonte interna composta para briefing, estados, sequência documental e benchmark.
- `SRC-SCANNER-RUNTIME-FOLLOWUP-001` — fonte operacional específica do Visual Symbol Scanner; não é Product Vision.
- `Sas-Executar/Sas-Executar/AGENTS.md` e legado funcional — referência observada para preservação do modelo mental, ciclos de 72h, fila elegível, dependências, evidência e offline.

## Regras de status

- `estruturado ≠ aprovado ≠ implementado ≠ testado ≠ verificado ≠ released`.
- Nenhuma capability do WF-02 é `READY` ainda porque faltam contracts, targets técnicos e áreas transversais aplicáveis.
- Nenhum gap é preenchido por benchmark sem classificação explícita.