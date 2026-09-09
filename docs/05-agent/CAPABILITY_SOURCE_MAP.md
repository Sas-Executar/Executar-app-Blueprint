---
id: AGENT-CAPABILITY-SOURCES-001
type: capability_source_map
status: registered_reference
version: 1.0.0
owner: null
---

# Capability Source Map

Este documento registra somente o papel arquitetural dos pacotes fornecidos. Não copia os pacotes nem declara produção aprovada.

## Productivity reference package

Fonte fornecida: `productivity.zip`.

Capabilities observadas:
- bootstrap do sistema de produtividade;
- sincronização/triagem de tarefas;
- task management;
- memória/contexto;
- varredura ampliada de chat, email, calendário e documentos quando connectors estiverem disponíveis.

Uso no EXECUTAR:
`SYNC + USER CONTEXT + TASK DISCOVERY`.

Observação:
o comportamento original do pacote inclui interações/confirmations próprias; o EXECUTAR deverá aplicar sua própria authority policy e não herdar automaticamente mutações.

## Operations reference package

Fonte fornecida: `operations.zip`.

Capabilities observadas:
- status report;
- capacity plan;
- process documentation;
- process optimization;
- runbook;
- risk/change/compliance/vendor capabilities adicionais.

Uso no EXECUTAR:
`STRUCTURE + OPERATE + REPORT + REPLAN`.

## MCP Executar reference

Fonte fornecida: `PRD-MCP.md` + master index CSV.

O material fornecido descreve:
- catálogo de 157 tools canônicas;
- famílias `ENTENDER`, `ESTRUTURAR`, `EXECUTAR`, `EMITIR`;
- adapters para providers externos;
- gates de implementação e perguntas ainda abertas.

Uso no EXECUTAR:
`EXTERNAL AI / PLATFORM MANAGEMENT SURFACE`.

Boundary:
MCP não é fonte de verdade; chama capabilities/contracts do EXECUTAR.

## Registration semantics

`registered_reference` significa que o pacote/documento foi usado para mapear capabilities. Não significa importado, implementado, aprovado, testado, verificado ou released.
