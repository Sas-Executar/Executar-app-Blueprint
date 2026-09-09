---
id: AGENT-ROUTINES-001
type: agent_mode
status: pre_approved
version: 0.9.0
owner: null
project: EXECUTAR
relates_to:
  - ADR-ROUTINES-001
  - PRD-ROUTINES-001
  - SPEC-ROUTINES-001
  - PROMPT-ROUTINES-001
---
# Modo Rotinas

## Definição
`Modo Rotinas` é o modo operacional em que o Copiloto EXECUTAR transforma uma intenção recorrente ou orientada a evento em uma automação governada, executa-a sem presença humana quando permitido e entrega um Status Report rastreável.

Não é um cron genérico. Uma rotina inclui contexto, autoridade, regras de estado, dependências, WIP, evidência, report e canais.

## Objetivo
Externalizar do usuário operações repetitivas de:
- consultar estado;
- reconciliar fontes;
- detectar o que está pronto;
- atualizar projeções de execução;
- calcular progresso;
- emitir fechamento/abertura;
- comunicar status.

## Como o usuário configura
O usuário pode descrever a rotina em linguagem natural. O agente deve converter a descrição em campos explícitos e não inventar dados ausentes.

Entrada mínima:
- `{{ROUTINE_NAME}}`;
- `{{PROJECT_OR_SCOPE}}`;
- `{{TRIGGER_OR_SCHEDULE}}`;
- `{{TIMEZONE}}`;
- `{{SOURCES}}`;
- `{{DESIRED_OUTCOME}}`;
- `{{DELIVERY_CHANNELS}}`.

Campos adicionais quando aplicáveis:
- regras de elegibilidade;
- transições automáticas autorizadas;
- recipient refs;
- template;
- retry;
- limites de capacidade;
- alertas.

## Comandos conceituais
- `/rotinas` — listar rotinas e estados;
- `/nova-rotina` — coletar configuração;
- `/rotina {{ROUTINE_ID}}` — inspecionar configuração;
- `/executar-rotina {{ROUTINE_ID}}` — executar agora;
- `/pausar-rotina {{ROUTINE_ID}}`;
- `/ativar-rotina {{ROUTINE_ID}}`;
- `/editar-rotina {{ROUTINE_ID}}`.

Os comandos são contrato de UX proposto; sua implementação depende da camada de produto/runtime.

## Ciclo de uma execução

```text
TRIGGER
→ LER
→ VALIDAR
→ SINCRONIZAR
→ CALCULAR
→ VERIFICAR AUTORIDADE
→ AUTOGERIR O PERMITIDO
→ DETERMINAR AGORA
→ GERAR REPORT
→ SALVAR EM REPORTS
→ ENTREGAR NOS CANAIS
→ VALIDAR RECIBOS
→ REGISTRAR RUN
```

## Regra de fonte de verdade
Cada fonte tem papel explícito. Exemplos de papéis:
- `definition_authority`: dependências, DoD, regras e evidência esperada;
- `state_authority`: estado vivo dos objetos;
- `mirror`: cópia derivada/sincronizada;
- `evidence`: prova necessária para promover estado.

O agente não escolhe silenciosamente qual fonte vence.

## Regra de autogestão
O baseline permite automação determinística e reversível/baixo risco, como sincronização e promoção para READY quando as dependências forem satisfeitas.

`DOING`, `VERIFY`, `DONE`, `TESTED`, `VERIFIED` e `PUBLISHED` não são promovidos automaticamente no baseline. A conclusão continua dependente da política de evidência e autoridade.

## Report padrão
Cada rotina pode emitir `EXECUTAR_ROUTINE_STATUS_V1`, adaptado do contrato visual de Status Report existente, contendo:
- header;
- progresso;
- profundidade;
- tríptico anterior/atual/próximo;
- AGORA;
- properties 3P+N;
- risco/prevenção;
- entrega;
- tags;
- bloqueios/evidências;
- delivery status.

## Canais
### App Reports
Versão completa, persistente e consultável.

### Email
Versão HTML completa + fallback texto.

### WhatsApp
Versão curta, orientada à decisão, com `AGORA`, progresso, bloqueio e link para o report completo quando disponível.

## Falha segura
- fonte obrigatória indisponível → `BLOCKED`;
- conflito de estado → `BLOCKED`;
- empate não resolvido → `EXIGE_HUMANO`;
- falha de canal → report permanece salvo; apenas a entrega falha;
- retry não repete mutações.

## Definição de sucesso
A rotina só é `SUCCESS` quando:
- fontes necessárias foram lidas;
- regras foram validadas;
- mutações realizadas estavam autorizadas;
- report canônico foi persistido;
- cada canal habilitado possui resultado registrado.

Um canal `FAILED` pode tornar o run `PARTIAL` sem invalidar o report ou o estado já reconciliado.
