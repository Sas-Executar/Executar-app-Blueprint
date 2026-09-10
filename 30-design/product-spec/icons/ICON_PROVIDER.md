# Icon Provider — WF-01

Status: `ACCEPTED`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`

## Provider primário

`lucide-react` é o provider canônico de **ícones genéricos de UI** na integração com `next-forge`.

Razões:

- já existe em `Sas-Executar/next-forge/packages/design-system`;
- evita introduzir uma segunda biblioteca sem necessidade;
- cobre navegação, busca, fechar, configuração, tema, abrir externo, pin, target e utilitários comuns;
- mantém os símbolos proprietários separados da iconografia genérica.

## Mapeamento núcleo

| Semântica | Lucide |
|---|---|
| menu | `Menu` |
| busca | `Search` |
| fechar/remover | `X` |
| abrir externo | `ExternalLink` |
| tema claro | `Sun` |
| tema escuro | `Moon` |
| configurações | `Settings` |
| informação | `Info` |
| fixar | `Pin` |
| objetivo/meta | `Target` |

## Símbolos proprietários

Não usar Lucide para substituir:

- `SYM-SCANNER-001`
- `SYM-SELECTOR-001`
- `SYM-FEITO-001`

Esses símbolos possuem masters próprios em `30-DESIGN/symbols/masters/`.

## Regra

Radix Icons pode permanecer onde já existir, mas novos usos genéricos devem priorizar Lucide para reduzir variação visual e retrabalho.

`GAP-DS-ICON-VECTOR-001 = CLOSED`
`GAP-DS-ICON-LIBRARY-001 = CLOSED`
