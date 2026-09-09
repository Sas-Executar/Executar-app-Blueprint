---
id: PRD-ROUTINES-001
type: product_requirement_document
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
date: 2026-09-09
depends_on:
  - PROD-001
  - ADR-ROUTINES-001
feeds:
  - SPEC-ROUTINES-001
---
# PRD-ROUTINES-001 — Modo Rotinas

## 1. Problema
O usuário não deve precisar abrir o aplicativo, revisar manualmente todas as tarefas e reconstruir o estado do projeto apenas para saber o que mudou, o que está elegível e o que deve acontecer a seguir.

## 2. Objetivo
Permitir que um agente configure e opere rotinas recorrentes ou orientadas a eventos para:
- ler o estado do trabalho;
- reconciliar fontes autorizadas;
- autogerenciar tarefas dentro de limites de autoridade;
- calcular progresso e elegibilidade;
- atualizar a próxima ação/projeções;
- gerar Status Reports;
- armazenar o report no app;
- opcionalmente entregar o mesmo report por e-mail e/ou WhatsApp.

## 3. Job principal
“Quando uma rotina ocorrer, quero que o EXECUTAR atualize a leitura do meu trabalho, faça apenas as mudanças automáticas autorizadas e me entregue um resumo confiável sem eu precisar administrar o sistema manualmente.”

## 4. Usuários
- trabalhador solo;
- operador de múltiplos projetos;
- usuário que depende do Copiloto EXECUTAR para retomada e priorização;
- futuros contextos multiusuário, sujeitos a tenancy e permissões próprias.

## 5. Conceito de Modo Rotinas
`Modo Rotinas` é a superfície de automação do EXECUTAR. O usuário descreve a rotina em linguagem natural; o agente converte essa intenção em uma `RoutineConfig` estruturada, apresenta os parâmetros relevantes e, após autorização, a rotina pode ser habilitada.

Exemplos de intenção, sempre parametrizados:
- “Todo {{DIA_OU_CADENCIA}} às {{HORARIO}}, atualize {{ESCOPO}} e gere meu status.”
- “Quando {{EVENTO}}, recalcule a próxima ação e publique em Reports.”
- “Envie o fechamento para {{CANAIS_AUTORIZADOS}}.”

## 6. Escopo P0
### Configuração
- criar rotina;
- editar;
- pausar;
- reativar;
- executar agora;
- excluir/desabilitar;
- escolher timezone;
- escolher trigger/cadência;
- definir projeto/escopo;
- selecionar fontes;
- definir canais;
- definir destinatários/autorização por canal;
- definir política de retry.

### Execução
- ler fontes;
- validar disponibilidade das fontes obrigatórias;
- reconciliar estado;
- calcular indicadores derivados;
- validar dependências;
- determinar elegibilidade;
- respeitar WIP;
- aplicar somente mutações autorizadas;
- gerar report;
- persistir o report;
- entregar em canais configurados;
- registrar recibo e log.

### Reports
Todo run deve poder produzir um Status Report canônico com:
- projeto/escopo;
- data/hora e run id;
- status da rotina;
- progresso sustentado;
- profundidade projeto/ciclo/hoje/tarefa/ação, quando disponível;
- ontem/hoje/amanhã ou equivalente temporal;
- `AGORA` / próxima ação;
- contexto;
- problema;
- processo;
- progresso;
- próximos passos;
- risco;
- prevenção;
- entrega/resultado;
- foco, estado e origem;
- evidências;
- bloqueios/lacunas;
- status de entrega por canal.

## 7. Canais de entrega
### App Reports
- sempre suportado no P0;
- report persistido e consultável por projeto, rotina e data;
- fonte visual canônica para histórico de runs.

### Email
- opcional por rotina;
- HTML self-contained + fallback plain text;
- assunto, destinatários e template parametrizados;
- sucesso exige receipt/message id do provedor.

### WhatsApp
- opcional por rotina;
- resumo curto adequado ao canal;
- pode incluir link para o report completo no app;
- envio exige conexão/provider e destinatário autorizados;
- sucesso exige receipt/message id quando o provider disponibilizar.

## 8. Autogestão de tarefas
### Permitido automaticamente no baseline
- sincronizar estado de fonte autoridade para espelhos;
- promover `BACKLOG_VALIDATED → READY` quando dependências/regras declaradas estiverem satisfeitas;
- recalcular próxima ação;
- atualizar projeções de execução;
- registrar report/log.

### Exige política/autorização específica
- criar/deletar tarefas;
- alterar prazo original;
- alterar owner;
- reordenar dependências;
- iniciar trabalho (`DOING`);
- enviar para revisão (`VERIFY`);
- concluir (`DONE`);
- marcar como testado/verificado/publicado.

Na ausência dessa política, tais ações ficam bloqueadas.

## 9. Estados da rotina
`DRAFT → ENABLED ↔ PAUSED → DISABLED`

Execução:
`SCHEDULED → RUNNING → SUCCESS | PARTIAL | BLOCKED | FAILED`

Entrega por canal:
`PENDING → SENT → DELIVERED | FAILED`

## 10. Requisitos funcionais
- `REQ-ROUT-001`: compilar intenção em RoutineConfig validável.
- `REQ-ROUT-002`: toda rotina deve declarar timezone e trigger.
- `REQ-ROUT-003`: toda fonte deve declarar papel de autoridade ou espelho.
- `REQ-ROUT-004`: nenhum run pode inventar estado ausente.
- `REQ-ROUT-005`: dependências devem ser verificadas antes de mutação de elegibilidade.
- `REQ-ROUT-006`: mutação automática deve possuir `authority_rule_id`.
- `REQ-ROUT-007`: report canônico deve ser persistido antes/independente dos canais externos.
- `REQ-ROUT-008`: falha em e-mail/WhatsApp não deve reverter ou promover tarefas.
- `REQ-ROUT-009`: cada envio deve armazenar resultado e receipt id quando existente.
- `REQ-ROUT-010`: retries de envio devem ser idempotentes.
- `REQ-ROUT-011`: usuário deve poder pausar/desabilitar rotina.
- `REQ-ROUT-012`: app deve mostrar histórico de runs e status de entrega.
- `REQ-ROUT-013`: report não pode usar valores de exemplo como dados reais.
- `REQ-ROUT-014`: conflitos/empates sem regra devem gerar `EXIGE_HUMANO`/`BLOCKED`.

## 11. Critérios de aceite P0
- uma rotina pode ser configurada com placeholders e habilitada;
- uma execução gera `run_id` único;
- leitura com fonte obrigatória indisponível resulta em `BLOCKED` sem mutação indevida;
- progressos são derivados de numerador/denominador, não inventados;
- exatamente uma próxima ação é emitida ou há razão explícita para ausência;
- Status Report aparece em Reports;
- canal externo habilitado recebe a mesma síntese canônica adaptada ao formato;
- falha de canal é registrada sem corromper o run;
- nenhuma transição proibida é feita automaticamente.

## 12. Fora do escopo inicial
- criação autônoma irrestrita de projetos;
- conclusão automática sem evidência;
- envio para destinatários não autorizados;
- canais sem provider/integração aprovada;
- decisões arbitrárias em empate.

## 13. Métricas
- taxa de runs `SUCCESS`;
- taxa de runs bloqueados por fonte;
- taxa de entrega por canal;
- tempo entre trigger e report disponível;
- número de mutações automáticas por regra;
- número de escaladas `EXIGE_HUMANO`;
- redução de replanejamento manual.
