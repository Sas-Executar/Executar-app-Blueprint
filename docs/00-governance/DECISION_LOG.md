---
id: GOV-004
type: decision_log
status: active
version: 1.7.0
owner: null
---
# Decision Log

| Date | Decision ID | Status | Summary | ADR | Owner |
|---|---|---|---|---|---|
| 2026-09-09 | DEC-PROD-001 | accepted | Registra `PROD-001 — EXECUTAR — Visão do Produto` como `pre_approved` e autorizado para derivação documental. A decisão não implica implementação, teste, verificação ou release. | n/a | — |
| 2026-09-09 | DEC-AGENT-001 | accepted | Registra os pacotes `executar-mapa-os` e `copiloto-executar`, seus contratos declarados e modelos de entregáveis com placeholders. `registered` não implica aprovação para produção, deploy ou vínculo com sistemas externos. | n/a | — |
| 2026-09-09 | DEC-ROUTINES-001 | accepted | Adota `Routine` como objeto agentic configurável para automação/autogestão governada de tarefas e geração de Status Reports; App Reports é persistência canônica e Email/WhatsApp são canais derivados. | ADR-ROUTINES-001 | — |
| 2026-09-09 | DEC-MAPA-002 | accepted | Registra `executar-mapa-os v1.1.0` como gerador do entregável analógico de gestão de tarefas e destaca internamente dois prompts, o template Prisma A4 V4 e três workflows. O exemplo preenchido permanece `example_only`. | n/a | — |
| 2026-09-09 | DEC-SCANNER-001 | accepted | Separa Scanner do Mapa-OS: Mapa-OS gera a superfície física; Scanner reconhece símbolos e produz `VisualSymbolId`; `CommandDispatcher` resolve ações de domínio. O Scanner possui PRD, ADR, SPEC e Action Contract próprios. | ADR-SCANNER-001 | — |
| 2026-09-09 | DEC-OMNI-001 | accepted | Aprova a direção omnicanal do EXECUTAR: `PROD-FLOW-001`, `PRD-OMNI-001`, `AGENT-FLOW-001` e `SPEC-WORKSPACE-001` são promovidos a `pre_approved`; `ADR-OMNI-001` é aceito. A decisão estabelece um único estado canônico com App, MCP, WhatsApp, Email, Copiloto e Mapa-OS + Scanner como superfícies/adapters. Não declara essas integrações como implementadas, testadas, verificadas ou released. | ADR-OMNI-001 | — |
| 2026-09-09 | DEC-DS-001 | accepted | Registra `UI-005 — EXECUTAR Design System Contract` como referência externa `pre_approved`. O repositório declarado `Sas-Executar/Desyng-System-ecossitema` permanece a autoridade pretendida; o extract local preserva package/tokens como `CORPUS_DIRECT` e o showroom reconstruído como `CORPUS_DERIVED`. O `final_bundle.html` original permanece `GAP`. | n/a | — |
| 2026-09-09 | DEC-BUS-001 | accepted | Autoriza `BUS-MODEL-001`, `PRICING-001` e `UNIT-ECON-001` como baseline `pre_approved` para modelagem e testes no Brasil. Trial 14 dias, Solo R$49,90, Pro R$89,90 e Business Workspace R$499/5 seats são preços `PROPOSED`, não publicados. Unit economics deve usar COGS mensurável, franquias de IA/WhatsApp e tributação por faixa; o cenário de 5.000 contas ultrapassa o limite modelado do Simples e permanece `GAP` tributário até definição de regime pós-Simples. | n/a | — |
