---
id: HIG-AUDIT-CHAT-AGENT-001
type: ui_hig_compliance_report
status: BLOCKED
version: 0.1.0
owner: A DEFINIR
project: EXECUTAR
date: 2026-09-12
surface: Chat com Agente de IA
depends_on:
  - MST-XP-HIG-TP-001
  - D22-DEC-003
  - SPEC-CHAT-AGENT-001
  - UI-005
registry: docs/09-frontend/hig/APPLE_HIG_CONTRACT_REGISTRY_CHAT_AGENT.json
---
# HIG-AUDIT-CHAT-AGENT-001 — Chat com Agente de IA

## STATUS

`BLOCKED`

A revisão visual e documental foi executada, mas o workflow não pode atingir `VALIDATED` ou `DONE` porque faltam código, árvore de acessibilidade e testes de runtime para os MUST aplicáveis.

## SUMMARY

A superfície analisada é o wireframe do Chat com Agente de IA registrado em `D22-DEC-003` e detalhado por `SPEC-CHAT-AGENT-001`.

A composição observada é coerente com a intenção de baixa densidade e apresenta separação clara entre top utility bar, conversation surface, context suggestions e composer. A imagem também mostra controles afastados visualmente das regiões de sistema. Isso é evidência visual, não prova de Safe Area implementada.

O baseline de `11 alvos interativos` é uma `PROJECT_RULE` do EXECUTAR e não deve ser apresentado como valor HIG da Apple. O baseline de 44×44 pt no iOS permanece regra explícita do contrato `MST-XP-HIG-TP-001`; sua validação exige medida em pontos no runtime.

## CONTRACTS_EVALUATED

19

## PASS_COUNT

0

## FAIL_COUNT

0

## BLOCKED_COUNT

14

## REVIEW_REQUIRED_COUNT

5

## EXCEPTIONS

Nenhuma exceção aprovada.

## CRITICAL_FINDINGS

1. **Safe Area — REVIEW_REQUIRED.** A captura mostra clearance visual em relação ao status bar e ao home indicator, porém não há evidência de `safeAreaInsets`, constraints, SwiftUI safe-area behavior ou mecanismo equivalente. Não promover a PASS somente pela imagem.
2. **Hit targets — BLOCKED.** A dimensão real em pontos dos botões Menu, utilitário, anexar, ferramentas, microfone, voz/live, segmentos e sugestões não pode ser derivada com segurança da captura.
3. **Icon-only controls — BLOCKED.** Menu, ação utilitária, anexar, ferramentas, microfone e voz/live exigem semântica acessível; `accessibilityLabel`, role e state não são observáveis no screenshot.
4. **Dynamic Type — BLOCKED.** Não há evidência de semantic text styles, scaling nem comportamento nos maiores tamanhos de acessibilidade. Apple orienta layouts a acomodar mudanças de tamanho de texto e permitir crescimento/reflow dos containers.
5. **Chat / Work selected state — REVIEW_REQUIRED.** O estado selecionado é distinguível visualmente pela cápsula preenchida, mas falta evidência de estado `selected` exposto à tecnologia assistiva.
6. **VoiceOver — BLOCKED.** Nenhum teste de jornada, ordem de foco ou árvore de acessibilidade foi fornecido.
7. **Differentiate Without Color — REVIEW_REQUIRED.** A seleção visual usa forma/fill além do texto, o que é favorável, mas é necessário validar grayscale, selected state semântico e demais estados (erro, voz, atividade de ferramenta).
8. **Light/Dark — BLOCKED.** A captura evidencia somente uma aparência clara. Dark Mode não pode ser declarado suportado.
9. **Increase Contrast — BLOCKED.** Os cinzas de texto secundário e superfícies leves precisam de teste com a configuração ativada.
10. **Reduce Motion — BLOCKED.** Estados `STREAMING`, `TOOL_RUNNING`, `VOICE_ACTIVE` e transições de modo ainda não possuem evidência de adaptação à preferência do sistema.
11. **Localization/RTL — BLOCKED.** Os labels observados estão em inglês; não há teste com strings longas, pseudo-localização ou RTL.
12. **Async feedback — REVIEW_REQUIRED.** `SPEC-CHAT-AGENT-001` declara estados de sending/streaming/tool/error/voice, porém não há runtime que demonstre feedback visual e semântico para cada transição.
13. **Native component preference — BLOCKED.** O wireframe não permite saber se segmented control, buttons, text input e menus usam controles nativos, nativos estilizados ou customização integral.
14. **Keyboard/pointer/focus — BLOCKED até definição de plataforma.** A referência é tablet-like; caso iPadOS esteja no alvo, esses testes entram no gate.

