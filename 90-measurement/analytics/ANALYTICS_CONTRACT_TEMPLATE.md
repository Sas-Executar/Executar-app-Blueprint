# Analytics Contract Template

Todo evento de analytics do EXECUTAR deve possuir um Analytics Contract
com os campos abaixo.

```yaml
EVENT_ID:
event:
trigger:
properties: []
identity:                    # como o evento identifica o usuário/sessão
destination:                  # sistema de analytics de destino (packages/analytics)
related_capability:            # CAPABILITY_ID
related_requirement:            # id em 10-PRODUCT/requirements
KPI:                              # referenciar 90-MEASUREMENT/kpis
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
