---
id: ADR-SCANNER-001
type: architecture_decision_record
status: registered_from_source
source_status: accepted
version: 1.0.0
owner: null
project: EXECUTAR
scope: mobile/scanner
source: PRD SCANNER - EXECUTAR APP.md
---
# Replace encoded scanner tokens with visual instance recognition

## Context
O Scanner físico atual descrito pela fonte depende de QR/payload. O produto passa a exigir que a própria aparência gráfica do símbolo seja sua identidade.

## Decision drivers
- reconhecimento on-device;
- funcionamento offline;
- baixa latência;
- ausência de códigos impressos;
- enrollment sem retreinamento;
- integração com Expo/React Native;
- separação entre reconhecimento visual e ação de domínio.

## Options
- QR/encoded marker: rejected.
- OCR: rejected.
- template matching puro: rejected como engine principal; MAY servir como benchmark.
- classificador específico treinado: rejected para V1.
- visual embeddings + nearest-neighbor: accepted.

## Decision
Adotar Visual Instance Recognition por embeddings.

Encoder inicial declarado na fonte: `DINOv2 ViT-S/14`.
Runtime declarado: `ONNX Runtime React Native`.
Execução: on-device.
Matching: similaridade de embeddings com rejeição de desconhecidos.

Pipeline:

`Camera → ROI → ImagePreprocessor → VisualEncoder → Embedding → SymbolMatcher → VisualSymbolId → CommandDispatcher`

## Boundary
O modelo visual determina identidade. O domínio determina ação. Essas responsabilidades MUST permanecer desacopladas.

Mapa-OS não executa a ação: ele pode carregar o símbolo físico como parte do entregável analógico. Scanner reconhece. CommandDispatcher executa.

## Trigger semantics
Eventos devem ser edge-triggered:

`ABSENT → ENTER → FIRED → PRESENT → ABSENT`

Frames repetidos em `PRESENT` MUST NOT disparar novamente.

## Consequences
- remove QR/OCR do caminho físico principal;
- exige registry local de símbolos/embeddings;
- exige mecanismo de enrollment;
- exige Action Resolver/CommandDispatcher independente;
- exige Undo para mutações de conclusão descritas pelo PRD;
- limiar de similaridade precisa ser calibrado por testes.

## Status note
Decisão registrada a partir do corpus. Não foi revalidada contra o código do produto neste registro.
