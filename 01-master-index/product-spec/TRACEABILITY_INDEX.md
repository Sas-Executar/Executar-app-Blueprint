# Traceability Index

## Cadeia suportada

```
SOURCE
  → DECISION
  → CAPABILITY
  → REQUIREMENT
  → ACCEPTANCE CRITERIA
  → CONTRACT
  → IMPLEMENTATION TARGET
  → TEST
  → RELEASE
  → KPI
  → LEARNING
```

## Escopo deste repositório

Este repositório é responsável pela cadeia **até `IMPLEMENTATION TARGET`**
(inclusive):

| Elo | Onde vive |
|---|---|
| `SOURCE` | `99-SOURCES/raw`, `99-SOURCES/imported`, com registro em `99-SOURCES/provenance` |
| `DECISION` | `80-GOVERNANCE/ADR`, `80-GOVERNANCE/decisions` |
| `CAPABILITY` | `10-PRODUCT/capabilities`, indexado em `00-MANIFEST/CAPABILITY_MAP.md` |
| `REQUIREMENT` | `10-PRODUCT/requirements` |
| `ACCEPTANCE CRITERIA` | `10-PRODUCT/acceptance-criteria` |
| `CONTRACT` | `60-CONTRACTS/*` |
| `IMPLEMENTATION TARGET` | `95-INTEGRATION/NEXT_FORGE_MAPPING.md`, `PACKAGE_MAPPING.md`, `APP_MAPPING.md` |

**Não inventar `TEST` ou `RELEASE` neste repositório se eles ainda não
existirem.** Esses elos e `KPI`/`LEARNING` vivem no repositório de
aplicação e nos sistemas de analytics reais — este repositório apenas
referencia o `KPI` esperado (`90-MEASUREMENT/kpis`) sem afirmar que ele já
foi medido.

## Uso

Cada capability em `00-MANIFEST/CAPABILITY_MAP.md` deve, quando aplicável,
apontar para os elos correspondentes desta cadeia. Uma capability sem
requirement, sem acceptance criteria ou sem contract associado é uma
capability `PARTIAL`, não `READY` — ver estados em
`00-MANIFEST/CAPABILITY_MAP.md`.

Nenhuma linha de traceability foi criada neste bootstrap: o índice está
pronto para receber entradas assim que as primeiras capabilities forem
especificadas.
