# Customization Map

Mapa entre áreas de capacidade e seus alvos no chassis técnico
(`Sas-Executar/next-forge`). É a versão de alto nível do mapeamento — o
detalhamento técnico por pacote vive em `95-INTEGRATION/NEXT_FORGE_MAPPING.md`
e `95-INTEGRATION/PACKAGE_MAPPING.md`.

Ações possíveis: `CONFIGURE` · `ADAPT` · `EXTEND` · `GENERATE` ·
`IMPLEMENT`. Nunca usar `BUILD` se a fundação já existir no next-forge
(reuse-first — ver `80-GOVERNANCE/CONTRIBUTION_RULES.md`).

Evidência: `D · INTERNAL` para todas as linhas abaixo — baseada em leitura
direta da árvore de `packages/` e `apps/` de `Sas-Executar/next-forge` em
2026-09-07.

| AREA | PRODUCT SPEC | NEXT-FORGE TARGET | ACTION | STATUS | EVIDENCE |
|---|---|---|---|---|---|
| Autenticação | `20-DOMAIN/permissions` (regras de autorização do produto) | `packages/auth` | CONFIGURE / ADAPT | PENDING | D · INTERNAL |
| Banco de dados / persistência | `20-DOMAIN/entities`, `60-CONTRACTS/schemas` | `packages/database` | IMPLEMENT | PENDING | D · INTERNAL |
| Storage de arquivos | `40-CONTENT/assets` (política de uso) | `packages/storage` | ADAPT | PENDING | D · INTERNAL |
| Pagamentos | `TBD` (nenhuma capability de billing ingerida) | `packages/payments` | CONFIGURE | PENDING | D · INTERNAL |
| Agentes de IA | `50-AGENTS/agents`, `60-CONTRACTS/agents` | `packages/ai` | EXTEND | PENDING | D · INTERNAL |
| Observabilidade | `80-GOVERNANCE/policies` (o que deve ser observado) | `packages/observability` | CONFIGURE | PENDING | D · INTERNAL |
| Segurança | `80-GOVERNANCE/security` | `packages/security` | CONFIGURE / ADAPT | PENDING | D · INTERNAL |
| Analytics | `90-MEASUREMENT/analytics`, `events` | `packages/analytics` | CONFIGURE | PENDING | D · INTERNAL |
| E-mail | `40-CONTENT/copy` (conteúdo dos templates de e-mail) | `packages/email` | ADAPT | PENDING | D · INTERNAL |
| Notificações | `TBD` | `packages/notifications` | CONFIGURE | PENDING | D · INTERNAL |
| Feature flags | `80-GOVERNANCE/policies` | `packages/feature-flags` | CONFIGURE | PENDING | D · INTERNAL |
| Rate limiting | `80-GOVERNANCE/security` | `packages/rate-limit` | CONFIGURE | PENDING | D · INTERNAL |
| CMS | `40-CONTENT/pages`, `copy` | `packages/cms` | ADAPT | PENDING | D · INTERNAL |
| SEO | `40-CONTENT/seo` | `packages/seo` | CONFIGURE | PENDING | D · INTERNAL |
| Internacionalização | `TBD` | `packages/internationalization` | CONFIGURE | PENDING | D · INTERNAL |
| Webhooks | `60-CONTRACTS/webhooks`, `70-INTEGRATIONS` | `packages/webhooks` | ADAPT | PENDING | D · INTERNAL |
| Design system (foundation) | `30-DESIGN/tokens`, `components` | `packages/design-system` | GENERATE / ADAPT | PENDING | D · INTERNAL |
| Colaboração | `TBD` | `packages/collaboration` | CONFIGURE | PENDING | D · INTERNAL |

Nenhuma linha acima representa uma decisão de implementação — todas estão
`PENDING` até que a capability correspondente seja especificada em
`10-PRODUCT/` e o mapeamento seja revisitado com evidência real (não a
partir apenas da lista de pacotes do next-forge).
