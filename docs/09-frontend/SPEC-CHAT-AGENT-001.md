---
id: SPEC-CHAT-AGENT-001
type: ui_product_spec
title: Chat com Agente de IA — Wireframe, Componentes e Contratos HIG
status: draft_for_pre_approval
version: 1.0.0
owner: null
project: EXECUTAR
date: 2026-09-12
depends_on:
  - D22-DEC-001
  - D22-DEC-003
  - UI-005
  - SPEC-WORKSPACE-001
  - MST-XP-HIG-TP-001
related:
  - HIG-AUDIT-CHAT-AGENT-001
  - APPLE_HIG_CONTRACT_REGISTRY_CHAT_AGENT.json
---
# SPEC-CHAT-AGENT-001 — Chat com Agente de IA

## 1. Objetivo

Definir a composição, o inventário de componentes, os estados, a responsividade, a semântica de interação e os contratos mínimos de acessibilidade da área **Chat com Agente de IA** do EXECUTAR.

A especificação parte do wireframe visual fornecido em 2026-09-12 e da decisão `D22-DEC-003`, preservando baixa densidade, foco no diálogo e uma única superfície primária de composição.

A referência visual é evidência de layout e hierarquia. Não autoriza cópia de marca, ícones proprietários ou identidade de terceiros.

## 2. Princípios obrigatórios

1. **Conversa primeiro:** a maior parte do viewport pertence à Conversation Surface.
2. **Composer dominante:** a ação primária persistente é compor/enviar uma mensagem.
3. **Baixa densidade:** capacidades adicionais entram por progressive disclosure antes de criar novos controles permanentes.
4. **Semântica antes de aparência:** controles devem possuir papel, label, estado e comportamento verificáveis.
5. **Adaptação antes de dimensão fixa:** layout deve reagir ao espaço disponível, tamanho de texto, teclado e ambiente.
6. **Acessibilidade é gate:** ausência de evidência para contratos MUST impede aprovação final da UI.
7. **Design System canônico:** tokens e componentes locais não podem redefinir silenciosamente `UI-005`.

## 3. Estrutura macro

A tela possui quatro zonas funcionais:

1. `Top Utility Bar` — navegação, seleção de modo e utilidades globais.
2. `Conversation Surface` — área dominante de conversa e resultados do agente.
3. `Context Suggestions` — sugestões contextuais de baixa prioridade.
4. `Composer Dock` — entrada multimodal persistente na base da interface.

Hierarquia de interação:

`Composer > Conversation > Suggestions > Mode Switch > Utilities`

## 4. Inventário canônico de componentes

### 4.1 Top Utility Bar

| Componente | Qtde. | Papel | Regra |
|---|---:|---|---|
| Context/App Indicator | 1 | identificação/contexto | pode ser não interativo |
| Menu/Navegação | 1 | button | alvo mínimo aplicável; label acessível obrigatório |
| Chat segment | 1 | tab/segment | estado selected perceptível visual e semanticamente |
| Work segment | 1 | tab/segment | estado selected perceptível visual e semanticamente |
| Utility Action | 1 | button | função específica; label acessível obrigatório |

Alvos interativos permanentes no topo: **máximo 4**, contando `Chat` e `Work` separadamente e excluindo o indicador quando não interativo.

### 4.2 Conversation Surface

Uma única superfície principal que pode apresentar:

- mensagem do usuário;
- mensagem do agente;
- streaming parcial;
- resultado de ferramenta;
- erro e retry;
- estado aguardando usuário;
- artefato incorporado;
- status de operação prolongada.

No estado `EMPTY`, não existem cards permanentes obrigatórios.

A ordem visual deve corresponder à ordem lógica de leitura e navegação assistiva.

### 4.3 Context Suggestions

Baseline: `0–2` sugestões visíveis imediatamente antes do composer.

Cada sugestão:

- é clicável como linha inteira;
- possui título textual curto;
- pode conter ícone complementar;
- não depende exclusivamente do ícone para transmitir significado;
- deve suportar texto maior e localização longa sem truncamento essencial.

Sugestões desaparecem ou perdem prioridade conforme a conversa ganha conteúdo.

### 4.4 Composer Dock

O composer contém no máximo cinco alvos interativos permanentes:

