---
id: DELIV-ONB-001
type: deliverable_template
status: registered
version: 1.0.0
placeholder_policy: UPPER_SNAKE_CASE
---

# {{PRODUCT_NAME}} · Onboarding Operacional

## 1. Seu sistema
- Usuário: {{USER_NAME_OR_ROLE}}
- Contexto: {{USER_CONTEXT}}
- Projetos ativos: {{ACTIVE_PROJECTS_SUMMARY}}
- Canal principal: {{PRIMARY_CHANNEL}}
- Canal alternativo: {{SECONDARY_CHANNELS}}

## 2. Como o fluxo funciona

```mermaid
flowchart TD
  A[{{SYNC_SOURCES}}] --> B[Copiloto]
  B --> C[{{PLAN_OR_REPLAN}}]
  C --> D[{{DELIVERABLES_PREVIEW}}]
  D --> E[Pré-aprovação]
  E --> F[{{DECOMPOSED_EXECUTION}}]
  F --> G[{{CANONICAL_STATE}}]
  G --> H[{{PRIMARY_EXECUTION_SURFACE}}]
```

## 3. Comandos do Copiloto

| Comando | Para que serve | Resultado |
|---|---|---|
| `{{COMMAND_01}}` | {{COMMAND_01_PURPOSE}} | {{COMMAND_01_OUTPUT}} |
| `{{COMMAND_02}}` | {{COMMAND_02_PURPOSE}} | {{COMMAND_02_OUTPUT}} |
| `{{COMMAND_03}}` | {{COMMAND_03_PURPOSE}} | {{COMMAND_03_OUTPUT}} |
| `{{COMMAND_04}}` | {{COMMAND_04_PURPOSE}} | {{COMMAND_04_OUTPUT}} |
| `{{COMMAND_05}}` | {{COMMAND_05_PURPOSE}} | {{COMMAND_05_OUTPUT}} |

## 4. Como usar o Mapa-OS

1. Gere/receba `{{MAPA_OS_ARTIFACT}}`.
2. Imprima em `{{PRINT_FORMAT}}`.
3. Consulte `{{MAPA_OS_SECTIONS}}`.
4. Execute `{{NEXT_ACTION_RULE}}`.
5. Use o Scanner para registrar ações suportadas.

## 5. Como usar o Scanner

Símbolos configurados:

| Símbolo | ID | Ação | Confirmação |
|---|---|---|---|
| {{SYMBOL_01_LABEL}} | {{SYMBOL_01_ID}} | {{SYMBOL_01_ACTION}} | {{SYMBOL_01_CONFIRMATION}} |
| {{SYMBOL_02_LABEL}} | {{SYMBOL_02_ID}} | {{SYMBOL_02_ACTION}} | {{SYMBOL_02_CONFIRMATION}} |
| {{SYMBOL_03_LABEL}} | {{SYMBOL_03_ID}} | {{SYMBOL_03_ACTION}} | {{SYMBOL_03_CONFIRMATION}} |

Fluxo:
`imagem → reconhecimento → VisualSymbolId → CommandDispatcher → ação → feedback → {{UNDO_POLICY}}`

## 6. Onde acompanhar

- Overview: {{OVERVIEW_PATH}}
- Agora: {{NOW_PATH}}
- Reports: {{REPORTS_PATH}}
- Mapa-OS: {{MAPA_OS_PATH}}
- Scanner: {{SCANNER_PATH}}
- Automações: {{AUTOMATIONS_PATH}}

## 7. Gestão sem abrir o app

Canais habilitados:
- App: {{APP_ENABLED}}
- MCP: {{MCP_ENABLED}}
- WhatsApp: {{WHATSAPP_ENABLED}}
- Email: {{EMAIL_ENABLED}}
- Copiloto: {{COPILOT_ENABLED}}
- Mapa-OS + Scanner: {{MAPA_SCANNER_ENABLED}}

Regra: {{OMNICHANNEL_CANONICAL_STATE_RULE}}

## 8. Próxima ação

{{ONBOARDING_NEXT_ACTION}}
