---
id: AGENT-DELIV-REGISTRY-001
type: deliverable_registry
status: registered
version: 1.1.0
owner: null
---
# Deliverable Registry

| ID | Skill / associação | Entregável | Modelo | Autoridade |
|---|---|---|---|---|
| DELIV-MAPA-001 | executar-mapa-os | Mapa operacional | `deliverables/templates/mapa-projections.template.md` | Projeção declarada |
| DELIV-MAPA-002 | executar-mapa-os | Agora / Próximo / Depois | `deliverables/templates/mapa-projections.template.md` | Projeção declarada |
| DELIV-MAPA-003 | executar-mapa-os | Status terminal | `deliverables/templates/mapa-projections.template.md` | Projeção declarada |
| DELIV-MAPA-004 | executar-mapa-os | Prisma 7d · payload | `deliverables/templates/prism-7d-payload.template.json` | Derivado do contrato de projeção |
| DELIV-COP-001 | copiloto-executar | `/bomdia` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-002 | copiloto-executar | `/agora` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-003 | copiloto-executar | `/estado` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-004 | copiloto-executar | `/fechardia` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-005 | copiloto-executar | `/replanejamento` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-006 | copiloto-executar | Saída estruturada do orquestrador | `deliverables/templates/copiloto-orchestrator-output.template.json` | Derivado do schema da skill |
| DELIV-ROUT-001 | Modo Rotinas / copiloto-executar | Status Report canônico HTML | `deliverables/templates/status-report-routine.template.html` | ADR/PRD/SPEC de Rotinas; derivado do Status Report fornecido |
| DELIV-ROUT-002 | Modo Rotinas / canais | Variantes App Reports / Email / WhatsApp | `deliverables/templates/status-report-routine-channel-variants.template.md` | Projeções de entrega do mesmo report canônico |
| DELIV-SUP-001 | Supporting model | Plano da Semana · Prisma A4 · `LAYOUT-PRISM-002` | `deliverables/templates/plano-semana-prisma-a4.template.html` | Modelo fornecido; não declarado canônico pelo `SKILL.md` |
| DELIV-SUP-002 | Supporting model | Processo de trabalho + formulário de ciclo + semana | `deliverables/templates/processo-trabalho-formulario-semana.template.html` | Modelo fornecido; associação a skill ainda não determinada |

## Placeholder rule
Todo conteúdo variável dos modelos reutilizáveis usa `{{UPPER_SNAKE_CASE}}`. Exemplos preenchidos não podem se tornar defaults de template.

## Routine delivery rule
`DELIV-ROUT-001` é o report canônico. `DELIV-ROUT-002` adapta a mesma informação para cada canal. Falha em Email ou WhatsApp não cria ou modifica estado de tarefa e não altera o report persistido em App Reports.

## Canonicality rule
O `prisma_7d` do `executar-mapa-os` continua subordinado ao contrato V4 declarado no pacote-fonte. O `LAYOUT-PRISM-002` é um modelo de apoio e não substitui silenciosamente o template V4 do pacote.

## Source-boundary rule
HTMLs fornecidos como exemplos são convertidos para modelos parametrizados. Datas, tarefas, temas, métricas, progresso, destinatários, trilhas, marcos e conteúdo específico devem ser substituídos por placeholders antes de registro como template reutilizável.