| Componente | Qtde. | Semântica | Requisitos mínimos |
|---|---:|---|---|
| Campo de composição | 1 | text input | texto escalável, foco previsível, label/hint acessível |
| Adicionar/Anexar | 1 | button | label acessível; não depende apenas do ícone |
| Ferramentas/Modo | 1 | button/menu | progressive disclosure para capabilities adicionais |
| Microfone | 1 | button | estado disponível/ativo/disabled exposto semanticamente |
| Voz/Live | 1 | button | somente quando capability existir; estado ativo perceptível sem depender só de cor |

O botão de envio pode substituir contextualmente um dos controles do composer quando houver texto pronto para envio, sem elevar o limite permanente de densidade. A regra exata de alternância deve ser definida na implementação e testada quanto à previsibilidade.

## 5. Contagem consolidada

Baseline do estado vazio:

- zonas funcionais: **4**;
- blocos visuais principais: **5**;
- topo: **máximo 4** alvos permanentes;
- sugestões: **0–2** alvos;
- composer: **máximo 5** alvos permanentes;
- máximo de referência no estado inicial: **11 alvos interativos**;
- sem sugestões: **9 alvos interativos**.

A contagem de 11 é `PROJECT_RULE` do EXECUTAR. Não é valor HIG da Apple.

## 6. Regra de densidade e progressive disclosure

SE uma nova capability exigir uma ação adicional, ENTÃO ela deve primeiro ser avaliada como:

1. item de `Ferramentas/Modo`;
2. menu contextual;
3. ação inline no conteúdo;
4. comando do agente;
5. painel contextual temporário.

Somente após rejeição documentada dessas opções pode ser proposto novo botão permanente.

Aumento do limite de topo, composer ou sugestões exige revisão explícita desta SPEC ou de `D22-DEC-003`.

## 7. LayoutContract

### 7.1 Safe Areas

- Top Utility Bar deve permanecer dentro da região segura aplicável.
- Composer Dock deve permanecer acima da safe area inferior.
- Teclado virtual não pode ocultar o composer nem a última mensagem relevante.
- Conteúdo decorativo pode ultrapassar safe area somente quando deliberado e sem comprometer controles/conteúdo funcional.

### 7.2 Adaptação

- `hardcodedDeviceWidth`: **proibido**, exceto preview/teste isolado.
- Padding, spacing, radius e dimensões recorrentes devem vir do Design System.
- Layout deve reflowar antes de cortar conteúdo essencial.
- Scroll deve preservar conteúdo e targets; não deve mascarar falhas estruturais de layout.
- Orientação, resize e multitarefa devem ser testados quando aplicáveis à plataforma-alvo.

## 8. InteractionContract

- Baseline iOS de alvo interativo: **44×44 pt quando aplicável**.
- Área de toque não pode ser reduzida ao tamanho visual do ícone.
- Todo botão icon-only deve possuir `accessibilityLabel` significativo.
- Controles devem expor `normal`, `pressed/active` quando aplicável e `disabled` quando aplicável.
- Gesto oculto não pode ser a única forma de executar ação essencial.
- Scroll passivo nunca conclui tarefa ou altera estado operacional sem regra de produto explícita.

## 9. TypographyContract

- Tipografia funcional deve usar estilos semânticos de sistema ou mapeamento equivalente do Design System.
- Dynamic Type é obrigatório em superfícies iOS onde aplicável.
- Tamanho absoluto não pode ser a única estratégia de texto funcional.
- Nos maiores tamanhos suportados, o layout deve expandir, reflowar ou empilhar antes de truncar conteúdo essencial.
- `Chat`, `Work`, sugestões, mensagens, placeholder e estados do composer devem ser testados com categorias de acessibilidade.

## 10. ColorContract

- Preferir cores semânticas do sistema ou tokens semânticos de `UI-005`.
- Light Mode e Dark Mode devem ser suportados quando exigidos pela plataforma/superfície.
- Seleção, erro, sucesso, atividade e disabled não podem depender apenas de cor.
- `Chat / Work` deve combinar texto + forma/estado selecionado e expor selected state semanticamente.
- Voz ativa, tool running, erro e offline devem possuir sinal redundante: texto, ícone, shape, label ou equivalente.
- Increase Contrast e Differentiate Without Color devem ser validados quando aplicáveis.

