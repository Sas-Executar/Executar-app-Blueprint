# sas-executar-blueprints · transição em revisão

## 1. Propósito
ESPECIFICAR: produto, requisitos, AC, domínio, arquitetura, contratos e development packets. Nome atual: `Executar-app-Blueprint`. O nome alvo ainda não foi aplicado.

## 2. Não é
Runtime, deploy e autoridade de governança documental pertencem aos repositórios correspondentes.

## 3. Source of Truth
[MASTER_INDEX.md](MASTER_INDEX.md) conserva os caminhos canônicos existentes. Novos diretórios são interfaces de navegação e áreas de especificação propostas.

## 4. Relação entre repositórios
Governance → Blueprints → Ecosystem. Maestro atua transversalmente.

- [Maestro](https://github.com/Sas-Executar/Maestr-Docs): OPERAR.
- [Blueprints](https://github.com/Sas-Executar/Executar-app-Blueprint): ESPECIFICAR.
- [Governance](https://github.com/Sas-Executar/Programa-Sas): GOVERNAR.
- [Ecosystem](https://github.com/Sas-Executar/next-forge): IMPLEMENTAR + RELEASE.

## 5. Estrutura
- `00-governance/`
- `01-master-index/`
- `10-product/`
- `20-domain/`
- `30-design/`
- `40-content/`
- `50-agent-contracts/`
- `60-contracts/`
- `70-integrations/`
- `80-architecture/`
- `90-measurement/`
- `95-target-mapping/`
- `blueprints/`
- `development-packets/`
- `queue/`
- `references/`

As estruturas anteriores são preservadas durante a transição. Diretórios novos não promovem artefatos a canônicos automaticamente.

## 6. Workflow
Entrada → inventário → trabalho em branch → validação → PR → decisão explícita → merge → atualização dos índices.

## 7. Estados
`draft ≠ review ≠ approved ≠ implemented ≠ tested ≠ verified ≠ released`. Preservar também pre_approved, accepted e demais estados encontrados. `registered`, `registered_reference`, `registered_from_source` e `registered_analysis` não significam implementação. A classificação de proveniência não altera a classificação das afirmações da fonte.

## 8. Contribuição
Usar migration/*, blueprint/*, wf/*, integration/*, fix/* ou release/*. Branch representa trabalho. main é o estado-alvo canônico após aprovação e integração explícitas. Se main não existir, a branch default observada não comprova aprovação. Não reescrever histórico ou remover fontes durante a migração.

## 9. Traceability
Origem repo/branch/SHA/path → ID → requisito → AC → target → teste/evidência → release. Campos desconhecidos: GAP; owner desconhecido fica vazio. PROPOSED não é requisito existente.

## 10. Migration status
PASS_WITH_GAPS: estrutura em revisão, fontes preservadas. Renomeação, absorções, redistribuição e archive pendentes. A cópia documental do Maestro está nos PRs 2–4 do Programa-Sas; verificação de bytes não é aprovação documental.

[README anterior](00-governance/README_BEFORE_MIGRATION.md) preservado como snapshot de referência com caminhos relativos do contexto original.
