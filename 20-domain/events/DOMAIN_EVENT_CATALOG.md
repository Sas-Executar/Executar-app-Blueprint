# DOMAIN_EVENT_CATALOG

Status: `PARTIAL_SPECIFIED`
Sources: manifesto + blueprint + legado funcional

| EVENT_ID | Evento | Quando ocorre | Classificação |
|---|---|---|---|
| `EVT-EXEC-001` | `project.created` | Project criado | `CORPUS_DERIVED` |
| `EVT-EXEC-002` | `work.structured` | Estrutura Project→...→Action preparada | `CORPUS_DERIVED` |
| `EVT-EXEC-003` | `action.ready` | Action passa a estar elegível | `CORPUS_DERIVED` |
| `EVT-EXEC-004` | `action.focused` | Action assume FOCUS | `CORPUS_DERIVED` |
| `EVT-EXEC-005` | `action.blocked` | blocker/dependência impede execução | `CORPUS_DERIVED` |
| `EVT-EXEC-006` | `action.unblocked` | blocker resolvido e elegibilidade recalculada | `CORPUS_DERIVED` |
| `EVT-EXEC-007` | `action.completed` | Action muda para DONE | `CORPUS_DERIVED` |
| `EVT-EXEC-008` | `evidence.recorded` | Evidence é registrada/associada | `CORPUS_DERIVED` |
| `EVT-EXEC-009` | `execution.checked_in` | sessão operacional inicia | `CORPUS_DERIVED` |
| `EVT-EXEC-010` | `execution.checked_out` | estado de saída/retomada é persistido | `CORPUS_DERIVED` |
| `EVT-EXEC-011` | `plan.replanned` | capacidade/dependência/realidade muda o caminho | `CORPUS_DERIVED` |
| `EVT-EXEC-012` | `cycle.started` | ciclo operacional de 72h inicia | `CORPUS_DERIVED` |
| `EVT-EXEC-013` | `cycle.closed` | ciclo operacional encerra | `CORPUS_DERIVED` |
| `EVT-EXEC-014` | `scanner.symbol_recognized` | símbolo conhecido reconhecido | `CORPUS_DIRECT/CORPUS_DERIVED` |
| `EVT-EXEC-015` | `status_report.generated` | report derivado do estado é emitido | `CORPUS_DERIVED` |

## Regra

Os nomes acima são normalização canônica inicial, não payloads finais. Schema, versionamento, idempotência e envelopes serão definidos no WF-05 Contracts.

## Gaps

- payloads e versões;
- actor/tenant metadata;
- correlation/causation IDs;
- delivery guarantees;
- retention/audit policy;
- eventos de Project/Deliverable lifecycle ainda não fechados.