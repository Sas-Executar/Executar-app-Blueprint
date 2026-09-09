---
id: AGENT-SKILL-REGISTRY-001
type: skill_registry
status: registered
version: 1.1.0
owner: null
---
# Skill Registry

## SKILL-MAPA-OS-001 · executar-mapa-os
- Entry point: `skills/executar-mapa-os/SKILL.md`
- Imported/source version: `1.1.0`
- Source package: `executar-mapa-os-v1.1.0(1).zip`
- Source SHA-256: `4fd46e031f3482e77ffa5953a783385d85f0efb633980d152d02cd6a3de5513b`
- Source inventory: `skills/executar-mapa-os/SOURCE_MANIFEST.json`
- Internal asset index: `skills/executar-mapa-os/INTERNAL_ASSET_INDEX.md`
- Product role: agent-generated analog/imprintable task-management deliverable over the canonical digital state.
- Official prompt model 01: `skills/executar-mapa-os/references/prompts/01-prompt-mestre-prisma.md`.
- Official prompt model 02: `skills/executar-mapa-os/references/prompts/02-exemplo-preenchido-prisma.md` — illustrative only.
- Internal template: `skills/executar-mapa-os/assets/templates/status-report-prisma-a4-v4.html`.
- Registered workflows: `WF-MAPA-001`, `WF-MAPA-002`, `WF-MAPA-003`.
- Declared projections: `mapa_operacional`, `agora_proximo_depois`, `status_terminal`, `prisma_7d`.
- Authority: generation/projection layer; it does not replace canonical project state and does not perform Scanner recognition itself.

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

## Scanner boundary
The Visual Symbol Scanner is a separate product/technical capability. It MAY consume symbols printed in a Mapa-OS, but recognition and task mutation are governed by `PRD-SCANNER-001`, `ADR-SCANNER-001`, `SPEC-SCANNER-001` and `API-SCANNER-ACTION-001`.

## Registration semantics
`registered` means identity, provenance and declared contracts are inventoried. It does not mean production approval, deployment, external-system binding, CI verification or release.
