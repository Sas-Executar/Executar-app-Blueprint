# Foundation Tokens — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`
Executable source: `30-DESIGN/tokens/DESIGN_TOKENS_FINAL.json`

## Typography

### App EXECUTAR
- UI/leitura: IBM Plex Sans.
- técnica: IBM Plex Mono.
- Display 48–64px; H1 40–48px; H2 32–36px; H3 24–28px; Body Large 18px; Body 16px; Small 14px; Caption 12px.
- leitura longa: 17–18px; line-height 1.6–1.7; 65–75ch.

### Editorial Hybrid
- UI: SF Pro/system.
- leitura longa: New York/Iowan/Palatino/Georgia.
- display-lg: `clamp(2.5rem,6vw,5rem)`.
- display-md: `clamp(2rem,4vw,3.5rem)`.

### Brand
- direção monospaced + uppercase + expanded tracking.
- wordmark oficial deve usar o asset recebido quando a família exata não estiver publicada.

## Spacing

Escala App preservada: `4, 8, 12, 16, 24, 32, 48, 64, 96px`.

## Radius — canônico

| Token | Valor |
|---|---:|
| `radius.none` | `0px` |
| `radius.xs` | `4px` |
| `radius.sm` | `8px` |
| `radius.md` | `12px` |
| `radius.lg` | `16px` |
| `radius.xl` | `24px` |
| `radius.full` | `9999px` |

Bindings: nav icon/chip → xs; button/input → sm; card default → md; panel/card amplo → lg; modal/hero surface quando aplicável → xl.

## Elevation — canônico

| Token | Valor |
|---|---|
| `elevation.0` | `none` |
| `elevation.1` | `0 1px 2px rgba(0,0,0,.06)` |
| `elevation.2` | `0 2px 8px rgba(0,0,0,.08)` |
| `elevation.3` | `0 8px 24px rgba(0,0,0,.10)` |
| `elevation.4` | `0 16px 40px rgba(0,0,0,.14)` |

Bindings: card → 0/1; sticky/nav → 2; popover/drawer → 3; modal → 4.

## Breakpoints App — canônico

| Token | Início |
|---|---:|
| `bp.xs` | `320px` |
| `bp.sm` | `480px` |
| `bp.md` | `640px` |
| `bp.lg` | `1024px` |
| `bp.xl` | `1366px` |
| `bp.2xl` | `1920px` |

Composição: mobile `<640px`; tablet `640–1023px`; desktop `>=1024px`.

## Motion App

- micro: 120–180ms.
- default: 180–250ms.
- large: 250–400ms.
- easing: ease-out.
- permitido: opacity, translate, scale-subtle, layer-depth.

## Editorial Hybrid — valores preservados

`--read:720px`, `--radius-card:0px`, `--radius-btn:8px`, `--radius-nav-icon:4px`, `--nav-h:56px`, `--bottombar-h:64px`, `--drawer-w:min(84vw,360px)`, `--ease:cubic-bezier(.22,1,.36,1)`.

`GAP-DS-RADIUS-001 = CLOSED`
`GAP-DS-ELEVATION-001 = CLOSED`
`GAP-DS-BREAKPOINT-APP-001 = CLOSED`
