---
id: PRD-STUDIO-001
type: product_requirement_document
status: draft_for_pre_approval
version: 0.9.0
owner: null
project: EXECUTAR
date: 2026-09-12
depends_on:
  - D22-DEC-001
  - D22-DEC-002
  - UI-005
  - SPEC-WORKSPACE-001
feeds:
  - SPEC-STUDIO-001
---
# PRD-STUDIO-001 — Studio / Consultoria

## 1. Problema

O EXECUTAR possui superfícies orientadas à execução, automação e acompanhamento, mas precisa separar formalmente o trabalho de **explorar, diagnosticar, conceber e prototipar** do trabalho já aprovado e decomposto para execução.

Sem essa separação, ideias, hipóteses, protótipos e recomendações podem ser confundidos com requisitos aprovados, tarefas executáveis ou estado operacional real.

## 2. Objetivo

Criar uma área persistente denominada **Studio / Consultoria** para cocriação entre usuário e agente, capaz de transformar uma intenção, briefing, problema, oportunidade ou conjunto de evidências em artefatos progressivamente refinados, mantendo rastreabilidade e um handoff explícito para o Workspace operacional.

O Studio deve permitir trabalhar visualmente e de forma iterativa sem se tornar uma fonte paralela de verdade operacional.

## 3. Job principal

“Quando eu ainda estiver entendendo um problema ou criando uma solução, quero trabalhar com o Copiloto em uma área própria para investigar, comparar alternativas, produzir protótipos e consolidar uma proposta antes de transformá-la em trabalho executável.”

## 4. Usuários e contextos

- usuário individual estruturando uma ideia, produto, projeto ou decisão;
- usuário que solicita consultoria do agente antes de criar um plano operacional;
- operador que precisa transformar evidências em alternativas e recomendações;
- designer/product builder que precisa gerar wireframes, mockups ou protótipos;
- usuário que precisa criar one-pagers, documentos de decisão, apresentações ou outros artefatos de apoio;
- equipes futuras, sujeitas a tenancy, permissões, comentários e regras de colaboração próprias.

## 5. Princípio de produto

O Studio representa a fase de **exploração e criação**.

O Workspace operacional representa a fase de **execução**.

Fluxo canônico:

`Entrada → Contexto → Consultoria → Direções → Artefato → Refinamento → Protótipo → Aprovação → Handoff`

Somente o `Handoff` pode promover ou vincular um resultado do Studio a objetos operacionais canônicos.

## 6. Modelo de área de trabalho

Cada workspace de Studio deve suportar os seguintes conceitos funcionais:

### 6.1 Contexto
- briefing;
- problema;
- objetivo;
- restrições;
- referências;
- arquivos e evidências de entrada;
- critérios conhecidos;
- lacunas e perguntas abertas.

### 6.2 Consultoria
- diálogo estruturado com o agente;
- perguntas de diagnóstico;
- hipóteses;
- recomendações;
- alternativas;
- riscos;
- decisões pendentes;
- registro da origem de cada conclusão relevante.

### 6.3 Canvas / Artefato
Superfície principal para visualizar e refinar a saída produzida. Deve suportar, conforme o tipo de artefato:
- texto;
- blocos estruturados;
- layout visual;
- componentes;
- imagens e referências;
- preview;
- estados ou telas relacionadas;
- anotações e comentários.

### 6.4 Variações
- criar alternativas sem sobrescrever silenciosamente a versão principal;
- nomear e comparar direções;
- promover uma variação para principal explicitamente;
- manter vínculo com a origem e a versão anterior.

### 6.5 Protótipo
- representação navegável ou demonstrável quando o artefato exigir interação;
- estado claramente identificado como `prototype/draft`;
- capacidade de preview sem equivaler a implementação de produção.

### 6.6 Handoff
- promover ou vincular um resultado a Projeto, Value Stream, Entregável, Tarefa, Ação ou outro objeto permitido;
- preparar handoff para código ou integração autorizada quando aplicável;
- preservar `studio_workspace_id`, `artifact_id`, versão, origem e evidências;
- exigir confirmação explícita quando o handoff implicar criação ou mutação operacional.

## 7. Tipos de trabalho P0

O P0 deve suportar pelo menos:
- diagnóstico / consultoria;
- one-pager;
- documento de decisão;
- wireframe;
- mockup;
- exploração visual;
- protótipo interativo;
- especificação conceitual;
- apresentação/deck quando fizer parte da entrega;
- artefato livre estruturado pelo agente.

A lista é extensível e não cria automaticamente novos tipos de objeto no domínio operacional.

## 8. Jornada P0

### Entrada
O usuário inicia por prompt, briefing, arquivo, evidência, referência ou contexto existente do EXECUTAR.

### Contextualização
O agente organiza o que é conhecido, o que é inferido, o que está ausente e o objetivo da sessão.

