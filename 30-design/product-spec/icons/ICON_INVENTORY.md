# Icon Inventory — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`
Provider: `lucide-react` para ícones genéricos de UI

## Regra canônica

- ícones genéricos de UI → `lucide-react`;
- símbolos proprietários → SVGs próprios em `30-DESIGN/symbols/masters/`;
- Radix Icons pode permanecer em legado, mas não é o provider primário de novos ícones.

O provider foi escolhido por REUSE-FIRST: `lucide-react` já existe no `Sas-Executar/next-forge/packages/design-system`.

## Mapeamento núcleo

| ICON_ID | Semântica | Provider / asset |
|---|---|---|
| `ICON-SCANNER-001` | scanner / leitura visual | custom → `SYM-SCANNER-001` |
| `ICON-SELECTOR-001` | seletor / seleção neutra | custom → `SYM-SELECTOR-001` |
| `ICON-FEITO-001` | concluído / done | custom → `SYM-FEITO-001` |
| `ICON-MENU-001` | menu | Lucide `Menu` |
| `ICON-SEARCH-001` | busca | Lucide `Search` |
| `ICON-CLOSE-001` | fechar/remover | Lucide `X` |
| `ICON-OPEN-EXTERNAL-001` | abrir externo | Lucide `ExternalLink` |
| `ICON-LIGHT-MODE-001` | tema claro | Lucide `Sun` |
| `ICON-DARK-MODE-001` | tema escuro | Lucide `Moon` |
| `ICON-SETTINGS-001` | configurações | Lucide `Settings` |
| `ICON-INFO-001` | informação | Lucide `Info` |
| `ICON-PIN-001` | fixar | Lucide `Pin` |
| `ICON-TARGET-001` | objetivo/meta | Lucide `Target` |
| `ICON-CAMERA-001` | câmera | Lucide `Camera` |
| `ICON-LOCATION-001` | localização | Lucide `MapPin` |
| `ICON-CLOUD-001` | cloud/sync context | Lucide `Cloud` |
| `ICON-SPARKLES-001` | AI/enhancement quando permitido pelo contexto | Lucide `Sparkles` |
| `ICON-HEART-001` | favorito/afinidade quando aplicável | Lucide `Heart` |

## Acessibilidade

- IconButton sempre possui `aria-label`/nome acessível;
- ícone decorativo recebe `aria-hidden="true"`;
- não comunicar estado apenas pela mudança de ícone ou cor quando houver impacto semântico;
- stroke/size devem seguir component tokens no target técnico.

## Resultado

`GAP-DS-ICON-MAPPING-001 = CLOSED`
`GAP-DS-ICON-VECTOR-001 = CLOSED`
`GAP-DS-ICON-LIBRARY-001 = CLOSED`
`UI_ICON_REFERENCE_READY = PASS`
`UI_ICON_SEMANTIC_MAPPING_READY = PASS`
`UI_ICON_VECTOR_SOURCE_READY = PASS`
