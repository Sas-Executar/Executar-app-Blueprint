# SRC-EXECUTION-PROTOTYPE-001

| Campo | Valor |
|---|---|
| `SOURCE_ID` | `SRC-EXECUTION-PROTOTYPE-001` |
| `source_name` | `executar-pwa-prototype-fluent-mobile-design-contract-v3.html` |
| `date_ingested` | `2026-09-09` |
| `type` | Protótipo funcional / contrato de UX e regras de execução |
| `epistemic_classification` | `A · OBSERVED` + `D · INTERNAL` |
| `source_location` | ChatGPT Library `file_00000000c73c81f79f290928dbb2a985` |
| `normalization_status` | `CANONICALIZED_PARTIAL` |

## Evidência observada relevante

O protótipo implementa/expõe diretamente:

- ciclo operacional de 72h dividido em 3 dias;
- opção de capacidade `6h/dia → 18h/ciclo`;
- ação atômica de `15 min`;
- cálculo `actions = floor(executable_hours * 4)`;
- capacidade bruta exibida como `72 ações` quando 18h estão disponíveis;
- `WIP = 1` como invariante visual/funcional;
- `capacityRemaining = cycle.capacity - DONE/VERIFIED`;
- bloqueados deixam de ser bloqueados quando dependência é satisfeita;
- Task agrega estado a partir dos estados de suas Actions;
- Gate usa conclusão, DoD, evidência, dependências e carryover;
- mudança de capacidade gera nova projeção preservando IDs/histórico;
- prioridade é descrita na UX como elegibilidade → dependências → caminho crítico → valor → prazo → similaridade cognitiva.

## Limitação importante

O protótipo **não prova que o ranking completo de Best Next Action está implementado**. O despacho observado no código percorre Actions READY em ordem. Portanto:

- capacidade/15 min/WIP/dependency release = evidência observada;
- copy de ranking = intenção funcional;
- algoritmo completo BNA = ainda exige decisão/implementação própria.

## Targets canônicos

- `20-DOMAIN/rules/CORE_BUSINESS_RULES.md`
- `10-PRODUCT/requirements/CORE_REQUIREMENTS.md`
- `10-PRODUCT/acceptance-criteria/CORE_ACCEPTANCE_CRITERIA.md`
- `10-PRODUCT/WF-02-STATUS.md`
