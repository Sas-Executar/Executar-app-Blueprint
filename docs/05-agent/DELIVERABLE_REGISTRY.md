---
id: AGENT-DELIV-REGISTRY-001
type: deliverable_registry
status: registered
version: 1.0.0
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
| DELIV-SUP-001 | Supporting model | Plano da Semana · Prisma A4 · `LAYOUT-PRISM-002` | `deliverables/templates/plano-semana-prisma-a4.template.html` | Modelo fornecido; não declarado canônico pelo `SKILL.md` |
| DELIV-SUP-002 | Supporting model | Processo de trabalho + formulário de ciclo + semana | `deliverables/templates/processo-trabalho-formulario-semana.template.html` | Modelo fornecido; associação a skill ainda não determinada |

## Placeholder rule

Todo conteúdo variável dos modelos reutilizáveis usa `{{UPPER_SNAKE_CASE}}`. Exemplos preenchidos não podem se tornar defaults de template.

## Canonicality rule

O `prisma_7d` do `executar-mapa-os` continua subordinado ao contrato V4 declarado no pacote-fonte. O `LAYOUT-PRISM-002` é um modelo de apoio e não substitui silenciosamente o template V4 do pacote.

## Source-boundary rule

Os dois HTMLs fornecidos foram convertidos de exemplos preenchidos para modelos parametrizados. Datas, tarefas, temas, métricas, progresso, trilhas, marcos e conteúdo editorial foram removidos como valores concretos e substituídos por placeholders.
