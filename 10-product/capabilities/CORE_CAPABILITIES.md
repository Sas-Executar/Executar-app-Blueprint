# CORE_CAPABILITIES

Status: `PARTIAL_SPECIFIED`
Primary source: `SRC-PRODUCT-MANIFESTO-001`
Secondary sources: `SRC-PRODUCT-BLUEPRINT-001`, `SRC-SCANNER-RUNTIME-FOLLOWUP-001`

## Capabilities centrais

| ID | Capability | Descrição | Classificação | Dependências principais |
|---|---|---|---|---|
| `CAP-EXEC-001` | Context Understanding | Consolidar objetivo, problema, restrições, dependências, capacidade, estado, evidências e bloqueios em contexto operacional persistente. | `CORPUS_DIRECT` | Estado canônico |
| `CAP-EXEC-002` | Work Structuring | Decompor trabalho em `Projeto → Value Stream → Entregável → Tarefa → Ação → Evidência`. | `CORPUS_DIRECT` | Context Understanding |
| `CAP-EXEC-003` | Capacity Planning | Determinar quanto trabalho cabe, o que excede e o que precisa ser replanejado com base em capacidade disponível. | `CORPUS_DIRECT` | Estrutura, estimativas, calendário/contexto |
| `CAP-EXEC-004` | Dependency & Eligibility | Considerar dependências, bloqueios e estado para definir o que está elegível para execução. | `CORPUS_DIRECT/CORPUS_DERIVED` | Estrutura, dependências |
| `CAP-EXEC-005` | Best Next Action | Apresentar uma próxima ação executável com precedência clara, reduzindo necessidade de escolha manual. | `CORPUS_DIRECT` | Eligibility, capacidade, WIP |
| `CAP-EXEC-006` | WIP 1:1 Execution | Proteger a execução com uma ação ativa de precedência cognitiva clara. | `CORPUS_DIRECT` | Best Next Action |
| `CAP-EXEC-007` | Evidence Capture | Registrar evidência associada à execução/conclusão e alimentar governança automaticamente. | `CORPUS_DIRECT` | Execução, storage/contratos futuros |
| `CAP-EXEC-008` | Continuous Replanning | Reorganizar caminho quando capacidade, dependência ou realidade mudarem sem reconstrução integral do projeto. | `CORPUS_DIRECT` | Estado, dependências, capacidade |
| `CAP-EXEC-009` | Check-in / Checkout / Resume | Persistir início, encerramento, ponto de parada, trabalho aberto, bloqueios e próximo movimento para retomada. | `CORPUS_DIRECT` | Estado canônico |
| `CAP-EXEC-010` | Mapa-OS | Representar visualmente estado, ativo, concluído, bloqueios, dependências, próximo movimento, capacidade e excedente. | `CORPUS_DIRECT` | Estado, capacidade, dependências |
| `CAP-EXEC-011` | Visual Symbol Scanner | Reconectar ação física ao estado digital por reconhecimento de símbolos e comandos. | `CORPUS_DIRECT` | Mapa-OS, estado canônico, contratos de ação |
| `CAP-EXEC-012` | Copilot Orchestration | Compreender entradas, estruturar, avaliar capacidade, orientar execução, detectar bloqueios, replanejar e emitir outputs operacionais. | `CORPUS_DIRECT` | Core Domain, Agent workflow futuro |
| `CAP-EXEC-013` | Status Report Generation | Derivar progresso, entregas, bloqueios, capacidade, desvios, evidências e próximos passos do estado registrado. | `CORPUS_DIRECT` | Evidência, estado |
| `CAP-EXEC-014` | Routines & Workflows | Automatizar rotinas e workflows temporais/operacionais sobre o mesmo estado de execução. | `CORPUS_DIRECT` | Estado, regras, Agents/Integrations futuros |
| `CAP-EXEC-015` | Omnichannel State Continuity | Permitir App, Copiloto, Scanner, papel e integrações operarem conceitualmente sobre um único estado canônico. | `CORPUS_DERIVED` | Estado canônico, contratos |

## Regra de readiness

Uma capability não muda para `READY` apenas porque está descrita aqui. Para `READY`, deve cumprir a Definition of Ready: requisitos, AC, regras, estados, dependências, permissões, contratos aplicáveis, design, analytics/security e target técnico.

## Estado atual resumido

- Core de produto: `PARTIAL → SPECIFIED` em progresso.
- Scanner: capability registrada; contratos específicos ficam em WF-05/WF-03/integração.
- Copiloto: capability registrada; regras de agente ficam em WF-03.
- Mapa-OS: capability registrada; page/assets detalhados ficam em WF-04.
- Analytics, security e NFRs: ainda não suficientes para `READY`.