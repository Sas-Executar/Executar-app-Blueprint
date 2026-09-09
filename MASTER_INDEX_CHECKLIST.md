---
id: MASTER-CHECK-001
type: governance_checklist
title: EXECUTAR — Master Index Checklist
status: active
version: 1.0.0
owner: null
last_updated: 2026-09-09
---

# EXECUTAR — MASTER INDEX CHECKLIST

Este checklist representa o estado documental do repositório `Executar-app-Blueprint` após a consolidação dos PRs #1 a #6.

## Legenda

- `[x]` estruturado/registrado no repositório.
- `[ ]` ainda requer preenchimento, decisão, implementação ou validação.
- `pre_approved` valida direção documental; não significa implementação.
- `accepted` registra decisão arquitetural aceita; não significa código entregue.
- `registered` / `registered_from_source` registra corpus/contrato; não significa implementação.
- `template_only` indica estrutura criada, porém conteúdo canônico ainda não preenchido.

---

# 1. FUNDAÇÃO E GOVERNANÇA

- [x] `README.md` — entrada do blueprint.
- [x] `AGENTS.md` — instruções de leitura e mudança para agentes.
- [x] `MASTER_INDEX.md` — índice canônico.
- [x] `MASTER_INDEX_CHECKLIST.md` — checklist consolidado.
- [x] `CHANGELOG.md` — estrutura de mudanças.
- [x] `.env.example` — variáveis sem segredos.
- [x] `GOV-001` `DOCUMENT_STANDARD.md` — padrão documental.
- [x] `GOV-002` `SOURCE_OF_TRUTH.md` — regras de canonicalidade.
- [x] `GOV-003` `TRACEABILITY_MATRIX.md` — estrutura de rastreabilidade.
- [x] `GOV-004` `DECISION_LOG.md` — decisões registradas.
- [x] `GOV-005` `CONTRIBUTING.md` — contribuição.
- [x] `.github/PULL_REQUEST_TEMPLATE.md`.
- [x] `.github/ISSUE_TEMPLATE/feature.md`.
- [x] `.github/ISSUE_TEMPLATE/bug.md`.
- [x] `.github/CODEOWNERS` — placeholder estrutural.
- [x] `.github/workflows/quality-gates.yml` — gate estrutural.
- [ ] Substituir placeholders de `CODEOWNERS` por owners reais.
- [ ] Evoluir CI estrutural para typecheck, testes, evals e security scans quando existir toolchain real.

# 2. VISÃO E FLUXO DE PRODUTO

- [x] `PROD-001` — Product Vision — `pre_approved`.
- [x] `PROD-FLOW-001` — Fluxo de Uso Omnicanal — `pre_approved`.
- [x] Princípio `planejar uma vez → operar por múltiplos canais`.
- [x] Estado canônico único como princípio transversal.
- [x] Mapa-OS + Scanner como superfície prioritária de continuidade analógica.
- [x] Gate deliverable-first antes da decomposição detalhada.
- [x] Mermaid como visualização de pré-aprovação.
- [x] Entregáveis padrão do agente: Onboarding, Status Report e Mapa-OS.
- [ ] `PROD-002` `PRODUCT_BRIEF.md` — `template_only`.
- [ ] `PROD-003` `ICP.md` — `template_only`.
- [ ] `PROD-004` `JTBD.md` — `template_only`.
- [ ] `PROD-005` `USER_JOURNEYS.md` — `template_only`.
- [ ] `PROD-006` `ROADMAP.md` — `template_only`.
- [ ] Formalizar `PRODUCT_STRUCTURE` / estrutura de produto como próximo artefato derivado da visão.

# 3. GESTÃO OMNICANAL

- [x] `PRD-OMNI-001` — Gestão Omnicanal — `pre_approved`.
- [x] `ADR-OMNI-001` — Single Canonical Work State — `accepted`.
- [x] `SPEC-WORKSPACE-001` — Workspace, Routes and Task Visualization — `pre_approved` conceitualmente.
- [x] Canais previstos: App, MCP, WhatsApp, Email, Copiloto, Mapa-OS + Scanner.
- [x] Regra: canal não é fonte de verdade.
- [x] Regra: mutação externa retorna ao estado canônico.
- [x] Regra: falha de delivery não altera estado da tarefa.
- [x] Auditabilidade de canal/actor/comando/objeto/resultado prevista no PRD.
- [ ] Especificar providers reais de WhatsApp e Email.
- [ ] Definir autenticação/identidade por canal.
- [ ] Definir conflito, ordering, cache e realtime.
- [ ] Implementar adapters omnicanal.

