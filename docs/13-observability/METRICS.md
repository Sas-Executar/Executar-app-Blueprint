---
id: OBS-004
type: metrics_contract
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
related:
  - OBS-BIZ-001
  - UNIT-ECON-001
  - PRICING-001
---
# EXECUTAR — Metrics Contract

## 1. Regra

Targets marcados `PROPOSED` são guardrails de planejamento, não desempenho observado.

| Metric | Definition | Unit | Source | Target / State |
|---|---|---|---|---|
| MRR | receita recorrente mensal normalizada | BRL/mês | billing | observed após runtime |
| ARR | MRR × 12 | BRL/ano | derived | observed após MRR |
| Paid Accounts | contas pagantes ativas | count | billing | observed |
| Paid Users/Seats | usuários/seats cobertos por assinatura ativa | count | billing/domain | observed |
| ARPA | MRR / paid accounts | BRL/account | derived | observed |
| ARPU | MRR / paid users | BRL/user | derived | observed |
| Trial Starts | trials iniciados no período | count | billing/product | observed |
| Activation Rate | trials/usuários que atingem activation contract | % | product | baseline GAP |
| Trial→Paid | trials convertidos / trials elegíveis | % | billing | baseline GAP |
| Upgrade Rate | contas que sobem de plano / contas elegíveis | % | billing | baseline GAP |
| Logo Churn | contas perdidas / contas no início do período | %/mês | billing | baseline GAP |
| Gross Revenue Churn | MRR perdido+contraction / MRR inicial | %/mês | billing | baseline GAP |
| NRR | (MRR inicial - perdas - contraction + expansion) / MRR inicial | % | billing | calcular quando aplicável |
| AI COGS | custo reconciliado de modelos | BRL | provider usage | observed_reconciled |
| AI COGS / Revenue | AI COGS / receita reconhecida | % | derived | Solo ≤8%; Pro ≤10%; Business ≤12% PROPOSED |
| WhatsApp/Channel COGS | custo de mensagens/canais pagos | BRL | provider | observed_reconciled |
| Payment COGS | taxas de gateway/billing | BRL | gateway | observed_reconciled |
| Variable Infra COGS | infraestrutura variável atribuível | BRL | infra billing | observed_reconciled |
| Tax Provision | provisão tributária do período | BRL | finance/accounting | reconciled |
| Contribution | receita - imposto - COGS variável | BRL | derived | observed derived |
| Contribution Margin | contribution / receita | % | derived | Solo ≥70%; Pro ≥65%; Business ≥60% PROPOSED |
| CAC | aquisição atribuída / novas contas pagantes | BRL/account | finance+attribution | baseline GAP |
| CAC Payback | CAC / contribuição mensal da coorte adquirida | months | derived | Solo/Pro ≤6; Business ≤9 PROPOSED |
| LTV | valor de contribuição de coorte conforme método declarado | BRL | cohort analysis | somente amostra madura |
| LTV/CAC | LTV / CAC | ratio | derived | somente com LTV e CAC confiáveis |
| Plan Mix | distribuição de contas/receita por plano | % | billing | observed |
| Annual Mix | participação anual vs mensal | % | billing | observed |
| Credit Overage Rate | contas com top-up / contas elegíveis | % | billing+AI | baseline GAP |

## 2. Dimensions mínimas

Sempre que a cardinalidade e privacidade permitirem:

- plan;
- billing interval;
- account/workspace;
- capability;
- channel;
- model/provider;
- acquisition source;
- cohort month;
- country/currency sem geolocalização desnecessariamente granular.

## 3. Activation

A definição final de `activation_completed` permanece `GAP` até Product/ICP/JTBD/Journey serem consolidados e haver validação comportamental. Não inferir activation apenas por login ou criação de conta.

## 4. LTV

Não usar `1 / churn` como LTV oficial sem declarar a hipótese. Para reporting canônico, preferir análise de coorte de contribuição quando houver maturidade suficiente.

## 5. Alertas

Alertas econômicos são propostos em `OBS-BIZ-001`. Alertas técnicos permanecem dependentes de SLOs e runtime reais.
