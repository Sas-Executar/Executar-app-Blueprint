---
id: PROD-001
type: product_vision
title: EXECUTAR — Visão do Produto
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
source_of_truth: true
approved_for: product_derivation
approval_date: 2026-09-09
epistemic_model:
  A: Observado
  B: Primário
  C: Publicado
  D: Interno
  E: Inferido
depends_on: []
feeds:
  - PROD-002
  - PROD-003
  - PROD-004
  - PROD-005
  - PROD-006
  - PROD-007
  - PROD-008
source_notes:
  - Executar App - Blueprint..md
---

# EXECUTAR — VISÃO DO PRODUTO

## 1. Definição executiva

O **EXECUTAR** é um sistema operacional adaptativo de execução para trabalhadores solo, concebido para transformar objetivos, projetos, processos e compromissos em uma sequência continuamente recalculada de ações concretamente executáveis.

[D — Interno]

O produto não tem como função principal armazenar tarefas, exibir planos ou exigir que o usuário gerencie continuamente prioridades. Sua função principal é **absorver parte da carga operacional normalmente transferida ao executor e devolver uma próxima ação elegível, contextual e compatível com sua capacidade real**.

[E — Inferido]

A arquitetura parte de uma distinção fundamental:

- o **plano** preserva estrutura, dependências, objetivos e baseline;
- a **rota de execução** muda conforme disponibilidade, contexto, bloqueios, dependências, WIP e progresso observado.

[D — Interno]

Metáfora central: **GPS de execução** — o destino permanece; a rota pode mudar conforme as condições.

[E — Inferido]

## 2. Problema central

Sistemas convencionais de produtividade e gestão de projetos exigem que o próprio usuário execute continuamente operações como:

- planejar;
- decompor;
- organizar;
- priorizar;
- lembrar;
- acompanhar;
- estimar duração;
- administrar dependências;
- decidir o que fazer agora;
- reconstruir contexto;
- reorganizar o plano após interrupções;
- controlar progresso;
- reconhecer quando uma entrega realmente terminou.

[D — Interno]

Essa transferência de responsabilidade cria uma camada adicional de trabalho: **gerenciar o sistema de trabalho antes de conseguir executar o próprio trabalho**.

[E — Inferido]

Para usuários com dificuldades de planejamento, priorização, iniciação, memória de trabalho, percepção temporal, monitoramento ou troca de contexto, essa exigência pode aumentar atrito operacional.

[D — Interno]

Problema-alvo: **o excesso de carga executiva necessária para transformar intenção e planejamento em ação contínua**.

[E — Inferido]

## 3. Problema operacional fundamental

O usuário pode possuir objetivos claros, projetos estruturados, tarefas cadastradas, tempo disponível, ferramentas e conhecimento necessário e ainda assim não conseguir determinar rapidamente:

**“O que exatamente devo executar agora?”**

[D/E — Interno + Inferido]

O problema aumenta quando existem simultaneamente múltiplos projetos, dependências, interrupções, capacidade variável, prazos, bloqueios, diferentes contextos, tarefas de tamanhos diferentes e necessidade frequente de retomada.

## 4. Usuário principal

O perfil inicialmente mais natural para o EXECUTAR é o **knowledge worker / trabalhador intelectual solo que administra simultaneamente múltiplos projetos, entregáveis, responsabilidades e interrupções**.

[D/E — Interno + Inferido]

O documento direciona especialmente a arquitetura para trabalhadores solo neurodivergentes e considera dificuldades executivas operacionais como variável explícita de produto e design.

[D — Interno]

Perfis secundários compatíveis incluem freelancer, consultor, founder solo, creator, pesquisador, profissional de projetos, profissional autônomo e operador intelectual.

[E — Inferido]

## 5. Princípio neuroadaptativo

O EXECUTAR parte do princípio de que determinadas operações executivas podem ser parcialmente externalizadas para o ambiente e para o sistema.

[D — Interno]

Formulação de produto: **transferir carga executiva evitável do operador para o sistema, preservando decisão, autonomia e controle humano**.

[D/E — Interno + Inferido]

