# Token Model

Todo token de design do EXECUTAR segue obrigatoriamente o modelo de três
camadas:

```
PRIMITIVE
  ↓
SEMANTIC
  ↓
COMPONENT
```

Exemplo:

```
primitive.green.500
  ↓
action.primary
  ↓
button.primary.background
```

- **`PRIMITIVE`** (`30-DESIGN/tokens`) — valores brutos (cor, tamanho,
  espaçamento) sem significado semântico. Vivem apenas aqui.
- **`SEMANTIC`** (`30-DESIGN/semantic-tokens`) — tradução de primitivos
  para intenção de uso (ex.: `action.primary`, `surface.danger`).
- **`COMPONENT`** (`30-DESIGN/component-tokens`) — tokens consumidos
  diretamente por um componente específico (ex.:
  `button.primary.background`), sempre derivados de um token semântico.

## Regra

**Não espalhar valores visuais diretamente por documentos ou
componentes.** Um component spec (`30-DESIGN/components`) referencia um
component token, nunca um valor primitivo bruto.

## Status

Nenhum valor real de token foi ingerido ainda — este documento define
apenas o modelo. Os valores reais entram via
`80-GOVERNANCE/CONTRIBUTION_RULES.md` (lote "Design System").
