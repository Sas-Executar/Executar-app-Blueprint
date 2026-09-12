# Placeholder Source Manifest

Registro de proveniência dos três arquivos fornecidos pelo usuário em 2026-09-12 e normalizados como placeholders reutilizáveis.

| Source upload | SHA-256 | Papel registrado | Placeholder derivado |
|---|---|---|---|
| `status-report-a4.html` | `2022e3aa58fa5c3dc30b896d30e103b12bccc2e03b9d149b7214483ba2b9fce8` | Status Report A4 diário emitido pelo Modo Rotinas via agente Copiloto | `status-report-a4-daily.placeholder.html` |
| `templated.html` | `739f5cb22349ab127a2738e9a15b047987b29d5d4fbdb7f567258b4d39ecd168` | Mapa-OS Prisma One Page; entrega permanente do pacote | `mapa-os-prisma-onepage.placeholder.html` |
| `executar_status_report_obsidian_terminal(1).html` | `96f381f87fe2a1037f7b0fa139db83cb96caa19be09b497a2700e5dd7b8bbe34` | Status Report Obsidian/Terminal; entrega permanente do pacote | `executar-status-report-obsidian-terminal.placeholder.html` |

## Normalization rule

Os arquivos de origem continham dados exemplificativos. Na normalização, o layout e a função foram preservados e dados variáveis foram convertidos para placeholders no padrão `{{UPPER_SNAKE_CASE}}`. O Mapa-OS mantém a composição macOS/Apple-like, três faces A4, onboarding, calendário semanal, símbolos do Scanner e workflow; imagens inline foram convertidas para placeholders de asset (`{{ICON_*_SRC}}`) para evitar fixar conteúdo visual codificado como dado de exemplo.

## Delivery policy

- `status-report-a4-daily.placeholder.html`: emitido diariamente pelo Modo Rotinas através do agente Copiloto.
- `mapa-os-prisma-onepage.placeholder.html`: entregue sempre.
- `executar-status-report-obsidian-terminal.placeholder.html`: entregue sempre.

Este registro documenta templates e política de entrega; não implica implementação, envio efetivo, teste ou release do runtime.
