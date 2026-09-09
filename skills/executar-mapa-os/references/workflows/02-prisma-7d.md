---
id: WF-MAPA-002
type: skill_workflow
status: registered
version: 1.1.0
skill: executar-mapa-os
---
# Workflow · Prisma 7d

## Activation
- `01`
- `Mapa 01`
- `/criar-mapa-semanal`
- linguagem natural equivalente

## Flow
1. Ler `references/prompts/01-prompt-mestre-prisma.md`.
2. Coletar apenas os dados indispensáveis ausentes.
3. Executar `WF-MAPA-001` para construir o objeto canônico.
4. Validar IDs, pais, dependências, estados, evidências e WIP=1.
5. Gerar payload conforme `schemas/prism-report.schema.json`.
6. Resolver os 100 placeholders canônicos do template.
7. Renderizar `assets/templates/status-report-prisma-a4-v4.html`.
8. Executar `scripts/validate_mapa.py`, `scripts/render_prism.py` e `scripts/audit_prism.py` quando disponíveis.
9. Entregar os quatro artefatos: objeto canônico JSON, payload Prisma JSON, HTML A4 e mapa de placeholders.

## Physical output
O HTML é uma superfície analógica/imprimível A4 de gestão de tarefas gerada pelo agente. A projeção não substitui o estado digital canônico.

## Geometry
- A4 retrato: 210 × 297 mm;
- três faces físicas de 99 mm;
- escala de impressão 100%;
- namespaces `DOC_*`, `EPIC_*`, `CALENDAR_*`, `RESULT_*`.
