# SRC-DESIGN-BRAND-ASSETS-001

| Campo | Valor |
|---|---|
| `SOURCE_ID` | `SRC-DESIGN-BRAND-ASSETS-001` |
| `date_received` | 2026-09-07 |
| `type` | owner upload: ZIP de brand assets + brand guidelines + referências de ícones |
| `epistemic_classification` | `B · Primário` |
| `source_filename` | `Arquivo(1).zip` |
| `sha256` | `fcf1b5b1075728950556d6538f094dca3d9018579d885433774ba95db78f968f` |
| `drive_copy` | `SOURCE — EXECUTAR-brand-assets-icons-symbols-v1.zip` |
| `normalization_status` | `CANONICALIZED_WITH_REMAINING_GAPS` |

## Conteúdo observado

O ZIP contém:

1. `EXECUTAR_Brand_PNG_Package_v1.0/` com `README.txt`, `manifest.csv` e 82 exports PNG catalogados;
2. quatro pranchas PNG de brand guidelines/aplicações;
3. três pranchas JPG de referências de glyphs/ícones.

### Pacote PNG — inventário do `manifest.csv`

| Categoria | Quantidade de exports |
|---|---:|
| logo mark | 23 |
| wordmark | 8 |
| lockups | 12 |
| app icons (iOS/Android/PWA) | 23 |
| favicon | 7 |
| social | 8 |
| brand preview | 1 |
| **Total** | **82** |

### Regras de brand identity confirmadas

- paleta primária: Black `#000000`, Dark Gray `#2D2D2D`, Gray `#9A9A9A`, Light Gray `#E5E5E5`, Off White `#F8F8F8`, White `#FFFFFF`;
- direção tipográfica: monospaced, uppercase, expanded tracking;
- o wordmark PNG foi rasterizado de uma fonte monoespaçada de sistema; nenhum arquivo de fonte é distribuído;
- clear space mínimo do ícone: `X`, onde `X` equivale à altura do check mark dentro do ícone;
- tamanho mínimo do ícone: `16 × 16 px`;
- largura mínima do wordmark horizontal: `80 px`;
- variantes: primary, black/dark, reverse, horizontal, stacked, app icon;
- exports específicos para iOS, Android, PWA, favicon e social.

### Pranchas de glyphs/ícones

- `IMG_0980.JPG`: grade 5×5, 25 slots visuais;
- `IMG_0981.JPG`: grade 4×2, 8 slots visuais;
- `IMG_0982.JPG`: grade 4×2, 8 slots visuais;
- existem repetições entre as pranchas; portanto 41 slots não equivalem a 41 ícones únicos.

As pranchas não publicam nomes semânticos, provider, arquivos vetoriais individuais ou mapeamento para comandos de produto. A normalização registra a referência visual sem inventar significado.

## Hashes de arquivos-chave

| Arquivo | SHA-256 |
|---|---|
| `IMG_0980.JPG` | `d2de50be2da0e44ea68767db50fdfc22544e8ca43f0db5fbee1d62777a043702` |
| `IMG_0981.JPG` | `9b0cf2f9f5ca3c7f69ad3a3aa18a8e15d3f016e7b6e2e5b53021cf0d177631c2` |
| `IMG_0982.JPG` | `fb848f35ebb3e5366efdfe840c165294c348405bf50af65e51c8cdb2dda6877c` |
| `8DA82016-B000-4601-BC51-790C67099E54.PNG` | `45f6eadee7fde354bd60d037b4b2fe349432182a6f053b1770dcdcbeaa547f9d` |
| `613886BA-995F-4A08-9C81-930B61216232.PNG` | `3ae1142cbb8ef9f0e9b15b7dc604837d553194516552c0da91cb1f9fdbdce436` |
| `C97B32F2-35F6-4344-B8B4-5243E894CC90.PNG` | `84777c74936e82f349b6fbdfbb794a606e83f2e9ddf7df765b408610655a95f7` |
| `C6645123-18B1-4EDB-A5C4-E723F21E4013.PNG` | `4c9e6db97ee9d47f796c26709bc9ad875f899f937689d1776dcd7f0f235ceb81` |
| `README.txt` | `b8ea1c83318986b8f1a8db3e7f6443ff005f43478f52ef786c16c70bde8cd495` |
| `manifest.csv` | `9e4d1e994d1a0f312182d93dbc5e0da2cc2cc6fed3e887464fcfe4434de812bc` |

## Canonical targets

- `30-DESIGN/foundations/DESIGN_SCOPE_MATRIX.md`
- `30-DESIGN/foundations/FOUNDATION_TOKENS.md`
- `30-DESIGN/tokens/PRIMITIVE_TOKENS.md`
- `30-DESIGN/icons/ICON_INVENTORY.md`
- `30-DESIGN/symbols/SYMBOL_INVENTORY.md`
- `30-DESIGN/WF-01-STATUS.md`

## O que esta fonte fecha

- brand mark/wordmark/lockups de produção em PNG;
- app icon exports para iOS/Android/PWA;
- favicon exports;
- social/OG assets;
- paleta monocromática de identidade;
- regras de clear space e tamanho mínimo;
- referências visuais de ícones/glyphs;
- ausência anterior de screenshots/referências de brand.

## Gaps que esta fonte não fecha

- valores Green 50–900 e Azure 50–900 do sistema Green+Expo;
- mapeamento numérico `neutral-200/300/500/600` do Green+Expo;
- escala completa de radius/elevation do Green+Expo;
- breakpoint numérico do App Green+Expo;
- nomes semânticos/provider e masters vetoriais da biblioteca UI de ícones;
- mapeamento explícito dos símbolos de produto (Scanner/Seletor/Copiloto/Feito) para glyphs/assets específicos;
- focus trap do drawer Editorial Hybrid.

A paleta monocromática desta fonte é uma camada de **brand identity** e não deve substituir automaticamente as paletas de UI Green+Expo ou Editorial Hybrid sem decisão explícita de escopo.