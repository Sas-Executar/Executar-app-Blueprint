# DEC-DS-FOUNDATION-CLOSURE-001

Status: `ACCEPTED`
Data: `2026-09-07`
Tipo: `DECISION`
Classificação epistêmica: `D · Interno` + `E · Inferido` para valores derivados
Owner approval: solicitação explícita para fechar 100% o WF-01

## Objetivo

Fechar os gaps restantes do `WF-01 — Design System` por decisão explícita, sem reclassificar valores derivados como `CORPUS_DIRECT`.

Esta decisão não altera o `next-forge`. Ela transforma gaps de especificação em contratos canônicos prontos para futura integração.

## Benchmarks externos usados

Classificação `C · Publicado`:

- Fluent 2 Design Tokens: https://fluent2.microsoft.design/design-tokens
- Fluent 2 Layout / Breakpoints: https://fluent2.microsoft.design/layout
- W3C WAI-ARIA APG Modal Dialog Pattern: https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/

## 1. Escalas Green e Azure

As cores-base recebidas permanecem autoridade:

- Green 500 = `#00BF63`
- Azure 500 = `#1F93FF`

As demais nuances são uma `DECISION` derivada perceptualmente em torno dessas bases, preservando hue e progressão clara→escura.

### Green

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

### Azure

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

Fecha `GAP-DS-COLOR-001` e `GAP-DS-COLOR-002`.

## 2. Neutral scale

| Shade | HEX | Origem |
|---:|---|---|
| 50 | `#F8F8F8` | brand source |
| 100 | `#F6F6F6` | Green+Expo source |
| 200 | `#E5E5E5` | brand source |
| 300 | `#D2D2D7` | Editorial Hybrid source |
| 400 | `#B8B8BC` | `DECISION / E` |
| 500 | `#9A9A9A` | brand source |
| 600 | `#6E6E73` | Editorial Hybrid source |
| 700 | `#4B4A4A` | Green+Expo source |
| 800 | `#2D2D2D` | brand source |
| 900 | `#111111` | Editorial Hybrid source |

Bindings: `text.primary → neutral-700`, `text.secondary → neutral-600`, `text.muted → neutral-500`, `border.subtle → neutral-200`, `border.default → neutral-300`.

Fecha `GAP-DS-NEUTRAL-001`.

## 3. Radius scale

| Token | Valor | Uso padrão |
|---|---:|---|
| `radius.none` | `0px` | editorial/card square |
| `radius.xs` | `4px` | nav icon/chips compactos |
| `radius.sm` | `8px` | button/input |
| `radius.md` | `12px` | card default |
| `radius.lg` | `16px` | card/panel amplo |
| `radius.xl` | `24px` | modal/hero surface quando aplicável |
| `radius.full` | `9999px` | pill/avatar |

Fecha `GAP-DS-RADIUS-001`.

## 4. Elevation scale

| Token | Valor |
|---|---|
| `elevation.0` | `none` |
| `elevation.1` | `0 1px 2px rgba(0,0,0,.06)` |
| `elevation.2` | `0 2px 8px rgba(0,0,0,.08)` |
| `elevation.3` | `0 8px 24px rgba(0,0,0,.10)` |
| `elevation.4` | `0 16px 40px rgba(0,0,0,.14)` |

Uso: card default → 0/1; nav/sticky → 2; popover/drawer → 3; modal → 4.

Fecha `GAP-DS-ELEVATION-001`.

## 5. Breakpoints App EXECUTAR

| Token | Início |
|---|---:|
| `bp.xs` | `320px` |
| `bp.sm` | `480px` |
| `bp.md` | `640px` |
| `bp.lg` | `1024px` |
| `bp.xl` | `1366px` |
| `bp.2xl` | `1920px` |

Contrato: mobile `<640px`; tablet `640–1023px`; desktop `>=1024px`.

Fecha `GAP-DS-BREAKPOINT-APP-001`.

## 6. Provider de ícones

- ícones genéricos de UI → `lucide-react`, já presente no `Sas-Executar/next-forge/packages/design-system`;
- símbolos proprietários → SVG próprios versionados neste repositório;
- Radix Icons pode permanecer em legado, mas não é o provider primário para novos ícones genéricos.

Fecha `GAP-DS-ICON-VECTOR-001` e `GAP-DS-ICON-LIBRARY-001`.

## 7. Masters dos símbolos

Masters canônicos:

- `30-DESIGN/symbols/masters/scanner.svg`
- `30-DESIGN/symbols/masters/selector.svg`
- `30-DESIGN/symbols/masters/feito.svg`

A geometria é própria e coerente com a decisão benchmark-based; não é declarada como cópia literal das pranchas raster.

Fecha `GAP-DS-SYMBOL-MASTER-001` e `GAP-DS-SYMBOL-VECTOR-001`.

## 8. Search / zero-result

Estados: `IDLE`, `TYPING`, `LOADING`, `RESULTS`, `EMPTY`, `ERROR`.

Contrato:
- container `role="search"`;
- input com nome acessível;
- botão limpar quando houver query;
- quantidade de resultados em `aria-live="polite"`;
- `EMPTY`: `Nenhum resultado encontrado` + `Tente outro termo ou ajuste os filtros.`;
- `ERROR`: preservar query e oferecer `Tentar novamente`;
- seleção/estado nunca depende apenas de cor.

Fecha `GAP-DS-SEARCH-001`.

## 9. Drawer accessibility

O blocker vira requisito obrigatório de implementação `REQ-A11Y-DRAWER-001`:

- conteúdo externo ao drawer fica `inert` ou equivalente enquanto modal;
- foco inicial entra no drawer;
- Tab/Shift+Tab circulam apenas dentro do drawer;
- Escape fecha;
- ao fechar, foco retorna ao trigger, salvo fluxo logicamente diferente;
- `aria-labelledby` e, quando útil, `aria-describedby`;
- teste obrigatório com teclado e leitor de tela.

A especificação está completa conforme W3C APG. A verificação de código pertence ao gate de integração/produção, não ao WF-01.

Fecha `BLOCKER-A11Y-DRAWER-001` como blocker de especificação e o converte em requisito de implementação.

## 10. Component APIs

`GAP-DS-COMP-001` deixa de ser gap do WF-01. Props/APIs React e React Native são detalhe do target `next-forge` e ficam `DEFERRED_TO_INTEGRATION`, preservando estados e variantes definidos aqui.

## Gate

`DESIGN_FOUNDATION_READY = PASS`

Isso significa **especificação de Design pronta para integração**, não implementação de produção já verificada.