# 4. WORKSPACE E EXPERIÊNCIA

- [x] Rotas conceituais definidas:
  - Projeto(s)
  - Documentos
  - Calendário
  - Overview
  - Roadmap
  - Sprint
  - Agora
  - Hoje
  - Amanhã
  - Ontem
  - Copiloto
  - Mapa-OS
  - Scanner
  - Reports
  - Automações
  - Workflows
- [x] Views: `WIP 1:1`, `Lista`, `Kanban`.
- [x] Scopes: `Single Project`, `Remix Multi-project`.
- [x] Separação semântica: `StandaloneTask`, `ProjectTask`, `ProcessStep/Task`, `Deliverable`, `Action`.
- [x] Documentos definidos como anexos/recursos ligados a objetos/entregáveis.
- [ ] Definir rotas Next.js finais.
- [ ] Definir modelo técnico de portfolio/remix.
- [ ] Implementar IA/navegação e views reais.

# 5. COPILOTO E ORQUESTRAÇÃO

- [x] `SKILL-COP-001` — `copiloto-executar` registrado.
- [x] `AGENT-FLOW-001` — Copiloto orchestration flow — `pre_approved`.
- [x] Ordem operacional:
  - SYNC
  - UNDERSTAND
  - STRUCTURE
  - VISUALIZE
  - PRE_APPROVE
  - DECOMPOSE
  - EXECUTE / MANAGE
  - RECONCILE
  - REPORT
  - REPLAN
- [x] Gate de pré-aprovação antes de decompor novos planos relevantes.
- [x] `AGENT-CAPABILITY-SOURCES-001` — Productivity / Operations / MCP mapeados como fontes de capability.
- [x] Comandos registrados: `/bomdia`, `/agora`, `/estado`, `/fechardia`, `/replanejamento`.
- [x] Template de saída estruturada do orquestrador.
- [ ] Formalizar authority matrix final do Copiloto por ação/canal.
- [ ] Implementar runtime real do orquestrador no app.
- [ ] Validar integração real com fontes autorizadas do usuário.

# 6. ROTINAS, AUTOMAÇÃO E AUTOGESTÃO

- [x] `PRD-ROUTINES-001` — Modo Rotinas — `pre_approved`.
- [x] `ADR-ROUTINES-001` — Routine agentic — `accepted`.
- [x] `SPEC-ROUTINES-001` — runtime/data/delivery spec — `draft`.
- [x] `AGENT-ROUTINES-001` — descrição do Modo Rotinas — `pre_approved`.
- [x] `PROMPT-ROUTINES-001` — prompt mestre parametrizado — `pre_approved`.
- [x] `API-ROUTINE-DELIVERY-001` — contrato App Reports / Email / WhatsApp — `draft`.
- [x] Regra: rotina produz `RoutineRun` + `StatusReport`.
- [x] Regra: App Reports é persistência; canais externos são delivery adapters.
- [x] Regra: passagem do tempo não promove estado.
- [x] Regra baseline: transições automáticas somente quando determinísticas/autorizadas.
- [ ] Implementar scheduler/runner real.
- [ ] Implementar authority gate real.
- [ ] Implementar report repository real.
- [ ] Implementar delivery adapters.
- [ ] Criar testes de idempotência, retry e reconciliação.

# 7. MAPA-OS

- [x] `SKILL-MAPA-OS-001` — `executar-mapa-os v1.1.0` registrado.
- [x] Mapa-OS definido como entregável analógico/imprimível gerado pelo agente.
- [x] `SKILL-MAPA-OS-ASSETS-001` — índice interno dos ativos.
- [x] Dois prompts internos destacados:
  - `PROMPT-MAPA-001` Prompt Mestre Prisma.
  - `PROMPT-MAPA-002` Exemplo Preenchido, `example_only`.
- [x] Template interno oficial `TEMPLATE-MAPA-001` Prisma A4 V4.
- [x] 100 placeholders canônicos no template Prisma.
- [x] Namespaces `DOC_*`, `EPIC_*`, `CALENDAR_*`, `RESULT_*`.
- [x] Workflows internos:
  - `WF-MAPA-001` Build Mapa-OS.
  - `WF-MAPA-002` Prisma 7d.
  - `WF-MAPA-003` Example Test, `example_only`.
- [x] Projeções: mapa operacional, Agora/Próximo/Depois, status terminal, Prisma 7d.
- [x] WIP 1 entrega → 1 fluxo → 1 ação preservado no contrato da skill.
- [x] Evidência e dependência preservadas como regras de elegibilidade.
- [ ] Integrar geração do Mapa-OS ao runtime real do app.
- [ ] Implementar histórico/versionamento de Mapas emitidos.

