# Primitive Tokens — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`
Executable source: `30-DESIGN/tokens/DESIGN_TOKENS_FINAL.json`

## Regra epistêmica

As cores-base recebidas são fonte primária/interna. Shades derivados e o nível `neutral-400` são `DECISION · D/E`, aprovados para fechar o WF-01; não são reclassificados como `CORPUS_DIRECT`.

Método de derivação das escalas Green/Azure: progressão perceptual em OKLCH em torno da cor-base 500, preservando o hue e ajustando lightness/chroma para produzir a sequência 50→900. A decisão final é normativa; a interpolação é apenas o método de geração.

## Green

| Shade | HEX |
|---:|---|
| 50 | `#E5FCEA` |
| 100 | `#CBF4D5` |
| 200 | `#9EE5B1` |
| 300 | `#76D693` |
| 400 | `#46CB78` |
| 500 | `#00BF63` |
| 600 | `#179951` |
| 700 | `#03773C` |
| 800 | `#04572A` |
| 900 | `#023B1B` |

## Azure

| Shade | HEX |
|---:|---|
| 50 | `#EFF6FF` |
| 100 | `#D8EAFF` |
| 200 | `#B1D5FD` |
| 300 | `#8FC2FC` |
| 400 | `#6EB2FE` |
| 500 | `#1F93FF` |
| 600 | `#0B81E5` |
| 700 | `#0C64B3` |
| 800 | `#074883` |
| 900 | `#00305D` |

## Neutral

| Shade | HEX |
|---:|---|
| 50 | `#F8F8F8` |
| 100 | `#F6F6F6` |
| 200 | `#E5E5E5` |
| 300 | `#D2D2D7` |
| 400 | `#B8B8BC` |
| 500 | `#9A9A9A` |
| 600 | `#6E6E73` |
| 700 | `#4B4A4A` |
| 800 | `#2D2D2D` |
| 900 | `#111111` |

## Outros primitivos preservados

Editorial Hybrid: Yellow `#FFCC00`, Black `#000000`, Charcoal `#111111`, Charcoal Soft `#1C1C1E`, Ink `#1D1D1F`, Muted `#6E6E73`, Paper `#FFFFFF`, Soft `#F5F5F7`, Line `#D2D2D7`.

Brand: Black `#000000`, Dark Gray `#2D2D2D`, Support `#9A9A9A`, Light Gray `#E5E5E5`, Off White `#F8F8F8`, White `#FFFFFF`.

Componentes consomem tokens semânticos; não usar `primitive.*` diretamente quando houver alias semântico.

`GAP-DS-COLOR-001 = CLOSED`
`GAP-DS-COLOR-002 = CLOSED`
`GAP-DS-NEUTRAL-001 = CLOSED`
