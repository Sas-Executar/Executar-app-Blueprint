---
id: OBS-BIZ-001
type: business_telemetry_contract
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
feeds:
  - UNIT-ECON-001
  - PRICING-001
  - OBS-004
  - OBS-006
---
# EXECUTAR — Business & Unit Economics Telemetry Contract

## 1. Objetivo

Definir a telemetria mínima para transformar as hipóteses comerciais de `BUS-MODEL-001`, `PRICING-001` e `UNIT-ECON-001` em dados observáveis após existir runtime real.

Este documento é um contrato de instrumentação. `pre_approved` não significa que os eventos, pipelines, dashboards ou alertas já estejam implementados.

## 2. Princípio

`PREÇO/HIPÓTESE → EVENTO → CUSTO/RECEITA ATRIBUÍVEL → MÉTRICA → GUARDRAIL → REVALIDAÇÃO`

Nenhum preço, CAC, churn, LTV, ARPA, COGS ou margem passa a `observed` sem evento ou fonte financeira rastreável.

## 3. Entidades de atribuição

Toda telemetria econômica deve, quando aplicável, ser atribuível a:

- `account_id`;
- `user_id` interno;
- `subscription_id`;
- `plan_id`;
- `billing_interval`;
- `workspace_id` quando Business;
- `capability_id`;
- `channel`;
- `provider`;
- `model` quando IA;
- `trace_id` / `request_id`;
- `occurred_at` em UTC.

Não registrar PII desnecessária em eventos analíticos.

## 4. Eventos mínimos

### Receita e assinatura

- `billing.trial_started`
- `billing.trial_converted`
- `billing.subscription_started`
- `billing.subscription_renewed`
- `billing.plan_changed`
- `billing.subscription_cancelled`
- `billing.invoice_paid`
- `billing.invoice_failed`
- `billing.refund_recorded`
- `billing.payment_fee_recorded`

### Ativação e retenção

- `product.activation_completed`
- `product.core_action_completed`
- `product.mapa_os_generated`
- `product.scanner_action_completed`
- `product.status_report_generated`
- `product.routine_run_completed`

### IA

- `ai.usage_recorded`
- `ai.credit_consumed`
- `ai.credit_topup_purchased`

Campos mínimos de `ai.usage_recorded`:

- provider;
- model;
- capability;
- input_tokens;
- output_tokens;
- cached_input_tokens quando disponível;
- provider_cost_native;
- native_currency;
- fx_rate_brl;
- cost_brl;
- account_id;
- user_id;
- trace_id.

### WhatsApp e canais pagos

- `channel.message_sent`
- `channel.message_delivered`
- `channel.message_failed`
- `channel.cost_recorded`

Campos mínimos de custo:

- channel;
- provider;
- message/category type;
- provider_cost_native;
- currency;
- fx_rate_brl;
- cost_brl;
- account_id;
- trace_id quando houver.

### Infraestrutura variável

- `infra.variable_cost_recorded`

Deve permitir atribuição por serviço e, quando tecnicamente possível, por conta/plano/capability.

## 5. Métricas obrigatórias

### Receita

- MRR;
- ARR;
- paid accounts;
- paid users/seats;
- ARPA;
- ARPU;
- plan mix;
- annual-plan mix;
- expansion MRR;
- contraction MRR.

### Funil

- trial starts;
- activation rate;
- trial-to-paid conversion;
- upgrade rate;
- downgrade rate.

### Retenção

- logo churn;
- gross revenue churn;
- net revenue retention quando houver expansão suficiente para cálculo útil.

### Custo

- AI COGS total e por plano;
- AI COGS por capability;
- WhatsApp/channel COGS;
- payment processing COGS;
- infrastructure variable COGS;
- tax provision;
- total variable COGS.

### Economia unitária

- contribution per account;
- contribution margin por plano;
- blended contribution margin;
- CAC;
- CAC payback;
- LTV quando houver coorte madura;
- LTV/CAC quando ambos forem observáveis.

## 6. Fórmulas canônicas

`MRR = soma da receita recorrente mensal normalizada das assinaturas ativas`

`ARR = MRR × 12`

`ARPA = MRR / paid_accounts`

`ARPU = MRR / paid_users`

`CAC = sales_and_marketing_spend_attributed / new_paying_accounts`

`CAC_PAYBACK_MONTHS = CAC / monthly_contribution_per_new_account`

`CONTRIBUTION = recognized_revenue - tax_provision - payment_fees - AI_COGS - channel_COGS - variable_infra_COGS - other_variable_service_COGS`

`CONTRIBUTION_MARGIN = CONTRIBUTION / recognized_revenue`

`LOGO_CHURN = lost_paying_accounts / paying_accounts_at_period_start`

`GROSS_REVENUE_CHURN = lost_MRR_and_contraction / MRR_at_period_start`

LTV não deve ser publicado com base apenas em poucos meses iniciais. O método de LTV deve declarar horizonte/coorte e maturidade da amostra.

## 7. Guardrails comerciais PROPOSED

Até haver dados observados, usar somente como guardrail de planejamento:

| Métrica | Solo | Pro | Business |
|---|---:|---:|---:|
| AI COGS / revenue | ≤ 8% | ≤ 10% | ≤ 12% |
| Contribution margin | ≥ 70% | ≥ 65% | ≥ 60% |
| CAC payback | ≤ 6 meses | ≤ 6 meses | ≤ 9 meses por conta |

Os thresholds acima são `PROPOSED`, não benchmarks observados do EXECUTAR.

## 8. Revalidação de pricing

Abrir revisão de `PRICING-001` quando qualquer condição persistir por dois períodos mensais completos:

1. contribution margin abaixo do guardrail do plano;
2. AI COGS/revenue acima do guardrail;
3. channel COGS alterar materialmente a margem do Pro/Business;
4. CAC payback exceder o guardrail;
5. plan mix real divergir materialmente das premissas de `UNIT-ECON-001`;
6. mudança relevante de tarifa de provedor, câmbio, gateway ou regime tributário.

A revisão pode resultar em preço, franquia, routing, custo incluído ou pacote diferente. Não deve alterar preço publicado automaticamente.

## 9. Dashboard mínimo

O primeiro dashboard financeiro-operacional deve apresentar, por período e plano:

- MRR/ARR;
- paid accounts/users;
- ARPA/ARPU;
- activation e trial conversion;
- churn;
- AI COGS;
- WhatsApp/channel COGS;
- payment fees;
- variable infrastructure;
- tax provision;
- contribution e contribution margin;
- CAC e payback quando o gasto de aquisição estiver disponível.

## 10. Estados de evidência

- Antes do runtime: `PROPOSED` / `GAP`.
- Evento gerado sem reconciliação financeira: `observed_unreconciled`.
- Evento reconciliado com provider/billing/accounting: `observed_reconciled`.
- Métrica calculada sobre dados reconciliados: `derived_observed`.

Nenhum dashboard deve apresentar hipótese e observado no mesmo campo sem identificação explícita.

## 11. Implementação pendente

`GAP` até existir runtime:

- event producer real;
- event store/warehouse;
- reconciliação com billing/gateway;
- reconciliação com provedores de IA e canais;
- tax provision real;
- dashboard;
- alertas;
- testes de integridade e idempotência.
