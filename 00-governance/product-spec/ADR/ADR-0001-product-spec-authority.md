# ADR-0001 — Criação do repositório EXECUTAR-Product-Spec como fonte canônica da camada proprietária

- **Status:** Accepted
- **Data:** 2026-09-07
- **Classificação:** `DECISION`
- **Evidência:** `D · INTERNAL`

## Contexto

O next-forge resolve infraestrutura técnica (monorepo, Next.js, TypeScript,
auth foundation, database foundation, storage, payments, AI SDK,
observability, security, analytics, email, notifications, collaboration,
feature flags, rate limiting, CMS, SEO, i18n, webhooks, design-system
foundation), mas não deve se tornar depósito de PRDs, tokens de design,
agentes, copy e contratos de negócio do produto EXECUTAR.

## Decisão

Criar um repositório separado, `Sas-Executar/EXECUTAR-Product-Spec`, como
fonte canônica única da camada proprietária do produto EXECUTAR: produto,
domínio, design, conteúdo, agentes, contratos, integrações, governança e
medição.

A relação entre os repositórios é:

```
next-forge            = plataforma / infraestrutura / foundation
EXECUTAR-Product-Spec  = produto / domínio / design / contratos / comportamento
integração             = aplicação EXECUTAR
```

A integração entre os dois repositórios ocorre por mapeamento explícito e
rastreável (`95-INTEGRATION/NEXT_FORGE_MAPPING.md`), nunca por cópia direta
de conteúdo nem por decisão implícita.

## Consequências

- Toda decisão sobre "como o EXECUTAR deve parecer, funcionar, decidir,
  comunicar, medir ou se integrar" pertence a este repositório.
- Toda decisão sobre "qual infraestrutura genérica usamos para executar
  isso" pertence ao next-forge.
- Nenhuma infraestrutura genérica (auth, storage, ORM, database client,
  payment SDK, observability SDK, AI SDK, email/notifications
  infrastructure, feature flags, rate limiting, CMS, webhooks, i18n, SEO)
  deve ser recriada neste repositório.
- O next-forge nunca deve ser tratado como fonte da verdade de produto.
- Este repositório nunca deve ser tratado como fonte da verdade de
  infraestrutura genérica.
- Toda a estrutura, taxonomia e regras de contribuição estão documentadas
  em `README.md` e `80-GOVERNANCE/`.

## Alternativas consideradas

- **Manter tudo dentro do next-forge** (ex.: pasta `docs/` ou `product/`
  no próprio monorepo). Rejeitada: mistura conhecimento de produto com
  chassis técnico, dificultando versionamento independente e criando risco
  de o time tratar next-forge como fonte de verdade de produto.
- **Nomear o repositório apenas `docs`, `requirements` ou
  `customization`.** Rejeitada: subestima a autoridade do repositório, que
  é a especificação de produto completa (Product Specification Repository),
  não apenas documentação de apoio.