O produto deve reduzir a necessidade de o usuário manter mentalmente prioridades, dependências, sequência, estado, contexto, prazos, progresso, critérios de conclusão, retomadas e disponibilidade relativa das alternativas.

As referências científicas e clínicas mencionadas no corpus devem ser verificadas individualmente antes de serem promovidas a evidência científica canônica do produto.

[GAP — validação bibliográfica]

## 6. Proposta central

O EXECUTAR organiza conhecimento operacional, projetos, processos, entregáveis, tarefas, ações, evidências, dependências, capacidade e execução.

[D — Interno]

Sua proposta central não é apenas registrar esses elementos. É **orquestrar sua execução**.

[E — Inferido]

Categoria de produto proposta: **Execution OS / Adaptive Work Execution System**.

[E — Inferido]

## 7. Proposta de valor

O EXECUTAR pretende reduzir decisões operacionais repetitivas relacionadas a:

- o que fazer;
- em qual ordem;
- quando iniciar;
- quando retomar;
- o que está disponível;
- o que está bloqueado;
- o que cabe no tempo existente;
- qual ação mantém o fluxo;
- quando algo pode ser considerado concluído.

[D/E — Interno + Inferido]

Proposta de valor condensada: **Você define o resultado. O EXECUTAR organiza a execução e mantém uma rota executável até ele.**

## 8. Promessa principal

O produto pretende diminuir carga cognitiva operacional, fadiga decisória, dependência de planejamento contínuo, dependência de múltiplas plataformas, troca desnecessária de contexto, necessidade de reconstruir estado após interrupções, personalização excessiva e reorganização manual constante.

[D — Interno]

E aumentar clareza da próxima ação, continuidade, retomabilidade, previsibilidade, capacidade de concluir, rastreabilidade e percepção de progresso real.

[E — Inferido]

## 9. Pergunta principal do produto

**“Dadas minhas prioridades, dependências, contexto e capacidade atual, qual é a melhor próxima ação executável?”**

[D — Interno]

Perguntas derivadas:

- O que cabe agora?
- O que está pronto?
- O que está bloqueado?
- O que devo fazer primeiro?
- O que mantém o fluxo?
- O que estava fazendo?
- Como retomo?
- O que comprova que concluí?
- Quanto progresso real foi produzido?

## 10. Objeto fundamental

A menor unidade operacional do EXECUTAR é **ACTION**.

Uma Action deve representar a menor unidade de trabalho concretamente executável, observável, contextualizável, estimável, concluível e verificável.

[D/E — Interno + Inferido]

Uma Action não deve existir isoladamente. Ela deve preservar rastreabilidade até o resultado que pretende avançar.

## 11. Hierarquia conceitual

**OUTCOME  
↓  
PROJECT / VALUE STREAM  
↓  
DELIVERABLE  
↓  
TASK  
↓  
ACTION  
↓  
EVIDENCE**

[D/E — Interno + Inferido]

Princípio estrutural: **a decomposição deve terminar em uma unidade observável e executável**.

`Evidence` demonstra ou registra a conclusão e sustenta progresso verificável.

## 12. Arquitetura lógica central

**OUTCOME  
→ PLAN  
→ DAG / DEPENDENCIES  
→ READY POOL  
→ CAPACITY FILTER  
→ FLOW  
→ CONTEXT  
→ BEST NEXT ACTION  
→ WIP  
→ EXECUTE  
→ DoD / EVIDENCE  
→ PROGRESS  
→ LEARNING  
→ RECALCULATE**

[D/E — Interno + Inferido]

Essa cadeia constitui o núcleo lógico do produto.

## 13. Plano versus rota

### PLAN

O plano preserva resultado, estrutura, decomposição, WBS, dependências, baseline e relações entre objetos.

[D — Interno]

### ROUTE

A rota representa a sequência efetivamente recomendada para execução e pode ser recalculada conforme capacidade disponível, dependências, bloqueios, WIP, contexto, estado, progresso e alterações operacionais.

[D — Interno]

Princípio: **uma alteração de contexto não deve destruir o plano; deve produzir uma nova rota válida dentro dele**.

## 14. Elegibilidade