### Consultoria
O agente conduz diagnóstico e estrutura caminhos possíveis sem tratar hipótese como requisito aprovado.

### Direções
Uma ou mais alternativas podem ser geradas e comparadas.

### Artefato
A direção escolhida gera um artefato editável e persistente.

### Refinamento
Usuário e agente iteram sobre conteúdo, estrutura, layout ou comportamento.

### Protótipo
Quando necessário, o artefato pode ganhar comportamento navegável/demonstrável.

### Aprovação
Uma versão pode ser marcada como candidata a handoff. Isso ainda não significa implementação.

### Handoff
O resultado é explicitamente promovido ou vinculado a uma superfície de execução, código ou integração autorizada.

## 9. Estrutura de navegação funcional

A nomenclatura técnica final será definida na SPEC. Conceitualmente, a área deve possuir:
- **Studio Home** — workspaces recentes, modelos e novos trabalhos;
- **Workspace** — contexto, consultoria e artefatos de um trabalho;
- **Canvas / Preview** — superfície principal do artefato;
- **Variações / Versões** — histórico e comparação;
- **Handoff** — preparação e confirmação da promoção para execução.

Uma rota como `/studio` é `PROPOSED`, não decisão técnica final deste PRD.

## 10. Design System e experiência

O Studio deve consumir `UI-005` e permanecer subordinado a `D22-DEC-001`.

Requisitos de experiência:
- não criar um design system paralelo;
- reutilizar tokens e componentes canônicos;
- manter responsividade, safe areas, acessibilidade, texto escalável e redução de movimento;
- permitir uma superfície de canvas própria sem romper os contratos globais de navegação;
- diferenciar visualmente `rascunho`, `variação`, `candidato aprovado`, `handoff preparado` e `handoff concluído`;
- preservar os modos e padrões de navegação definidos para o aplicativo quando aplicáveis.

## 11. Benchmark público

Referência funcional: `https://claude.com/product/design`.

Classificação: `C_PUBLICADO`.
Consulta: 2026-09-12.

Capacidades observadas e utilizadas apenas como benchmark:
- geração de protótipos interativos e compartilháveis;
- wireframes e mockups;
- exploração de múltiplas direções;
- criação de decks, materiais e documentos;
- geração a partir de design systems, repositórios ou codebases reais;
- refinamento direto de texto e elementos do artefato;
- controles visuais de layout e aparência;
- handoff entre ambiente de design e ambiente de código;
- exportação para formatos e ferramentas externas.

O benchmark não autoriza cópia de marca, interface ou implementação de terceiros.

## 12. Estados

### Workspace de Studio
`DRAFT → ACTIVE → READY_FOR_REVIEW → APPROVED_FOR_HANDOFF → HANDED_OFF | ARCHIVED`

### Artefato
`DRAFT → ITERATING → CANDIDATE → APPROVED → HANDED_OFF | SUPERSEDED | ARCHIVED`

### Protótipo
`DRAFT → PREVIEWABLE → REVIEWED → APPROVED_FOR_HANDOFF`

Esses estados são estados do Studio e não equivalem a `READY`, `DOING`, `VERIFY`, `DONE`, `tested`, `verified` ou `released` do domínio operacional.

## 13. Requisitos funcionais

- `REQ-STUDIO-001`: criar e persistir um workspace de Studio com contexto próprio.
- `REQ-STUDIO-002`: registrar entradas, arquivos, referências e evidências ligadas ao workspace.
- `REQ-STUDIO-003`: manter diálogo de consultoria associado ao mesmo contexto e artefatos.
- `REQ-STUDIO-004`: criar artefatos editáveis sem promover seu conteúdo automaticamente a requisitos ou tarefas.
- `REQ-STUDIO-005`: suportar múltiplas variações com versionamento e origem rastreável.
- `REQ-STUDIO-006`: permitir comparar variações sem sobrescrever silenciosamente a versão principal.
- `REQ-STUDIO-007`: suportar preview/protótipo quando o tipo de artefato permitir.
- `REQ-STUDIO-008`: todo protótipo executável deve permanecer identificado como `prototype/draft` até o fluxo de implementação e verificação correspondente.
- `REQ-STUDIO-009`: consumir o Design System canônico quando a integração técnica estiver disponível.
- `REQ-STUDIO-010`: o agente deve distinguir evidência, observação, inferência, proposta e decisão.
- `REQ-STUDIO-011`: nenhuma alteração no Studio deve mutar estado operacional sem handoff explícito e autorização aplicável.
- `REQ-STUDIO-012`: o handoff deve preservar origem, IDs, versão e evidências do artefato.
- `REQ-STUDIO-013`: handoff para Projeto/Entregável/Tarefa/Ação deve usar contratos canônicos do domínio, não duplicar estado.
- `REQ-STUDIO-014`: handoff para código ou ferramenta externa deve registrar destino e resultado quando a integração fornecer recibo/identificador.
- `REQ-STUDIO-015`: falha de exportação ou integração externa não pode promover estado operacional.
- `REQ-STUDIO-016`: o usuário deve poder arquivar um workspace sem apagar silenciosamente seus vínculos e evidências.
- `REQ-STUDIO-017`: o sistema deve deixar claro qual versão do artefato está sendo visualizada, comparada ou promovida.
- `REQ-STUDIO-018`: permissões de colaboração futuras devem respeitar tenancy e authority boundaries.

