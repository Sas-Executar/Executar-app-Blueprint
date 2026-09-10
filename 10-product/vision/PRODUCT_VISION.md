# PRODUCT_VISION

Status: `PRE_APPROVED_FROM_PRIMARY_SOURCE`
Version: `0.1.0`
Primary source: `SRC-PRODUCT-MANIFESTO-001`
Secondary source: `SRC-PRODUCT-BLUEPRINT-001`

## 1. Categoria do produto

**CORPUS_DIRECT / CORPUS_DERIVED**

O EXECUTAR é um **Sistema Operacional de Execução Adaptativa** orientado à transformação de contexto e capacidade em execução comprovável.

Formulação simples:

> Um sistema que organiza o trabalho e decide com o usuário o que executar agora, preservando contexto, capacidade, dependências, estado e evidência.

O produto não deve ser reduzido a task manager, calendário, kanban, chatbot, CRM ou repositório documental. Pode incorporar capacidades dessas categorias, mas sua unidade de valor é outra:

`capacidade → decisão → ação → evidência`

## 2. Problema central

A execução de trabalho transfere ao operador uma carga recorrente de planejar, organizar, priorizar, lembrar, acompanhar, estimar, iniciar, alternar, monitorar, corrigir, replanejar e concluir.

O EXECUTAR existe para **transferir carga executiva evitável do operador para o sistema**, preservando a decisão legítima e a autoridade do usuário.

## 3. Público inicial

**CORPUS_DIRECT + CORPUS_DERIVED**

Prioridade inicial: trabalhador/profissional solo que precisa executar trabalho complexo, projetos, processos e tarefas sem sustentar continuamente o sistema operacional do trabalho na própria memória.

A arquitetura considera dificuldades executivas que podem afetar a realização do trabalho, sem presumir diagnóstico, universalidade ou causalidade clínica.

`GAP-ICP-001`: segmentação comercial detalhada, atributos firmográficos/comportamentais e critérios de exclusão ainda exigem documento ICP próprio.

## 4. Promessa central

O EXECUTAR busca reduzir:

- carga cognitiva evitável;
- fadiga decisória;
- dependência de memória de trabalho;
- necessidade constante de planejar e priorizar;
- troca de contexto;
- fragmentação entre superfícies;
- esforço de retomada após interrupção;
- tempo gasto administrando o próprio sistema.

## 5. Quatro operações

### ENTENDER
Transformar entradas dispersas em contexto operacional: objetivo, problema, entregáveis, restrições, dependências, capacidade, estado, evidências, bloqueios e trabalho realizado.

### ESTRUTURAR
Converter contexto em estrutura executável:

`Projeto → Value Stream → Entregável → Tarefa → Ação → Evidência`

Inclui decomposição, sequenciamento, dependências, estados, capacidade, caminho crítico, agrupamento semântico e preparação da próxima ação.

### EXECUTAR
Reduzir escolhas, telas, alternâncias e decisões operacionais durante a ação. A unidade fundamental é a **próxima ação executável**.

### EMITIR
Transformar execução em estado, evidência, progresso, histórico, Status Report, Mapa-OS, indicadores, próximos passos e insumos para replanejamento.

## 6. Core Engine

**CORPUS_DERIVED do blueprint + manifesto**

`Understand → Structure → Plan → Eligibility → Dispatch → Execute → Evidence → Learn/Replan`

A formulação `Plan → Eligibility → Dispatch → Execute → Evidence → Learn` aparece no blueprint e é expandida aqui apenas para alinhar às quatro operações do manifesto.

## 7. Princípios de produto

1. Estado persistente: o sistema lembra onde o trabalho parou.
2. Menos decisões operacionais: regras seguras devem reduzir escolhas repetitivas.
3. WIP 1:1: uma ação ativa possui precedência cognitiva clara.
4. Planejamento por capacidade: o sistema considera quanto trabalho cabe.
5. Dependências importam: trabalho bloqueado não deve competir como executável.
6. Replanejamento contínuo: mudanças de realidade não exigem reconstrução integral.
7. Agrupamento semântico: reduzir custo de transição entre contextos.
8. Continuidade analógico-digital: papel pode ser superfície de ação; o digital preserva estado e lógica.
9. Evidência nasce da execução: governança não deve depender de reconstrução manual posterior.
10. Automação reduz carga sem reduzir autonomia.
11. A interface aparece quando necessária e desaparece quando não é necessária.
12. Personalização existe quando altera execução, não como valor por si só.

## 8. Diferenciais proprietários registrados

- Mapa-OS como representação do estado operacional;
- Scanner como ponte físico-digital;
- Copiloto como camada operacional;
- execução orientada por capacidade;
- próxima ação executável;
- WIP 1:1;
- evidência integrada ao fluxo;
- continuidade omnicanal sobre estado canônico único.

## 9. Métrica de valor

O sucesso não é maximizar sessões ou tempo de tela. Indicadores coerentes incluem:

- tempo entre intenção e início;
- decisões operacionais exigidas;
- alternância de contexto;
- taxa de ações concluídas;
- retomada após interrupção;
- volume de trabalho bloqueado;
- aderência capacidade planejada × realizada;
- replanejamentos manuais;
- tempo administrando o sistema;
- evidências produzidas automaticamente;
- entregáveis concluídos.

## 10. Out of scope do núcleo inicial

**CORPUS_DERIVED do blueprint**

Não tratar como core inicial, salvo decisão posterior:

- CRM completo;
- Service Desk;
- colaboração empresarial pesada;
- customização ilimitada;
- Marketplace como dependência do core execution engine.

## 11. Gaps ainda abertos

- `GAP-ICP-001` — ICP detalhado.
- `GAP-JTBD-001` — JTBD canônico por segmento.
- `GAP-VALUE-001` — value proposition comercial por plano/segmento.
- `GAP-NFR-001` — requisitos não funcionais consolidados do produto.

Esses gaps não impedem a canonicalização do Core Domain, mas impedem declarar o WF-02 inteiro como `READY`.