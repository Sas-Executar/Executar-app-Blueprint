# EDGE_CASES_OFFLINE_SYNC

Status: `PARTIAL`
Sources: manifesto + blueprint + referência funcional PWA/offline

## Edge cases já sustentados pelo corpus

### EC-EXEC-001 — Nenhuma Action elegível
Quando não houver Action em READY, o sistema não deve inventar uma próxima ação. Deve expor blockers, dependências ou necessidade de replanejamento.

### EC-EXEC-002 — Action torna-se bloqueada durante FOCUS
O estado/contexto deve ser persistido, o blocker registrado e a Action removida da competição por execução até liberação.

### EC-EXEC-003 — Capacidade insuficiente
Quando o trabalho exceder a capacidade, o excedente deve permanecer explícito e não ser mascarado como compromisso executável.

### EC-EXEC-004 — Interrupção sem conclusão
Checkout deve permitir persistir ponto de parada e próximo movimento sem forçar DONE.

### EC-EXEC-005 — Dependência concluída
Sucessores previamente bloqueados devem ter elegibilidade recalculada.

### EC-EXEC-006 — Scanner desconhece símbolo
O Visual Symbol Scanner deve rejeitar `UNKNOWN`; reconhecimento não pode executar comando arbitrário.

### EC-EXEC-007 — Mutação do Scanner com undo
A fonte operacional do Scanner V2 prevê Done → COMPLETE_LATEST_OPEN_TASK com Undo; contrato final será normalizado no WF-05.

## Offline

A referência funcional vigente preserva comportamento PWA/offline, portanto a continuidade offline é uma capacidade existente a preservar durante evolução.

### Requisitos conhecidos

- estado local deve permanecer utilizável quando a rede estiver indisponível, quando a capability permitir;
- offline não autoriza criar estado paralelo definitivo;
- ao reconectar, o estado deve convergir para a autoridade canônica;
- reconhecimento visual do Scanner V2 foi especificado para funcionar on-device/offline.

## Sync — gaps ainda abertos

`GAP-SYNC-001` — estratégia de conflito quando duas superfícies modificam a mesma entidade offline.

`GAP-SYNC-002` — precedência de timestamps/version vectors/revision IDs ainda não definida.

`GAP-SYNC-003` — fila de mutations, retries e idempotência ainda não contratada.

`GAP-SYNC-004` — quais entidades suportam criação/edição offline ainda não definido.

`GAP-SYNC-005` — comportamento de evidence upload offline ainda não definido.

## Regra de governança

Os gaps de sync não devem ser preenchidos por escolha técnica dentro do WF-02. Eles serão convertidos em contrato/ADR no WF-05/integração, preservando o requisito de continuidade e estado canônico único.