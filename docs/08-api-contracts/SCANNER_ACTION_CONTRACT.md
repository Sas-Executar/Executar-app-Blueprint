---
id: API-SCANNER-ACTION-001
type: action_contract
status: registered_from_source
version: 1.0.0
owner: null
project: EXECUTAR
---
# Scanner Action Contract

## Boundary
Recognition and action are separate stages:

`Image → VisualSymbolId → Command → Domain Result`

The visual model MUST NOT mutate domain state directly.

## Commands

```ts
type VisualCommand =
  | "OPEN_CHAT"
  | "OPEN_SELECTOR"
  | "COMPLETE_LATEST_OPEN_TASK";
```

## Recognition output

```ts
type RecognitionResult =
  | { status: "RECOGNIZED"; symbolId: string; similarity: number }
  | { status: "UNKNOWN"; similarity?: number };
```

## Dispatch

```ts
dispatch(symbolId: string): Promise<CommandResult>
```

Mappings V1:
- `SYM-CHAT-001 → OPEN_CHAT`
- `SYM-SELECTOR-001 → OPEN_SELECTOR`
- `SYM-DONE-001 → COMPLETE_LATEST_OPEN_TASK`

## Done mutation

```ts
interface TaskCompletionMutation {
  mutationId: string;
  taskId: string;
  previousState: TaskState;
  newState: "DONE";
  createdAt: string;
}
```

Undo:

```ts
undo(mutationId: string): Promise<CommandResult>
```

If no open task can be resolved, return `NO_OPEN_TASK` and do not mutate state.

## Event semantics
One visual appearance generates one command. Repeated frames while the same symbol remains present MUST NOT generate repeated dispatches.

## Mapa-OS relationship
The printed Mapa-OS may expose the three visual symbols as physical controls. The Scanner resolves the symbol against the current digital state; the printed artifact itself does not contain or own the mutation state.