## 11. ComponentContract

Ordem de preferência:

1. componente nativo;
2. componente nativo estilizado;
3. componente próprio composto sobre primitivas nativas;
4. controle integralmente customizado somente com justificativa.

Aplicação à superfície:

- segmented control de `Chat / Work`: usar equivalente nativo quando semanticamente adequado;
- botões icon-only: usar `Button`/equivalente nativo quando disponível;
- input do composer: usar `TextField`, `TextEditor` ou equivalente conforme comportamento necessário;
- menus e pickers: usar primitivas nativas quando semanticamente corretas.

Qualquer customização não pode remover acessibilidade, estados, adaptação de plataforma ou comportamento esperado.

## 12. NavigationContract — Chat × Work

`Chat / Work` representa mudança de modo dentro da mesma experiência agentic, não duas aplicações separadas.

### Chat

Diálogo direto para perguntas, comandos, consultas e ações rápidas.

### Work

Contexto persistente de trabalho com arquivos, artefatos, projetos, tarefas, Studio/Consultoria e operações prolongadas.

Regras:

- modo selecionado deve ser perceptível visualmente e por tecnologia assistiva;
- a troca deve preservar contexto quando permitido;
- não pode duplicar silenciosamente estado operacional;
- back, dismiss, modal e deep link devem manter comportamento previsível;
- significado de ações equivalentes não muda entre modos sem indicação explícita.

## 13. AccessibilityContract

A superfície deve atender, quando aplicável:

- VoiceOver identifica cada controle, valor e estado relevante;
- ordem de foco acompanha a ordem lógica da tarefa;
- ícones decorativos ficam fora da árvore de acessibilidade;
- ícones informativos possuem descrição adequada;
- controles compostos expõem semântica correta;
- Differentiate Without Color;
- Reduce Motion para motion não essencial;
- nenhuma informação essencial depende apenas de posição, cor, animação ou som.

Jornada crítica obrigatória de teste:

`abrir Chat → alternar Chat/Work → acionar sugestão → focar composer → anexar/ferramenta → digitar → enviar → receber streaming → tool result → erro/retry → voz, quando disponível`.

## 14. LocalizationRTLContract

- labels não podem assumir largura fixa baseada em inglês/português curto;
- validar strings longas e pseudo-localização;
- não embutir texto localizável em imagem;
- RTL deve ser suportado quando houver locale RTL no produto;
- ícones direcionais espelham quando semanticamente apropriado;
- ordem dos elementos deve respeitar direção de leitura quando aplicável.

## 15. MotionFeedbackContract

Estados assíncronos devem comunicar progresso, conclusão ou falha quando a latência for perceptível.

- animação não é única evidência de mudança;
- motion respeita Reduce Motion quando aplicável;
- háptico/som complementa, nunca substitui feedback visual/semântico;
- streaming, tool running e voice active devem possuir fallback não animado compreensível.

## 16. SystemAdaptationContract

Validar quando aplicável:

- Light Mode;
- Dark Mode;
- Dynamic Type;
- Increase Contrast;
- Differentiate Without Color;
- Reduce Motion;
- orientação/redimensionamento/multitarefa;
- teclado externo, ponteiro e foco.

## 17. Responsividade por classe de superfície

### Mobile / tablet compacto

- top bar em uma única linha quando houver espaço;
- se não houver, preservar funções por reorganização, não por truncamento essencial;
- composer respeita safe area inferior;
- sugestões ficam imediatamente acima do composer;
- teclado não cobre composer nem a mensagem relevante;
- controles mantêm hit area mínima mesmo quando visualmente compactos.

### Desktop / largura expandida

- inventário funcional permanece o mesmo;
- maior largura não autoriza toolbar permanente adicional;
- painéis contextuais aparecem somente quando necessários;
- conteúdo mantém largura de leitura e hierarquia adequadas.

## 18. Estados obrigatórios

`EMPTY`
`TYPING`
`SENDING`
`STREAMING`
`TOOL_RUNNING`
`TOOL_RESULT`
`WAITING_FOR_USER`
`ERROR_RETRYABLE`
`OFFLINE_DEGRADED`
`CONVERSATION_WITH_ARTIFACT`
`VOICE_ACTIVE` quando suportado
`DISABLED` quando uma capability estiver indisponível

