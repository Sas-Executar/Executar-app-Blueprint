# COMMAND_QUERY_CATALOG

Status: `PARTIAL_SPECIFIED`
Sources: manifesto + blueprint + scanner follow-up

## Commands iniciais

| COMMAND_ID | Command | Intenção | Classificação |
|---|---|---|---|
| `CMD-EXEC-001` | `CreateProject` | criar Project | `CORPUS_DERIVED` |
| `CMD-EXEC-002` | `StructureWork` | decompor contexto em estrutura operacional | `CORPUS_DERIVED` |
| `CMD-EXEC-003` | `StartAction` | mover Action elegível para FOCUS | `CORPUS_DERIVED` |
| `CMD-EXEC-004` | `CompleteAction` | concluir Action | `CORPUS_DERIVED` |
| `CMD-EXEC-005` | `RecordEvidence` | associar Evidence à execução | `CORPUS_DERIVED` |
| `CMD-EXEC-006` | `BlockAction` | registrar blocker e estado BLOCKED | `CORPUS_DERIVED` |
| `CMD-EXEC-007` | `UnblockAction` | remover blocker e recalcular eligibility | `CORPUS_DERIVED` |
| `CMD-EXEC-008` | `CheckInExecution` | iniciar sessão/contexto operacional | `CORPUS_DERIVED` |
| `CMD-EXEC-009` | `CheckOutExecution` | persistir ponto de parada/retomada | `CORPUS_DERIVED` |
| `CMD-EXEC-010` | `ReplanWork` | recalcular caminho futuro | `CORPUS_DERIVED` |
| `CMD-EXEC-011` | `GenerateMapaOS` | emitir projeção Mapa-OS | `CORPUS_DERIVED` |
| `CMD-EXEC-012` | `GenerateStatusReport` | emitir report derivado do estado | `CORPUS_DERIVED` |
| `CMD-EXEC-013` | `OpenChat` | abrir Copiloto/Chat via símbolo/ação | `CORPUS_DIRECT` Scanner V2 |
| `CMD-EXEC-014` | `OpenSelector` | abrir Seletor configurável | `CORPUS_DIRECT` Scanner V2 |
| `CMD-EXEC-015` | `CompleteLatestOpenTask` | concluir item aberto mais recente pelo fluxo Scanner Done | `CORPUS_DIRECT` Scanner V2 |

## Queries iniciais

| QUERY_ID | Query | Resultado esperado |
|---|---|---|
| `QRY-EXEC-001` | `GetOperationalState` | estado canônico do contexto atual |
| `QRY-EXEC-002` | `GetEligibleActions` | Actions em condição de iniciar |
| `QRY-EXEC-003` | `GetBestNextAction` | próxima Action recomendada/despachável |
| `QRY-EXEC-004` | `GetBlockedWork` | itens bloqueados + blockers/dependências |
| `QRY-EXEC-005` | `GetCapacityWindow` | capacidade disponível/planejada/realizada aplicável |
| `QRY-EXEC-006` | `GetDependencyPath` | dependências/caminho aplicável |
| `QRY-EXEC-007` | `GetResumeContext` | ponto de parada, aberto, blockers, próximo movimento |
| `QRY-EXEC-008` | `GetProgressSnapshot` | progresso/evidências/estado agregados |

## Limite

Os nomes acima são semântica de domínio, não assinatura de API. Inputs, outputs, auth, idempotência e schemas serão definidos no WF-05 Contracts.