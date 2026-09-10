# Component Token Mapping — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`

Este arquivo normaliza os bindings de componentes para os tokens canônicos finais.

## App EXECUTAR — Green + Expo

| Componente | Propriedade | Binding canônico |
|---|---|---|
| Button primary | background | `action.primary → green-500` |
| Button primary | radius | `radius.sm = 8px` |
| Button secondary | background/border | `action.secondary → azure-500` |
| Button | focus | `focus.ring → azure-500` |
| Input/Select/Textarea | radius | `radius.sm = 8px` |
| Input/Select/Textarea | border | `border.default → neutral-300` |
| Card | background | `background.surface → #FFFFFF` |
| Card | border | `border.subtle → neutral-200 = #E5E5E5` |
| Card | radius | `radius.md = 12px` default |
| Card | elevation | `elevation.0` ou `elevation.1` |
| Card | padding | `16–32px` |
| Drawer | elevation | `elevation.3` |
| Modal | elevation | `elevation.4` |
| Body copy | font | IBM Plex Sans |
| Technical labels | font | IBM Plex Mono |
| Feito success | color | `state.success → green-500` |
| Seletor | color | neutral; sem success por default |

Estados obrigatórios de Button: `DEFAULT`, `HOVER`, `FOCUS`, `ACTIVE`, `DISABLED`, `LOADING`.

## Editorial Hybrid v6

| Componente | Propriedade | Valor preservado |
|---|---|---|
| `.btn` | min-height | 56px |
| `.btn` | radius | 8px |
| `.btn` | focus | yellow, outline 2px, offset 3px |
| `.global-nav` | height | 56px |
| `.bottom-bar` | height | 64px |
| `.drawer` | width | `min(84vw,360px)` |
| cards/surfaces | radius | 0px |
| nav icon surface | radius | 4px |
| `.feature-media` | height | min 100vh, full width |
| `.selection-card` image | ratio | 3:4 |
| `.carousel-card .visual` | ratio | 3:4 |

## Regra

Os bindings do App derivados da decisão de fechamento são `DECISION · D/E`; os valores literais do Editorial permanecem rastreáveis à fonte.

A geração técnica para `next-forge/packages/design-system` ocorre no workflow de integração, sem alterar esses contratos.

`COMPONENT_TOKENS_READY = PASS`