Para cada estado, a implementação deve definir:

- trigger;
- feedback visual;
- feedback semântico/acessível;
- ações permitidas;
- ação de saída/recuperação;
- comportamento com Reduce Motion quando houver animação.

## 19. Integração com Studio / Consultoria

Fluxo conceitual:

`Chat → intenção/briefing → Studio → artefato/protótipo → handoff`

Regras:

- Chat pode iniciar uma sessão de Studio;
- o canvas persistente pertence ao Studio;
- Studio não vira card permanente do Chat;
- contexto pode ser transferido conforme policy;
- handoff não altera estado operacional sem contrato/autorização aplicável.

## 20. Design System

A implementação consome `UI-005` e `D22-DEC-001`.

Obrigatório:

- tokens semânticos para spacing, color, typography, radius e motion;
- componentes canônicos reutilizados em vez de cópias locais;
- nenhuma dimensão dependente de modelo específico de aparelho;
- exceções documentadas com motivo, impacto e owner.

## 21. Matriz mínima de validação

| Gate | Resultado exigido para aprovação |
|---|---|
| Safe Area | PASS |
| Targets 44×44 pt quando aplicável | PASS |
| Dynamic Type | PASS |
| VoiceOver | PASS |
| Light Mode | PASS |
| Dark Mode | PASS quando aplicável |
| Increase Contrast | PASS ou NOT_APPLICABLE |
| Differentiate Without Color | PASS ou NOT_APPLICABLE |
| Reduce Motion | PASS ou NOT_APPLICABLE |
| Localização longa | PASS |
| RTL | PASS ou NOT_APPLICABLE |
| Estados normal/pressed/disabled/loading/error | PASS quando aplicáveis |
| Componente nativo quando disponível | PASS |
| Sem dimensões dependentes de aparelho | PASS |
| Sem truncamento essencial | PASS |
| Evidências anexadas | PASS |
| MUST aberto | ZERO |

## 22. Critérios de aceite da SPEC

A SPEC está documentalmente correta quando:

- mantém uma única Conversation Surface e um composer dominante;
- topo não ultrapassa 4 alvos permanentes sem revisão explícita;
- composer não ultrapassa 5 alvos permanentes sem revisão explícita;
- estado inicial mostra no máximo 2 sugestões;
- funções adicionais usam progressive disclosure;
- `Chat` e `Work` possuem semântica distinta e selected state definido;
- Safe Area e teclado possuem contrato explícito;
- hit targets possuem baseline verificável;
- Dynamic Type, VoiceOver, Light/Dark, contraste, Reduce Motion, localização e RTL possuem gates;
- estados assíncronos possuem feedback visual e semântico;
- componente nativo é preferido quando semanticamente adequado;
- nenhuma evidência visual isolada é usada para declarar conformidade final.

## 23. Definition of Done — implementação

Uma implementação desta SPEC só pode ser marcada `validated` quando todos os MUST aplicáveis estiverem em `PASS`, `NOT_APPLICABLE` justificado ou `EXCEPTION` aprovada.

Uma screenshot ou protótipo visual não é suficiente para validar:

- Safe Area implementada;
- hit targets em pt;
- accessibility labels/traits;
- VoiceOver;
- Dynamic Type;
- Dark Mode;
- Increase Contrast;
- Reduce Motion;
- RTL;
- teclado/ponteiro/foco.

## 24. Estado e evidência

- referência visual: `A_OBSERVADO`;
- decisão de composição: `D22-DEC-003 — ACEITA`;
- contrato HIG: `MST-XP-HIG-TP-001 — TEMPLATE / CANONICAL`;
- auditoria: `HIG-AUDIT-CHAT-AGENT-001 — BLOCKED` por ausência de runtime/código/testes;
- especificação: `draft_for_pre_approval`;
- implementação: `NÃO CONFIRMADA`;
- testes: `NÃO CONFIRMADOS`;
- release: `NÃO CONFIRMADO`.

A correção desta SPEC não altera automaticamente o estado da auditoria, da implementação ou do release.