## 14. Handoff para execução

O contrato conceitual mínimo deve transportar:

```text
studio_workspace_id
artifact_id
artifact_version
source_refs[]
evidence_refs[]
selected_direction
approval_state
handoff_target_type
handoff_target_id? 
requested_operation
requested_by
timestamp
```

Regras:
- se o alvo já existe, o Studio deve vincular ou propor alteração conforme policy;
- se o alvo não existe, a criação deve ser explícita;
- nenhuma conclusão do Studio pode marcar automaticamente trabalho como implementado, testado, verificado ou lançado;
- o artefato original permanece consultável após o handoff.

## 15. Integrações P0/P1

### P0
- contexto interno do EXECUTAR;
- arquivos suportados pelo produto;
- Design System canônico;
- Copiloto;
- handoff para objetos do Workspace;
- exportação básica de artefatos suportados.

### P1 / dependente de contrato
- GitHub / repositórios;
- Vercel / preview ou publicação governada;
- Google Drive/Docs/Slides;
- outras ferramentas de design ou colaboração;
- conectores externos adicionais.

Conexão disponível não implica autoridade para mutação ou publicação.

## 16. Critérios de aceite P0

- usuário consegue criar um workspace de Studio sem criar automaticamente um Projeto operacional;
- contexto e briefing permanecem disponíveis ao reabrir o workspace;
- agente consegue gerar pelo menos um artefato editável com origem rastreável;
- usuário consegue gerar uma segunda direção sem perder a primeira;
- versão principal e variações são distinguíveis;
- um wireframe/mockup/protótipo pode ser visualizado em preview;
- um artefato pode ser refinado sem alterar objetos operacionais existentes;
- handoff exige ação explícita e mostra destino e operação proposta;
- handoff concluído registra vínculo entre artefato e objeto operacional criado/afetado;
- cancelar ou falhar o handoff mantém o estado operacional anterior;
- a UI usa o Design System do EXECUTAR ou registra explicitamente a indisponibilidade da integração;
- nenhum protótipo é apresentado como `implemented`, `tested`, `verified` ou `released` sem evidência correspondente;
- acessibilidade e comportamento responsivo seguem os contratos globais do aplicativo.

## 17. Fora do escopo inicial

- publicação irrestrita em produção a partir do canvas;
- mutação silenciosa de tarefas/projetos;
- geração autônoma de requisitos aprovados sem gate humano/policy;
- edição simultânea multiusuário avançada;
- marketplace público de templates;
- substituição de ferramentas profissionais de design em toda sua profundidade;
- tratar preview como release;
- copiar UX, marca ou componentes proprietários do benchmark.

## 18. Métricas

- tempo da entrada até primeiro artefato útil;
- percentual de workspaces que chegam a `APPROVED_FOR_HANDOFF`;
- percentual de handoffs concluídos sem retrabalho estrutural;
- quantidade média de variações antes da direção selecionada;
- taxa de reabertura/refinamento de artefatos;
- incidência de handoff bloqueado por falta de evidência ou autorização;
- taxa de protótipos promovidos posteriormente para implementação;
- divergências detectadas entre artefato aprovado e implementação final.

## 19. Evidência e classificação

- `D22-DEC-002` — `D_INTERNO`, decisão aceita do ecossistema.
- `D22-DEC-001` — `D_INTERNO`, padrão canônico de interface.
- `UI-005` — `D_INTERNO`, contrato de consumo do Design System.
- `SPEC-WORKSPACE-001` — `D_INTERNO`, fronteiras do Workspace operacional.
- `https://claude.com/product/design` — `C_PUBLICADO`, benchmark externo observado em 2026-09-12.
- Estrutura específica de entidades, rotas técnicas e persistência ainda não definida — `GAP` para `SPEC-STUDIO-001`.

## 20. Estado documental

- decisão de produto: **ACEITA** em `D22-DEC-002`;
- PRD: **DRAFT_FOR_PRE_APPROVAL**;
- SPEC técnica: **NÃO CRIADA**;
- protótipo canônico: **NÃO CRIADO**;
- implementação: **NÃO CONFIRMADA**;
- testes: **NÃO CONFIRMADOS**;
- release: **NÃO CONFIRMADO**.
