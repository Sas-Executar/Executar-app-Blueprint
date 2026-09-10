# CORE_REQUIREMENTS

Status: `PARTIAL_SPECIFIED`
Sources: `SRC-PRODUCT-MANIFESTO-001`, `SRC-PRODUCT-BLUEPRINT-001`

> Regra: requisitos abaixo foram extraídos/normalizados das fontes. Quando a formulação operacional excede a literalidade da fonte, a classificação é `CORPUS_DERIVED`.

| REQ_ID | Requisito | Classe | Capability |
|---|---|---|---|
| `REQ-EXEC-001` | O sistema deve persistir contexto operacional suficiente para retomar trabalho sem reconstrução manual integral. | `CORPUS_DIRECT` | CAP-EXEC-001, 009 |
| `REQ-EXEC-002` | O sistema deve suportar a hierarquia `Project → ValueStream → Deliverable → Task → Action → Evidence`. | `CORPUS_DIRECT` | CAP-EXEC-002 |
| `REQ-EXEC-003` | O sistema deve distinguir trabalho executável de trabalho bloqueado por dependência/condição impeditiva. | `CORPUS_DIRECT` | CAP-EXEC-004 |
| `REQ-EXEC-004` | O sistema deve apresentar/priorizar uma próxima ação executável com precedência clara. | `CORPUS_DIRECT` | CAP-EXEC-005 |
| `REQ-EXEC-005` | O sistema deve preservar WIP 1:1 para a ação ativa, sem impedir a existência de múltiplos projetos. | `CORPUS_DIRECT` | CAP-EXEC-006 |
| `REQ-EXEC-006` | O sistema deve planejar considerando capacidade disponível, dependências, precedência, excedente e necessidade de replanejamento. | `CORPUS_DIRECT` | CAP-EXEC-003 |
| `REQ-EXEC-007` | O sistema deve suportar ciclos operacionais de 72h. | `CORPUS_DIRECT` | CAP-EXEC-003 |
| `REQ-EXEC-008` | O sistema deve recalcular/reorganizar o plano quando capacidade, dependência ou realidade mudarem. | `CORPUS_DIRECT` | CAP-EXEC-008 |
| `REQ-EXEC-009` | O sistema deve registrar checkout com ponto de parada, realizado, aberto, blocker e próximo movimento. | `CORPUS_DIRECT` | CAP-EXEC-009 |
| `REQ-EXEC-010` | O sistema deve associar execução/conclusão a evidência quando exigido pela regra da capability. | `CORPUS_DIRECT/CORPUS_DERIVED` | CAP-EXEC-007 |
| `REQ-EXEC-011` | Conclusão deve atualizar progresso/estado e permitir reavaliação de sucessores/dependências. | `CORPUS_DERIVED` | CAP-EXEC-004, 007 |
| `REQ-EXEC-012` | O Mapa-OS deve representar estado operacional, ativo, concluído, bloqueado, dependências, próximo movimento e capacidade/excedente. | `CORPUS_DIRECT` | CAP-EXEC-010 |
| `REQ-EXEC-013` | O Scanner deve permitir reconectar ações físicas ao estado digital sem depender de QR/OCR no fluxo Visual Symbol Scanner V2. | `CORPUS_DIRECT` | CAP-EXEC-011 |
| `REQ-EXEC-014` | O Copiloto deve operar sobre contexto/estado real do sistema e apoiar estruturar, orientar, detectar bloqueios e replanejar. | `CORPUS_DIRECT` | CAP-EXEC-012 |
| `REQ-EXEC-015` | Status Report deve ser derivável do estado/histórico de execução, não de reconstrução manual posterior. | `CORPUS_DIRECT` | CAP-EXEC-013 |
| `REQ-EXEC-016` | App, Copiloto, Mapa-OS, Scanner e integrações aplicáveis devem convergir para um estado operacional canônico único. | `CORPUS_DERIVED` | CAP-EXEC-015 |
| `REQ-EXEC-017` | A interface de execução deve reduzir informação, escolhas e alternâncias concorrentes ao mínimo necessário. | `CORPUS_DIRECT` | CAP-EXEC-005, 006 |
| `REQ-EXEC-018` | Automação não deve retirar decisões legítimas da autoridade do usuário. | `CORPUS_DIRECT` | transversal |

## Requisitos não funcionais ainda não consolidados

- performance/latência global;
- disponibilidade;
- segurança/privacidade;
- tenancy;
- retenção;
- acessibilidade transversal;
- sync/offline;
- observabilidade;
- custos/limites de IA.

`GAP-NFR-001` permanece aberto e será fechado em conjunto com WF-05/WF-07 e decisões técnicas aplicáveis.