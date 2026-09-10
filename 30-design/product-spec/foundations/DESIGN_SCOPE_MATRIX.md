# Design Scope Matrix — WF-01

Status: `CANONICALIZED_WITH_REMAINING_GAPS`
Workflow: `WF-01 Design System`
Data: `2026-09-07`

## Regra de autoridade

Este arquivo normaliza as fontes existentes; não substitui os arquivos brutos nem cria implementação.

| Escopo | Sistema | Fonte primária | Classificação | Estado |
|---|---|---|---|---|
| App EXECUTAR — UI | Green + Expo | `Sas-Executar/Desyng-System-ecossitema.` → `references/source-docs/ADR-SYSTEM.md` | CORPUS_DIRECT | Accepted/SOT na fonte |
| Ecossistema editorial fora do App — UI | Editorial Hybrid — NatGeo × Apple UX v6 | handoff `DESIGN-HYBRID-APPLE-007` v6 + `tokens-hybrid.css/json` + protótipo HTML | CORPUS_DIRECT | fonte recebida; decisão de escopo registrada como rascunho em Programa-Sas |
| EXECUTAR — identidade de marca e exports | Monochrome Brand PNG Package v1.0 | `SRC-DESIGN-BRAND-ASSETS-001` | CORPUS_DIRECT | fonte primária recebida para completar assets/gaps de brand |
| Fractal Fluent | histórico / não-SoT segundo D11 draft | `Sas-Executar/Sas-Executar` + registro D11 | CORPUS_DIRECT para existência; decisão de substituição ainda pendente de validação formal | histórico |

## Green + Expo — App EXECUTAR

- Green `#00BF63`: ação principal, execução, progresso, confirmação e estado positivo.
- Azure `#1F93FF`: informação, navegação, links e interação secundária.
- Dark Gray `#4B4A4A`, Light Gray `#F6F6F6`, White `#FFFFFF`.
- Tipografia: IBM Plex Sans; IBM Plex Mono para IDs, métricas, código, prompts e metadados.
- Regra crítica: componentes não consomem HEX diretamente; usam tokens semânticos.
- Linguagem: superfícies neutras, linhas finas, sombras mínimas, alto espaço negativo.

## Editorial Hybrid v6 — superfícies editoriais

- Ação primária preta `#000000`; accent amarelo `#ffcc00`.
- Sem azul como cor de ação.
- Superfície clara dominante; `#111111` reservado ao momento escuro de seleção.
- UI em SF Pro/system; leitura longa em New York/Iowan/Georgia fallback.
- Cards e imagens com cantos retos; botão com raio 8px.
- Desktop `>=900px`; mobile/tablet `<900px`; mobile pequeno `<620px`.
- Drawer + bottom bar de exatamente 3 destinos no mobile.

## Brand Identity Layer — Monochrome Brand PNG Package v1.0

Esta camada governa **marca e exports**, não substitui automaticamente a receita visual das interfaces.

- Black `#000000` — primary.
- Dark Gray `#2D2D2D` — secondary.
- Gray `#9A9A9A` — support.
- Light Gray `#E5E5E5` — background.
- Off White `#F8F8F8` e White `#FFFFFF` — superfícies neutras presentes no README do pacote.
- direção tipográfica: monospaced, uppercase, expanded tracking.
- logo/wordmark em variantes primary, dark/black, reverse, horizontal e stacked.
- clear space mínimo do ícone: `X`, onde `X` é a altura do check mark dentro do ícone.
- tamanho mínimo do ícone: `16×16px`.
- largura mínima do wordmark horizontal: `80px`.
- exports: iOS, Android, PWA, favicon, social/OG.

A fonte entrega wordmark rasterizado; não distribui arquivo de fonte. Portanto, **não reconstruir o wordmark digitando uma fonte aproximada** quando o asset oficial estiver disponível.

## Regra de coexistência

As três camadas não devem ser confundidas:

1. **Brand identity** define marca, wordmark, app icon, favicon e identidade monocromática.
2. **Green + Expo** define a UI do App EXECUTAR.
3. **Editorial Hybrid v6** define as superfícies editoriais fora do App.

Um app icon monocromático pode coexistir com uma interface Green+Expo; isso não autoriza substituir `#00BF63`/`#1F93FF` na UI. Da mesma forma, a marca monocromática não reintroduz uma terceira cor de ação no Editorial Hybrid.

## Gaps preservados após `SRC-DESIGN-BRAND-ASSETS-001`

- Aprovação formal do escopo global Editorial Hybrid no documento D11 continua pendente.
- Green 50–900 e Azure 50–900 continuam sem valores publicados.
- `neutral-200/300/500/600` do Green+Expo continuam sem mapeamento explícito; a paleta monocromática não é promovida automaticamente a esses níveis.
- biblioteca UI de ícones possui referência visual, mas ainda não possui nomes semânticos/provider/masters vetoriais individuais.
- sistema de símbolos de produto possui capacidade documentada e referências visuais candidatas, mas ainda não existe mapeamento explícito `símbolo → asset → significado → ação`.

Nenhum desses gaps autoriza inventar assets, valores ou significado.