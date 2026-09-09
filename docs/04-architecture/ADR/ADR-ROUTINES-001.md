---
id: ADR-ROUTINES-001
type: architecture_decision_record
status: accepted
version: 1.0.0
owner: null
project: EXECUTAR
date: 2026-09-09
relates_to:
  - PROD-001
  - PRD-ROUTINES-001
  - SPEC-ROUTINES-001
  - SKILL-COP-001
  - SKILL-MAPA-OS-001
---
# ADR-ROUTINES-001 — Rotinas agentic para automação e autogestão de tarefas

## Contexto
O EXECUTAR precisa executar rotinas configuráveis sem exigir presença contínua do usuário. As rotinas devem ler fontes autorizadas, reconciliar estado, calcular elegibilidade e progresso, selecionar a próxima ação quando determinístico, registrar resultados e emitir Status Reports.

O corpus operacional existente estabelece WIP=1, dependências como fonte de elegibilidade, distinção entre plano e estado e promoção de estado somente quando sustentada por regra/evidência. Também existe um contrato visual de Status Report e um fluxo desacompanhado de leitura → validação → sincronização → cálculo → registro → emissão → validação de entrega.

## Decisão
Adotar `Routine` como objeto configurável pelo agente e autorizado pelo usuário.

Uma rotina é compilada pelo agente a partir de linguagem natural para um contrato estruturado contendo:
- `routine_id`;
- nome e descrição;
- projeto/escopo;
- trigger e schedule;
- timezone;
- fontes e autoridade de cada fonte;
- política de estado;
- política de elegibilidade/priorização;
- ações automáticas permitidas;
- ações proibidas ou que exigem humano;
- template de relatório;
- canais de entrega;
- política de retry/falha;
- auditoria.

## Arquitetura

```text
USER INTENT
  → AGENT CONFIGURATOR
  → ROUTINE CONFIG
  → SCHEDULER / EVENT TRIGGER
  → SOURCE READERS
  → STATE RECONCILER
  → ELIGIBILITY + WIP ENGINE
  → AUTHORITY GATE
  → ALLOWED TASK MUTATIONS
  → STATUS REPORT BUILDER
  → REPORT STORE
  → DELIVERY ADAPTERS
      ├── APP_REPORTS
      ├── EMAIL
      └── WHATSAPP
  → DELIVERY RECEIPT + AUDIT LOG
```

## Separação canônica
`RoutineRun` e `StatusReport` são canônicos. App, e-mail e WhatsApp são projeções/canais de entrega do mesmo report; um canal não cria estado concorrente.

Falha de canal altera apenas `delivery_status`. Não deve alterar tarefa, progresso, evidência ou conteúdo do report.

## Autoridade de autogestão
A rotina pode automaticamente:
- ler fontes autorizadas;
- sincronizar espelhos a partir da fonte de estado declarada;
- calcular progresso derivado;
- validar dependências;
- calcular elegibilidade;
- selecionar uma única próxima ação quando a precedência for determinística;
- promover somente transições explicitamente autorizadas e de baixo risco, por exemplo `BACKLOG_VALIDATED → READY` quando todas as condições forem verificadas;
- atualizar projeções como `Agora` e `Reports`;
- gerar e distribuir Status Reports;
- registrar logs e recibos.

Por padrão, a rotina NÃO pode promover automaticamente itens para `DOING`, `VERIFY`, `DONE`, `verified`, `published` ou equivalentes quando o contrato exigir ação humana ou evidência. Essas promoções só podem ocorrer se uma política futura específica for aprovada e possuir evidência/autoridade explícitas.

## Canais
- `APP_REPORTS`: persistência e renderização na área Reports do próprio app.
- `EMAIL`: envio HTML + fallback texto para destinatários autorizados.
- `WHATSAPP`: envio de resumo compacto e, quando suportado, link/artefato do report para destinatários autorizados.

Os endpoints, destinatários, IDs e credenciais nunca são defaults de template; são parâmetros seguros da configuração da rotina.

## Falha segura
Se uma fonte obrigatória não puder ser lida, se houver conflito de autoridade, dependência não resolvida ou empate sem regra de precedência:
- não inventar estado;
- não realizar mutações de tarefa;
- marcar a execução como `BLOCKED` ou `PARTIAL`;
- registrar causa;
- gerar alerta conforme canais configurados, quando permitido.

## Entrega e confirmação
Uma entrega externa só recebe `sent/delivered` quando o adaptador retornar recibo/ID de sucesso. Falha de entrega deve ser registrada e pode executar retry conforme política configurada.

## Consequências
### Positivas
- autogestão determinística sem criar metodologia paralela;
- um report canônico distribuído em múltiplos canais;
- redução de decisões operacionais repetitivas;
- rastreabilidade de cada execução e mutação.

### Trade-offs
- exige matriz de autoridade por rotina;
- exige adapters de canal e gestão de credenciais;
- exige idempotência e deduplicação de runs/envios;
- exige auditoria de mutações agentic.

## Invariantes
1. passagem do tempo não promove estado;
2. dependências governam elegibilidade;
3. WIP=1 permanece regra padrão do modo EXECUTAR;
4. “feito” não substitui evidência;
5. um report não é fonte de verdade do estado;
6. exemplos não viram dados padrão;
7. canais não alteram o conteúdo canônico do report;
8. toda mutação automática deve indicar a regra que a autorizou.
