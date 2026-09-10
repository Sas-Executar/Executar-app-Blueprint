# SRC-METHOD-EXECUTION-001

| Campo | Valor |
|---|---|
| `SOURCE_ID` | `SRC-METHOD-EXECUTION-001` |
| `source_name` | `METHOD.docx` |
| `date_ingested` | `2026-09-09` |
| `type` | Método / arquitetura de seleção da execução |
| `epistemic_classification` | `D · INTERNAL` / componentes `E · INFERRED/PROPOSED` conforme a própria fonte |
| `source_location` | ChatGPT Library `file_000000008484820e9fadc5e0d025ec5b` |
| `normalization_status` | `CLASSIFIED_PARTIAL` |

## Modelo descrito

A fonte descreve:

```text
Candidates = Ready ∩ DependencySatisfied ∩ FitsTime ∩ CurrentCycle
BestNext = argmax(Candidates, Flow, Context)
CycleProgress = Σ PP_done / 100
```

Também registra a arquitetura:

`WBS + DAG → READY POOL → TIME/FLOW/CONTEXT → RANKING → BEST NEXT ACTION → WIP=1 → EXECUTE → DoD → PROGRESS → recalcular → NEXT`.

## Classificação explícita da própria fonte

- restrições de precedência/capacidade e WIP: fundamentadas;
- modelo Progress + Flow + Context, `100 PP por C72` e UX de faixas temporais: `E · arquitetura inferida/proposta`.

## Regra de canonicalização

O filtro de candidatos pode ser usado como **modelo de referência** do WF-02, porque coincide com os princípios já observados de READY, dependência e fit de capacidade.

O ranking/score completo e Progress Points **não são promovidos a requisito aprovado** neste WF sem decisão própria.

## Targets

- `20-DOMAIN/rules/BEST_NEXT_ACTION_POLICY.md`
- `20-DOMAIN/rules/CORE_BUSINESS_RULES.md`
- `10-PRODUCT/WF-02-STATUS.md`
