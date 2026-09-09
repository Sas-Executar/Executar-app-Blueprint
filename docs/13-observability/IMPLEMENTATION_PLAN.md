---
id: OBS-PLAN-001
type: implementation_plan
status: draft
version: 0.9.0
owner: null
project: EXECUTAR
depends_on:
  - OBS-001
  - OBS-002
  - OBS-004
  - OBS-006
  - OBS-BIZ-001
---
# EXECUTAR — Telemetry Implementation Plan

## Objetivo

Transformar os contratos de observabilidade em instrumentação executável quando o runtime real do aplicativo existir.

Este plano não declara código implementado.

## Ordem recomendada

1. **Event envelope** — implementar `OBS-002` como schema compartilhado.
2. **Billing events** — trial, subscription, invoice, refund, fees.
3. **AI meter** — registrar modelo, tokens, capability e custo por trace/account.
4. **Channel meter** — Email/WhatsApp/outros provedores pagos com delivery + custo.
5. **Variable infrastructure attribution** — registrar custos atribuíveis quando disponível.
6. **Reconciliation jobs** — comparar eventos locais com provider/gateway/billing.
7. **Metrics layer** — materializar fórmulas de `OBS-004`.
8. **Economic dashboard** — plano, MRR/ARR, ARPA/ARPU, COGS, contribution, CAC/payback.
9. **Alerts/guardrails** — aplicar thresholds `PROPOSED` de `OBS-BIZ-001`/`OBS-006`.
10. **Pricing review loop** — alimentar `PRICING-001` sem alteração automática de preço.

## Primeiro milestone executável

Quando houver runtime funcional, o primeiro slice deve comprovar end-to-end:

`one paid account → one invoice → one AI call → one reconciled AI cost → one contribution calculation`

Definition of Done:

- trace_id presente;
- account/plan atribuídos;
- receita reconciliada;
- fee de pagamento reconciliada;
- uso de IA reconciliado;
- custo em BRL registrado com FX;
- métrica de contribution reproduzível;
- teste de idempotência impede dupla contabilização.

## Segundo milestone

Adicionar:

- trial/activation/conversion;
- churn;
- WhatsApp/channel COGS;
- plan mix;
- CAC attribution.

## Dependências/GAP

Antes de implementar no app é necessário:

- runtime/toolchain funcional em `src/`;
- billing provider escolhido;
- schema/data model reais;
- política de privacy/retention;
- provider real de WhatsApp/Email;
- estratégia de warehouse/analytics;
- regime tributário e fonte de tax provision.

## Testes obrigatórios

- duplicate event/idempotency;
- retry sem dupla contabilização;
- currency/FX conversion;
- provider reconciliation mismatch;
- subscription upgrade/downgrade;
- refund;
- annual billing normalization para MRR;
- ausência de PII não necessária no payload;
- falha de telemetria não promove domain state.
