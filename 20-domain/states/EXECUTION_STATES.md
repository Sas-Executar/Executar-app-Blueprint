# EXECUTION_STATES

Status: `PARTIAL_SPECIFIED`
Source: `SRC-PRODUCT-BLUEPRINT-001` + manifesto

## Estados canônicos iniciais da unidade executável

| Estado | Significado | Classificação |
|---|---|---|
| `BACKLOG` | Trabalho identificado, mas ainda não preparado/elegível para execução imediata. | `CORPUS_DIRECT` no briefing WF-02 |
| `READY` | Trabalho preparado e elegível para iniciar, sem bloqueio impeditivo conhecido. | `CORPUS_DIRECT` no briefing WF-02 + alinhado ao legado funcional |
| `FOCUS` | Unidade atualmente ativa, com precedência cognitiva clara sob WIP 1:1. | `CORPUS_DIRECT` no briefing WF-02 + manifesto |
| `BLOCKED` | Unidade cuja execução está impedida por dependência, restrição ou blocker. | `CORPUS_DIRECT` |
| `DONE` | Unidade concluída, com estado final de execução; evidência pode ser obrigatória conforme regra/contrato aplicável. | `CORPUS_DIRECT` |

## Semântica operacional

### BACKLOG
- não aparece como próxima ação apenas por existir;
- precisa passar por estruturação/eligibility para entrar em READY.

### READY
- pode competir por Next Action;
- deve ter dependências bloqueantes resolvidas;
- pode deixar de ser elegível se a realidade mudar.

### FOCUS
- deve haver no máximo uma ação com precedência operacional ativa no contexto de WIP 1:1;
- representa “o que fazer agora”.

### BLOCKED
- não compete pela fila executável;
- deve expor razão/bloqueador suficiente para orientar liberação.

### DONE
- conclusão deve atualizar estado agregado e liberar sucessores quando dependências forem satisfeitas;
- pode gerar Evidence e eventos derivados.

## Estados agregados

Project, ValueStream e Deliverable podem possuir status derivados próprios, mas as fontes atuais não definem enums completos para cada agregado.

`GAP-STATE-AGG-001`: lifecycle específico de Project.
`GAP-STATE-AGG-002`: lifecycle específico de ValueStream.
`GAP-STATE-AGG-003`: lifecycle específico de Deliverable.

## Estados auxiliares propostos não promovidos

Termos como `ARCHIVED`, `CANCELLED`, `PAUSED`, `DRAFT` e `IN_REVIEW` são comuns em produtos de trabalho, mas **não são requisitos canônicos neste momento**. Permanecem fora do enum até fonte/decisão.