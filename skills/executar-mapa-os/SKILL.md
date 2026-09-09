---
name: executar-mapa-os
description: Transforme documentos, planos, cronogramas, status e evidências do ecossistema EXECUTAR em um Mapa-OS operacional rastreável, com posição canônica, horizontes Agora/Próximo/Depois, próxima ação elegível, evidências e projeção Prisma A4 opcional. Use quando o usuário pedir Mapa-OS, mapa operacional, centro de comando, retomada, status EXECUTAR, Agora/Próximo/Depois, plano semanal Prisma, ou precisar converter material disperso em estado executável. Não use para promover estados sem evidência nem para substituir a fonte canônica do projeto.
---

# EXECUTAR Mapa-OS

Converta material de projeto em uma leitura operacional única e rastreável. A saída deve responder: onde o projeto está, o que está ativo, o que bloqueia, qual evidência existe e qual é a única próxima ação elegível.

## Antes de operar

Leia sempre [references/architecture-executar.md](references/architecture-executar.md) e [references/mapa-os-contract.md](references/mapa-os-contract.md). Leia [references/projections.md](references/projections.md) somente quando emitir uma projeção visual ou imprimível. Leia [references/source-audit.md](references/source-audit.md) quando precisar distinguir o corpus canônico dos protótipos anexados.

## Entradas

Aceite arquivos, texto no chat ou o objeto de `schemas/input.schema.json`. Extraia apenas conteúdo sustentado pelas fontes. Classifique cada insumo como norma, decisão, estado, evidência, plano, template, exemplo ou conteúdo ilustrativo.

Se faltar informação:

- continue nas partes independentes;
- use `NAO_DETERMINADO` para lacunas não bloqueantes;
- use `BLOCKED` apenas quando a lacuna impedir uma saída obrigatória;
- pergunte somente o mínimo que destrava a operação.

## Fluxo

1. Inventarie todas as fontes e preserve seus IDs, nomes, versões e datas.
2. Extraia objetos e relações na hierarquia `Projeto → Entrega/Dia Lógico → Fluxo → Ação`.
3. Classifique cada comportamento como `DETERMINISTICO`, `INTERPRETATIVO`, `EXIGE_HUMANO` ou `NAO_DETERMINADO`.
4. Preserve dependências, critérios de conclusão, gates, evidências, prazos originais e previsões atuais.
5. Reconcilie conflitos somente quando uma fonte com autoridade explícita resolver a disputa. Caso contrário, registre o conflito.
6. Calcule apenas derivações determinísticas sustentadas, como percentuais com numerador e denominador, datas relativas com base explícita e elegibilidade por dependências.
7. Determine a posição operacional e aplique WIP=1: no máximo uma entrega, um fluxo e uma ação ativos.
8. Selecione `next_action` apenas entre ações elegíveis e não bloqueadas. Se houver empate sem regra de precedência, pare em `EXIGE_HUMANO`.
9. Organize projeções `Agora`, `Próximo` e `Depois` sem criar objetos novos ou mudar seus estados.
10. Valide a saída com `schemas/output.schema.json` e, quando disponível, `scripts/validate_mapa.py`.
11. Emita a resposta documental e os artefatos solicitados. Não declare como testado, verificado ou publicado o que apenas foi criado ou implementado.

## Invariantes

- Posição é estado operacional.
- Dia Lógico é entrega; não é data do calendário.
- Passagem do tempo não altera estado sozinha.
- WIP operacional é `1 entrega → 1 fluxo → 1 ação`.
- Dependências válidas governam elegibilidade; ordem numérica é apenas preferencial.
- `existente ≠ completo ≠ aprovado ≠ implementado ≠ testado ≠ verificado ≠ publicado`.
- Uma declaração de “feito” não fecha objeto cujo contrato exige evidência ou gate.
- Atraso preserva prazo original e recebe previsão atual separada; nunca sobrescreva um pelo outro.
- Agora/Próximo/Depois, calendário e Prisma são projeções da mesma fonte; não são estruturas concorrentes.
- Contagens de três são referências de template, não limites ontológicos.

## Evidência e classificação epistêmica

Use `A_OBSERVADO`, `B_PRIMARIO`, `C_PUBLICADO`, `D_INTERNO` ou `E_INFERIDO`. Nunca apresente inferência como observação, dado primário ou fonte publicada. Vincule toda promoção de estado à evidência e ao critério que ela satisfaz.

## Saída canônica

Produza um objeto compatível com `schemas/output.schema.json` contendo, no mínimo:

- identidade documental e referências de fonte;
- projeto e posição atual;
- síntese 3P+N;
- itens hierárquicos, dependências, estados e evidências;
- horizontes Agora/Próximo/Depois;
- `next_action` única ou motivo explícito para sua ausência;
- bloqueios, conflitos e lacunas;
- projeção solicitada e estado de validação.

Na resposta humana, comece pelo Document Reader definido em [references/mapa-os-contract.md](references/mapa-os-contract.md), depois entregue conclusão, desenvolvimento e próximos passos. O bloco documental não substitui o artefato solicitado.

## Projeções

- `mapa_operacional`: leitura de retomada, foco, bloqueios, evidência e próxima ação.
- `agora_proximo_depois`: três horizontes sem mutar a estrutura canônica.
- `status_terminal`: síntese compacta de progresso, posição, 3P+N e tags.
- `prisma_7d`: status semanal A4 de três faces. Leia [references/projections.md](references/projections.md), construa payload conforme `schemas/prism-report.schema.json` e renderize com `scripts/render_prism.py`.

Se o usuário não escolher uma projeção, use `mapa_operacional`. Não gere calendário de sete dias quando as fontes não sustentarem sete dias; registre a lacuna ou peça o mínimo necessário.

## Prisma A4 V4

O template em `assets/templates/status-report-prisma-a4-v4.html` é imutável durante população: A4 retrato 210 × 297 mm, três faces de 99 mm e 100 placeholders canônicos nos namespaces `DOC_*`, `EPIC_*`, `CALENDAR_*` e `RESULT_*`.

Não edite HTML/CSS para acomodar conteúdo. Condense semanticamente dentro dos limites do schema; se houver perda inevitável, retorne erro de fit. Renderize com:

```bash
python scripts/render_prism.py payload.json output.html
```

## Limites de autoridade

Não invente requisitos, integrações, permissões, evidências, datas, owners, IDs ou estados. Não envie mensagens, publique, faça deploy ou altere sistemas externos sem solicitação e autorização específicas. Não escolha arbitrariamente entre duas próximas ações igualmente elegíveis. Não transforme exemplos preenchidos do corpus em regra normativa.

## Critérios de conclusão

A execução termina somente quando:

- fontes e lacunas estão registradas;
- hierarquia e IDs são consistentes;
- WIP e dependências foram verificados;
- estados não foram promovidos sem evidência;
- existe uma única próxima ação elegível ou justificativa explícita para ausência;
- saída valida no schema;
- projeções preservam a fonte canônica;
- artefatos pedidos foram criados e validados no nível realmente alcançado.
