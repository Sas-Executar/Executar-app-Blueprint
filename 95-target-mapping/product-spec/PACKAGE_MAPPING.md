# Package Mapping

Pacotes reais de `Sas-Executar/next-forge/packages` (lidos diretamente do
repositório em 2026-09-07) e seu status de mapeamento a partir deste
repositório. Ver ações e alvos detalhados em `NEXT_FORGE_MAPPING.md`.

| PACKAGE | CAPACIDADE GENÉRICA | SPEC AREA CORRESPONDENTE | STATUS |
|---|---|---|---|
| `packages/ai` | AI SDK | `50-AGENTS/*`, `60-CONTRACTS/agents` | NOT MAPPED |
| `packages/analytics` | Analytics | `90-MEASUREMENT/*` | NOT MAPPED |
| `packages/auth` | Autenticação | `20-DOMAIN/permissions` | NOT MAPPED |
| `packages/cms` | CMS | `40-CONTENT/pages`, `copy` | NOT MAPPED |
| `packages/collaboration` | Colaboração | `TBD` | NOT MAPPED |
| `packages/database` | ORM / database client | `20-DOMAIN/entities`, `60-CONTRACTS/schemas` | NOT MAPPED |
| `packages/design-system` | Design system foundation | `30-DESIGN/*` | NOT MAPPED |
| `packages/email` | Email infrastructure | `40-CONTENT/copy` | NOT MAPPED |
| `packages/feature-flags` | Feature flags | `80-GOVERNANCE/policies` | NOT MAPPED |
| `packages/internationalization` | i18n | `TBD` | NOT MAPPED |
| `packages/next-config` | Configuração Next.js compartilhada | — (infraestrutura pura, sem spec de produto) | N/A |
| `packages/notifications` | Notifications infrastructure | `TBD` | NOT MAPPED |
| `packages/observability` | Observability SDK | `80-GOVERNANCE/policies` | NOT MAPPED |
| `packages/payments` | Payment SDK | `TBD` | NOT MAPPED |
| `packages/rate-limit` | Rate limiting | `80-GOVERNANCE/security` | NOT MAPPED |
| `packages/security` | Segurança genérica | `80-GOVERNANCE/security` | NOT MAPPED |
| `packages/seo` | SEO infrastructure | `40-CONTENT/seo` | NOT MAPPED |
| `packages/storage` | Storage genérico | `40-CONTENT/assets` | NOT MAPPED |
| `packages/typescript-config` | Configuração TS compartilhada | — (infraestrutura pura, sem spec de produto) | N/A |
| `packages/webhooks` | Webhook infrastructure | `60-CONTRACTS/webhooks`, `70-INTEGRATIONS` | NOT MAPPED |

`NOT MAPPED` significa que nenhuma spec real deste repositório foi ainda
vinculada a esse pacote — a coluna "SPEC AREA CORRESPONDENTE" indica apenas
onde essa spec deverá viver quando existir.
