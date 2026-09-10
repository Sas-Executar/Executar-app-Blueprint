# Next-Forge Mapping

Ponte determinística entre elementos proprietários deste repositório e seus
alvos técnicos em `Sas-Executar/next-forge`.

**Este arquivo é preenchido incrementalmente**, conforme os lotes de
conteúdo (Design System → Produto/Core Domain → Agents → Pages/Copy/Assets
→ Contracts → Integrations → Analytics/Security, ver
`80-GOVERNANCE/CONTRIBUTION_RULES.md`) forem ingeridos, classificados e
canonicalizados. Ele só deve ser tratado como ponte confiável e completa
depois que o repositório estiver suficientemente populado — não neste
bootstrap.

## Modelo de mapeamento

```
SPEC
  ↓
TARGET
  ↓
ACTION
```

Ações permitidas: `CONFIGURE` · `ADAPT` · `EXTEND` · `GENERATE` ·
`IMPLEMENT`. `BUILD` nunca é usado aqui — se a resposta fosse `BUILD`, a
necessidade ainda não foi validada contra reuse-first
(`80-GOVERNANCE/CONTRIBUTION_RULES.md`).

## Exemplos ilustrativos (do desenho original do repositório)

| SPEC | TARGET | ACTION |
|---|---|---|
| Design Tokens (`30-DESIGN/tokens`) | `packages/design-system` | GENERATE / ADAPT |
| Agent Contract (`50-AGENTS/agents`, `60-CONTRACTS/agents`) | `packages/ai` | EXTEND |
| Domain Schema (`20-DOMAIN/entities`, `60-CONTRACTS/schemas`) | `packages/database` | IMPLEMENT |
| Storage Policy (`40-CONTENT/assets`) | `packages/storage` | ADAPT |

Estes são exemplos do modelo de mapeamento, não mapeamentos confirmados —
nenhum token, agente, schema ou política real foi ingerido ainda.

## Mapeamento por área (estado atual)

| SPEC AREA | TARGET (next-forge) | ACTION | STATUS |
|---|---|---|---|
| `30-DESIGN/*` | `packages/design-system` | GENERATE / ADAPT | NOT STARTED |
| `50-AGENTS/*`, `60-CONTRACTS/agents` | `packages/ai` | EXTEND | NOT STARTED |
| `20-DOMAIN/*`, `60-CONTRACTS/entities`, `schemas` | `packages/database` | IMPLEMENT | NOT STARTED |
| `40-CONTENT/assets` | `packages/storage` | ADAPT | NOT STARTED |
| `60-CONTRACTS/api` | `apps/api` | IMPLEMENT | NOT STARTED |
| `40-CONTENT/pages`, `routes` | `apps/app`, `apps/web` | IMPLEMENT | NOT STARTED |
| `60-CONTRACTS/webhooks`, `70-INTEGRATIONS` | `packages/webhooks` | ADAPT | NOT STARTED |
| `90-MEASUREMENT/*` | `packages/analytics` | CONFIGURE | NOT STARTED |
| `80-GOVERNANCE/security` | `packages/security` | CONFIGURE / ADAPT | NOT STARTED |

Ver detalhamento por pacote em `PACKAGE_MAPPING.md` e por app em
`APP_MAPPING.md`.
