# Responsive & Motion — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`

## App EXECUTAR — Green + Expo

### Breakpoints canônicos

| Faixa | Contrato |
|---|---|
| `<480px` | small mobile; composição linear, prioridade para conteúdo/ação |
| `480–639px` | mobile amplo |
| `640–1023px` | tablet; visual reduzido + conteúdo |
| `>=1024px` | desktop; visual + conteúdo lado a lado |
| `>=1366px` | desktop amplo |
| `>=1920px` | large display; limitar medidas de leitura/shell |

Tokens: `320, 480, 640, 1024, 1366, 1920px` conforme `DESIGN_TOKENS_FINAL.json`.

Objetos isométricos complexos devem ser simplificados no mobile, não apenas reduzidos.

### Motion

- micro 120–180ms;
- default 180–250ms;
- large 250–400ms;
- easing ease-out;
- motion comunica estado, hierarquia ou deslocamento espacial;
- `prefers-reduced-motion` deve ser respeitado.

## Editorial Hybrid v6

Preservar os contratos publicados:

- desktop `>=900px`;
- tablet/mobile `<900px`;
- mobile pequeno `<620px`;
- nav + bottom bar sincronizados 280ms;
- drawer 320ms;
- button pressed 150ms;
- hero 900ms uma vez;
- feature media reveal uma vez;
- no máximo dois momentos animados de conteúdo por página sem revisão.

As escalas responsivas do App e do Editorial permanecem namespaces diferentes; não substituir 900/620 pelos breakpoints do App.

`GAP-DS-BREAKPOINT-APP-001 = CLOSED`
