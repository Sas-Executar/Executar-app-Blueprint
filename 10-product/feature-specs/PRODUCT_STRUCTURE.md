# PRODUCT_STRUCTURE

Status: `PARTIAL_SPECIFIED`
Authority: estrutura funcional e mapa de módulos do EXECUTAR
Sources: manifesto + blueprint + referência funcional atual

## 1. Estrutura do trabalho

Autoridade de entidades detalhadas: `20-DOMAIN/entities/CORE_ENTITY_MODEL.md`.

Estrutura canônica:

`Project → ValueStream → Deliverable → Task → Action → Evidence`

## 2. Core Engine

```text
ENTENDER
  ↓
ESTRUTURAR
  ↓
PLANEJAR CAPACIDADE
  ↓
ELIGIBILITY
  ↓
DISPATCH / BEST NEXT ACTION
  ↓
EXECUTAR (WIP 1:1)
  ↓
EVIDENCIAR
  ↓
EMITIR
  ↓
LEARN / REPLAN
```

## 3. Módulos funcionais

| Módulo | Responsabilidade | Capabilities |
|---|---|---|
| `Context` | manter objetivo, restrições, estado, bloqueios e histórico suficiente para continuidade | CAP-EXEC-001, 009 |
| `Structure` | decompor e organizar trabalho | CAP-EXEC-002 |
| `Planning` | capacidade, ciclos, dependências, caminho/ordem | CAP-EXEC-003, 004, 008 |
| `Execution` | Best Next Action, FOCUS, WIP 1:1, conclusão | CAP-EXEC-005, 006 |
| `Evidence` | comprovação, histórico e insumo de governança | CAP-EXEC-007 |
| `Mapa-OS` | projeção visual do estado operacional | CAP-EXEC-010 |
| `Scanner` | ponte símbolo/ação física → comando digital | CAP-EXEC-011 |
| `Copilot` | orquestração assistida por IA sobre estado real | CAP-EXEC-012 |
| `Reporting` | Status Report e outputs derivados | CAP-EXEC-013 |
| `Routines` | automações e workflows operacionais | CAP-EXEC-014 |
| `Omnichannel State` | manter coerência entre superfícies | CAP-EXEC-015 |

## 4. Superfícies

- App/Web: visão e operação digital principal.
- Mobile: execução e captura móvel quando disponível.
- Mapa-OS: superfície física/visual de execução.
- Scanner: entrada física por símbolo.
- Copiloto: superfície conversacional/agentic.
- integrações futuras: Calendar, Email, WhatsApp, MCP e outras, sem criar estado paralelo.

## 5. Views funcionais já preservadas pelo produto atual

A referência funcional vigente preserva:

- Visão Geral;
- Foco com Próximo 1 por vez;
- fila apenas do que pode começar;
- “Ainda não pode” para dependências bloqueantes;
- calendário de resultados/ciclos de 72h;
- caminho visual de dependências;
- evidências.

Detalhes de rota/layout/copy pertencem ao WF-04 Pages/Copy/Assets.

## 6. Boundaries

Este documento define **o que o produto faz**, não como o next-forge implementa. Auth, storage, database provider, payments, observability e outros fundamentos técnicos continuam fora desta autoridade e serão apenas mapeados em `95-INTEGRATION/`.