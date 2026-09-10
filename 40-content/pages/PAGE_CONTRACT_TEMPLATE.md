# Page Contract Template

Todo página do produto EXECUTAR deve possuir um Page Contract com os
campos abaixo antes de ser considerada `READY` para implementação.

```yaml
PAGE_ID:
route:
purpose:
ICP:
primary_action:
secondary_actions: []
sections: []
components: []      # referenciar 30-DESIGN/components
states: []           # ex.: loading, empty, error, success
copy_refs: []        # referenciar 40-CONTENT/copy
asset_refs: []       # referenciar 40-CONTENT/assets
SEO:
  title:
  description:
  # detalhamento completo em 40-CONTENT/seo
analytics: []        # referenciar 90-MEASUREMENT/events
responsive:
  # comportamento por breakpoint (ver 30-DESIGN/foundations)
accessibility:
  # requisitos aplicáveis (ver 30-DESIGN/accessibility)
requirements: []      # referenciar 10-PRODUCT/requirements
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