Uma Action somente deve concorrer à seleção quando cumprir as restrições estruturais aplicáveis.

**READY ∧ DependenciesDone ∧ FitsCapacity ∧ WIPAvailable**

[D — Interno]

Princípio: **Elegibilidade precede prioridade**.

Uma tarefa prioritária que não pode ser executada agora não deve necessariamente ocupar a recomendação atual.

## 15. Best Next Action

Depois de eliminar ações inelegíveis, o sistema deve reduzir o espaço de alternativas e produzir uma recomendação dominante: **BEST_NEXT_ACTION**.

[D — Interno]

O objetivo da experiência não é apresentar ao usuário uma lista crescente de possibilidades. O objetivo é reduzir possibilidades até uma ação executável.

[E — Inferido]

## 16. Capacidade

Tempo deve funcionar primariamente como **restrição de capacidade**, não como indicador automático de progresso.

[D — Interno]

O usuário informa ou disponibiliza uma janela de capacidade. O motor elimina ações incompatíveis com essa janela.

Exemplo conceitual: **“Quanto tempo você tem agora?” → filtrar ações elegíveis → recomendar ação compatível.**

A capacidade futura poderá ser progressivamente inferida a partir de duração observada, throughput, cycle time e padrões de execução.

[D/E — Interno + Inferido]

## 17. WIP e foco

O EXECUTAR deve utilizar WIP reduzido como mecanismo estrutural de execução.

[D — Interno]

O corpus destaca **WIP 1:1**.

A intenção não é transformar foco em disciplina comportamental exigida do usuário. A intenção é reduzir arquiteturalmente a quantidade de trabalho concorrente exposto ao executor.

[E — Inferido]

## 18. Progresso

Progresso não deve equivaler simplesmente a tempo gasto, tarefa iniciada ou atividade registrada.

[D — Interno]

O progresso deve representar conclusão verificável. O corpus propõe `Progress Points` creditados após cumprimento da Definition of Done.

Estrutura: **EXECUTE → DoD → EVIDENCE → PROGRESS**.

## 19. Retomada

O sistema deve persistir estado e contexto suficientes para que uma interrupção não obrigue o usuário a reconstruir manualmente todo o cenário de trabalho.

[D — Interno]

Princípio: **interrupção ≠ reinício do planejamento**.

Após uma intercorrência:

1. preservar estado;
2. reavaliar capacidade/contexto;
3. recalcular elegibilidade;
4. localizar outra Action válida, se necessário;
5. continuar avançando o resultado.

## 20. Papel da interface

A interface deve aplicar o princípio de **mínimo operacional necessário**.

[D — Interno]

Isso inclui menor quantidade possível de informação concorrente, redução de variáveis visíveis, menor necessidade de configuração, acesso direto à tarefa corrente, atalhos cognitivos, visualização orientada ao estado atual e redução de alternância entre superfícies.

O produto não deve exigir exploração constante de dashboards para permitir execução.

[E — Inferido]

## 21. Relação entre acesso ao aplicativo e execução

O corpus estabelece uma decisão estratégica: **o EXECUTAR não deve depender da abertura constante do aplicativo para que o usuário consiga executar**.

[D — Interno]

A aplicação funciona como infraestrutura operacional persistente, mas superfícies de execução podem ser reduzidas, incluindo atalhos, notificações, elementos impressos, scanner, símbolos, controles rápidos e integração analógico-digital.

Visão resultante: **usar o sistema continuamente não significa necessariamente navegar continuamente no aplicativo**.

## 22. Integração analógico-digital

O documento estabelece como direção relevante a capacidade de executar e controlar ações por superfícies físicas.

[D — Interno]

Exemplos mencionados: papel, scanner, símbolos, atalhos para tarefa recente e emissão de materiais relacionados à execução.

O papel deixa de representar um sistema independente e passa a funcionar como uma superfície de interação com o estado digital.

[E — Inferido]

## 23. Copiloto EXECUTAR

O `Copiloto EXECUTAR` é uma capability central prevista no produto.

[D — Interno]

Sua função deve ser subordinada ao modelo operacional do EXECUTAR. O agente não deve funcionar apenas como chat genérico.

