---
id: AGENT-DELIV-REGISTRY-001
type: deliverable_registry
status: registered
version: 1.2.0
owner: null
---
# Deliverable Registry

| ID | Skill / associação | Entregável | Modelo | Autoridade |
|---|---|---|---|---|
| DELIV-MAPA-001 | executar-mapa-os | Mapa operacional | `deliverables/templates/mapa-projections.template.md` | Projeção declarada |
| DELIV-MAPA-002 | executar-mapa-os | Agora / Próximo / Depois | `deliverables/templates/mapa-projections.template.md` | Projeção declarada |
| DELIV-MAPA-003 | executar-mapa-os | Status terminal | `deliverables/templates/mapa-projections.template.md` | Projeção declarada |
| DELIV-MAPA-004 | executar-mapa-os | Prisma 7d · payload | `deliverables/templates/prism-7d-payload.template.json` | Derivado do contrato de projeção |
| DELIV-MAPA-005 | executar-mapa-os | Mapa-OS analógico Prisma A4 V4 | `skills/executar-mapa-os/assets/templates/status-report-prisma-a4-v4.html` | Template interno oficial da skill |
| DELIV-MAPA-006 | Mapa-OS + Scanner | Faixa física Copiloto / Seletor / Feito | `deliverables/templates/mapa-os-scanner-symbol-strip.template.html` | Superfície física parametrizada; reconhecimento pertence ao Scanner |
| DELIV-COP-001 | copiloto-executar | `/bomdia` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-002 | copiloto-executar | `/agora` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-003 | copiloto-executar | `/estado` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-004 | copiloto-executar | `/fechardia` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-005 | copiloto-executar | `/replanejamento` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-006 | copiloto-executar | Saída estruturada do orquestrador | `deliverables/templates/copiloto-orchestrator-output.template.json` | Derivado do schema da skill |
| DELIV-ROUT-001 | Modo Rotinas / copiloto-executar | Status Report canônico HTML | `deliverables/templates/status-report-routine.template.html` | ADR/PRD/SPEC de Rotinas |
| DELIV-ROUT-002 | Modo Rotinas / canais | Variantes App Reports / Email / WhatsApp | `deliverables/templates/status-report-routine-channel-variants.template.md` | Projeções do mesmo report canônico |
| DELIV-SUP-001 | Supporting model | Plano da Semana · Prisma A4 · `LAYOUT-PRISM-002` | `deliverables/templates/plano-semana-prisma-a4.template.html` | Modelo de apoio |
| DELIV-SUP-002 | Supporting model | Processo de trabalho + formulário de ciclo + semana | `deliverables/templates/processo-trabalho-formulario-semana.template.html` | Modelo de apoio |

## Mapa-OS rule
O Mapa-OS físico é uma projeção do estado digital canônico gerada pelo agente para gestão analógica das tarefas. Impressão, calendário ou símbolos não criam estado paralelo.

## Scanner rule
Os símbolos físicos podem integrar o Mapa-OS, porém `visual recognition`, `command dispatch` e mutações são responsabilidade da feature Scanner e de seus contratos próprios.

## Placeholder rule
Todo conteúdo variável dos modelos reutilizáveis usa `{{UPPER_SNAKE_CASE}}`. Exemplos preenchidos não podem se tornar defaults de template.

## Routine delivery rule
`DELIV-ROUT-001` é o report canônico. `DELIV-ROUT-002` adapta a mesma informação para cada canal. Falha em Email ou WhatsApp não altera estado de tarefa.

## Canonicality rule
O `prisma_7d` do `executar-mapa-os` permanece subordinado ao contrato V4 e ao índice interno da própria skill.
