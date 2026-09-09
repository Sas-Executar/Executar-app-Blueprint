---
name: executar-mapa-os
source_version: 1.1.0
description: Transforme documentos, planos, cronogramas, status e evidências do ecossistema EXECUTAR em um Mapa-OS operacional rastreável e em seu entregável analógico/imprimível, com posição canônica, horizontes Agora/Próximo/Depois, próxima ação elegível, evidências e projeção Prisma A4 opcional. Para começar sem jargão, aceite 00, 01 e 02, seus comandos verbais e pedidos equivalentes em linguagem natural. Não use para promover estados sem evidência nem para substituir a fonte canônica do projeto.
---

# EXECUTAR Mapa-OS

Converta material de projeto em uma leitura operacional única e rastreável. A saída deve responder: onde o projeto está, o que está ativo, o que bloqueia, qual evidência existe e qual é a única próxima ação elegível.

## Papel do produto

O **Mapa-OS é o entregável gerado pelo agente para gestão analógica das tarefas**. A projeção física/imprimível materializa a fonte digital canônica, mas não cria um segundo estado do projeto.

O Scanner é uma capability externa à skill: ele pode reconhecer símbolos físicos presentes no Mapa-OS e encaminhá-los ao Action Resolver. `Mapa-OS ≠ Scanner ≠ mutação de tarefa`.

## Ativos internos destacados

Leia `INTERNAL_ASSET_INDEX.md` como índice obrigatório dos ativos internos.

### Dois prompts oficiais
1. `references/prompts/01-prompt-mestre-prisma.md` — prompt mestre reutilizável; ativação `01` / `/criar-mapa-semanal`.
2. `references/prompts/02-exemplo-preenchido-prisma.md` — exemplo preenchido exclusivamente ilustrativo; ativação `02` / `/testar-mapa-prisma`.

### Template oficial
- `assets/templates/status-report-prisma-a4-v4.html` — Prisma A4 V4, 210 × 297 mm, três faces de 99 mm e 100 placeholders canônicos.

### Workflows internos
- `references/workflows/01-build-mapa-os.md`
- `references/workflows/02-prisma-7d.md`
- `references/workflows/03-example-test.md`

## Ativação simples para usuários leigos

- 00, `/ajuda-mapa` ou frases equivalentes exibem o menu curto.
- 01, `/criar-mapa-semanal` ou equivalente inicia o Prompt Mestre Prisma.
- 02, `/testar-mapa-prisma` ou equivalente inicia o Exemplo Preenchido, sempre identificado como ilustrativo.

IDs numéricos só ativam este roteador quando a mensagem for exatamente 00, 01 ou 02, ou vier com prefixo explícito `Mapa`.

## Antes de operar

Leia sempre `INTERNAL_ASSET_INDEX.md`, `references/architecture-executar.md` e `references/mapa-os-contract.md`. Leia `references/projections.md` quando emitir projeção visual/imprimível.

## Entradas

Aceite arquivos, texto no chat ou objeto de schema. Extraia apenas conteúdo sustentado pelas fontes. Classifique cada insumo como norma, decisão, estado, evidência, plano, template, exemplo ou conteúdo ilustrativo.

Se faltar informação:
- continue nas partes independentes;
- use `NAO_DETERMINADO` para lacunas não bloqueantes;
- use `BLOCKED` apenas quando a lacuna impedir uma saída obrigatória;
- pergunte somente o mínimo que destrava a operação.

## Fluxo

1. Inventarie fontes e preserve IDs, nomes, versões e datas.
2. Extraia `Projeto → Entrega/Dia Lógico → Fluxo → Ação`.
3. Classifique comportamento como `DETERMINISTICO`, `INTERPRETATIVO`, `EXIGE_HUMANO` ou `NAO_DETERMINADO`.
4. Preserve dependências, critérios, gates, evidências, prazos originais e previsões atuais.
5. Reconcilie conflitos somente com autoridade explícita.
6. Calcule derivações determinísticas sustentadas.
7. Determine posição operacional e aplique WIP=1.
8. Selecione `next_action` apenas entre ações elegíveis e não bloqueadas.
9. Organize Agora/Próximo/Depois sem criar objetos novos.
10. Valide a saída.
11. Emita a resposta documental e os artefatos solicitados.

## Invariantes

- Posição é estado operacional.
- Dia Lógico é entrega; não é data.
- Passagem do tempo não altera estado sozinha.
- WIP é `1 entrega → 1 fluxo → 1 ação`.
- Dependências governam elegibilidade.
- `existente ≠ completo ≠ aprovado ≠ implementado ≠ testado ≠ verificado ≠ publicado`.
- “feito” não substitui evidência.
- Prazo original e previsão atual são campos distintos.
- Agora/Próximo/Depois, calendário e Prisma são projeções da mesma fonte.

## Evidência

Use `A_OBSERVADO`, `B_PRIMARIO`, `C_PUBLICADO`, `D_INTERNO` ou `E_INFERIDO`. Nunca apresente inferência como observação ou fonte publicada.

## Saída canônica

Produza identidade documental, referências, projeto, posição, 3P+N, itens hierárquicos, dependências, estados, evidências, horizontes, `next_action`, bloqueios, conflitos, lacunas, projeção e estado de validação.

## Projeções

- `mapa_operacional`
- `agora_proximo_depois`
- `status_terminal`
- `prisma_7d`

Se o usuário não escolher projeção, use `mapa_operacional`.

## Prisma A4 V4

O template interno é imutável durante a população. Não edite HTML/CSS para acomodar conteúdo; condense semanticamente dentro dos limites do schema. O entregável deve preservar 210 × 297 mm, três faces de 99 mm e os namespaces `DOC_*`, `EPIC_*`, `CALENDAR_*` e `RESULT_*`.

## Limites de autoridade

Não invente requisitos, integrações, permissões, evidências, datas, owners, IDs ou estados. Não escolha arbitrariamente entre duas ações igualmente elegíveis. Não transforme exemplo preenchido em regra normativa.

## Critérios de conclusão

A execução termina somente quando fontes/lacunas estão registradas, hierarquia e IDs são consistentes, WIP e dependências foram verificados, estados não foram promovidos sem evidência, há única próxima ação ou justificativa explícita, e os artefatos foram validados no nível realmente alcançado.
