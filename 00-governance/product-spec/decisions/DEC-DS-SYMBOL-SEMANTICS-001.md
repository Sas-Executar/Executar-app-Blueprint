# DEC-DS-SYMBOL-SEMANTICS-001

Status: `ACCEPTED`
Data: `2026-09-07`
Tipo: `Design · Decisão de semântica de símbolos`

## Contexto

O WF-01 recebeu benchmark visual suficiente para associar semanticamente os três símbolos funcionais centrais do EXECUTAR. O corpus já estabelecia a existência da capacidade de símbolos (`Scanner / Seletor / automacao de simbolos / atalhos`), porém faltava a amarração entre função e forma visual.

## Decisão

Adotar a família de glyphs em rounded square do benchmark recebido como trio canônico de símbolos de produto:

- `SYM-SCANNER-001` = rounded square com quatro pontos.
- `SYM-SELECTOR-001` = rounded square vazado.
- `SYM-FEITO-001` = rounded square com check.

## Justificativa

1. pertencem à mesma família visual;
2. possuem silhuetas facilmente distinguíveis;
3. suportam leitura rápida e potencial reconhecimento visual futuro;
4. preservam a semântica desejada do produto:
   - scanner = leitura;
   - seletor = neutro/seleção;
   - feito = conclusão.
5. são compatíveis com regras já estabelecidas:
   - Seletor sem cor semântica de sucesso;
   - Feito pode usar verde no App EXECUTAR;
   - Scanner permanece neutro/funcional.

## Consequências

### Fechado

- `GAP-DS-SYMBOL-MAPPING-001`
- parte núcleo de `GAP-DS-ICON-MAPPING-001`

### Ainda aberto

- `GAP-DS-SYMBOL-MASTER-001`
- `GAP-DS-SYMBOL-VECTOR-001`
- `GAP-DS-ICON-VECTOR-001`
- `GAP-DS-ICON-LIBRARY-001`

## Regra de uso

- não usar `SYM-FEITO-001` para qualquer ação genérica de “ok”; seu significado principal é conclusão/feito;
- não usar `SYM-SELECTOR-001` para done/success;
- não usar `SYM-SCANNER-001` como ícone de menu;
- futuras implementações devem manter consistência de container, peso visual e contraste.

## Referências

- `99-SOURCES/imported/SRC-DESIGN-BRAND-ASSETS-001.md`
- `30-DESIGN/icons/ICON_INVENTORY.md`
- `30-DESIGN/symbols/SYMBOL_INVENTORY.md`
