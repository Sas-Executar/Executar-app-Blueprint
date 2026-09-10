# CAPACITY_CYCLE_CONTRACT

Status: `CANONICALIZED_FROM_OBSERVED_FUNCTIONAL_REFERENCE`
Sources: `SRC-EXECUTION-PROTOTYPE-001`, manifesto, blueprint

## Invariantes funcionais observados

### C72

- janela operacional: `72h` / `3 dias`;
- capacidade selecionável por dia no protótipo: `2h`, `4h`, `6h`;
- no modo `6h/dia`: `18h executáveis/ciclo`;
- ação atômica de referência: `15 min`;
- conversão funcional: `4 ações/hora`;
- capacidade máxima correspondente a `18h`: `72 ações`;
- WIP de execução: `1`.

## Fórmula

Para a referência funcional atual:

```text
cycle_days = 3
executable_hours = daily_available_hours × cycle_days
action_minutes = 15
actions_per_hour = 60 / action_minutes = 4
available_actions = floor(executable_hours × 4)
```

Exemplos observados:

| Disponibilidade | Horas executáveis/ciclo | Capacidade em ações |
|---|---:|---:|
| 2h/dia | 6h | 24 |
| 4h/dia | 12h | 48 |
| 6h/dia | 18h | 72 |

## Capacidade bruta, disponível e demanda

- **capacidade bruta**: teto teórico do ciclo para a disponibilidade selecionada;
- **capacidade disponível**: quantidade de ações que ainda cabe após considerar trabalho já consumido/realizado e restrições aplicáveis;
- **demanda**: ações estimadas para o escopo;
- **excedente**: `max(0, demanda - capacidade disponível)`;
- o excedente deve permanecer explícito, não ser escondido dentro do ciclo.

## Capacidade restante

Referência funcional observada:

```text
capacity_remaining = max(0, cycle_capacity - count(DONE | VERIFIED))
```

Esta fórmula mede slots restantes no protótipo. Implementação final poderá separar melhor capacidade de agenda, capacidade consumida e throughput sem alterar os invariantes acima.

## Replanejamento

Mudança de disponibilidade gera nova projeção, preservando IDs, objetos já concluídos, evidências e histórico.

## Classificação

- 72h, 3 dias, 6h/dia → 18h/ciclo, 15 min/ação, 72 ações e WIP=1: `A · OBSERVED / D · INTERNAL` na referência funcional.
- uso desses valores como contrato atual do EXECUTAR: `CORPUS_DERIVED` por convergência entre manifesto, blueprint e protótipo.

## Não definido aqui

- estimador automático de duração diferente de 15 min;
- buffer por contexto/energia;
- disponibilidade extraída automaticamente de calendário;
- pesos de risco/complexidade;
- Progress Points.

Esses itens não alteram o contrato básico do C72 e exigem decisão própria se forem promovidos.