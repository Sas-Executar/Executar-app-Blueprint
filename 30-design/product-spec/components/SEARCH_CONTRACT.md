# Search Contract — WF-01

Status: `DONE`
Decision: `DEC-DS-FOUNDATION-CLOSURE-001`
Classificação: `CONTRACT · D/E`

## Estados obrigatórios

`IDLE` → `TYPING` → `LOADING` → `RESULTS | EMPTY | ERROR`

## Estrutura

- container com `role="search"`;
- input com nome acessível;
- botão limpar quando houver query;
- resultado mantém a query visível;
- quantidade de resultados anunciada em `aria-live="polite"`;
- navegação por teclado preserva foco visível;
- seleção/estado não depende somente de cor.

## EMPTY

Título: `Nenhum resultado encontrado`

Apoio: `Tente outro termo ou ajuste os filtros.`

Ações permitidas: limpar busca, remover filtros, voltar ao estado anterior.

## ERROR

- preservar query e filtros;
- mensagem clara de falha;
- CTA `Tentar novamente`;
- não transformar erro técnico em zero-result.

## RESULTS

- exibir contagem quando útil;
- não mover foco automaticamente para o primeiro resultado;
- resultados acionáveis precisam de nome acessível e estado de foco.

`GAP-DS-SEARCH-001 = CLOSED`