# 8. SCANNER

- [x] `PRD-SCANNER-001` — registrado de fonte.
- [x] `ADR-SCANNER-001` — arquitetura de reconhecimento visual — registrado de fonte.
- [x] `SPEC-SCANNER-001` — spec técnica — registrado de fonte.
- [x] `API-SCANNER-ACTION-001` — contrato `VisualSymbolId → command → domain result`.
- [x] Boundary: Mapa-OS gera superfície; Scanner reconhece; domínio executa.
- [x] Símbolos V1 registrados: Copiloto, Seletor, Feito.
- [x] Template físico de faixa de símbolos com placeholders.
- [x] Configuração símbolo → VisualSymbolId → comando → ação/policy prevista no fluxo omnicanal.
- [ ] Elaborar plano de implementação do Scanner.
- [ ] Materializar registry de símbolos configuráveis no data model.
- [ ] Implementar visual encoder / matcher / latch / dispatcher.
- [ ] Implementar feedback e Undo conforme policy.
- [ ] Criar dataset/evals de reconhecimento e falsos positivos.

# 9. ENTREGÁVEIS E TEMPLATES

- [x] Política global `{{UPPER_SNAKE_CASE}}` para placeholders.
- [x] `DELIV-ONB-001` — onboarding Copiloto + Mapa-OS + Scanner.
- [x] `DELIV-ROUT-001` — Status Report HTML canônico.
- [x] `DELIV-ROUT-002` — variantes App Reports / Email / WhatsApp.
- [x] `DELIV-MAPA-001` — mapa operacional.
- [x] `DELIV-MAPA-002` — Agora / Próximo / Depois.
- [x] `DELIV-MAPA-003` — status terminal.
- [x] `DELIV-MAPA-004` — Prisma 7d payload.
- [x] `DELIV-MAPA-005` — Prisma A4 V4 analógico.
- [x] `DELIV-MAPA-006` — faixa física Scanner.
- [x] `DELIV-COP-001..005` — outputs dos comandos do Copiloto.
- [x] `DELIV-COP-006` — output estruturado do orquestrador.
- [x] Modelos de apoio preservados e parametrizados.
- [ ] Definir versionamento formal de entregáveis emitidos por usuário/projeto.

# 10. MCP E GESTÃO POR OUTRAS AIS

- [x] MCP registrado como capability/referência do fluxo omnicanal.
- [x] Princípio: MCP expõe capabilities e não substitui domínio/authority.
- [x] Fontes `PRD-MCP.md` + Master Index fornecido foram mapeadas como referência.
- [x] Gate de implementação do MCP preservado; não foi promovido a implementado.
- [ ] Importar/normalizar PRD MCP como artefato canônico do blueprint quando autorizado pelo gate próprio.
- [ ] Definir tool registry EXECUTAR final.
- [ ] Definir scopes/auth/tenant propagation do MCP.
- [ ] Implementar e testar MCP server/tools.

# 11. DOCUMENTAÇÃO GENÉRICA DE PRODUTO/REQUISITOS

Estrutura criada, ainda majoritariamente `template_only`:

- [ ] `PRODUCT_BRIEF.md`.
- [ ] `ICP.md`.
- [ ] `JTBD.md`.
- [ ] `USER_JOURNEYS.md`.
- [ ] `ROADMAP.md`.
- [ ] `PRD.md` genérico.
- [ ] `FUNCTIONAL_REQUIREMENTS.md`.
- [ ] `NON_FUNCTIONAL_REQUIREMENTS.md`.
- [ ] `ACCEPTANCE_CRITERIA.md`.
- [ ] `OUT_OF_SCOPE.md`.

# 12. DOMÍNIO

Estrutura criada, conteúdo canônico ainda a preencher/consolidar:

- [ ] `DOMAIN_MODEL.md`.
- [ ] `GLOSSARY.md`.
- [ ] `BUSINESS_RULES.md`.
- [ ] `STATE_MACHINES.md`.
- [ ] `EVENT_CATALOG.md`.

Prioridade: consolidar objetos `Project`, `Process`, `Deliverable`, `Task`, `Action`, `Evidence`, `Routine`, `StatusReport`, `WorkflowDefinition`, `Attachment`, `VisualSymbol`, `DomainCommand`.

# 13. ARQUITETURA BASE

Templates estruturados:

