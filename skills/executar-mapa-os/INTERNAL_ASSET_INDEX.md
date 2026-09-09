---
id: SKILL-MAPA-OS-ASSETS-001
type: internal_asset_index
status: registered
version: 1.1.0
owner: null
skill: executar-mapa-os
---
# EXECUTAR Mapa-OS · Internal Asset Index

Este arquivo destaca os ativos internos que fazem parte do pacote `executar-mapa-os v1.1.0` e define sua autoridade.

## Product role

O **Mapa-OS** é o entregável operacional gerado pelo agente para gestão das tarefas em uma superfície analógica/imprimível. Ele materializa a mesma fonte canônica do projeto em uma projeção física de execução; não cria uma segunda fonte de verdade.

O Scanner não pertence internamente à skill Mapa-OS. O Scanner é uma capability separada que pode reconhecer símbolos impressos no Mapa-OS e converter esses símbolos em comandos do aplicativo por meio de seu próprio Action Resolver.

## Two prompt models

| ID | Ativo | Path | Papel | Autoridade |
|---|---|---|---|---|
| PROMPT-MAPA-001 | Prompt Mestre Prisma | `references/prompts/01-prompt-mestre-prisma.md` | roteiro reutilizável de coleta e geração | normativo para ativação `01` |
| PROMPT-MAPA-002 | Exemplo Preenchido Prisma | `references/prompts/02-exemplo-preenchido-prisma.md` | demonstração preenchida | ilustrativo; nunca fonte de verdade de projeto real |

## Internal template

| ID | Ativo | Path | Papel |
|---|---|---|---|
| TEMPLATE-MAPA-001 | Status Report Prisma A4 V4 | `assets/templates/status-report-prisma-a4-v4.html` | template físico do Mapa-OS semanal, A4 retrato, três faces de 99 mm, namespaces canônicos de placeholders |

## Workflows

| ID | Workflow | Path | Saída |
|---|---|---|---|
| WF-MAPA-001 | Construção canônica do Mapa-OS | `references/workflows/01-build-mapa-os.md` | objeto Mapa-OS validável |
| WF-MAPA-002 | Prisma semanal | `references/workflows/02-prisma-7d.md` | payload + placeholders + HTML A4 |
| WF-MAPA-003 | Teste ilustrativo | `references/workflows/03-example-test.md` | demonstração isolada, sem contaminar dados reais |

## Reading order

`SKILL.md → INTERNAL_ASSET_INDEX.md → prompt selecionado → workflow correspondente → schemas → template → validações`.

## Boundary

`Mapa-OS generation ≠ Scanner recognition ≠ task mutation`.

- Mapa-OS gera a projeção analógica.
- Scanner reconhece um símbolo físico.
- Action Resolver decide/executa o comando de domínio.
- A mutação de tarefa pertence ao contrato do Scanner/domínio, não ao template físico.
