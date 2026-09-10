# Integration Contract Template

Toda integração com um provider externo deve possuir um Integration
Contract com os campos abaixo.

```yaml
INTEGRATION_ID:
provider:
purpose:
auth:
read_objects: []
write_objects: []
events: []
webhooks: []            # referenciar 60-CONTRACTS/webhooks
sync_direction:          # one-way (in) | one-way (out) | bidirectional
rate_limits:
retry:
timeout:
idempotency:
failure_behavior:         # referenciar 70-INTEGRATIONS/failure-policies
data_ownership:            # qual sistema é a fonte da verdade para cada objeto
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
