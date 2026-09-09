---
id: OBS-002
type: trace_schema
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
related:
  - OBS-001
  - OBS-BIZ-001
  - OBS-006
---
# EXECUTAR — Trace Schema

## 1. Objetivo

Definir o envelope mínimo de correlação para request, agent run, tool/model calls, rotinas, canais, mutações e custos.

## 2. Envelope comum

```yaml
trace_id: string
span_id: string
parent_span_id: string|null
request_id: string|null
session_id: string|null
account_id: string|null
workspace_id: string|null
user_id: string|null
plan_id: string|null
occurred_at: datetime_utc
component: string
event_name: string
outcome: success|partial|blocked|error
error_class: string|null
latency_ms: number|null
```

IDs devem ser internos. Não usar email/telefone como identificadores analíticos.

## 3. Agent/tool/model spans

Quando aplicável:

```yaml
agent_run_id: string|null
tool_call_id: string|null
routine_run_id: string|null
capability_id: string|null
provider: string|null
model: string|null
input_tokens: number|null
output_tokens: number|null
cached_input_tokens: number|null
provider_cost_native: number|null
native_currency: string|null
fx_rate_brl: number|null
cost_brl: number|null
```

## 4. Channel spans

```yaml
delivery_id: string|null
channel: APP_REPORTS|EMAIL|WHATSAPP|MCP|COPILOT|SCANNER|null
provider: string|null
message_category: string|null
provider_cost_native: number|null
cost_brl: number|null
delivery_status: string|null
```

Delivery status não substitui domain state.

## 5. Domain correlation

Quando uma ação produzir mutação:

```yaml
mutation_id: string|null
object_type: string|null
object_id: string|null
previous_state: string|null
new_state: string|null
evidence_id: string|null
```

A telemetria referencia o resultado canônico do domínio; não o cria.

## 6. Billing/economic correlation

```yaml
subscription_id: string|null
invoice_id: string|null
billing_interval: monthly|annual|null
recognized_revenue_brl: number|null
payment_fee_brl: number|null
tax_provision_brl: number|null
reconciliation_state: proposed|observed_unreconciled|observed_reconciled|derived_observed
```

## 7. Privacy and content

Por padrão, trace não deve armazenar:

- conteúdo integral do prompt;
- conteúdo integral de documentos do usuário;
- credenciais/tokens;
- telefone/email quando um ID interno resolver a correlação.

A captura de payloads para debugging/evals deve ter policy específica e controles de acesso/retention.

## 8. Idempotência

Eventos financeiros e de custo devem carregar um identificador estável de origem/provider quando disponível para impedir dupla contabilização durante retries/reconciliation.

## 9. GAP

Persistência, sampling, retention, schema registry e backend de tracing ainda não estão implementados.
