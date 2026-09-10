# Provenance Policy

Toda fonte bruta futura deve entrar primeiro como fonte, nunca diretamente como spec canônica. Fluxo completo em `80-GOVERNANCE/CONTRIBUTION_RULES.md`.

## Registro de proveniência

Cada fonte recebida deve ter registro correspondente em `99-SOURCES/provenance/` ou `99-SOURCES/imported/`, com:

| Campo | Descrição |
|---|---|
| `SOURCE_ID` | Identificador único da fonte. |
| `date_received` | Data em que a fonte foi recebida. |
| `author` | Autor/origem, quando conhecido. |
| `type` | Tipo de material. |
| `epistemic_classification` | `A` a `E`, conforme `80-GOVERNANCE/TAXONOMY.md`. |
| `raw_location` / `source_location` | Caminho/referência imutável da fonte. |
| `normalization_status` | `RAW` / `CLASSIFIED` / `NORMALIZED` / `CANONICALIZED`. |
| `canonical_targets` | Arquivos canônicos gerados a partir da fonte. |

## Regras

- fonte bruta nunca é editada para virar spec;
- normalização gera novo artefato na autoridade canônica;
- conflitos exigem `CONFLICT → DECISION → CANONICAL SPEC`;
- hashes registram uploads quando o original não é armazenado diretamente no repositório;
- conteúdo histórico, benchmark ou sugestão não é promovido automaticamente a requisito.

## Fontes ingeridas — WF-01 Design

| SOURCE_ID | Domínio | Estado | Registro |
|---|---|---|---|
| `SRC-DESIGN-GREEN-EXPO-001` | Design / App EXECUTAR | `CANONICALIZED_WITH_DECISIONS` | `99-SOURCES/imported/SRC-DESIGN-GREEN-EXPO-001.md` |
| `SRC-DESIGN-HYBRID-V6-001` | Design / ecossistema editorial | `CANONICALIZED_WITH_DECISIONS` | `99-SOURCES/imported/SRC-DESIGN-HYBRID-V6-001.md` |
| `SRC-DESIGN-BRAND-ASSETS-001` | Brand / icons / symbols | `CANONICALIZED_WITH_DECISIONS` | `99-SOURCES/imported/SRC-DESIGN-BRAND-ASSETS-001.md` |

WF-01 foi fechado por decisões explícitas; `DESIGN_FOUNDATION_READY = PASS` não transforma inferência em corpus direto.

## Fontes ingeridas — WF-02 Produto & Core Domain

| SOURCE_ID | Domínio | Estado | Registro |
|---|---|---|---|
| `SRC-PRODUCT-MANIFESTO-001` | Product Vision / Core Domain | `CANONICALIZED_PARTIAL` | `99-SOURCES/imported/SRC-PRODUCT-MANIFESTO-001.md` |
| `SRC-PRODUCT-BLUEPRINT-001` | Blueprint / briefing / benchmark / status | `CLASSIFIED_AND_PARTIALLY_CANONICALIZED` | `99-SOURCES/imported/SRC-PRODUCT-BLUEPRINT-001.md` |
| `SRC-SCANNER-RUNTIME-FOLLOWUP-001` | Scanner / runtime / commands | `CLASSIFIED` | `99-SOURCES/imported/SRC-SCANNER-RUNTIME-FOLLOWUP-001.md` |

## Hashes dos uploads WF-02

- `Manisfesto.md` → `07110c4c7f742f3aac52e539297da5317a5805841e7bfae0e8ce48e393d8bd9f`
- `Executar App - Blueprint.(1).md` → `567655bf0bfa16ebd8a485d27081c70c9f5c87fa6a54a0035fce944ae21472cd`
- `visao.md` → `afbcf7b7b63f395a50f2312bb4c02b7209536c9414e06376d9e617e8d788cd1d`

## Roteamento importante

`visao.md` foi classificado corretamente como follow-up operacional do Scanner, e **não** como Product Vision.

O manifesto é a fonte primária para tese, princípios, quatro operações, estrutura de trabalho, WIP, capacidade, continuidade e outputs.

O blueprint é fonte composta: suas seções de benchmark, preço e sugestões permanecem `REFERENCE/PROPOSAL` salvo decisão específica.

## Preservação externa

Arquivos binários ou uploads que não sejam copiados para o repositório devem permanecer preservados em Drive/Conversation/Library com SHA-256 no registro de proveniência.