[E — Inferido]

Seu papel deve incluir capacidades como interpretar contexto, auxiliar decomposição, identificar lacunas, apoiar planejamento, consultar estado, explicar recomendações, auxiliar replanejamento, produzir estrutura, operar ferramentas autorizadas e apoiar retomada.

A autoridade específica do agente, permissões e ações sujeitas a aprovação humana deverão ser definidas posteriormente em `AGENT_CHARTER`, `TOOL_REGISTRY` e `HUMAN_APPROVAL_POLICY`.

[GAP]

## 24. Principais capabilities

O corpus sustenta inicialmente:

- aplicação de metodologias estruturadas;
- decomposição de trabalho;
- agrupamento de ações;
- estruturação de dependências;
- planejamento por capacidade;
- controle por capacidade;
- WIP;
- priorização sistêmica;
- seleção da próxima ação;
- rastreabilidade;
- Definition of Done;
- evidências;
- automação de rotinas;
- replanejamento;
- retomada;
- Copiloto EXECUTAR;
- Mapa-OS;
- Status Report;
- visualização neuroadaptada;
- linguagem e semântica controladas;
- execução por scanner;
- integração analógico-digital.

[D — Interno]

## 25. Mapa função humana → compensação sistêmica

O EXECUTAR pretende deslocar determinadas operações do usuário para o sistema:

- lembrar tudo → memória externa persistente;
- decompor projeto → decomposição assistida;
- recalcular prioridades → motor de prioridade;
- decidir continuamente o próximo passo → Best Next Action;
- reconstruir contexto → estado persistente;
- estimar capacidade intuitivamente → capacidade baseada em execução observada;
- lembrar prazos → sistema temporal;
- acompanhar dependências → dependency engine;
- perceber progresso → progressão automática;
- identificar conclusão → DoD verificável;
- reorganizar após interrupção → retomada/replanejamento;
- navegar entre diversas superfícies → centralização por objeto.

[D — Interno]

## 26. Estratégia → execução

Todo trabalho deve preservar rastreabilidade vertical:

**Outcome → Deliverable → Task → Action → Evidence**

[D/E — Interno + Inferido]

O usuário não deve receber uma próxima ação sem que o sistema consiga relacioná-la ao resultado que ela pretende avançar.

## 27. Customização

O EXECUTAR deve permitir customização suficiente para diferentes formas de trabalho, incluindo workflows, tipos de objeto, regras, critérios de conclusão, contexto, prioridades e automações.

[E — Inferido]

**Customização não deve permitir violar invariantes estruturais do motor.**

O produto deve evitar transformar configuração em trabalho adicional para o usuário.

## 28. O que não constitui o núcleo inicial

O corpus não sustenta como núcleo P0:

- CRM;
- Service Desk;
- gestão empresarial pesada;
- colaboração empresarial complexa;
- customização ilimitada.

Essas funções podem futuramente existir como módulos, templates, workflows ou extensões sobre a infraestrutura principal.

## 29. Colaboração

A colaboração é secundária para a visão inicial.

[E — Inferido]

A arquitetura poderá posteriormente permitir atribuição, compartilhamento, validação, aprovação e colaboração entre participantes, sem transformar colaboração multiusuário em premissa obrigatória do núcleo inicial sem evidência adicional.

## 30. O que o EXECUTAR não é

O EXECUTAR não deve ser definido primordialmente como:

- lista de tarefas;
- calendário;
- Pomodoro;
- Kanban board;
- Gantt;
- chat;
- planner estático;
- CRM;
- gerenciador genérico de projetos.

Essas interfaces ou mecanismos podem existir dentro do ecossistema, mas não constituem sua proposta fundamental.

## 31. Diferencial estrutural

Ferramentas convencionais frequentemente organizam informação de trabalho. O EXECUTAR pretende organizar **execução**.

[E — Inferido]

Posicionamento comparativo proposto no corpus:

- TickTick → organiza tarefas;
- Linear → organiza entregas;
- monday → organiza processos;
- EXECUTAR → organiza **capacidade → decisão → ação → evidência**.

