---
id: SPEC-SCANNER-001
type: technical_specification
status: registered_from_source
version: 1.0.0
owner: null
project: EXECUTAR
feature: visual-symbol-scanner
depends_on:
  - ADR-SCANNER-001
  - PRD-SCANNER-001
source: PRD SCANNER - EXECUTAR APP.md
---
# Technical Specification · Visual Symbol Scanner

## Runtime architecture

```text
CameraView
  ↓
FrameSource
  ↓
ROIExtractor
  ↓
ImagePreprocessor
  ↓
VisualEncoder
  ↓
SymbolMatcher ← SymbolRegistry
  ↓
ScanEventLatch
  ↓
VisualCommandDispatcher
  ├─ OPEN_CHAT
  ├─ OPEN_SELECTOR
  └─ COMPLETE_LATEST_OPEN_TASK
```

## Modules
- `camera-frame-source`
- `roi-extractor`
- `image-preprocessor`
- `dinov2-encoder`
- `symbol-matcher`
- `symbol-registry`
- `symbol-enrollment`
- `scan-event-latch`
- `visual-command-dispatcher`
- domain mutation adapters
- notification/undo adapter

## Recognition contract

```ts
recognize(frame): Promise<{
  symbolId: VisualSymbolId | "UNKNOWN";
  similarity: number;
}>
```

Recognition MUST support rejection. A nearest neighbor alone MUST NOT authorize execution.

## Registry contract

```ts
interface VisualSymbol {
  id: string;
  semantic: "chat" | "selector" | "done";
  command: "OPEN_CHAT" | "OPEN_SELECTOR" | "COMPLETE_LATEST_OPEN_TASK";
  embeddings: Float32Array[];
  enabled: boolean;
}
```

Seed V1:
- `SYM-CHAT-001`
- `SYM-SELECTOR-001`
- `SYM-DONE-001`

## Enrollment

```ts
registerSymbol(images, command): Promise<VisualSymbol>
```

Enrollment MUST preprocessar imagens, gerar embeddings, persistir embeddings e associá-los ao comando sem treinar/fine-tunar o encoder.

## Event latch
`ABSENT → ENTER → FIRED → PRESENT → ABSENT`.

Enquanto o mesmo símbolo permanecer `PRESENT`, nenhum comando adicional é emitido.

## Command dispatcher

```ts
dispatch(symbolId): Promise<CommandResult>
undo(mutationId): Promise<CommandResult>
```

### Chat
`SYM-CHAT-001 → OPEN_CHAT`.

### Selector
`SYM-SELECTOR-001 → OPEN_SELECTOR`.

### Done
`SYM-DONE-001 → COMPLETE_LATEST_OPEN_TASK`.

Mutação de Done bem-sucedida deve persistir:

```ts
interface TaskCompletionMutation {
  mutationId: string;
  taskId: string;
  previousState: TaskState;
  newState: "DONE";
  createdAt: string;
}
```

## Unknown/no task
- visual desconhecido → `UNKNOWN` → nenhuma ação;
- nenhuma tarefa aberta → `NO_OPEN_TASK` → nenhuma mutação.

## Technology target from source
- visual feature extractor: `DINOv2 ViT-S/14`;
- mobile runtime: `ONNX Runtime React Native`;
- camera source: Expo/React Native camera stack descrita no corpus;
- inference: local/on-device;
- runtime model artifact: ONNX empacotado no app.

## Target implementation boundaries
O corpus propõe módulos em `apps/mobile/src/features/scanner/vision/`, comandos separados em `scanner/commands/`, assets de modelo/símbolos e contrato compartilhado `visual-symbols.ts`. A implementação real deve seguir a navegação existente e MUST NOT criar arquitetura paralela de rotas.

## Performance and telemetry
Meta declarada, ainda não verificada: `scan-to-command p95 <= 500ms`.

Telemetria proposta:
- `capturedAt`
- `embeddingStartedAt`
- `embeddingCompletedAt`
- `matchedAt`
- `dispatchStartedAt`
- `dispatchCompletedAt`

## Tests
- um ENTER produz um comando;
- PRESENT não repete comando;
- saída/reentrada pode produzir novo evento;
- UNKNOWN não executa;
- offline funciona;
- enrollment não altera pesos;
- Undo restaura a mutação correspondente.

## Mapa-OS integration
Scanner não altera a estrutura do Mapa-OS. O Mapa-OS pode imprimir os símbolos; a ação é resolvida contra o estado digital do app pelo Scanner/CommandDispatcher.
