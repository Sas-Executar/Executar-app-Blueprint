# Component Catalog — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`

## App EXECUTAR — biblioteca mínima

`Button`, `IconButton`, `SegmentedControl`, `Input`, `Textarea`, `Select`, `Card`, `Callout`, `Badge`, `Tabs`, `Modal`, `Drawer`, `Navigation`, `Article`, `CodeBlock`, `Metric`, `Progress`, `Diagram`, `Search`.

### Button

Estados obrigatórios: `DEFAULT`, `HOVER`, `FOCUS`, `ACTIVE`, `DISABLED`, `LOADING`.

- Primary: Green, ação principal.
- Secondary: Azure ou outline/white conforme contexto.
- Tertiary: texto, baixo peso visual.
- Nunca três botões de mesmo peso disputando atenção.

### Card

- background White;
- border `neutral-200`;
- radius default `radius.md = 12px`, podendo usar `sm`/`lg` conforme composição;
- elevation 0/1;
- padding 16–32px.

### Drawer

Contrato visual e acessível definido em `30-DESIGN/accessibility/ACCESSIBILITY_CONTRACT.md`.

### Search

Contrato completo em `30-DESIGN/components/SEARCH_CONTRACT.md`.

Estados: `IDLE`, `TYPING`, `LOADING`, `RESULTS`, `EMPTY`, `ERROR`.

## Editorial Hybrid v6 — catálogo preservado

| Componente | Regra principal |
|---|---|
| `.global-nav` | fixed; menu/marca/busca no mobile |
| `.nav-links-desktop` | desktop `>=900px` |
| `.category-rail-desktop` | desktop; 1 item ativo |
| `.drawer` + backdrop | mobile `<900px`; links min-height 56px |
| `.bottom-bar` | mobile; exatamente 3 destinos |
| `.btn` | primary/accent/outline; min-height 56px |
| `.hero` | eyebrow + h1 + p + máximo 2 botões |
| `.feature-media` | única por página; full width; min-height 100vh |
| `.tile` | soft/dark/yellow; 1 CTA por tile |
| `.article` | lead, parágrafos, h2, pullquote 0–1, inline-media 0–1 |
| `.selection` | superfície charcoal; imagem 3:4 |
| `.carousel-card` | visual 3:4; scroll horizontal com snap |
| `footer` | links + legal; não repete navegação principal |

## Edge cases

- títulos longos quebram naturalmente; não truncar;
- drawer possui overflow-y auto;
- imagens preservam aspect-ratio;
- labels internacionais podem crescer;
- busca distingue `EMPTY` de `ERROR`;
- reduced motion deve ser respeitado.

## Integração

Props/APIs React e React Native não são gaps do WF-01. Elas ficam `DEFERRED_TO_INTEGRATION` no target `next-forge`, preservando estados, variantes, tokens e requisitos definidos aqui.

`GAP-DS-COMP-001 = CLOSED_BY_SCOPE`
`GAP-DS-SEARCH-001 = CLOSED`
