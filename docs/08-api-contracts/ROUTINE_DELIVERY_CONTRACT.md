---
id: API-ROUTINE-DELIVERY-001
type: delivery_contract
status: draft
version: 0.9.0
owner: null
project: EXECUTAR
---
# Routine Report Delivery Contract

## Objetivo
Padronizar entrega do mesmo `StatusReport` canônico em App Reports, Email e WhatsApp sem permitir que canais criem estados de projeto concorrentes.

## Entrada comum
```json
{
  "delivery_id": "{{DELIVERY_ID}}",
  "report_id": "{{REPORT_ID}}",
  "run_id": "{{RUN_ID}}",
  "channel": "app_reports|email|whatsapp",
  "recipient_ref": "{{RECIPIENT_REF_OR_NULL}}",
  "idempotency_key": "{{IDEMPOTENCY_KEY}}",
  "payload_ref": "{{PAYLOAD_REF}}"
}
```

## Saída comum
```json
{
  "delivery_id": "{{DELIVERY_ID}}",
  "status": "sent|delivered|failed|skipped",
  "provider_message_id": "{{PROVIDER_MESSAGE_ID_OR_NULL}}",
  "delivered_at": "{{DELIVERED_AT_OR_NULL}}",
  "error_code": "{{ERROR_CODE_OR_NULL}}",
  "error_message": "{{ERROR_MESSAGE_OR_NULL}}"
}
```

## App Reports
- `recipient_ref` não é obrigatório;
- payload completo é persistido;
- retorno inclui `{{REPORT_URL}}`/resource ref;
- persistência do report ocorre antes dos canais externos.

## Email
- `recipient_ref` resolve endereço em storage seguro;
- payload inclui `subject`, HTML self-contained e fallback texto;
- template não armazena endereço real;
- `sent` exige sucesso do provider e message id quando fornecido.

## WhatsApp
- `recipient_ref` resolve telefone/contact handle em storage seguro;
- payload padrão é resumo compacto + `report_url`;
- anexos/templates de provider são extensões posteriores;
- template não armazena telefone real;
- `sent` exige receipt/message id quando suportado.

## Retry e idempotência
Retry é permitido somente para falha de canal. Não pode:
- refazer mutações da rotina;
- gerar novo report;
- duplicar mensagem já confirmada pelo provider.

## Segurança
- nenhum secret no payload de domínio;
- destinatários devem estar previamente autorizados na rotina;
- minimizar conteúdo sensível por canal;
- logs armazenam refs/receipts, não credenciais.
