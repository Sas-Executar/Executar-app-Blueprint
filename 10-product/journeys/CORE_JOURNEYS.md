# CORE_JOURNEYS

Status: `PARTIAL_SPECIFIED`
Sources: `SRC-PRODUCT-MANIFESTO-001`, `SRC-PRODUCT-BLUEPRINT-001`

## JRN-EXEC-001 — Criar e estruturar trabalho

Objetivo: transformar uma intenção/projeto em estrutura operacional.

Fluxo canônico:

1. usuário fornece objetivo/contexto;
2. sistema consolida problema, restrições, capacidade e evidências existentes;
3. sistema estrutura `Project → ValueStream → Deliverable → Task → Action`;
4. sistema identifica dependências e blockers;
5. sistema calcula/organiza o que está dentro e fora da capacidade;
6. sistema prepara ações elegíveis;
7. usuário revisa/aprova decisões relevantes quando aplicável.

Resultado: trabalho estruturado e pronto para planejamento/execução.

## JRN-EXEC-002 — Planejar por capacidade

1. ler capacidade/contexto disponível;
2. considerar dependências e precedência;
3. distinguir trabalho que cabe e excedente;
4. identificar caminho prioritário/crítico;
5. produzir conjunto elegível/planejado;
6. registrar ciclo/estado de planejamento.

Resultado: plano executável, não apenas lista priorizada.

## JRN-EXEC-003 — Executar próxima ação

1. sistema avalia elegibilidade;
2. sistema despacha uma Best Next Action;
3. ação assume FOCUS respeitando WIP 1:1;
4. interface reduz informação concorrente;
5. usuário executa a ação;
6. sistema preserva contexto e estado.

Resultado: uma ação ativa com precedência clara.

## JRN-EXEC-004 — Concluir e evidenciar

1. usuário ou canal autorizado sinaliza conclusão;
2. sistema valida regra/contrato aplicável;
3. ação muda para DONE;
4. evidência é registrada/associada quando aplicável;
5. dependências/sucessores são recalculados;
6. progresso e outputs operacionais são atualizados;
7. próxima ação elegível pode ser disponibilizada.

Resultado: execução comprovável alimentando o estado canônico.

## JRN-EXEC-005 — Bloqueio e liberação

1. blocker/dependência impeditiva é detectada;
2. item muda para BLOCKED;
3. sistema remove item da fila executável;
4. blocker permanece visível e rastreável;
5. quando resolvido, eligibility é recalculada;
6. item pode retornar a READY.

Resultado: trabalho inviável não compete com trabalho acionável.

## JRN-EXEC-006 — Checkout e retomada

1. usuário interrompe/encerra sessão;
2. sistema registra onde parou, o que fez, o que ficou aberto, blockers e próximo movimento;
3. estado persiste;
4. no retorno, sistema reconstrói contexto sem depender da memória do usuário;
5. sistema reapresenta estado e próxima ação disponível.

Resultado: retomada com menor custo cognitivo.

## JRN-EXEC-007 — Replanejar

1. realidade/capacidade/dependência muda;
2. sistema identifica impacto;
3. eligibility/ordem/caminho é recalculado;
4. decisões relevantes são apresentadas ao usuário quando necessário;
5. plano é atualizado sem apagar evidência/histórico anterior.

Resultado: plano adaptado ao estado real.

## JRN-EXEC-008 — Executar por Mapa-OS + Scanner

1. sistema estrutura e emite Mapa-OS;
2. papel apresenta estado/ação/símbolos;
3. usuário executa fora da interface principal;
4. Scanner reconhece símbolo/comando permitido;
5. comando atua sobre o mesmo estado canônico;
6. sistema registra mudança/evidência/undo quando aplicável;
7. próxima ação é disponibilizada.

Resultado: continuidade analógico-digital sem retornar continuamente à tela de planejamento.

## JRN-EXEC-009 — Gerar Status Report

1. sistema lê estado e histórico de execução;
2. consolida progresso, entregas, bloqueios, capacidade, desvios, evidências e decisões;
3. emite report e próximos passos;
4. usuário não reconstrói manualmente o período.

Resultado: governança derivada da execução.

## Gaps

- `GAP-JRN-ONBOARD-001` — onboarding detalhado ainda não especificado.
- `GAP-JRN-ERROR-001` — matriz de erros/empty/loading por jornada pertence ao WF-04/WF-05.
- `GAP-JRN-PERM-001` — papéis/permissões detalhados por etapa ainda não fechados.
- `GAP-JRN-OFFLINE-001` — política completa de offline/sync ainda requer contrato.