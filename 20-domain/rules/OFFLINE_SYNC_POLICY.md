# OFFLINE_SYNC_POLICY

Status: `CANONICALIZED_BASELINE`
Sources: `SRC-LEGACY-DOMAIN-DESKOS-001` + current PWA preservation requirement

## Princípio

Offline não cria uma segunda autoridade de estado.

O sistema deve preservar continuidade local e convergir para o estado canônico quando a conexão retorna.

## Baseline funcional

```text
Remote canonical snapshot
  → local cache
  → read-only offline navigation
  → optional queued SAFE commands
  → reconnect
  → version/authorization validation
  → reconciliation
  → canonical state projection
```

## Política para mutations offline

### Default

Mutations offline ficam **bloqueadas** quando não existir contrato explícito que prove:

- operação segura para fila;
- idempotency key;
- expected version / optimistic concurrency;
- tenant/authorization context preservado;
- estratégia de conflito;
- retry determinístico;
- auditabilidade.

### Safe queued command

Uma mutation só pode ser enfileirada offline quando seu contrato no WF-05 a classificar explicitamente como `OFFLINE_QUEUE_SAFE`.

## Reconciliation

Ao reconectar:

1. recuperar versão remota atual;
2. revalidar tenant/autorização;
3. comparar expected version da operação;
4. aplicar comando somente se a precondição ainda for válida;
5. em conflito, não sobrescrever silenciosamente;
6. produzir erro/conflito explícito para resolução/replan quando necessário;
7. projetar o novo snapshot canônico.

## Event/concurrency primitives reutilizáveis

A fonte anterior já contém:

- `stream_version`;
- `correlation_id`;
- `causation_id`;
- `idempotency_key`;
- fluxo `Expected version check → Domain transition → Event append`.

Essas primitives ficam registradas como `REUSE CANDIDATE` para o WF-05, sem impor o antigo pacote de implementação.

## Scanner

Reconhecimento visual on-device pode funcionar offline, mas **reconhecer símbolo ≠ autorizar mutation offline**. O command resultante segue a mesma policy de segurança/sync da mutation correspondente.

## Resultado

- `GAP-SYNC-001` é reduzido: conflito silencioso é proibido e expected-version é o baseline.
- `GAP-SYNC-002` é reduzido: versionamento explícito é o mecanismo de precedência, não timestamp last-write-wins por padrão.
- `GAP-SYNC-003` migra para WF-05: schema exato de queued command, retry e idempotency.
- `GAP-SYNC-004/005` permanecem capability-specific: quais writes/evidence uploads podem operar offline serão decididos por contrato.
