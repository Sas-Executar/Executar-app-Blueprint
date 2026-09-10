# Accessibility Contract — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`

## Regras comuns

- texto de corpo: contraste `>=4.5:1`;
- texto grande: contraste `>=3:1` quando aplicável;
- controles: alvo mínimo 44px;
- foco sempre visível;
- informação nunca depende somente de cor;
- `prefers-reduced-motion` deve ser respeitado;
- botões somente-ícone exigem nome acessível.

## Drawer modal — requisito obrigatório

`REQ-A11Y-DRAWER-001`

Quando o drawer estiver aberto:

1. conteúdo externo fica `inert` ou equivalente;
2. foco inicial entra em elemento apropriado dentro do drawer;
3. `Tab` e `Shift+Tab` permanecem no ciclo de foco do drawer;
4. `Escape` fecha o drawer;
5. ao fechar, foco retorna ao trigger, salvo fluxo logicamente diferente;
6. usar `aria-labelledby` e `aria-describedby` quando apropriado;
7. trigger mantém `aria-expanded` / `aria-controls` coerentes;
8. validação de integração deve incluir teclado e leitor de tela.

O contrato segue o W3C WAI-ARIA APG Modal Dialog Pattern. A verificação de código pertence ao gate de integração/produção, não ao WF-01.

## Search

Ver `30-DESIGN/components/SEARCH_CONTRACT.md`:

- container `role="search"`;
- contagem/status em `aria-live="polite"`;
- estados `IDLE`, `TYPING`, `LOADING`, `RESULTS`, `EMPTY`, `ERROR`;
- erro não pode ser apresentado como zero-result.

## Resultado

`BLOCKER-A11Y-DRAWER-001 = CLOSED_AS_SPEC`

A implementação continua sujeita a verificação no target técnico. Isso não é um gap restante da fundação de Design.
