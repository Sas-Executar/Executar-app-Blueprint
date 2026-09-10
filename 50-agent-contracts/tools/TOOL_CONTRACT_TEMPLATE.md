# Tool Contract Template

Toda tool disponível para agentes do EXECUTAR deve possuir um Tool
Contract com os campos abaixo.

```yaml
TOOL_ID:
name:
purpose:
input_schema:        # referenciar 60-CONTRACTS/schemas quando aplicável
output_schema:
authorization:
side_effects: []
idempotency:          # true | false, com justificativa
errors: []
approval:              # requerida? sob quais condições?
audit_event:           # referenciar 90-MEASUREMENT/events se aplicável
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
