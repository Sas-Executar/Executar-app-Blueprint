# NON_FUNCTIONAL_REQUIREMENTS

Status: `PARTIAL`

## NFRs sustentados pelas fontes atuais

| NFR_ID | Requisito | Classe |
|---|---|---|
| `NFR-EXEC-001` | O produto deve preservar continuidade de estado entre interrupções e superfícies autorizadas. | `CORPUS_DIRECT/CORPUS_DERIVED` |
| `NFR-EXEC-002` | A evolução do produto deve preservar funcionamento PWA/offline aplicável até existir equivalência comprovada. | `CORPUS_DIRECT` da governança atual do app |
| `NFR-EXEC-003` | Escritas multi-tenant não podem vazar dados entre organizações/tenants. | `CORPUS_DIRECT` da governança atual do app |
| `NFR-EXEC-004` | Ações de agente que modificam estado devem possuir autorização explícita e trilha de auditoria; efeitos relevantes/irreversíveis exigem política de aprovação humana aplicável. | `CORPUS_DIRECT` da governança atual do app |
| `NFR-EXEC-005` | Scanner Visual V2 deve suportar reconhecimento on-device/offline e rejeição de UNKNOWN conforme sua spec operacional. | `CORPUS_DIRECT` da fonte Scanner |
| `NFR-EXEC-006` | A experiência de execução deve minimizar densidade decisória, informação concorrente e alternância desnecessária. | `CORPUS_DIRECT` do manifesto |

## Gaps NFR

- `GAP-NFR-PERF-001` — budgets globais de performance/latência.
- `GAP-NFR-AVAIL-001` — disponibilidade/SLO.
- `GAP-NFR-SEC-001` — baseline de segurança transversal completa.
- `GAP-NFR-PRIV-001` — privacy, retention e deletion policy.
- `GAP-NFR-SYNC-001` — consistência e conflito offline/sync.
- `GAP-NFR-A11Y-001` — critérios transversais de acessibilidade do produto além do WF-01 Design.
- `GAP-NFR-OBS-001` — telemetria/observabilidade operacional.
- `GAP-NFR-AI-001` — limites de custo, steps, tempo e repetição para agentes.

Esses gaps serão fechados por Contracts/Analytics & Security/Integration. O WF-02 apenas registra o que já é exigido pelo produto.