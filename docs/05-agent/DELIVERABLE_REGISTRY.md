---
id: AGENT-DELIV-REGISTRY-001
type: deliverable_registry
status: registered
version: 1.4.0
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
| DELIV-MAPA-007 | executar-mapa-os + Scanner | Mapa-OS Prisma One Page | `deliverables/placeholders/mapa-os-prisma-onepage.placeholder.html` | Entrega permanente do pacote; placeholder normalizado do arquivo fornecido pelo usuário |
| DELIV-COP-001 | copiloto-executar | `/bomdia` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-002 | copiloto-executar | `/agora` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-003 | copiloto-executar | `/estado` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-004 | copiloto-executar | `/fechardia` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-005 | copiloto-executar | `/replanejamento` | `deliverables/templates/copiloto-command-outputs.template.md` | Comando declarado |
| DELIV-COP-006 | copiloto-executar | Saída estruturada do orquestrador | `deliverables/templates/copiloto-orchestrator-output.template.json` | Derivado do schema da skill |
| DELIV-ONB-001 | Copiloto / Omnichannel Flow | Onboarding operacional: Copiloto + Mapa-OS + Scanner | `deliverables/templates/onboarding-copilot-scanner.template.md` | Derivado de `PROD-FLOW-001` / `PRD-OMNI-001`; conteúdo variável por placeholders |
| DELIV-ROUT-001 | Modo Rotinas / copiloto-executar | Status Report canônico HTML | `deliverables/templates/status-report-routine.template.html` | ADR/PRD/SPEC de Rotinas |
| DELIV-ROUT-002 | Modo Rotinas / canais | Variantes App Reports / Email / WhatsApp | `deliverables/templates/status-report-routine-channel-variants.template.md` | Projeções do mesmo report canônico |
| DELIV-ROUT-003 | Modo Rotinas / copiloto-executar | Status Report A4 diário | `deliverables/placeholders/status-report-a4-daily.placeholder.html` | Saída diária do Modo Rotinas via agente Copiloto; placeholder normalizado do arquivo fornecido pelo usuário |
| DELIV-STATUS-001 | Copiloto / pacote EXECUTAR | Status Report Obsidian / Terminal | `deliverables/placeholders/executar-status-report-obsidian-terminal.placeholder.html` | Entrega permanente do pacote; placeholder normalizado do arquivo fornecido pelo usuário |
| DELIV-SUP-001 | Supporting model | Plano da Semana · Prisma A4 · `LAYOUT-PRISM-002` | `deliverables/templates/plano-semana-prisma-a4.template.html` | Modelo de apoio |
| DELIV-SUP-002 | Supporting model | Processo de trabalho + formulário de ciclo + semana | `deliverables/templates/processo-trabalho-formulario-semana.template.html` | Modelo de apoio |

## Default agent deliverables
O bundle padrão passa a distinguir cadência de emissão:
- `DELIV-MAPA-007` e `DELIV-STATUS-001` são entregas permanentes: devem acompanhar sempre a entrega do pacote EXECUTAR correspondente.
- `DELIV-ROUT-003` é a saída diária do Modo Rotinas, emitida pelo agente Copiloto.
- `DELIV-ONB-001`, `DELIV-ROUT-001/002`, `DELIV-MAPA-001..006` e modelos de apoio permanecem registrados e não são apagados ou substituídos silenciosamente.

## Mapa-OS rule
O Mapa-OS físico é uma projeção do estado digital canônico gerada pelo agente para gestão analógica das tarefas. Impressão, calendário ou símbolos não criam estado paralelo. `DELIV-MAPA-007` é a apresentação One Page registrada para entrega permanente e pode integrar os símbolos do Scanner sem transferir ao papel a autoridade de estado.

## Scanner rule
Os símbolos físicos podem integrar o Mapa-OS, porém `visual recognition`, `command dispatch` e mutações são responsabilidade da feature Scanner e de seus contratos próprios.

## Placeholder rule
Todo conteúdo variável dos modelos reutilizáveis usa `{{UPPER_SNAKE_CASE}}`. Exemplos preenchidos não podem se tornar defaults de template. A proveniência dos três placeholders fornecidos em 2026-09-12 está registrada em `deliverables/placeholders/SOURCE_MANIFEST.md`.

## Routine delivery rule
`DELIV-ROUT-003` é o Status Report A4 diário efetivamente designado para emissão pelo Modo Rotinas via agente Copiloto. `DELIV-ROUT-001` e `DELIV-ROUT-002` permanecem como contratos/modelos canônicos anteriores de report e canais até decisão explícita de substituição. Falha em Email ou WhatsApp não altera estado de tarefa.

## Always-delivered rule
`DELIV-MAPA-007` e `DELIV-STATUS-001` são entregáveis obrigatórios do bundle padrão. A regra "sempre entregue" descreve política documental/produto; não deve ser usada para declarar envio, teste ou release sem evidência de runtime.

## Canonicality rule
O `prisma_7d` do `executar-mapa-os` permanece subordinado ao contrato V4 e ao índice interno da própria skill.
