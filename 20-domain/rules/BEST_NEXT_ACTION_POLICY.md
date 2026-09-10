# BEST_NEXT_ACTION_POLICY

Status: `PARTIAL_CANONICALIZED`
Sources: `SRC-METHOD-EXECUTION-001`, `SRC-EXECUTION-PROTOTYPE-001`, manifesto

## Objetivo

Selecionar uma Action executável para responder à pergunta de produto:

> O que devo fazer agora?

## Stage 1 — Candidate filter

O conjunto candidato é definido por restrições que convergem entre as fontes:

```text
Candidates =
  READY
  ∩ DependencySatisfied
  ∩ FitsAvailableTime
  ∩ CurrentCycle
```

Adicionalmente:

- BLOCKED não compete;
- DONE/VERIFIED não compete;
- a Action selecionada deve respeitar WIP 1:1;
- quando não há Candidates, o produto deve mostrar blockers/replan, não inventar uma ação.

Este estágio é `CORPUS_DERIVED` com suporte observado no protótipo e no método.

## Stage 2 — Ranking

As fontes registram critérios/intenção de ranking:

- caminho/flow;
- contexto/similaridade cognitiva;
- valor;
- prazo/urgência;
- capacidade/fit temporal;
- desbloqueio de sucessores.

O METHOD propõe `argmax [Flow(a), Context(a)]`; o protótipo comunica na UI uma cadeia mais ampla: `eligibilidade → dependências → caminho crítico → valor → prazo → similaridade cognitiva`.

## Conflito encontrado

`CONFLICT-BNA-001`

- intenção/documentação: ranking multi-critério;
- implementação observada no protótipo: `dispatchNext()` percorre a ordem atual e escolhe a próxima Action READY, sem prova de score multi-critério.

Portanto **não declarar o algoritmo de ranking como implementado ou aprovado**.

## Política canônica atual

1. Candidate filter é obrigatório.
2. WIP 1:1 é obrigatório.
3. Dependência e fit temporal precedem preferência subjetiva.
4. Ranking além do filtro permanece `GAP-BNA-SCORE-001` até decisão formal.
5. O ranking futuro deve ser determinístico/auditável o suficiente para explicar “por que esta ação?”.

## Saída mínima da decisão

Uma recomendação de Best Next Action deve poder explicar:

- Action selecionada;
- tempo estimado;
- por que está elegível;
- dependência relevante;
- qual entrega/caminho avança;
- blockers ignorados/ausentes;
- critérios de ranking usados, quando existirem.

## Fora de escopo

Progress Points (`PP`) e `100 PP/C72` permanecem `E · PROPOSED` na fonte METHOD e não são requisito canônico neste momento.