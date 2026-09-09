---
id: OBS-006
type: ai_cost_budget
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
related:
  - UNIT-ECON-001
  - OBS-BIZ-001
---
# EXECUTAR — AI Cost Budget

## 1. Objetivo

Controlar custo de IA por plano, capability e conta, preservando a proposta de valor sem prometer uso ilimitado.

## 2. Roteamento econômico

Baseline `PROPOSED`:

- ações simples e frequentes → modelo de menor custo compatível;
- estruturação/análise média → modelo intermediário;
- decisões/replanejamento complexo → modelo de maior capacidade quando necessário.

A escolha do modelo deve ser orientada por qualidade mínima + custo, não apenas pelo plano comercial.

## 3. Campos obrigatórios por chamada

Quando o provider disponibilizar:

- provider;
- model;
- capability_id;
- plan_id;
- account_id;
- user_id interno;
- trace_id;
- input_tokens;
- output_tokens;
- cached_input_tokens;
- tool/runtime cost adicional quando aplicável;
- native_currency;
- provider_cost_native;
- fx_rate_brl;
- cost_brl;
- started_at;
- completed_at;
- outcome/error_class.

## 4. Guardrails PROPOSED

| Plano | AI COGS / receita recorrente |
|---|---:|
| Solo | ≤ 8% |
| Pro | ≤ 10% |
| Business | ≤ 12% |

São limites de planejamento até telemetria real.

## 5. Franchises e Execution Credits

A arquitetura comercial prevista é:

`assinatura → franquia de uso incluída → aviso → Execution Credits/top-up`

Regras:

1. não expor tokens como unidade principal ao usuário;
2. não degradar silenciosamente qualidade sem policy explícita;
3. não bloquear comandos locais/ações de domínio que não dependem de IA por esgotamento de créditos;
4. registrar consumo por capability;
5. permitir reconciliar top-ups com billing;
6. limites exatos de créditos continuam `GAP` até dados reais de uso.

## 6. Métricas

- AI COGS total;
- AI COGS/account;
- AI COGS/user;
- AI COGS/plan;
- AI COGS/capability;
- AI COGS/model;
- tokens/call;
- cost/successful capability outcome;
- cached-token ratio quando aplicável;
- overage/top-up rate.

## 7. Alertas econômicos

Abrir investigação quando:

- AI COGS/revenue ultrapassar guardrail do plano em período mensal;
- uma capability concentrar custo desproporcional ao uso/valor;
- mudança de preço/provider/câmbio alterar materialmente o custo estimado;
- P95 de custo por execução crescer materialmente sem aumento equivalente de valor/qualidade.

`materialmente` requer threshold operacional posterior; permanece `GAP` até distribuição real.

## 8. Reconciliation

O evento local de uso é `observed_unreconciled` até comparação com billing/usage do provider. Somente custo conciliado deve alimentar reporting financeiro canônico.

## 9. Não implementado

Ainda não existem no blueprint:

- meter real;
- provider reconciliation job;
- credit ledger;
- enforcement runtime;
- top-up billing;
- alerting automático.
