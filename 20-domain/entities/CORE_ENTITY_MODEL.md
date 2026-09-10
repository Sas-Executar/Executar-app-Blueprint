# CORE_ENTITY_MODEL

Status: `PARTIAL_SPECIFIED`
Primary source: `SRC-PRODUCT-MANIFESTO-001`
Secondary source: `SRC-PRODUCT-BLUEPRINT-001`

## Hierarquia canônica

`Project → ValueStream → Deliverable → Task → Action → Evidence`

A hierarquia acima é `CORPUS_DIRECT` do manifesto/blueprint.

## Entidades

### Project
Representa um objetivo/projeto que precisa ser transformado em execução controlável.

Relações:
- possui `0..n` ValueStreams;
- possui estado agregado, capacidade/planejamento e histórico derivados dos níveis inferiores.

Campos funcionais mínimos `CORPUS_DERIVED`:
- id;
- title/name;
- objective;
- status;
- constraints;
- owner/tenant reference;
- created_at / updated_at.

### ValueStream
Agrupa componentes de trabalho que contribuem para o fluxo de valor/entrega dentro de um Project.

Relações:
- pertence a 1 Project;
- possui `0..n` Deliverables.

`GAP-DOM-VS-001`: regras formais de criação, cardinalidade mínima e lifecycle específico ainda não aparecem nas fontes.

### Deliverable
Representa uma entrega observável/resultante do trabalho.

Relações:
- pertence a 1 ValueStream;
- possui `0..n` Tasks;
- pode depender de outros Deliverables ou de Tasks conforme futura modelagem de contrato.

### Task
Representa uma unidade planejável de trabalho necessária para produzir um Deliverable.

Relações:
- pertence a 1 Deliverable;
- possui `1..n` Actions quando decomposta para execução;
- pode possuir dependências e blockers;
- pode produzir/relacionar Evidence.

### Action
É a unidade fundamental da experiência de execução: a próxima ação observável/executável.

Relações:
- pertence a 1 Task;
- possui estado de execução;
- pode ser elegível ou inelegível conforme dependências, capacidade e estado;
- pode gerar Evidence ao ser concluída.

### Evidence
Comprova execução/conclusão e alimenta histórico, Status Report, governança e replanejamento.

Relações:
- pertence a uma Action e/ou Task conforme contrato futuro;
- possui referência a artefato, evento ou registro que demonstra a conclusão.

`GAP-DOM-EVID-001`: cardinalidade final Action↔Evidence, tipos de evidência e política de obrigatoriedade serão definidos em Contracts/Data Model.

## Entidades operacionais derivadas

As fontes exigem conceitos adicionais, mas ainda não há decisão suficiente para afirmar se serão tabelas/aggregates independentes ou value objects:

- `CapacityWindow` — janela de capacidade disponível/realizada;
- `ExecutionCycle` — ciclo de 72h registrado no blueprint e produto legado;
- `Dependency` — relação bloqueante entre objetos executáveis;
- `Blocker` — condição que impede elegibilidade;
- `ExecutionSession` — check-in/checkout/retomada;
- `OperationalState` — estado canônico agregado usado pelas superfícies;
- `EvidenceRecord` — metadados de evidência;
- `ReplanDecision` — mudança de caminho decorrente de capacidade/dependência/realidade.

Todos permanecem `CORPUS_DERIVED` até data model/contract próprio.

## Invariantes funcionais

- Action é a unidade central da execução.
- Trabalho bloqueado não deve aparecer como próxima ação executável.
- O sistema deve preservar dependências e estado entre superfícies.
- Evidência deve nascer do fluxo de execução sempre que aplicável.
- O modelo deve suportar múltiplos projetos, mas WIP 1:1 na ação ativa.

## Gaps

- `GAP-DOM-IDS-001` — estratégia de IDs e chaves externas.
- `GAP-DOM-CARD-001` — cardinalidades finais para todos os objetos.
- `GAP-DOM-LIFECYCLE-001` — lifecycle detalhado de Project/ValueStream/Deliverable.
- `GAP-DOM-DATA-001` — tipos, constraints e índices do schema persistente.
- `GAP-DOM-TENANCY-001` — referência funcional completa de tenant/ownership neste modelo.

Esses gaps pertencem ao Data Model/Contracts e não invalidam a hierarquia funcional.