# Domain Contract Template

Estrutura mínima para cada tipo de elemento de domínio. Um arquivo por
elemento, na subpasta de `60-CONTRACTS/` correspondente ao tipo.

## ENTITY

```yaml
ENTITY_ID:
name:
description:
attributes: []
identity_key:
relationships: []
states: []            # referenciar 20-DOMAIN/states
permissions: []       # referenciar 20-DOMAIN/permissions
```

## VALUE_OBJECT

```yaml
VALUE_OBJECT_ID:
name:
description:
attributes: []
immutable: true
validation_rules: []
```

## STATE / STATE_MACHINE

```yaml
STATE_MACHINE_ID:
entity:               # ENTITY_ID ao qual pertence
states: []             # referenciar 20-DOMAIN/states
transitions:
  - from:
    to:
    trigger:
    guard:
    side_effects: []
```

## RULE

```yaml
RULE_ID:
description:
applies_to: []          # ENTITY_ID / CAPABILITY_ID
classification:          # CONSTRAINT | DECISION
evidence:                 # A-E, ver 80-GOVERNANCE/TAXONOMY.md
```

## COMMAND

```yaml
COMMAND_ID:
name:
input_schema:
preconditions: []
effects: []
emits_events: []          # referenciar 60-CONTRACTS/events
authorization:
```

## QUERY

```yaml
QUERY_ID:
name:
input_schema:
output_schema:
authorization:
```

## EVENT

```yaml
EVENT_ID:
name:
payload_schema:
emitted_by: []            # COMMAND_ID / trigger de domínio
consumed_by: []
```

## PERMISSION

```yaml
PERMISSION_ID:
description:
applies_to: []            # ENTITY_ID / COMMAND_ID / QUERY_ID
granted_to: []             # papéis/escopos
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
