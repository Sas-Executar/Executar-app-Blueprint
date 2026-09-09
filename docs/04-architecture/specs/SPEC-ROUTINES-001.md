---
id: SPEC-ROUTINES-001
type: technical_specification
status: draft
version: 0.9.0
owner: null
project: EXECUTAR
date: 2026-09-09
depends_on:
  - ADR-ROUTINES-001
  - PRD-ROUTINES-001
---
# SPEC-ROUTINES-001 — Runtime de Rotinas, Autogestão e Status Reports

## 1. Componentes

```text
RoutineConfigurator
RoutineStore
RoutineScheduler
RoutineRunner
SourceAdapter[]
StateReconciler
EligibilityEngine
AuthorityGate
TaskMutationExecutor
StatusReportBuilder
ReportRepository
DeliveryRouter
  ├─ AppReportsAdapter
  ├─ EmailAdapter
  └─ WhatsAppAdapter
AuditLog
```

## 2. RoutineConfig

```json
{
  "routine_id": "{{ROUTINE_ID}}",
  "name": "{{ROUTINE_NAME}}",
  "description": "{{ROUTINE_DESCRIPTION}}",
  "status": "enabled",
  "scope": {
    "project_id": "{{PROJECT_ID}}",
    "filters": ["{{SCOPE_FILTER}}"]
  },
  "trigger": {
    "type": "schedule",
    "schedule": "{{SCHEDULE_EXPRESSION}}",
    "timezone": "{{TIMEZONE}}"
  },
  "sources": [
    {
      "source_id": "{{SOURCE_ID}}",
      "provider": "{{SOURCE_PROVIDER}}",
      "role": "state_authority|definition_authority|mirror|evidence",
      "required": true
    }
  ],
  "execution_policy": {
    "wip_limit": 1,
    "eligibility_policy": "dependencies_first",
    "tie_policy": "human_escalation",
    "allowed_mutations": ["sync_mirror", "promote_ready"],
    "blocked_mutations": ["start", "verify", "complete", "publish"]
  },
  "report": {
    "template_id": "DELIV-STATUS-ROUTINE-001",
    "schema": "EXECUTAR_ROUTINE_STATUS_V1"
  },
  "delivery": [
    {"channel": "app_reports", "enabled": true},
    {"channel": "email", "enabled": "{{EMAIL_ENABLED}}", "recipient_ref": "{{EMAIL_RECIPIENT_REF}}"},
    {"channel": "whatsapp", "enabled": "{{WHATSAPP_ENABLED}}", "recipient_ref": "{{WHATSAPP_RECIPIENT_REF}}"}
  ],
  "retry": {
    "max_attempts": "{{MAX_ATTEMPTS}}",
    "backoff": "{{BACKOFF_POLICY}}"
  }
}
```

## 3. RoutineRun

```json
{
  "run_id": "{{RUN_ID}}",
  "routine_id": "{{ROUTINE_ID}}",
  "triggered_at": "{{TRIGGERED_AT}}",
  "started_at": "{{STARTED_AT}}",
  "finished_at": "{{FINISHED_AT}}",
  "status": "success|partial|blocked|failed",
  "source_snapshot_refs": ["{{SOURCE_SNAPSHOT_REF}}"],
  "mutations": [
    {
      "object_id": "{{OBJECT_ID}}",
      "from": "{{FROM_STATE}}",
      "to": "{{TO_STATE}}",
      "authority_rule_id": "{{AUTHORITY_RULE_ID}}",
      "evidence_refs": ["{{EVIDENCE_REF}}"]
    }
  ],
  "report_id": "{{REPORT_ID}}",
  "block_reason": "{{BLOCK_REASON_OR_NULL}}"
}
```

## 4. StatusReport

```json
{
  "report_id": "{{REPORT_ID}}",
  "run_id": "{{RUN_ID}}",
  "project_id": "{{PROJECT_ID}}",
  "generated_at": "{{GENERATED_AT}}",
  "status": "{{REPORT_STATUS}}",
  "progress": {
    "project_percent": "{{PROJECT_PROGRESS_PERCENT}}",
    "cycle_current": "{{CYCLE_CURRENT}}",
    "today_delta": "{{TODAY_DELTA}}"
  },
  "triptych": {
    "previous": {"title": "{{PREVIOUS_TITLE}}", "state": "{{PREVIOUS_STATE}}"},
    "current": {"title": "{{CURRENT_TITLE}}", "state": "{{CURRENT_STATE}}"},
    "next": {"title": "{{NEXT_TITLE}}", "state": "{{NEXT_STATE}}"}
  },
  "now": {
    "action_id": "{{NOW_ACTION_ID}}",
    "title": "{{NOW_ACTION_TITLE}}",
    "duration": "{{NOW_DURATION}}",
    "completion_criterion": "{{NOW_COMPLETION_CRITERION}}",
    "evidence_required": "{{NOW_EVIDENCE_REQUIRED}}"
  },
  "properties": {
    "context": "{{CONTEXT}}",
    "problem": "{{PROBLEM}}",
    "process": "{{PROCESS}}",
    "progress": "{{PROGRESS_TEXT}}",
    "next_1": "{{NEXT_1}}",
    "next_2": "{{NEXT_2}}",
    "next_3": "{{NEXT_3}}",
    "risk": "{{RISK}}",
    "prevention": "{{PREVENTION}}",
    "delivery": "{{DELIVERY_RESULT}}"
  },
  "evidence_refs": ["{{EVIDENCE_REF}}"],
  "gaps": ["{{GAP}}"]
}
```

