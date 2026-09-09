# Deliverables

Modelos reutilizáveis de saída das skills registradas do EXECUTAR.

## Regra de placeholder

Todo conteúdo variável deve usar `{{UPPER_SNAKE_CASE}}`.

Não usar como valor padrão:
- datas de exemplo;
- nomes de projeto;
- tarefas preenchidas;
- percentuais;
- evidências;
- temas editoriais;
- owners;
- estados derivados de exemplos.

Podem permanecer literais:
- rótulos de interface;
- IDs de layout/contrato;
- enums normativos;
- instruções estruturais;
- geometria e regras de apresentação.

## Regra de estado

Um template define forma, não prova fatos do projeto e não promove estado. Um artefato populado deve registrar sua fonte canônica e o nível de validação atingido.
