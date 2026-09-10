# CORE_ACCEPTANCE_CRITERIA

Status: `PARTIAL_SPECIFIED`
Linked requirements: `10-PRODUCT/requirements/CORE_REQUIREMENTS.md`

## Acceptance Criteria

### AC-EXEC-001 — Retomada
Given que uma execução foi interrompida e ocorreu checkout,
When o usuário retorna,
Then o sistema deve conseguir apresentar o estado persistido, itens abertos, blockers conhecidos e uma próxima ação disponível sem exigir reconstrução manual integral do contexto.

### AC-EXEC-002 — Hierarquia
Given um Project estruturado,
When sua decomposição é consultada,
Then deve ser possível rastrear a cadeia aplicável `Project → ValueStream → Deliverable → Task → Action → Evidence`.

### AC-EXEC-003 — Dependência bloqueante
Given uma Action com dependência impeditiva não concluída,
When a fila executável é calculada,
Then essa Action não deve aparecer como elegível para iniciar e deve permanecer identificável como bloqueada.

### AC-EXEC-004 — Liberação de sucessor
Given uma Action bloqueada apenas por uma dependência,
When a dependência é concluída e nenhum outro blocker existe,
Then a elegibilidade deve ser recalculada e a Action pode passar a READY.

### AC-EXEC-005 — WIP 1:1
Given que já existe uma Action em FOCUS,
When outra Action é selecionada para foco no mesmo contexto de execução,
Then o sistema deve aplicar a política WIP 1:1 e impedir duas ações com precedência ativa simultânea sem uma transição explícita.

### AC-EXEC-006 — Próxima ação
Given um conjunto de Actions com estados diferentes,
When o usuário entra no modo de execução,
Then o sistema deve privilegiar Action elegível/acionável e não uma lista indiscriminada de BACKLOG/BLOCKED.

### AC-EXEC-007 — Capacidade
Given uma capacidade disponível e um conjunto de trabalho estimado,
When o plano é estruturado,
Then o sistema deve distinguir o que cabe do que excede a capacidade e manter o excedente explicitamente identificável.

### AC-EXEC-008 — Replanejamento
Given alteração de capacidade, dependência ou realidade,
When o replanejamento ocorre,
Then o caminho futuro pode ser reorganizado sem apagar histórico de execução/evidência já registrada.

### AC-EXEC-009 — Conclusão
Given uma Action em FOCUS,
When sua conclusão é registrada,
Then seu estado deve mudar para DONE e o estado agregado/dependências relevantes devem ser recalculados.

### AC-EXEC-010 — Evidência
Given uma Action cuja regra exige Evidence,
When a conclusão for registrada,
Then a Evidence deve ser associável à execução antes de considerar satisfeita a condição de evidência dessa capability.

### AC-EXEC-011 — Checkout
Given uma sessão de execução ativa,
When ocorre checkout,
Then devem ser preservados ao menos ponto de parada, realizado, aberto, blocker conhecido e próximo movimento quando determinável.

### AC-EXEC-012 — Mapa-OS
Given estado operacional conhecido,
When o Mapa-OS é emitido,
Then deve ser possível representar ativo, concluído, bloqueado, dependências, próximo movimento e informação de capacidade/excedente aplicável.

### AC-EXEC-013 — Scanner
Given um símbolo Visual Scanner conhecido,
When ele é reconhecido com confiança suficiente,
Then deve resultar no command/action mapeado sobre o mesmo estado canônico; QR e OCR não são requisito do fluxo V2.

### AC-EXEC-014 — Status Report
Given histórico/estado suficiente de uma execução,
When um Status Report é emitido,
Then progresso, entregas, blockers, evidências e próximos passos devem ser derivados do estado registrado e não depender exclusivamente de memória manual do usuário.

### AC-EXEC-015 — Estado único entre superfícies
Given duas superfícies autorizadas do produto,
When ambas consultam a mesma unidade de trabalho,
Then devem convergir para o mesmo estado canônico, sujeito às regras de sincronização/consistência que serão definidas em contrato.

## Critérios que permanecem GAP

- tempos máximos globais de resposta;
- thresholds de performance do core;
- comportamento exato de conflito offline;
- regras detalhadas de tenancy/RBAC;
- DoD por tipo de Action/Deliverable;
- política universal de Evidence;
- algoritmo de Best Next Action.

Esses itens não devem ser preenchidos por benchmark sem decisão explícita.