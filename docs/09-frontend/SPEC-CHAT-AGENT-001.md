---
id: SPEC-CHAT-AGENT-001
type: ui_product_spec
title: Chat com Agente de IA — Wireframe e Inventário de Componentes
status: draft_for_pre_approval
version: 0.9.0
owner: null
project: EXECUTAR
date: 2026-09-12
depends_on:
  - D22-DEC-001
  - D22-DEC-003
  - UI-005
  - SPEC-WORKSPACE-001
---
# SPEC-CHAT-AGENT-001 — Chat com Agente de IA

## 1. Objetivo
Fixar a composição-base da área de chat com agente de IA do EXECUTAR a partir do wireframe visual fornecido em 2026-09-12, preservando baixa densidade visual, foco no diálogo e uma única superfície primária de composição.

A imagem de referência é evidência visual de layout e hierarquia, não autorização para copiar marca, ícones proprietários ou identidade de terceiros.

## 2. Estrutura macro
A tela possui quatro zonas funcionais:
1. `Top Utility Bar` — navegação e utilidades globais.
2. `Conversation Surface` — área principal de conversa, predominantemente livre.
3. `Context Suggestions` — atalhos/sugestões recentes ou relevantes.
4. `Composer Dock` — entrada multimodal persistente na parte inferior.

## 3. Inventário canônico do wireframe
### 3.1 Top Utility Bar
- 1 indicador/contexto visual de app;
- 1 botão Menu/Navegação;
- 1 segmented control com 2 opções: `Chat` e `Work`;
- 1 ação utilitária à direita.

Controles clicáveis no topo: **4 alvos interativos**, contando `Chat` e `Work` separadamente, mais Menu e a ação utilitária.

### 3.2 Conversation Surface
- 1 área principal de conversa;
- sem cards permanentes quando vazia;
- aceita mensagens, respostas do agente, tool results e artefatos embutidos.

### 3.3 Context Suggestions
Baseline: **2 linhas de sugestão** visíveis antes do composer.
Cada uma contém 1 ícone + 1 título curto e é clicável como linha inteira.
A quantidade pode variar entre `0–2` para não competir com a conversa.

### 3.4 Composer Dock
1 container com 5 elementos internos:
- 1 campo de composição;
- 1 botão adicionar/anexar;
- 1 botão de ferramenta/modo;
- 1 botão microfone;
- 1 botão voz/live.

Alvos interativos no composer: **5**.

## 4. Contagem consolidada
Baseline do estado vazio:
- blocos principais: **5**;
- topo: **4** alvos interativos;
- sugestões: **2**;
- composer: **5**;
- total máximo baseline: **11 alvos interativos**;
- sem sugestões: **9 alvos interativos**.

## 5. Hierarquia
`Composer > Conversation > Suggestions > Mode Switch > Utilities`

O composer é a ação primária persistente. Sugestões são secundárias. Utilidades do topo não podem crescer para uma toolbar extensa.

## 6. Regra de densidade
Limites permanentes:
- topo: máximo **4 alvos interativos**;
- composer: máximo **5 alvos interativos**;
- sugestões: máximo **2 visíveis** no estado inicial.

SE uma nova capability exigir comando permanente, ENTÃO deve primeiro ser avaliada como opção do botão Ferramentas/Modo, menu contextual ou disclosure progressivo.

## 7. Responsividade
### Mobile / tablet compacto
- top bar em linha única;
- composer acima da safe area inferior;
- segmented control central quando houver espaço;
- sugestões acima do composer;
- teclado não cobre composer nem a última mensagem relevante.

### Desktop
- mantém o mesmo inventário funcional;
- mais largura não autoriza adicionar toolbars permanentes;
- painéis contextuais somente quando necessários.

## 8. Estados obrigatórios
`EMPTY`, `TYPING`, `SENDING`, `STREAMING`, `TOOL_RUNNING`, `TOOL_RESULT`, `WAITING_FOR_USER`, `ERROR_RETRYABLE`, `OFFLINE/DEGRADED`, `CONVERSATION_WITH_ARTIFACT`, `VOICE_ACTIVE` quando suportado.

## 9. Chat × Work
O segmented control representa mudança de modo, não duas aplicações separadas.

### Chat
Diálogo direto com o agente para perguntas, comandos, consultas e ações rápidas.

### Work
Contexto persistente de trabalho com artefatos, arquivos, projetos, tarefas, Studio ou operações prolongadas.

A troca deve preservar contexto quando permitido e não duplicar estado operacional.

## 10. Integração com Studio / Consultoria
Fluxo conceitual:
`Chat → intenção/briefing → abrir Studio → continuar com contexto → gerar/refinar artefato → handoff`.

O Studio não deve virar um card permanente do Chat; o canvas persistente pertence ao Studio.

## 11. Design System
A implementação consome `UI-005` e `D22-DEC-001`.
A referência sustenta superfícies claras, controles arredondados, baixa densidade, separação por espaço, dock inferior e segmented control simples.
Ícones, tipografia, cores, tokens, motion e componentes finais pertencem ao Design System do EXECUTAR.

## 12. Critérios de aceite
- uma única superfície de conversa e um composer dominante;
- topo com no máximo 4 alvos permanentes;
- composer com no máximo 5 alvos permanentes;
- no máximo 2 sugestões no estado inicial;
- funções adicionais entram por progressive disclosure;
- Chat e Work semanticamente distintos;
- safe areas e teclado não escondem o composer;
- compatibilidade com `D22-DEC-001`;
- wireframe não implica implementação de integrações, tools ou voice.

## 13. Estado
- referência visual: `A_OBSERVADO`;
- decisão de composição: dependente de `D22-DEC-003`;
- especificação: `draft_for_pre_approval`;
- implementação: não confirmada;
- teste: não confirmado;
- release: não confirmado.
