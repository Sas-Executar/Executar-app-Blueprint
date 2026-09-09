---
id: DELIV-STATUS-ROUTINE-CHANNELS-001
type: deliverable_template
status: registered
version: 1.0.0
owner: null
placeholder_policy: UPPER_SNAKE_CASE
---
# Status Report · variantes por canal

## APP_REPORTS

### {{REPORT_TITLE}}
- Run: `{{RUN_ID}}`
- Rotina: `{{ROUTINE_NAME}}`
- Data: `{{REPORT_DATETIME}}`
- Status: `{{RUN_STATUS}}`
- Progresso: `{{PROJECT_PROGRESS_PERCENT}}%`
- Agora: `{{NOW_ACTION_ID}} — {{NOW_ACTION_TITLE}}`
- Conclui quando: `{{NOW_COMPLETION_CRITERION}}`
- Evidência: `{{NOW_EVIDENCE_REQUIRED}}`
- Bloqueio principal: `{{PRIMARY_BLOCKER}}`
- Próxima: `{{NEXT_1}}`
- Report ID: `{{REPORT_ID}}`

## EMAIL · fallback plain text

EXECUTAR · {{REPORT_TITLE}}
Data: {{REPORT_DATETIME}}
Status: {{RUN_STATUS}}
Progresso: {{PROJECT_PROGRESS_PERCENT}}%
Ciclo: {{CYCLE_CURRENT}}
Hoje: {{TODAY_DELTA}}

ANTERIOR
{{PREVIOUS_TITLE}} · {{PREVIOUS_STATE}}

ATUAL
{{CURRENT_TITLE}} · {{CURRENT_STATE}}

PRÓXIMO
{{NEXT_TITLE}} · {{NEXT_STATE}}

AGORA
{{NOW_ACTION_ID}} · {{NOW_ACTION_TITLE}}
{{NOW_META}}
Conclui quando: {{NOW_COMPLETION_CRITERION}}
Evidência: {{NOW_EVIDENCE_REQUIRED}}

Contexto: {{CONTEXT}}
Problema: {{PROBLEM}}
Processo: {{PROCESS}}
Progresso: {{PROGRESS_TEXT}}
Risco: {{RISK}}
Prevenção: {{PREVENTION}}
Entrega: {{DELIVERY_RESULT}}
Lacunas: {{GAPS_AND_BLOCKERS}}

Report: {{REPORT_URL}}

## WHATSAPP · resumo compacto

EXECUTAR · {{REPORT_TITLE}}
{{PROJECT_PROGRESS_PERCENT}}% · {{RUN_STATUS}}

AGORA: {{NOW_ACTION_TITLE}}
ID: {{NOW_ACTION_ID}}
Conclui quando: {{NOW_COMPLETION_CRITERION}}
Bloqueio: {{PRIMARY_BLOCKER}}
Próxima: {{NEXT_1}}

Report: {{REPORT_URL}}

## Regras
- Não incluir destinatário real no template.
- Não incluir telefone/e-mail como default.
- O WhatsApp usa versão curta; o histórico completo permanece em App Reports.
- Email usa o HTML `status-report-routine.template.html` e este bloco apenas como fallback.
- Toda entrega externa deve registrar `{{PROVIDER_MESSAGE_ID}}` ou `{{DELIVERY_ERROR}}`.
