---
id: PRD-SCANNER-001
type: product_requirements_document
status: registered_from_source
source_status: approved-for-implementation
version: 1.0.0
owner: null
project: EXECUTAR
feature: visual-symbol-scanner
source: PRD SCANNER - EXECUTAR APP.md
---
# Visual Symbol Scanner

## Product intent
Substituir o Scanner físico baseado em QR/OCR por reconhecimento visual on-device de símbolos, transformando a aparência gráfica do símbolo em identidade operacional.

Experiência alvo:

`ver símbolo → identificar símbolo → executar comando`

Sem QR, OCR, payload visual ou confirmação intermediária no fluxo principal descrito pela fonte.

## Relationship to Mapa-OS
O Mapa-OS é o entregável analógico/imprimível gerado pelo agente para gestão das tarefas. O Scanner é uma feature separada que lê símbolos físicos presentes nessa superfície ou em outros suportes e encaminha um comando ao aplicativo.

`Mapa-OS físico → símbolo → Scanner → VisualSymbolId → CommandDispatcher → ação EXECUTAR`

## V1 physical vocabulary
| Symbol ID | Semantic ID | Command |
|---|---|---|
| `SYM-CHAT-001` | `chat` | `OPEN_CHAT` |
| `SYM-SELECTOR-001` | `selector` | `OPEN_SELECTOR` |
| `SYM-DONE-001` | `done` | `COMPLETE_LATEST_OPEN_TASK` |

## In scope
- reconhecimento visual de símbolos;
- inferência local;
- Chat;
- Seletor;
- Feito;
- Undo de Feito;
- configuração visual dos símbolos;
- configuração das opções do Seletor;
- remoção de QR/OCR do Scanner físico.

## Out of scope V1
- QR como fallback;
- OCR como fallback;
- Entrada;
- Saída;
- QR Jump;
- identificação física individual de tarefas;
- confirmação antes de executar um símbolo;
- aprovação humana anterior à ação.

## Core requirements
### REQ-SCAN-001 · Visual recognition
O Scanner MUST reconhecer símbolos por aparência visual dentro de uma ROI perceptível ao usuário.

### REQ-SCAN-002 · Offline
Inferência e matching MUST funcionar sem rede após instalação.

### REQ-SCAN-003 · Registry
O produto MUST manter registry local de símbolos e embeddings.

### REQ-SCAN-004 · Enrollment
O usuário MAY substituir/cadastrar referência visual sem retreinar ou alterar os pesos do encoder.

### REQ-SCAN-005 · Event semantics
Uma aparição física válida MUST gerar no máximo um comando até que o símbolo saia da ROI e seja rearmado.

### REQ-SCAN-006 · Unknown
Visual desconhecido MUST resultar em `UNKNOWN`; nearest-neighbor não autoriza comando sem limiar de rejeição.

### REQ-SCAN-007 · Chat
`SYM-CHAT-001` → `OPEN_CHAT` → superfície Messages/Copiloto.

### REQ-SCAN-008 · Selector
`SYM-SELECTOR-001` → `OPEN_SELECTOR` → superfície configurável do Seletor.

### REQ-SCAN-009 · Done
`SYM-DONE-001` → `COMPLETE_LATEST_OPEN_TASK`; quando houver mutação bem-sucedida, persistir `mutationId`, `taskId`, `previousState`, `newState` e permitir Undo.

### REQ-SCAN-010 · No open task
Se nenhuma tarefa aberta puder ser resolvida, retornar `NO_OPEN_TASK` e não modificar tarefa alguma.

## Non-functional requirements
- reconhecimento on-device;
- operação offline;
- separação entre câmera, preprocessing, encoder, matching, registry, event-latch, command-dispatcher, domain mutations e notification;
- meta de produto declarada na fonte: `scan-to-command p95 <= 500ms`; ainda não verificada.

## Acceptance criteria
- Chat entrando na ROI emite exatamente um `OPEN_CHAT`.
- Selector entrando na ROI emite exatamente um `OPEN_SELECTOR`.
- Done com tarefa aberta muda exatamente uma tarefa e cria mutação reversível.
- Done mantido continuamente visível não completa tarefas adicionais.
- Visual não registrado gera `UNKNOWN` e nenhuma ação.
- Reconhecimento continua funcionando offline após instalação.
- Enrollment troca referência visual sem alterar pesos do modelo.

## Epistemic note
Este documento registra requisitos do arquivo-fonte. `registered_from_source` não significa implementação, teste ou verificação no repositório Blueprint.