## MATRIZ DE CONFORMIDADE — SUPERFÍCIE

| CONTRACT_ID | SUPERFÍCIE | SEVERITY | STATUS | EVIDENCE | ISSUE | REMEDIATION | OWNER |
|---|---|---:|---|---|---|---|---|
| HIG-LAYOUT-001 | tela/top/composer | MUST | REVIEW_REQUIRED | screenshot | Safe Area não comprovada por código/runtime | validar constraints/insets em devices alvo | A DEFINIR |
| HIG-LAYOUT-002 | tela/conversation/composer | MUST | BLOCKED | sem código | adaptação/fixed widths desconhecidos | auditar layout primitives | A DEFINIR |
| HIG-LAYOUT-006 | labels/suggestions/composer | MUST | BLOCKED | sem teste | accessibility text sizes desconhecidos | matriz Dynamic Type | A DEFINIR |
| HIG-INTERACTION-001 | controles clicáveis | MUST | BLOCKED | screenshot insuficiente | hit frame em pt desconhecido | medir runtime | A DEFINIR |
| HIG-INTERACTION-002 | icon-only buttons | MUST | BLOCKED | sem accessibility tree | labels/roles desconhecidos | VoiceOver + inspeção semântica | A DEFINIR |
| HIG-INTERACTION-003 | composer/mode/voice | MUST | REVIEW_REQUIRED | SPEC declara estados | implementação não comprovada | state matrix + previews/runtime | A DEFINIR |
| HIG-TYPOGRAPHY-002 | texto funcional | MUST | BLOCKED | sem runtime | Dynamic Type desconhecido | semantic styles + testes | A DEFINIR |
| HIG-COLOR-002 | tela/controls | MUST | BLOCKED | light screenshot | Dark Mode ausente | validar dark appearance | A DEFINIR |
| HIG-COLOR-004 | selection/status | MUST | REVIEW_REQUIRED | screenshot | semântica não confirmada | grayscale + accessibility state | A DEFINIR |
| HIG-COMPONENT-001 | segmented/buttons/input | SHOULD | BLOCKED | implementação ausente | nível de customização desconhecido | inventariar primitives | A DEFINIR |
| HIG-NAVIGATION-005 | Chat/Work | MUST | REVIEW_REQUIRED | seleção visual observada | selected state assistivo desconhecido | validar trait/state | A DEFINIR |
| HIG-ACCESSIBILITY-001 | superfície inteira | MUST | BLOCKED | sem teste | VoiceOver não validado | teste jornada crítica | A DEFINIR |
| HIG-ACCESSIBILITY-002 | ordem de foco | MUST | BLOCKED | sem teste | focus order desconhecida | VoiceOver/keyboard trace | A DEFINIR |
| HIG-ACCESSIBILITY-007 | motion states | MUST | BLOCKED | sem motion | Reduce Motion não validado | variante reduced motion | A DEFINIR |
| HIG-LOCALIZATION-001 | labels | MUST | BLOCKED | inglês somente | strings longas não testadas | pseudo-localização | A DEFINIR |
| HIG-LOCALIZATION-004 | layout direcional | MUST | BLOCKED | locale alvo A DEFINIR | RTL desconhecido | definir locales/testar RTL | A DEFINIR |
| HIG-MOTION-001 | sending/streaming/tool/voice | MUST | REVIEW_REQUIRED | estados na SPEC | feedback runtime ausente | testes de transição/erro | A DEFINIR |
| HIG-SYSTEM-003 | contraste | MUST | BLOCKED | sem teste | Increase Contrast desconhecido | matriz de acessibilidade | A DEFINIR |
| HIG-SYSTEM-007 | teclado/ponteiro/foco | MUST | BLOCKED | plataforma A DEFINIR | aplicabilidade/runtime desconhecidos | confirmar alvo e testar | A DEFINIR |

## REMEDIATION_ORDER

