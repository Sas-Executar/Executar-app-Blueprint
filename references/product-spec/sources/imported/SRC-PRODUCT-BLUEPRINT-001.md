# SRC-PRODUCT-BLUEPRINT-001

| Campo | Valor |
|---|---|
| `SOURCE_ID` | `SRC-PRODUCT-BLUEPRINT-001` |
| `source_name` | `Executar App - Blueprint.(1).md` |
| `date_received` | `2026-09-09` |
| `type` | Blueprint composto / briefing / benchmark / estado documental |
| `epistemic_classification` | `D · INTERNAL` — contém partes observadas, propostas, inferências e status históricos |
| `sha256` | `567655bf0bfa16ebd8a485d27081c70c9f5c87fa6a54a0035fce944ae21472cd` |
| `normalization_status` | `CLASSIFIED_AND_PARTIALLY_CANONICALIZED` |
| `raw_location` | Upload da conversa; original preservado pelo hash acima |

## Conteúdo útil para WF-02

- categoria proposta: Adaptive Work Execution OS / Sistema Operacional de Execução Adaptativa;
- core engine sugerido: `Plan → Eligibility → Dispatch → Execute → Evidence → Learn`;
- core proposition: execution OS para trabalhador solo;
- estrutura WF-02 explicitamente definida;
- objetos iniciais: Projeto, Value Stream, Entregável, Tarefa, Ação, Evidência;
- regras a especificar: ciclo 72h, capacidade, WIP, bloqueios, dependências, caminho crítico;
- estados iniciais registrados: `BACKLOG`, `READY`, `FOCUS`, `BLOCKED`, `DONE`;
- jornadas: criar projeto, planejar, executar, concluir, evidenciar, replanejar;
- cadeia documental: PRODUCT_STRUCTURE → PRODUCT_BRIEF → ICP → JTBD → USER_JOURNEYS → DOMAIN_MODEL → GLOSSARY → BUSINESS_RULES → STATE_MACHINES → EVENT_CATALOG → requisitos/AC → data model/ERD/RLS → contratos.

## Conteúdo que NÃO é promovido automaticamente a requisito

- benchmarks e preços;
- escolhas de provider mencionadas em exemplos históricos;
- declarações de implementação antiga;
- sugestões comerciais ainda não aprovadas;
- skills de engenharia genéricas.

Esses itens permanecem `PROPOSAL`, `REFERENCE` ou `HISTORICAL_STATUS` até decisão própria.

## Alvos canônicos

- `10-PRODUCT/vision/PRODUCT_VISION.md`
- `10-PRODUCT/capabilities/CORE_CAPABILITIES.md`
- `20-DOMAIN/states/EXECUTION_STATES.md`
- `10-PRODUCT/journeys/CORE_JOURNEYS.md`
- `10-PRODUCT/WF-02-STATUS.md`
- `00-MANIFEST/CAPABILITY_MAP.md`