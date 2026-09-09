---
id: BUS-INDEX-001
type: business_domain_index
status: active
version: 1.1.0
owner: null
---
# EXECUTAR — Business & Monetization

Domínio para modelo de negócio, pricing, unit economics e guardrails financeiros do EXECUTAR.

## Artefatos

- `BUS-MODEL-001` — `BUSINESS_MODEL.md`
- `PRICING-001` — `PRICING.md`
- `UNIT-ECON-001` — `UNIT_ECONOMICS.md`
- `UNIT-ECON-DATA-001` — `unit-economics-scenarios.csv`
- `OBS-BIZ-001` — `../13-observability/BUSINESS_TELEMETRY.md` — contrato de instrumentação para transformar hipóteses em métricas observadas.

## Cadeia operacional

`BUS-MODEL-001 → PRICING-001 → UNIT-ECON-001 → OBS-BIZ-001 → observed/reconciled metrics → pricing revalidation`

## Regra de evidência

- `CORPUS_DIRECT`: preço/tarifa/fato explicitamente publicado por fonte externa consultada ou já documentado no blueprint.
- `CORPUS_DERIVED`: cálculo reproduzível derivado de premissas documentadas.
- `PROPOSED`: preço, CAC, churn, mix, OPEX ou política comercial ainda não validada em operação.
- `GAP`: desempenho real ainda não observado.
- `observed_unreconciled`: evento observado, mas ainda não conciliado com fonte financeira/provider.
- `observed_reconciled`: evento conciliado com billing/provider/accounting.
- `derived_observed`: métrica calculada a partir de observações conciliadas.

Nenhum valor deste domínio deve ser interpretado como preço lançado, desempenho financeiro observado ou recomendação tributária definitiva sem promoção explícita de estado.
