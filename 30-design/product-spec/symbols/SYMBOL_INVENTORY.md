# Symbol Inventory — WF-01

Status: `DONE`
Decisions: `DEC-DS-SYMBOL-SEMANTICS-001` + `DEC-DS-FOUNDATION-CLOSURE-001`

## Símbolos canônicos

| SYMBOL_ID | Nome | Master | Semântica | Cor semântica |
|---|---|---|---|---|
| `SYM-SCANNER-001` | Scanner | `masters/scanner.svg` | leitura / reconhecimento / invocar scanner | neutra/monocromática |
| `SYM-SELECTOR-001` | Seletor | `masters/selector.svg` | seleção / modo seletor / alvo atual | neutra; não usar success |
| `SYM-FEITO-001` | Feito | `masters/feito.svg` | conclusão / marcar como feito | Green quando representar conclusão no App |

## Geometria

Os três masters usam `viewBox 0 0 24 24`, container rounded-square e `currentColor`. A geometria é própria, criada para implementar a decisão benchmark-based sem declarar cópia literal das pranchas raster.

### Scanner

Rounded square + quatro pontos internos. Não reutilizar como menu/categorias.

### Seletor

Rounded square vazado. Pode receber focus ring/active treatment, porém sem verde de sucesso como estado principal.

### Feito

Rounded square + check. Reservado para conclusão/feito; não usar como `OK` genérico para qualquer ação.

## Estados

| Símbolo | Default | Active | Success | Disabled |
|---|---|---|---|---|
| Scanner | monocromático | invertido/filled conforme componente | n/a | opacity reduzida |
| Seletor | vazado neutro | focus/selected treatment | n/a | opacity reduzida |
| Feito | neutro | filled/invertido | Green no App | opacity reduzida |

## Integração futura

- masters são a autoridade visual proprietária;
- componentes React/React Native devem consumir os SVGs sem alterar geometria;
- scanner visual/ML é outro contrato e não faz parte do WF-01;
- Copiloto não pertence ao trio aprovado neste workflow; sua identidade visual deve ser definida no workflow de Agents caso seja promovida a símbolo funcional.

## Resultado

`GAP-DS-SYMBOL-MAPPING-001 = CLOSED`
`GAP-DS-SYMBOL-MASTER-001 = CLOSED`
`GAP-DS-SYMBOL-VECTOR-001 = CLOSED`
`PRODUCT_SYMBOL_REFERENCE_READY = PASS`
`PRODUCT_SYMBOL_SEMANTIC_MAPPING_READY = PASS`
`PRODUCT_SYMBOL_MASTER_ASSETS_READY = PASS`