O diferencial estrutural é: **o usuário não precisa reorganizar continuamente o plano; o sistema preserva a integridade estrutural do plano e recalcula a rota operacional**.

## 32. Core Proposition

**Execution OS adaptativo para trabalhadores solo, com arquitetura orientada à redução de carga executiva operacional.**

[E — Inferido]

## 33. Core Engine

**PLAN → ELIGIBILITY → DISPATCH → EXECUTE → EVIDENCE → LEARN → RECALCULATE**

[E — Inferido]

## 34. Core Experience

A experiência fundamental pode ser reduzida a:

1. informar ou detectar a capacidade/contexto atual;
2. receber uma ação recomendada;
3. executar;
4. concluir segundo DoD;
5. registrar evidência;
6. atualizar progresso;
7. receber a próxima ação.

Na forma mais simples: **“Quanto tempo/capacidade você tem agora?” → “Faça isto agora.” → executar → concluir → próxima ação.**

## 35. Princípios do produto

### P01 — Execução antes de administração
O produto deve reduzir o esforço gasto administrando o próprio sistema.

### P02 — Elegibilidade antes de prioridade
Trabalho impossível de executar agora não deve competir com trabalho executável.

### P03 — Uma recomendação dominante
O sistema deve reduzir escolhas operacionais sempre que houver evidência suficiente para isso.

### P04 — WIP reduzido
A arquitetura deve limitar concorrência cognitiva.

### P05 — Estado persistente
O sistema deve lembrar o estado para que o usuário não precise reconstruí-lo.

### P06 — Plano estável, rota adaptativa
Intercorrências alteram a rota, não necessariamente o destino ou a estrutura.

### P07 — Capacidade real
Planejamento deve considerar disponibilidade e execução observada.

### P08 — Evidência antes de progresso
Conclusão deve possuir condição verificável.

### P09 — Customização limitada por invariantes
Flexibilidade não deve destruir a coerência operacional.

### P10 — Menor superfície necessária
Mostrar somente o necessário para a decisão/ação presente.

### P11 — Externalização de carga executiva
Sempre que tecnicamente apropriado, o sistema deve absorver operações repetitivas de organização e controle.

### P12 — Autonomia preservada
Automação deve auxiliar a execução sem retirar controle fundamental do usuário.

[D/E — Consolidação]

## 36. Invariantes preliminares

Os seguintes invariantes aparecem ou são fortemente sustentados pelo corpus:

- trabalho deve decompor-se até Action;
- Actions devem permanecer rastreáveis a resultados;
- dependências devem ser explícitas;
- uma Action só compete se elegível;
- WIP deve ser limitado;
- capacidade atua como restrição;
- tempo gasto não equivale automaticamente a progresso;
- conclusão depende de DoD/evidência;
- estado deve persistir;
- rota pode ser recalculada;
- plano não deve ser destruído por intercorrência operacional;
- o usuário deve conseguir identificar uma próxima ação dominante;
- customizações não podem quebrar invariantes do motor.

[D/E — Interno + Inferido]

Os valores quantitativos definitivos de ciclo, capacidade, WIP e demais regras deverão ser formalizados em `PROD-003 — Regras Centrais`.

## 37. Resultado esperado

O resultado pretendido não é simplesmente que o usuário possua um plano mais organizado. É que consiga saber o que fazer, iniciar com menor atrito, manter continuidade, reduzir reconstrução de contexto, executar dentro da capacidade existente, responder melhor a interrupções, concluir unidades verificáveis, observar progresso real e avançar resultados sem administrar manualmente toda a lógica subjacente.

[E — Inferido]

## 38. Métricas de sucesso preliminares

As métricas definitivas ainda precisam ser definidas.

[GAP]

Famílias de métricas coerentes com a visão:

- tempo até `BEST_NEXT_ACTION`;
- tempo entre abertura/entrada e início de execução;
- taxa de ações concluídas;
- taxa de retomada após interrupção;
- cycle time;
- throughput;
- aderência à capacidade;
- percentual de trabalho bloqueado;
- tempo em WIP;
- número de mudanças de contexto;
- percentual de conclusões com evidência;
- frequência de replanejamento manual;
- quantidade de decisões operacionais delegadas ao sistema;
- dependência de navegação na aplicação para executar.

