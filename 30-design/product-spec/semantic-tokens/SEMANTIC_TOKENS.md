# Semantic Tokens — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`
Executable source: `30-DESIGN/tokens/DESIGN_TOKENS_FINAL.json`

## App EXECUTAR — Green + Expo

| Token | Binding | Uso |
|---|---|---|
| `background.canvas` | `neutral-100` | canvas/fundo alternativo |
| `background.surface` | `#FFFFFF` | cards, painéis, inputs, modais |
| `text.primary` | `neutral-700` | texto principal |
| `text.secondary` | `neutral-600` | texto secundário |
| `text.muted` | `neutral-500` | apoio/legendas |
| `border.subtle` | `neutral-200` | divisórias sutis |
| `border.default` | `neutral-300` | borda padrão |
| `action.primary` | `green-500` | executar / CTA principal |
| `action.secondary` | `azure-500` | ação secundária |
| `state.success` | `green-500` | sucesso / Feito |
| `state.info` | `azure-500` | informação |
| `focus.ring` | `azure-500` | foco visível |

Warning/error devem ser definidos no contexto funcional quando suas capabilities forem especificadas; não bloqueiam o foundation visual porque não havia valor obrigatório anterior.

## Editorial Hybrid v6

Preservados: preto como ação principal, amarelo `#FFCC00` como destaque/accent, paper `#FFFFFF`, charcoal `#111111`, ink `#1D1D1F`, muted `#6E6E73`, line `#D2D2D7`, focus ring amarelo.

## Brand identity

Preservados: primary `#000000`, secondary `#2D2D2D`, support `#9A9A9A`, background `#E5E5E5`, offwhite `#F8F8F8`, white `#FFFFFF`.

## Regras

- App: Green executa; Azure informa/navega.
- `SYM-FEITO-001` pode usar `state.success` quando representar conclusão.
- `SYM-SELECTOR-001` permanece neutro.
- Editorial Hybrid não adota Azure como ação.
- Brand identity não substitui automaticamente os aliases de App/Editorial.

`GAP-DS-NEUTRAL-001 = CLOSED`
