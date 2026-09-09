<!-- SOURCE: mapa-operacional.template.md -->
---
id: DELIV-MAPA-001
type: deliverable_template
skill: executar-mapa-os
projection: mapa_operacional
status: template
---
# {{PROJECT_NAME}} · Mapa-OS

## Posição
- Projeto: {{PROJECT_ID}} — {{PROJECT_NAME}}
- Estado: {{CURRENT_STATE}}
- Progresso: {{PROGRESS_VALUE}}
- Entrega ativa: {{ACTIVE_DELIVERY_ID}} — {{ACTIVE_DELIVERY_TITLE}}
- Fluxo ativo: {{ACTIVE_WORKFLOW_ID}} — {{ACTIVE_WORKFLOW_TITLE}}

## Agora
- Ação: {{NOW_ACTION_ID}} — {{NOW_ACTION_TITLE}}
- Conclui quando: {{NOW_DOD}}
- Evidência esperada: {{NOW_EVIDENCE}}
- Bloqueios: {{NOW_BLOCKERS}}

## Próximo
{{NEXT_ITEMS}}

## Depois
{{LATER_ITEMS}}

## 3P+N
- Problema: {{PROBLEM}}
- Processo: {{PROCESS}}
- Progresso: {{PROGRESS_SUMMARY}}
- Next: {{NEXT_ACTION}}

## Validação
- Fonte canônica: {{CANONICAL_SOURCE}}
- Estado da validação: {{VALIDATION_STATUS}}
- Lacunas/conflitos: {{ISSUES}}

---

<!-- SOURCE: agora-proximo-depois.template.md -->
---
id: DELIV-MAPA-002
type: deliverable_template
skill: executar-mapa-os
projection: agora_proximo_depois
status: template
---
# {{PROJECT_NAME}} · Agora / Próximo / Depois

## AGORA · WIP=1
- {{NOW_ID}} — {{NOW_TITLE}}
- Estado: {{NOW_STATE}}
- Prazo original: {{NOW_ORIGINAL_DEADLINE}}
- Previsão atual: {{NOW_FORECAST}}
- DoD: {{NOW_DOD}}
- Evidência: {{NOW_EVIDENCE}}
- Bloqueio: {{NOW_BLOCKER}}

## PRÓXIMO
{{NEXT_ITEMS}}

## DEPOIS
{{LATER_ITEMS}}

## Fonte e validação
- Fonte: {{CANONICAL_SOURCE}}
- Validação: {{VALIDATION_STATUS}}

---

<!-- SOURCE: status-terminal.template.md -->
---
id: DELIV-MAPA-003
type: deliverable_template
skill: executar-mapa-os
projection: status_terminal
status: template
---
# {{PROJECT_ID}} · {{PROJECT_NAME}}
`{{PROGRESS_PCT}} · {{SPRINT_OR_CYCLE}} · {{GATE}}`

AGORA: {{NOW_ID}} — {{NOW_ACTION}}
POSIÇÃO: {{CURRENT_POSITION}}
PROGRESSO: {{PROGRESS_NUMERATOR}}/{{PROGRESS_DENOMINATOR}} = {{PROGRESS_PCT}}
RISCO: {{PRIMARY_RISK}}
PREVENÇÃO: {{PREVENTION}}
EVIDÊNCIA: {{EVIDENCE_SUMMARY}}
PRÓXIMA: {{NEXT_ACTION}}
TAGS: {{TAG_01}} · {{TAG_02}} · {{TAG_03}}
