# Agent Contract Template

Todo agente do EXECUTAR deve possuir um Agent Contract com os campos
abaixo. **Prompts não substituem contratos** — o prompt em
`50-AGENTS/prompts` implementa o contrato, não o define.

```yaml
AGENT_ID:
identity:
mission:
scope:
inputs: []
context: []
tools: []            # referenciar 50-AGENTS/tools
permissions: []
outputs: []
rules: []            # referenciar 50-AGENTS/policies
limits: []
approvals: []        # quando uma ação exige aprovação humana
memory:              # referenciar 50-AGENTS/memory
failure_behavior:
audit:               # o que é registrado, onde
evaluations: []      # referenciar 50-AGENTS/evaluations
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
