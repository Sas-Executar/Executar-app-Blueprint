# Skill Contract Template

Toda skill usada por um agente do EXECUTAR deve possuir um Skill Contract
com os campos abaixo.

```yaml
SKILL_ID:
trigger:
purpose:
inputs: []
preconditions: []
steps: []
tools: []            # referenciar 50-AGENTS/tools
output:
failure_states: []
evidence:            # classificação epistêmica quando aplicável (80-GOVERNANCE/TAXONOMY.md)
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
