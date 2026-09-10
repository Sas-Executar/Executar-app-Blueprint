# CORE_PERMISSIONS

Status: `PARTIAL_SPECIFIED`
Sources: `SRC-PRODUCT-MANIFESTO-001` + current application governance (`Sas-Executar/Sas-Executar/AGENTS.md`)

## Princípios canônicos

### PERM-EXEC-001 — Tenant isolation
Toda leitura/escrita de estado de produto deve respeitar o tenant/organização ativa. O produto atual usa organização como boundary de tenant; nenhuma escrita multi-tenant pode vazar dados entre organizações.

### PERM-EXEC-002 — User authority
Automação reduz carga operacional, mas o usuário mantém autoridade sobre decisões relevantes. Ações irreversíveis/relevantes executadas por agente exigem política de autorização e, quando aplicável, aprovação humana.

### PERM-EXEC-003 — Agent writes
Ferramentas de agente que alteram estado devem possuir autorização explícita e trilha de auditoria. O fato de um agente conseguir ler uma entidade não implica permissão de escrita.

### PERM-EXEC-004 — Surface neutrality
App, Copiloto, Scanner e integrações não criam autoridades de estado paralelas. Cada superfície deve operar sobre permissões e tenant do estado canônico.

## Matriz inicial

A matriz abaixo é deliberadamente mínima. Roles comerciais/finais ainda não foram publicados no corpus.

| Actor | Read own tenant | Write execution state | Change governance/permissions | Cross-tenant |
|---|---:|---:|---:|---:|
| Authenticated member | `YES`, conforme membership | `YES`, conforme role futuro | `GAP` | `NO` |
| Owner/Admin | `YES` | `YES` | `PROPOSED/GAP` — role final ainda não canonizado | `NO` |
| Copilot/Agent | somente contexto autorizado | somente tools/policies autorizadas | `NO` por padrão; exceção exige decisão | `NO` |
| Scanner | apenas command/action autorizado no contexto | mutação específica mapeada | `NO` | `NO` |
| External integration | scopes explícitos | somente operações contratadas | `NO` salvo contrato explícito | `NO` |

## Gaps

- `GAP-PERM-ROLE-001` — catálogo final de roles (`Owner`, `Admin`, `Member`, `Viewer`, etc.).
- `GAP-PERM-MATRIX-001` — matriz Resource × Action × Role.
- `GAP-PERM-SHARE-001` — regras de compartilhamento externo.
- `GAP-PERM-AGENT-001` — classificação formal read/reversible-write/irreversible-write por tool.
- `GAP-PERM-APPROVAL-001` — critérios objetivos de aprovação humana.

Nenhum role adicional foi promovido a requisito sem fonte.