# EXECUTION_STATE_MACHINE

Status: `PARTIAL_SPECIFIED`
Source: `SRC-PRODUCT-MANIFESTO-001` + `SRC-PRODUCT-BLUEPRINT-001`

## Máquina de estados inicial

```text
BACKLOG
   │ structure + eligibility satisfied
   ▼
READY
   │ dispatch / start
   ▼
FOCUS
   │ complete
   ▼
DONE

READY ───────────────► BLOCKED
FOCUS ───────────────► BLOCKED
BLOCKED ── unblock ──► READY
FOCUS ── interruption/checkout ──► READY* / persisted resume state
```

`*` A transição de interrupção para READY é `CORPUS_DERIVED`; a fonte exige persistência/retomada, mas não publica enum separado como `PAUSED`. Até decisão específica, a retomada é tratada como estado persistido + elegibilidade recalculada, não como novo enum.

## Transições

| ID | From | Trigger | To | Regra |
|---|---|---|---|---|
| `TR-EXEC-001` | BACKLOG | estruturação + critérios mínimos de elegibilidade | READY | item passou a poder competir por execução |
| `TR-EXEC-002` | READY | start/dispatch/focus | FOCUS | respeitar WIP 1:1 |
| `TR-EXEC-003` | READY | blocker/dependency impeditiva detectada | BLOCKED | remover da fila executável |
| `TR-EXEC-004` | FOCUS | blocker impeditivo detectado | BLOCKED | persistir contexto e blocker |
| `TR-EXEC-005` | BLOCKED | blocker resolvido + eligibility recalculada | READY | não retornar automaticamente a FOCUS sem novo despacho |
| `TR-EXEC-006` | FOCUS | complete | DONE | atualizar sucessores, progresso e evidência conforme contrato |
| `TR-EXEC-007` | FOCUS | checkout/interrupção | READY* | persistir ponto de parada e recalcular próxima ação ao retomar |

## Guardas mínimas

### G-EXEC-001 — Eligibility
Para ir a READY, dependências bloqueantes devem estar resolvidas e o item deve ser executável no contexto atual.

### G-EXEC-002 — WIP
Para ir a FOCUS, o sistema deve preservar a política WIP 1:1 do contexto de execução.

### G-EXEC-003 — Completion
Para ir a DONE, a ação precisa registrar conclusão; Evidence é aplicada conforme regra/contrato da capability.

### G-EXEC-004 — Replan
Mudanças de capacidade/dependência podem recalcular READY/BLOCKED e ordem de despacho sem alterar arbitrariamente DONE.

## Side effects esperados

- FOCUS iniciado → registrar check-in/contexto operacional quando aplicável.
- DONE → recalcular dependências, progresso, sucessores elegíveis e outputs de evidência/status.
- BLOCKED → registrar blocker e impedir competição no Next Action.
- checkout → persistir estado, aberto, próximo movimento e blockers.

## Gaps

- `GAP-SM-001` — semântica formal de cancelamento/arquivo não definida.
- `GAP-SM-002` — comportamento de reabertura de DONE não definido.
- `GAP-SM-003` — conflito de múltiplas superfícies atualizando o mesmo estado ainda requer contrato de sync.
- `GAP-SM-004` — regras exatas de undo além do Scanner/Done específico ficam para Contracts.