---
id: OBS-001
type: observability_architecture
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
related:
  - OBS-002
  - OBS-004
  - OBS-006
  - OBS-BIZ-001
---
# EXECUTAR — Observability Architecture

## 1. Objetivo

Definir como o EXECUTAR deve observar comportamento técnico, agentic e econômico sem confundir telemetria com estado de domínio.

`pre_approved` valida o contrato documental; não declara pipeline, dashboards ou alertas implementados.

## 2. Princípio

`Domain state ≠ telemetry state`.

Eventos de observabilidade descrevem execução, custo, latência, resultado e uso. Eles não promovem `Task`, `Action`, `Deliverable`, `Routine` ou qualquer outro objeto de domínio.

## 3. Fluxo conceitual

`Runtime / Agent / Channel / Billing → Telemetry Events → Trace/Event Store → Reconciliation → Metrics → Dashboards/Alerts → Learning/Pricing Review`

## 4. Pilares

### Logs
- diagnóstico operacional;
- erros;
- políticas/guardrails;
- delivery failures;
- sem segredos ou PII desnecessária.

### Traces
- request/session;
- agent run;
- tool call;
- model call;
- channel delivery;
- routine run;
- domain mutation reference;
- custo atribuível.

### Metrics
- disponibilidade/latência/erro;
- comportamento do agente;
- produto/ativação/retenção;
- business/unit economics.

### Economic telemetry
Regida por `OBS-BIZ-001` e `OBS-006`.

## 5. Correlation IDs

Quando aplicável, propagar:

- `trace_id`;
- `request_id`;
- `session_id`;
- `agent_run_id`;
- `tool_call_id`;
- `routine_run_id`;
- `delivery_id`;
- `mutation_id`;
- `account_id`;
- `user_id` interno.

## 6. Separação de estados

Telemetria pode registrar que uma operação foi tentada, concluída ou falhou. Isso não substitui a confirmação do domínio.

Exemplo:

`channel.message_delivered` não altera estado de tarefa.

`ai.usage_recorded` não implica sucesso da ação de negócio.

`scanner recognition success` não implica mutação de domínio sem `DomainMutationResult` correspondente.

## 7. Evidência e reconciliação

Telemetria econômica deve distinguir:

- `observed_unreconciled` — evento local sem confirmação financeira externa;
- `observed_reconciled` — conciliado com provider/billing/accounting;
- `derived_observed` — métrica derivada de dados reconciliados.

## 8. Privacidade

- coletar somente campos necessários;
- não registrar conteúdo integral de prompts/documentos por padrão;
- não registrar secrets/tokens de autenticação;
- usar IDs internos no lugar de email/telefone em analytics;
- retention e acesso permanecem dependentes dos artefatos de segurança/privacidade ainda pendentes.

## 9. Implementação

Ainda `GAP`:

- stack de observabilidade final;
- event transport;
- storage/warehouse;
- dashboards;
- alerting;
- retention;
- acesso/roles;
- implementação no runtime.