- [ ] `SYSTEM_ARCHITECTURE.md` — preencher arquitetura final.
- [ ] `SYSTEM_CONTEXT.md`.
- [ ] `CONTAINER_COMPONENT_MAP.md`.
- [ ] `DATA_FLOW.md`.
- [ ] `DEPENDENCY_MAP.md`.
- [x] ADR index/template disponíveis.
- [x] ADRs específicos de Rotinas, Scanner e Omnichannel registrados.

# 14. DADOS E SUPABASE

Estrutura criada:

- [ ] `DATA_MODEL.md` — preencher.
- [ ] `ERD.md` — preencher.
- [ ] `DATA_DICTIONARY.md` — preencher.
- [ ] `MIGRATION_POLICY.md` — preencher.
- [ ] `RLS_MATRIX.md` — preencher.
- [ ] `RETENTION_POLICY.md` — preencher.
- [ ] `SEED_DATA.md` — preencher.
- [x] `supabase/` com pastas de migrations/functions/tests e `seed.sql` placeholder.
- [ ] Criar migrations reais.
- [ ] Criar schema real e RLS real.
- [ ] Criar tenancy e constraints.

# 15. API E CONTRATOS

- [x] `OPENAPI.yaml` placeholder estrutural.
- [x] `ERROR_CONTRACT.md` estrutura.
- [x] `WEBHOOKS.md` estrutura.
- [x] `EVENT_CONTRACTS.md` estrutura.
- [x] `SCHEMAS/README.md` estrutura.
- [x] `API-ROUTINE-DELIVERY-001` específico.
- [x] `API-SCANNER-ACTION-001` específico.
- [ ] Formalizar `DomainMutationResult` canônico.
- [ ] Formalizar APIs reais do app.
- [ ] Formalizar schemas executáveis por versão.

# 16. FRONTEND

Estrutura criada:

- [x] `SPEC-WORKSPACE-001` conceitualmente pré-aprovado.
- [ ] `INFORMATION_ARCHITECTURE.md` — preencher com workspace aprovado.
- [ ] `ROUTE_MAP.md` — derivar rotas finais.
- [ ] `UI_STATES.md`.
- [ ] `COMPONENT_INVENTORY.md`.
- [ ] `DESIGN_SYSTEM.md`.
- [ ] `ACCESSIBILITY.md`.
- [ ] `RESPONSIVE_RULES.md`.
- [ ] Implementar frontend real.

# 17. BACKEND

Templates estruturados:

- [ ] `SERVICE_BOUNDARIES.md`.
- [ ] `USE_CASES.md`.
- [ ] `ERROR_HANDLING.md`.
- [ ] `IDEMPOTENCY.md`.
- [ ] `JOBS_AND_SCHEDULERS.md`.
- [ ] Implementar RoutineRunner, reconciler, domain command bus e adapters.

# 18. SEGURANÇA

Templates estruturados:

- [ ] `SECURITY.md`.
- [ ] `THREAT_MODEL.md`.
- [ ] `AI_THREAT_MODEL.md`.
- [ ] `PERMISSION_MATRIX.md`.
- [ ] `SECRETS_POLICY.md`.
- [ ] `PROMPT_INJECTION_POLICY.md`.
- [ ] `SUPPLY_CHAIN_POLICY.md`.
- [ ] `SECURITY_TEST_PLAN.md`.
- [ ] Consolidar authority/policy específica para canais omnicanal e Scanner.

# 19. TESTES E EVALS

Estrutura criada:

- [x] diretórios unit/integration/contract/e2e/security.
- [x] datasets placeholder em `evals/`.
- [ ] `TEST_STRATEGY.md` — preencher/validar.
- [ ] `UNIT_TEST_PLAN.md`.
- [ ] `INTEGRATION_TEST_PLAN.md`.
- [ ] `E2E_TEST_PLAN.md`.
- [ ] `CONTRACT_TEST_PLAN.md`.
- [ ] `AGENT_EVAL_STRATEGY.md`.
- [ ] `EVAL_DATASET_SCHEMA.md`.
- [ ] `GRADERS.md`.
- [ ] `QUALITY_GATES.md`.
- [ ] Criar testes executáveis do app.
- [ ] Criar evals executáveis de Copiloto, Mapa-OS, Rotinas e Scanner.

# 20. OBSERVABILIDADE

Templates estruturados:

- [ ] `OBSERVABILITY.md`.
- [ ] `TRACE_SCHEMA.md`.
- [ ] `LOGGING_POLICY.md`.
- [ ] `METRICS.md`.
- [ ] `SLO_SLA.md`.
- [ ] `AI_COST_BUDGET.md`.
- [ ] Definir traces omnicanal, delivery receipts e routine/scanner metrics.

# 21. DEVOPS E RELEASE

Estrutura criada:

- [ ] `LOCAL_DEVELOPMENT.md`.
- [ ] `ENVIRONMENT_MATRIX.md`.
- [ ] `CI_CD.md`.
- [ ] `DEPLOYMENT.md`.
- [ ] `ROLLBACK.md`.
- [ ] `RUNBOOK.md`.
- [ ] `INCIDENT_RESPONSE.md`.
- [ ] `BACKUP_RESTORE.md`.
- [ ] `RELEASE_CHECKLIST.md`.
- [ ] `RELEASE_NOTES.md`.
- [ ] `KNOWN_ISSUES.md`.

# 22. PERSONALIZAÇÃO

Templates estruturados:

- [ ] `USER_PROFILE_SCHEMA.md`.
- [ ] `PREFERENCE_SCHEMA.md`.
- [ ] `MEMORY_SCHEMA.md`.
- [ ] `MEMORY_WRITE_POLICY.md`.
- [ ] `INSTRUCTION_COMPOSITION.md`.
- [ ] `CONTEXT_PRECEDENCE.md`.
- [ ] `PRIVACY_BOUNDARIES.md`.
- [ ] Formalizar integração do Productivity Copilot com perfil/contexto do usuário.

# 23. CÓDIGO / RUNTIME

- [x] Estrutura `src/` criada com boundaries documentais para app, components, features, domain, agents, tools, guardrails, prompts, schemas, services, repositories e lib.
- [x] `instrumentation.ts` placeholder.
- [ ] `package.json`/toolchain funcional não estabelecido neste blueprint.
- [ ] Aplicação funcional não declarada.
- [ ] Runtime do agente não declarado implementado.
- [ ] Runtime de Rotinas não declarado implementado.
- [ ] Scanner não declarado implementado.
- [ ] MCP não declarado implementado.
- [ ] WhatsApp/Email adapters não declarados implementados.
- [ ] Supabase schema/migrations reais não declarados implementados.

# 24. STATUS GLOBAL

| Camada | Estado |
|---|---|
| Blueprint de governança | ESTRUTURADO |
| Product Vision | PRE_APPROVED |
| Fluxo omnicanal | PRE_APPROVED |
| ADR omnicanal | ACCEPTED |
| Workspace conceitual | PRE_APPROVED |
| Copiloto flow | PRE_APPROVED |
| Rotinas | PRD/MODE/PROMPT PRE_APPROVED + ADR ACCEPTED + SPEC DRAFT |
| Mapa-OS | REGISTERED v1.1.0 |
| Scanner | REGISTERED_FROM_SOURCE |
| Entregáveis/templates | REGISTERED / PLACEHOLDERIZED |
| MCP | REGISTERED_REFERENCE / GATE PENDENTE |
| Domínio detalhado | TEMPLATE_ONLY / PENDENTE |
| Data model real | PENDENTE |
| Frontend real | PENDENTE |
| Backend real | PENDENTE |
| Integrações reais | PENDENTE |
| Testes/evals reais | PENDENTE |
| Release | NÃO DECLARADO |

# 25. PRÓXIMA CADEIA CANÔNICA RECOMENDADA

1. [ ] `PRODUCT_STRUCTURE` — formalizar módulos, objetos e boundaries do produto.
2. [ ] Preencher `PRODUCT_BRIEF`, `ICP`, `JTBD`, `USER_JOURNEYS`.
3. [ ] Consolidar `DOMAIN_MODEL` e `GLOSSARY`.
4. [ ] Formalizar `BUSINESS_RULES`, `STATE_MACHINES`, `EVENT_CATALOG`.
5. [ ] Consolidar requisitos/AC transversais.
6. [ ] Projetar `DATA_MODEL`, ERD e RLS.
7. [ ] Formalizar command/event/API contracts.
8. [ ] Resolver decisões técnicas pendentes de Workspace/Omnichannel.
9. [ ] Criar plano de implementação de Rotinas.
10. [ ] Criar plano de implementação de Scanner.
11. [ ] Submeter MCP ao gate próprio e somente então planejar implementação.
12. [ ] Implementar domínio + persistência antes dos adapters externos.
13. [ ] Implementar App/Copiloto/Mapa-OS como primeiras superfícies sobre o estado canônico.
14. [ ] Implementar Scanner e adapters MCP/WhatsApp/Email conforme authority policies.
15. [ ] Criar testes, evals, observabilidade e quality gates reais.

## Regra final

`estruturado ≠ aprovado ≠ implementado ≠ testado ≠ verificado ≠ released`.

O checklist deve ser atualizado sempre que um artefato mudar de estado ou quando uma capability passar de documentação para implementação verificável.