### P0 — bloqueia aprovação de UI
1. Identificar implementação real da superfície e mapear componentes → arquivos → Design System.
2. Medir todos os hit targets aplicáveis e corrigir no componente-base.
3. Inspecionar/accessibility tree de todos os icon-only controls e `Chat / Work`.
4. Executar VoiceOver na jornada crítica: abrir Chat → alternar modo → usar sugestão → compor → anexar/ferramenta → enviar → receber streaming/tool result → erro/retry → voz quando disponível.
5. Executar Dynamic Type e garantir reflow/ausência de truncamento essencial.
6. Verificar Safe Area por código e runtime, inclusive com teclado aberto.

### P1 — adaptações de sistema
7. Light/Dark.
8. Increase Contrast.
9. Differentiate Without Color / grayscale.
10. Reduce Motion.
11. localização longa/pseudo-localização.
12. RTL quando aplicável.
13. teclado externo/ponteiro/foco quando aplicável.

### P2 — governança/componentização
14. Confirmar uso de componentes nativos/nativos estilizados antes de customização integral.
15. Levar correções recorrentes para Design System e revalidar consumidores.

## EVIDENCE_INDEX

### EVID-CHAT-HIG-001
- source: screenshot fornecido pelo usuário em 2026-09-12
- source_type: `A_OBSERVADO`
- surface: Chat com Agente de IA
- result: composição visual observada; sem acesso a implementação/runtime.

### EVID-CHAT-HIG-002
- source: `SPEC-CHAT-AGENT-001`
- source_type: projeto/documentação
- result: estrutura, inventário e estados declarados; não prova implementação.

### EVID-APPLE-HIG-LAYOUT-001
- source: `https://developer.apple.com/design/human-interface-guidelines/layout`
- source_type: Apple official
- accessed_at: 2026-09-12
- result: layout deve adaptar a tamanhos, orientação, multitarefa, text-size changes e respeitar safe areas.

### EVID-APPLE-VOICEOVER-001
- source: `https://developer.apple.com/help/app-store-connect/manage-app-accessibility/voiceover-evaluation-criteria`
- source_type: Apple official
- accessed_at: 2026-09-12
- result: controles customizados devem ser operáveis com VoiceOver e transmitir informação equivalente aos controles padrão.

### EVID-APPLE-COLOR-001
- source: `https://developer.apple.com/help/app-store-connect/manage-app-accessibility/differentiate-without-color-alone-evaluation-criteria`
- source_type: Apple official
- accessed_at: 2026-09-12
- result: tarefas comuns não devem depender de cor como único diferenciador.

### EVID-APPLE-MOTION-001
- source: `https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria`
- source_type: Apple official
- accessed_at: 2026-09-12
- result: motion problemático deve ser reduzido/substituído preservando significado.

## DEFINITION OF DONE

- Safe Area: `REVIEW_REQUIRED`
- Targets de interação: `BLOCKED`
- Dynamic Type: `BLOCKED`
- VoiceOver: `BLOCKED`
- Light Mode: evidência visual disponível, conformidade final `BLOCKED` sem implementação
- Dark Mode: `BLOCKED`
- Increase Contrast: `BLOCKED`
- Differentiate Without Color: `REVIEW_REQUIRED`
- Reduce Motion: `BLOCKED`
- Localização longa: `BLOCKED`
- RTL: `BLOCKED` / aplicabilidade A DEFINIR
- Estados normal/pressed/disabled/loading/error: `REVIEW_REQUIRED`
- Componente nativo quando disponível: `BLOCKED`
- Sem dimensões dependentes de aparelho: `BLOCKED`
- Sem truncamento essencial: `BLOCKED`
- Evidências anexadas: `PARTIAL`
- Sem MUST aberto: `FAIL_GATE`

## HANDOFF

**Status:** `BLOCKED`

**Entregáveis:**
- `docs/09-frontend/hig/APPLE_HIG_CONTRACT_REGISTRY_CHAT_AGENT.json`
- `docs/09-frontend/hig/HIG-AUDIT-CHAT-AGENT-001.md`
- `docs/09-frontend/SPEC-CHAT-AGENT-001.md`

**Pendências:** código da superfície, framework/plataforma mínima, Design System consumido no runtime, preview/test environment e testes de acessibilidade.

**Bloqueios:** contratos MUST sem evidência runtime.

**Próximo workflow:** `Engenharia/Correção → QA → Release Gate` depois da resolução P0.

**Owner seguinte:** `A DEFINIR`.
