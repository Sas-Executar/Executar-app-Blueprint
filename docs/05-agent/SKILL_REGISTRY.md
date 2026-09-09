---
id: AGENT-SKILL-REGISTRY-001
type: skill_registry
status: registered
version: 1.0.0
owner: null
---
# Skill Registry

## SKILL-MAPA-OS-001 · executar-mapa-os
- Entry point: `skills/executar-mapa-os/SKILL.md`
- Imported version: `1.0.0`
- Source package: `executar-mapa-os.skill(1).zip`
- Source SHA-256: `ef738400596a7a323d766bbbae082ba05d32f9519c39c94897158d48edd01aac`
- Source inventory: `skills/executar-mapa-os/SOURCE_MANIFEST.json`
- Registered contracts: Mapa-OS contract and projection contract.
- Purpose: convert project sources into a traceable operational Mapa-OS with WIP=1, evidence, horizons and one eligible next action.
- Declared projections: `mapa_operacional`, `agora_proximo_depois`, `status_terminal`, `prisma_7d`.
- Source-package validation executed before registration: `PASS`; WIP=1; evidence valid; Prisma placeholder audit passed.
- Authority: projection/orchestration layer; it does not replace the canonical project source.

## SKILL-COP-001 · copiloto-executar
- Entry point: `skills/copiloto-executar/SKILL.md`
- Source package: `copiloto-executar(1).zip`
- Source SHA-256: `c5eedcb739570667c412a0a10906c5274568c8356d7870e1157de8e674dd356d`
- Source inventory: `skills/copiloto-executar/SOURCE_MANIFEST.json`
- Registered contracts: command surface and orchestrator output schema.
- Purpose: operate the daily EXECUTAR runtime over one canonical source using progressive disclosure, WIP, DoD, evidence, gates and controlled state transitions.
- Primary command deliverables: `/bomdia`, `/agora`, `/estado`, `/fechardia`, `/replanejamento`.
- Runtime modules declared by source: `ORQ-COP-001`, `AGENTE-Copiloto-007`, `COP-PROD-001`, `COP-OPS-001`.
- Source-package validation executed before registration: `READY`.

## Registration semantics

`registered` means the supplied package, identity, provenance and declared contracts were inventoried in this repository. It does not mean production approval, deployment, external-system binding, CI verification or release.

The source manifests preserve the complete file inventory and hashes of each uploaded ZIP even when only the canonical entrypoints/contracts needed for this registration are materialized as repository files.