[E — Proposto]

## 39. Escopo inicial

### Incluído conceitualmente

- gestão individual do trabalho;
- projetos;
- processos;
- entregáveis;
- tarefas;
- Actions;
- dependências;
- capacidade;
- execução;
- evidências;
- replanejamento;
- automação;
- Copiloto;
- estado/contexto persistente;
- visualização orientada à execução;
- integração analógico-digital.

### Fora do núcleo inicial

- CRM completo;
- Service Desk completo;
- gestão organizacional complexa;
- colaboração enterprise;
- customização irrestrita.

## 40. Premissas ainda não validadas

Não devem ser tratadas como fatos aprovados sem validação adicional:

- dimensão exata do ICP inicial;
- tamanho e características do mercado;
- disposição do usuário para delegar priorização;
- efeito quantitativo do sistema sobre carga cognitiva;
- efeito quantitativo sobre troca de contexto;
- frequência ideal de interação com o aplicativo;
- eficácia do papel/scanner como superfície principal;
- valores ideais de WIP;
- parâmetros ideais dos ciclos;
- fórmula definitiva de capacidade;
- fórmula definitiva de Flow Score;
- fórmula definitiva de Context Score;
- impacto clínico ou terapêutico.

[GAP]

O EXECUTAR deve ser posicionado como sistema de produtividade/execução, não como tratamento médico, salvo eventual evidência e enquadramento regulatório específicos.

## 41. Cadeia de rastreabilidade

**PROD-001 · PRODUCT VISION  
↓  
PROD-002 · PRODUCT STRUCTURE  
↓  
PROD-003 · CORE RULES  
↓  
PROD-004 · STATES  
↓  
PROD-005 · JOURNEYS  
↓  
PROD-006 · CAPABILITY MAP  
↓  
PROD-007 · FUNCTIONAL DATA MODEL  
↓  
PROD-008 · REQUIREMENTS + ACCEPTANCE CRITERIA  
↓  
PROD-009 · PERMISSIONS + TENANCY  
↓  
PROD-010 · DOMAIN EVENTS + CONTRACTS**

Depois:

**WF-03 · AGENTS → agents → skills → tools → prompts → permissions → approvals → memory → evals**

## 42. Formulação curta da visão

**EXECUTAR é um sistema operacional adaptativo de execução para trabalho solo que transforma planos, dependências, contexto e capacidade em uma próxima ação concretamente executável, preservando estado, evidência e continuidade para reduzir a carga operacional necessária para planejar, priorizar, retomar e controlar o trabalho.**

## 43. Formulação curta da promessa

**Defina o resultado. O EXECUTAR organiza a rota e indica o que executar agora.**

## 44. Formulação curta do diferencial

**O EXECUTAR não organiza apenas tarefas. Organiza capacidade → decisão → ação → evidência.**

## 45. Critérios de pré-aprovação

Registrados como aceitos para derivação documental em 2026-09-09:

- [x] definição de Execution OS;
- [x] trabalhador solo como ICP primário;
- [x] neurodivergência/TDAH como foco explícito inicial;
- [x] Action como objeto fundamental;
- [x] hierarquia Outcome → Project/Value Stream → Deliverable → Task → Action → Evidence;
- [x] separação PLAN × ROUTE;
- [x] Best Next Action como mecanismo central;
- [x] capacidade como restrição;
- [x] WIP reduzido / WIP 1:1;
- [x] DoD + Evidence como base de progresso;
- [x] persistência de estado e retomada;
- [x] princípio de acesso mínimo à aplicação;
- [x] integração papel/scanner como parte da visão;
- [x] Copiloto como capability central;
- [x] CRM/Service Desk/enterprise collaboration fora do P0;
- [x] customização limitada por invariantes;
- [x] posicionamento do produto como sistema de produtividade/execução e não como tratamento clínico.

## 46. Decisão de pré-aprovação

**Status: PRE_APPROVED**

Autorizado para registro no repositório e para derivação dos artefatos seguintes. `pre_approved` não significa `implemented`, `tested`, `verified` ou `released`.
