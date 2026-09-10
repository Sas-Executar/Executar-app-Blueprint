# GLOSSARY

Status: `PARTIAL_SPECIFIED`
Sources: manifesto + blueprint

| Termo | Definição canônica inicial |
|---|---|
| `Project` | Unidade agregadora de um objetivo/projeto a ser transformado em execução. |
| `Value Stream` | Agrupamento de fluxo de valor dentro de um Project que contém Deliverables relacionados. |
| `Deliverable` | Entrega observável/resultante do trabalho. |
| `Task` | Unidade planejável necessária para produzir um Deliverable. |
| `Action` | Menor unidade operacional colocada em execução; a experiência privilegia a próxima Action executável. |
| `Evidence` | Registro/artefato que comprova execução/conclusão e alimenta governança. |
| `Capacity` | Quantidade de trabalho que pode ser absorvida em determinada janela/contexto. |
| `Execution Cycle` | Janela operacional de planejamento/execução; o corpus registra ciclos de 72h. |
| `Dependency` | Relação em que um item depende de outro para se tornar executável/concluído. |
| `Blocker` | Condição que impede a execução/elegibilidade de uma unidade de trabalho. |
| `Eligibility` | Condição de uma Action poder competir por execução no estado atual. |
| `Best Next Action` | Próxima Action executável escolhida/indicada pelo sistema a partir do estado, regras, capacidade e dependências. |
| `WIP 1:1` | Política de execução em que uma única Action possui precedência cognitiva ativa por vez, sem impedir múltiplos Projects. |
| `FOCUS` | Estado da Action atualmente ativa. |
| `READY` | Estado de uma Action preparada/elegível para início. |
| `BLOCKED` | Estado de uma Action impedida por blocker/dependência. |
| `DONE` | Estado de uma Action concluída. |
| `Check-in` | Registro de início/contexto de uma sessão operacional. |
| `Checkout` | Registro do ponto de parada, realizado, aberto, blockers e próximo movimento. |
| `Replan` | Reorganização do caminho futuro quando capacidade, dependência ou realidade mudam. |
| `Mapa-OS` | Representação visual do estado operacional do trabalho, incluindo ativo, concluído, bloqueios, dependências, próximo movimento e capacidade. |
| `Scanner` | Ponte físico-digital que reconhece símbolos e aciona comandos autorizados sobre o estado canônico. |
| `Copilot` | Camada operacional baseada em IA que compreende contexto, estrutura trabalho, orienta execução, detecta bloqueios e replaneja. |
| `Status Report` | Artefato emitido a partir do estado/histórico real da execução, não de reconstrução manual posterior. |
| `Canonical State` | Estado operacional único compartilhado pelas superfícies autorizadas do produto. |
| `Emitir` | Transformar execução em evidência, estado, histórico, indicadores, reports e próximos passos. |

## Gaps terminológicos

- distinção final entre `Task` e `Action` em granularidades limítrofes;
- uso formal de `Value Stream` em projetos que não possuam fluxo de valor explícito;
- definição de `Cycle` para além da janela de 72h;
- taxonomia formal de tipos de Evidence.