## 5. Pipeline de execução
1. carregar `RoutineConfig` ativo;
2. gerar `run_id` idempotency key;
3. adquirir lock por `routine_id + scheduled_slot`;
4. ler todas as fontes obrigatórias;
5. se leitura obrigatória falhar, registrar `BLOCKED` e pular mutações;
6. normalizar estados;
7. reconciliar autoridade → espelhos;
8. calcular progresso derivado;
9. validar dependências e gates;
10. calcular conjunto elegível;
11. aplicar WIP;
12. selecionar próxima ação ou `EXIGE_HUMANO`;
13. passar cada mutação pelo `AuthorityGate`;
14. executar mutações permitidas com idempotency key;
15. gerar `StatusReport` canônico;
16. persistir em `ReportRepository`;
17. adaptar e entregar por canal;
18. registrar receipts, retries e falhas;
19. fechar `RoutineRun`.

## 6. Algoritmo baseline de elegibilidade

```text
eligible(action) =
  required_dependencies_satisfied
  AND no_active_blocker
  AND required_gate_satisfied
  AND fits_authority
  AND fits_capacity_if_required

if eligible_actions.count == 1:
  next_action = eligible_actions[0]
elif eligible_actions.count > 1:
  apply declared precedence
  if unresolved: EXIGE_HUMANO
else:
  next_action = null
```

Precedência default do modo EXECUTAR, quando declarada pelo projeto:
1. dependências satisfeitas;
2. caminho crítico;
3. maior valor declarado;
4. prazo mais próximo;
5. similaridade com ação ativa;
6. empate restante → `EXIGE_HUMANO`.

## 7. AuthorityGate
Toda mutação recebe:
- `actor=agent:routine`;
- `routine_id`;
- `authority_rule_id`;
- estado anterior;
- estado proposto;
- dependências avaliadas;
- evidências utilizadas;
- decisão `ALLOW|BLOCK|HUMAN_REQUIRED`.

Baseline:
- `sync_mirror`: ALLOW;
- `BACKLOG_VALIDATED→READY`: ALLOW quando determinístico;
- `→DOING`: HUMAN_REQUIRED;
- `→VERIFY`: HUMAN_REQUIRED;
- `→DONE`: HUMAN_REQUIRED;
- `→TESTED/VERIFIED/PUBLISHED`: HUMAN_REQUIRED.

## 8. Delivery Router
### app_reports
- persiste report completo;
- URL/route: `{{REPORT_ROUTE_PATTERN}}`;
- status é confirmado após persistência.

### email
Input:
```json
{
  "to_ref": "{{EMAIL_RECIPIENT_REF}}",
  "subject": "{{EMAIL_SUBJECT}}",
  "html": "{{RENDERED_HTML}}",
  "text": "{{PLAIN_TEXT_FALLBACK}}"
}
```
Output:
```json
{"status":"sent|failed","provider_message_id":"{{MESSAGE_ID}}","error":"{{ERROR_OR_NULL}}"}
```

### whatsapp
Input:
```json
{
  "recipient_ref": "{{WHATSAPP_RECIPIENT_REF}}",
  "text": "{{WHATSAPP_SUMMARY}}",
  "report_url": "{{REPORT_URL}}"
}
```
Output:
```json
{"status":"sent|failed","provider_message_id":"{{MESSAGE_ID}}","error":"{{ERROR_OR_NULL}}"}
```

## 9. Idempotência
- `run_key = routine_id + scheduled_slot`;
- `mutation_key = run_id + object_id + target_state`;
- `delivery_key = report_id + channel + recipient_ref`;
- retries não podem gerar mutação ou envio duplicado quando o provider oferecer idempotency key/receipt verificável.

## 10. Segurança e privacidade
- referências de destinatário apontam para storage seguro; templates não contêm e-mail ou telefone reais;
- secrets nunca entram em RoutineConfig serializado para UI/log;
- dados sensíveis devem ser minimizados por canal;
- WhatsApp recebe por padrão versão curta; o report completo permanece no app;
- cada rotina usa somente conectores explicitamente autorizados.

## 11. Observabilidade
Eventos mínimos:
- `routine.triggered`;
- `routine.source_read`;
- `routine.blocked`;
- `routine.state_reconciled`;
- `routine.mutation_allowed|blocked`;
- `routine.report_created`;
- `routine.delivery_attempted|sent|failed`;
- `routine.completed`.

## 12. Testes obrigatórios
- source obrigatório indisponível;
- zero, uma e múltiplas ações elegíveis;
- empate sem desempate;
- dependência bloqueada;
- tentativa de promoção para DONE;
- retry sem duplicidade;
- falha de email com app report preservado;
- falha de WhatsApp com app report preservado;
- placeholders residuais no template;
- recipient refs ausentes;
- execução duplicada do mesmo scheduled slot.
