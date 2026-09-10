# Contribution Rules

## Fluxo de ingestão de fontes

```
RAW SOURCE
  ↓
PROVENANCE
  ↓
CLASSIFICATION
  ↓
NORMALIZATION
  ↓
CANONICAL SPEC
```

1. **RAW SOURCE** — o documento bruto entra em `99-SOURCES/raw/`, sem
   edição.
2. **PROVENANCE** — um registro é criado em `99-SOURCES/provenance/`
   seguindo o formato de `99-SOURCES/PROVENANCE.md`.
3. **CLASSIFICATION** — cada trecho relevante recebe uma classificação de
   conteúdo e, quando aplicável, epistêmica (`80-GOVERNANCE/TAXONOMY.md`).
4. **NORMALIZATION** — o conteúdo classificado é reescrito no formato
   canônico da área correspondente (capability, requirement, contract,
   etc.), sem alterar seu significado.
5. **CANONICAL SPEC** — o resultado é publicado na área canônica correta
   (`10-PRODUCT`, `20-DOMAIN`, `30-DESIGN`, etc.), com exatamente uma
   autoridade.

**Nunca copiar indiscriminadamente documentos brutos para áreas
canônicas.**

## Regra de conflito

```
SOURCE_A
+
SOURCE_B
↓
CONFLICT
```

Quando duas fontes conflitarem, registrar o conflito em
`80-GOVERNANCE/conflicts/` e seguir:

```
CONFLICT → DECISION → CANONICAL SPEC
```

**Nunca escolher uma versão silenciosamente.** Uma `DECISION` explícita
(registrada como ADR ou em `80-GOVERNANCE/decisions/`) deve preceder a
atualização da spec canônica.

## Fonte única de verdade

Cada informação possui exatamente uma autoridade canônica. Antes de criar
um novo documento, verificar em `00-MANIFEST/PRODUCT_MANIFEST.md` (tabela
de autoridades canônicas) se o tema já tem dono.

## Reuse-first

Antes de solicitar qualquer implementação:

```
NEED
  ↓
EXISTS IN NEXT-FORGE?
  ├── YES → REUSE / CONFIGURE / ADAPT
  └── NO
        ↓
      EXTERNAL MATURE CAPABILITY?
        ├── YES → INTEGRATE
        └── NO → BUILD
```

`BUILD` é sempre a última alternativa. Consultar
`95-INTEGRATION/PACKAGE_MAPPING.md` e `APP_MAPPING.md` antes de concluir
que algo não existe no next-forge.

## Definition of Ready (por capability)

Uma capability está pronta para implementação quando possuir, quando
aplicável:

- objetivo;
- comportamento;
- requisitos;
- acceptance criteria;
- regras de domínio;
- contratos;
- permissões;
- estados;
- dependências;
- design;
- copy;
- analytics;
- security constraints;
- target técnico (`95-INTEGRATION/NEXT_FORGE_MAPPING.md`);
- out of scope.

## Definition of Done (da especificação)

Uma spec está completa quando:

- possui autoridade clara (uma única área canônica dona do conteúdo);
- não contradiz outra fonte canônica;
- está ligada a uma capability (`00-MANIFEST/CAPABILITY_MAP.md`);
- possui requisitos rastreáveis;
- possui critérios de aceite;
- possui target de implementação;
- gaps estão explicitamente registrados (`GAP`, não omitidos);
- propostas não estão marcadas como requisitos (`PROPOSAL` ≠
  `REQUIREMENT`).

## Ordem de ingestão sugerida

Design System → Produto/Core Domain → Agents → Pages/Copy/Assets →
Contracts → Integrations → Analytics/Security.

Cada lote passa pelo fluxo de ingestão completo (ingest → classify →
deduplicate → conflict detection → normalize → canonicalize) antes do
próximo lote começar. `95-INTEGRATION/NEXT_FORGE_MAPPING.md` só deve ser
tratado como ponte determinística e confiável depois que o repositório
estiver suficientemente populado — não neste bootstrap.

## O que este repositório nunca deve conter

Infraestrutura genérica já resolvida pelo next-forge — ver lista em
`README.md` ("Princípio central").

## O que o next-forge nunca deve conter

O next-forge nunca deve ser usado como fonte da verdade de produto:
PRDs, tokens de design, agentes, copy e contratos de negócio pertencem a
este repositório, não ao chassis técnico.
