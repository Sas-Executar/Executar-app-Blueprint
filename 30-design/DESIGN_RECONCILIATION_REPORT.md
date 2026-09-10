# Design reconciliation · preliminary

Source snapshot: Desyng-System-ecossitema. at 3784189e789a5b16fc2bdaaa6854a4bdc1bcad77. Ecosystem snapshot: next-forge at f189de79ceef7c1ef69f61f12e272f99b4cdb699.

Only tree/path/blob comparisons are asserted. Presence is not implementation verification. Source authority currently follows the existing UI-005 contract and reference registry; no second SOT is created.

| Package | Source blobs | Ecosystem blobs | Identical same-path blobs |
|---|---:|---:|---:|
| packages/design-tokens | 14 | 0 | 0 |
| packages/design-system | 0 | 64 | 0 |
| packages/ui | 32 | 0 | 0 |
| packages/callout-protocol | 7 | 0 | 0 |

GAP: source alternate branches, UI-005 compatibility, dependency graph, tests, responsive/accessibility contracts and actual component behavior must be reconciled before code integration. Ecosystem structural/code changes and Design System archive remain BLOCKED.

DESIGN SOURCE → BLUEPRINT CONTRACT → ECOSYSTEM IMPLEMENTATION. Existing package trees must never be silently overwritten.
