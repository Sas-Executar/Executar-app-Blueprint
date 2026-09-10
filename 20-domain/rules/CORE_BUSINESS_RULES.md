# CORE_BUSINESS_RULES

Status: `PARTIAL_SPECIFIED`
Primary source: `SRC-PRODUCT-MANIFESTO-001`
Secondary sources: `SRC-PRODUCT-BLUEPRINT-001`, `SRC-EXECUTION-PROTOTYPE-001`, `SRC-METHOD-EXECUTION-001`, `SRC-LEGACY-DOMAIN-DESKOS-001`

## Regras canônicas

### BR-EXEC-001 — WIP 1:1
`CORPUS_DIRECT / A-D OBSERVED`

Múltiplos projetos podem existir, mas uma única Action deve possuir precedência ativa no contexto de execução. O protótipo funcional também implementa WIP=1.

### BR-EXEC-002 — Próxima ação executável
`CORPUS_DIRECT`

A experiência privilegia uma próxima Action executável, não uma lista indiferenciada de prioridades.

### BR-EXEC-003 — Elegibilidade antes do despacho
`CORPUS_DERIVED`

Baseline de candidatos:

`READY ∩ DependencySatisfied ∩ FitsAvailableTime ∩ CurrentCycle`.

BLOCKED, DONE e VERIFIED não competem. Ver `BEST_NEXT_ACTION_POLICY.md`.

### BR-EXEC-004 — Bloqueado não compete
`CORPUS_DIRECT / A OBSERVED`

Itens com dependência impeditiva permanecem BLOCKED e fora da fila executável. Quando a dependência é satisfeita, a elegibilidade pode ser recalculada para READY.

### BR-EXEC-005 — Planejamento por capacidade
`CORPUS_DIRECT`

O sistema considera tempo/capacidade, trabalho que cabe, dependências, precedência, excedente e necessidade de replanejamento.

### BR-EXEC-006 — C72 e ação atômica
`A · OBSERVED / D · INTERNAL + CORPUS_DERIVED`

Contrato funcional atual:

- ciclo = 72h / 3 dias;
- referência máxima = 6h executáveis/dia;
- 18h executáveis/ciclo;
- Action atômica de referência = 15 min;
- 4 Actions/hora;
- capacidade máxima no modo 6h/dia = 72 Actions;
- opções observadas: 2h/dia → 24 Actions, 4h/dia → 48, 6h/dia → 72.

Detalhes em `CAPACITY_CYCLE_CONTRACT.md`.

### BR-EXEC-007 — Dependências e caminho
`CORPUS_DIRECT`

Dependências devem orientar sequência, bloqueio, eligibility e caminho crítico/fluxo.

### BR-EXEC-008 — Estado persistente
`CORPUS_DIRECT`

O estado persiste entre interrupções e superfícies para reduzir reconstrução manual de contexto.

### BR-EXEC-009 — Check-in / checkout
`CORPUS_DIRECT`

Check-in registra início/contexto; checkout registra onde parou, realizado, aberto, blocker e próximo movimento quando determinável.

### BR-EXEC-010 — Retomada orientada
`CORPUS_DIRECT`

Ao retornar, o sistema apresenta estado anterior e próxima Action disponível, em vez de devolver toda a decisão ao usuário.

### BR-EXEC-011 — Replanejamento contínuo
`CORPUS_DIRECT / A OBSERVED`

Mudança de capacidade/dependência/realidade pode gerar nova projeção preservando IDs, objetos concluídos, evidência e histórico.

### BR-EXEC-012 — Evidência nasce da execução
`CORPUS_DIRECT`

Conclusão produz/associa Evidence quando a `completion_rule` da capability exigir e alimenta progresso, histórico, Status Report e governança.

A fonte anterior comprova suporte a `requires_evidence`, mas a obrigatoriedade continua capability-specific.

### BR-EXEC-013 — Autonomia preservada
`CORPUS_DIRECT`

Automação reduz carga operacional, mas decisões legítimas/relevantes permanecem sob autoridade do usuário.

### BR-EXEC-014 — Um estado canônico
`CORPUS_DERIVED`

App, Copiloto, Mapa-OS, Scanner e integrações aplicáveis devem refletir a mesma autoridade operacional, sem planos paralelos por superfície.

### BR-EXEC-015 — Continuidade analógico-digital
`CORPUS_DIRECT`

Papel pode ser superfície de ação; digital preserva contexto, lógica, rastreabilidade, estado, dependências e Evidence.

### BR-EXEC-016 — Interface mínima durante execução
`CORPUS_DIRECT`

Durante FOCUS, reduzir escolhas, telas, informações concorrentes, caminhos e alternâncias ao mínimo necessário.

### BR-EXEC-017 — Personalização apenas quando altera execução
`CORPUS_DIRECT`

Preferir padrões operacionais robustos a customização superficial que adiciona decisões sem alterar a execução.

### BR-EXEC-018 — Agrupamento semântico
`CORPUS_DIRECT`

Atividades relacionadas devem permanecer próximas quando isso reduzir custo de transição.

### BR-EXEC-019 — Offline conservador
`A/D OBSERVED + CORPUS_DERIVED`

Offline usa snapshot/cache local e não cria autoridade paralela. Mutations offline ficam bloqueadas por padrão até existir contrato `OFFLINE_QUEUE_SAFE` com idempotência, expected version, autorização, retry e conflito explícito. Ver `OFFLINE_SYNC_POLICY.md`.

### BR-EXEC-020 — Conflito não é last-write-wins silencioso
`CORPUS_DERIVED`

Execuções mutáveis devem validar versão esperada antes da transição; conflito não pode sobrescrever silenciosamente estado remoto mais novo.

## Gaps reais restantes

- `GAP-BNA-SCORE-001` — ranking/score final da Best Next Action. O candidate filter está fechado; o score não.
- `GAP-EVID-POLICY-001` — política de Evidence por capability/DoD.
- `GAP-PERM-ROLE-001` — roles e matriz final.
- `GAP-LIFECYCLE-AGG-001` — lifecycle específico Project/ValueStream/Deliverable na nova hierarquia.
- `GAP-SYNC-CONTRACT-001` — schema de queued commands e capabilities autorizadas offline (WF-05).

Não promover Progress Points/100 PP por C72: a fonte METHOD os classifica como arquitetura inferida/proposta.