# EXECUTAR Design System — Reference Extract

ID: `REF-DS-001`

## Declared origin

- Repository: `Sas-Executar/Desyng-System-ecossitema`
- Branch: `claude/design-handoff-specs-ulc1r1`
- Declared handoff package: `design-system/`
- Declared supporting packages: `packages/design-tokens/`, `packages/callout-protocol/`, `packages/ui/`

## Provenance rule

This directory is a governed reference copy created from the supplied extraction package `EXECUTAR_design_system_extract(1).zip`.

The current GitHub connector session could not directly read the declared source repository, so this folder does **not** claim independent remote verification of that repository/branch. It preserves the provenance stated by the supplied package and records SHA-256 hashes in `SOURCE_MANIFEST.json`.

## Classification

- `package.json` — `CORPUS_DIRECT`; supplied as the exact manifest of `packages/design-tokens/package.json`.
- `variables.css` — `CORPUS_DIRECT`; supplied token extraction.
- `EXECUTAR_Showroom_reconstructed.html` — `CORPUS_DERIVED`; standalone reconstruction based on supplied tokens/structure.
- original `final_bundle.html` / `bundle.html` — `GAP`; not present in the supplied extraction and must not be represented as original.

## Authority

The source Design System repository remains the intended source of truth. Files in this directory are reference evidence for the EXECUTAR App Blueprint and must not silently fork or override canonical tokens/components.

See `docs/09-frontend/DESIGN_SYSTEM.md` for the consumption/governance contract.
