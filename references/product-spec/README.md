# EXECUTAR · Product Specification Repository

Este repositório é a fonte canônica da camada proprietária do produto
**EXECUTAR**.

Ele existe para definir, organizar e versionar tudo aquilo que diferencia o
EXECUTAR do chassis técnico utilizado para implementá-lo.

O chassis técnico atual é baseado em
[`next-forge`](https://github.com/Sas-Executar/next-forge).

A relação entre os repositórios é:

```
next-forge
= plataforma / infraestrutura / foundation

EXECUTAR-Product-Spec
= produto / domínio / design / contratos / comportamento

integração
= aplicação EXECUTAR
```

⸻

## Princípio central

Este repositório **NÃO** deve reproduzir infraestrutura já resolvida pelo
chassis técnico.

Não recriar aqui:

- autenticação genérica;
- storage genérico;
- ORM;
- database client;
- payment SDK;
- observability SDK;
- AI SDK;
- email infrastructure;
- notifications infrastructure;
- feature flags;
- rate limiting;
- CMS infrastructure;
- webhook infrastructure;
- i18n infrastructure;
- SEO infrastructure;
- collaboration infrastructure;
- security infrastructure genérica.

Essas capacidades pertencem à plataforma (`next-forge`, ver
`packages/*` — mapeamento em `95-INTEGRATION/PACKAGE_MAPPING.md`).

Este repositório deve definir **o que essas capacidades significam para o
EXECUTAR**.

⸻

## Fonte da verdade

Cada informação possui uma única autoridade canônica.

Evitar:

- documentos duplicados;
- dois arquivos descrevendo a mesma regra;
- requisitos conflitantes sem registro;
- valores de design repetidos;
- prompts contendo regras que deveriam existir como contratos;
- decisão arquitetural sem vínculo com implementação futura.

Quando houver conflito:

```
SOURCE_A
+
SOURCE_B
↓
CONFLICT
↓
DECISION
↓
CANONICAL SPEC
```

Nunca resolver silenciosamente — ver `80-GOVERNANCE/CONTRIBUTION_RULES.md`
e `80-GOVERNANCE/conflicts/`.

⸻

## Estrutura

```
EXECUTAR-Product-Spec/
│
├── 00-MANIFEST/        → manifesto, mapas de customização/capability, índice de traceability
├── 10-PRODUCT/         → visão, capabilities, journeys, requirements, acceptance criteria, feature specs
├── 20-DOMAIN/          → entities, value objects, states, state machines, rules, permissions, events
├── 30-DESIGN/          → foundations, tokens (primitive→semantic→component), components, patterns, a11y
├── 40-CONTENT/         → routes, pages, copy, seo, images, video, assets
├── 50-AGENTS/          → agents, skills, tools, prompts, policies, memory, evaluations
├── 60-CONTRACTS/       → entities, schemas, commands, queries, events, api, webhooks, agents
├── 70-INTEGRATIONS/    → providers, mappings, sync, failure-policies
├── 80-GOVERNANCE/      → ADR, decisions, conflicts, security, privacy, policies, taxonomy
├── 90-MEASUREMENT/     → analytics, events, funnels, kpis, experiments
├── 95-INTEGRATION/     → mapeamento determinístico spec → next-forge
└── 99-SOURCES/         → raw, imported, provenance
```

Pastas só existem quando há conteúdo real ou quando são necessárias como
parte do bootstrap inicial. Cada pasta traz um `README.md` com seu
propósito e status.

⸻

## Classificação de conteúdo

Todo material recebido deve ser classificado como:

`SOURCE` · `REQUIREMENT` · `DECISION` · `CONSTRAINT` · `CONTRACT` · `GAP` ·
`CONFLICT` · `PROPOSAL`

Nunca converter automaticamente `PROPOSAL` em `REQUIREMENT`.

Ver `80-GOVERNANCE/TAXONOMY.md`.

⸻

## Classificação epistêmica

Quando necessário:

`A` · Observado — `B` · Primário — `C` · Publicado — `D` · Interno —
`E` · Inferido

Não apresentar inferência como evidência observada.

⸻

## Unidade principal: Capability

Este repositório é organizado para permitir desenvolvimento por
**capability**.

Exemplo: `CAP-EXEC-001 · Task Completion`.

Uma capability pode referenciar: PRD, requirement, acceptance criteria,
domain rule, state, contract, page, componente, agent tool, analytics
event, test expectation.

Ver `00-MANIFEST/CAPABILITY_MAP.md`.

⸻

## Traceability

A cadeia desejada é:

```
SOURCE → DECISION → CAPABILITY → REQUIREMENT → ACCEPTANCE CRITERIA →
CONTRACT → IMPLEMENTATION TARGET → TEST → RELEASE → KPI → LEARNING
```

Este repositório é responsável pela cadeia até `IMPLEMENTATION TARGET`. O
código implementado vive no repositório de aplicação. Ver
`00-MANIFEST/TRACEABILITY_INDEX.md`.

⸻

## Design System

Tokens devem ser classificados em:

```
PRIMITIVE → SEMANTIC → COMPONENT
```

Exemplo: `primitive.green.500 → action.primary →
button.primary.background`.

Não espalhar valores visuais diretamente por documentos ou componentes.
Ver `30-DESIGN/tokens/TOKEN_MODEL.md`.

⸻

## Integração com next-forge

Nenhum documento deste repositório deve ser copiado cegamente para o
next-forge. A integração ocorre por mapeamento:

```
SPEC → TARGET → ACTION
```

Ações permitidas: `CONFIGURE` · `ADAPT` · `EXTEND` · `GENERATE` ·
`IMPLEMENT`. `BUILD` é sempre a última alternativa (reuse-first — ver
`80-GOVERNANCE/CONTRIBUTION_RULES.md`).

Ver `95-INTEGRATION/NEXT_FORGE_MAPPING.md`.

⸻

## Regra de integração

O next-forge nunca deve ser usado como fonte da verdade de produto.

Este repositório nunca deve ser usado como fonte da verdade de
infraestrutura genérica.

A integração entre ambos deve ser explícita, rastreável e versionada.
