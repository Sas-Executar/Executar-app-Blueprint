# Taxonomy

Duas classificações são obrigatórias para todo conteúdo incorporado a este
repositório.

## 1. Classificação de conteúdo

| Tipo | Significado |
|---|---|
| `SOURCE` | Material bruto recebido, ainda não normalizado. |
| `REQUIREMENT` | Requisito confirmado, rastreável a uma capability. |
| `DECISION` | Decisão registrada (ADR ou registro em `80-GOVERNANCE/decisions`). |
| `CONSTRAINT` | Restrição de negócio, técnica, legal ou de segurança/privacidade. |
| `CONTRACT` | Especificação formal de interface (domínio, API, evento, agente, etc.). |
| `GAP` | Ausência de informação identificada e registrada explicitamente. |
| `CONFLICT` | Duas ou mais fontes se contradizem; registrado, não resolvido silenciosamente. |
| `PROPOSAL` | Ideia ou sugestão ainda não aprovada. |

**Regra central: `PROPOSAL` nunca deve ser apresentado ou convertido
automaticamente em `REQUIREMENT`.** A conversão exige uma `DECISION`
explícita e registrada.

## 2. Classificação epistêmica (evidência)

| Código | Significado |
|---|---|
| `A` | Observado — evidência direta observada (ex.: comportamento medido). |
| `B` | Primário — vindo diretamente do stakeholder/fonte primária. |
| `C` | Publicado — documentação ou material publicado externamente. |
| `D` | Interno — documento/decisão interna da organização. |
| `E` | Inferido — conclusão derivada, não observada nem declarada diretamente. |

**Regra central: uma inferência (`E`) nunca deve ser apresentada como
evidência observada (`A`).** Todo conteúdo classificado como `E` deve
declarar isso explicitamente.

## Onde aplicar

Toda página de capability, requirement, decision, contract ou fonte em
`99-SOURCES/` deve declarar sua classificação de conteúdo e, quando
aplicável, sua classificação epistêmica.
