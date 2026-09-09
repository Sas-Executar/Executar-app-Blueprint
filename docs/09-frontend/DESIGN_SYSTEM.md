---
id: UI-005
type: design_system_contract
status: pre_approved
version: 1.0.0
owner: null
source_of_truth: external_reference
external_source:
  repository: Sas-Executar/Desyng-System-ecossitema
  branch: claude/design-handoff-specs-ulc1r1
reference_extract: references/design-system/
related:
  - SPEC-WORKSPACE-001
  - DELIV-MAPA-005
  - PRD-SCANNER-001
  - DELIV-ROUT-001
---
# EXECUTAR Design System Contract

## 1. Papel

O Design System do ecossistema EXECUTAR deve ser consumido pelo aplicativo e pelas superfícies associadas sem redefinição silenciosa de tokens ou componentes no `Executar-app-Blueprint`.

O repositório declarado `Sas-Executar/Desyng-System-ecossitema`, branch `claude/design-handoff-specs-ulc1r1`, permanece a referência externa pretendida para o sistema visual.

## 2. Pacotes declarados no handoff

Segundo o pacote de extração fornecido, o sistema está distribuído em:

- `design-system/` — pacote principal de handoff;
- `packages/design-tokens/` — tokens canônicos;
- `packages/callout-protocol/` — protocolo/componente especializado;
- `packages/ui/` — componentes UI.

## 3. Tokens confirmados no pacote fornecido

O pacote anexado contém `package.json` de `@executar/design-tokens` v0.1.0 e `variables.css` com, entre outros:

- verde principal `#00BF63`;
- Azure `#1F93FF`;
- `IBM Plex Sans` como família sans;
- `IBM Plex Mono` como família monoespaçada;
- escalas de tipografia;
- spacing;
- radius;
- shadows;
- containers.

Os arquivos de referência estão preservados em `references/design-system/` com hashes SHA-256.

## 4. Exports declarados

O manifest fornecido declara exports para:

- `design-tokens.json`;
- `variables.css`;
- `theme.css`;
- `styles/reset.css`;
- `styles/typography.css`;
- `styles/layout.css`;
- `styles/utilities.css`;
- `tokens.native`;
- `design-tokens.yaml`.

## 5. Governança de consumo

1. O App deve consumir tokens/componentes do Design System externo quando a integração técnica estiver disponível.
2. Este blueprint não deve criar uma segunda fonte canônica de tokens.
3. Tokens copiados para `references/design-system/` são evidência/reference snapshot, não uma nova autoridade.
4. Mudanças visuais específicas do produto devem ser propostas como extensão/override governado, nunca como substituição silenciosa do SOT.
5. Mapa-OS, Scanner, Reports e Workspace devem declarar explicitamente quando usam componentes/tokens compartilhados ou uma gramática visual específica da superfície.

## 6. Proveniência

Classificação:

- `references/design-system/package.json` — `CORPUS_DIRECT` conforme pacote fornecido;
- `references/design-system/variables.css` — `CORPUS_DIRECT` conforme pacote fornecido;
- `references/design-system/SOURCE_README.txt` — `CORPUS_DIRECT` do pacote fornecido;
- `references/design-system/EXECUTAR_Showroom_reconstructed.html` — `CORPUS_DERIVED`.

O `SOURCE_MANIFEST.json` registra hashes e limitações.

## 7. GAP — HTML original

O `final_bundle.html` / `bundle.html` exibido como Claude Artifact não está presente no pacote fornecido. O showroom incluído é uma reconstrução standalone e não deve ser descrito como original ou byte-identical.

## 8. Limitação de verificação remota

Na sessão atual, o conector GitHub não conseguiu acessar diretamente o repositório externo declarado e retornou 404. Portanto, este registro preserva a proveniência do pacote fornecido sem declarar verificação independente da árvore remota.

## 9. Integrações dependentes

- `SPEC-WORKSPACE-001` — deve consumir a gramática do Design System na implementação final.
- Mapa-OS — mantém seu contrato físico/print específico; tokens compartilhados só são aplicados quando não conflitam com seu template canônico.
- Scanner — superfícies visuais e feedback devem referenciar o Design System, sem acoplar reconhecimento visual aos tokens de UI.
- Reports — templates podem consumir tipografia/tokens compartilhados, preservando requisitos de legibilidade e exportação.

## 10. Estado

`pre_approved` como contrato de referência e consumo. Não significa que `packages/ui`, tokens ou componentes já estejam instalados/importados no runtime do aplicativo.
