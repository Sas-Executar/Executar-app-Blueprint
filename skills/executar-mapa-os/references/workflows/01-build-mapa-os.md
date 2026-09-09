---
id: WF-MAPA-001
type: skill_workflow
status: registered
version: 1.1.0
skill: executar-mapa-os
---
# Workflow · Construção Canônica do Mapa-OS

## Input
Fontes de projeto, plano, cronograma, status e evidências.

## Flow
1. Inventariar fontes, IDs, versões e datas.
2. Classificar insumos como norma, decisão, estado, evidência, plano, template, exemplo ou conteúdo ilustrativo.
3. Extrair a hierarquia `Projeto → Entrega/Dia Lógico → Fluxo → Ação`.
4. Preservar dependências, critérios, gates, evidências, prazo original e previsão atual.
5. Reconciliar apenas conflitos resolvidos por autoridade explícita; demais conflitos permanecem registrados.
6. Validar estados sustentados por evidência.
7. Aplicar WIP operacional `1 entrega → 1 fluxo → 1 ação`.
8. Calcular elegibilidade por dependências e bloqueios.
9. Selecionar exatamente uma `next_action`, ou registrar `EXIGE_HUMANO`/ausência justificada.
10. Projetar `Agora / Próximo / Depois` sem criar objetos paralelos.
11. Produzir objeto conforme `schemas/output.schema.json`.
12. Executar validação antes de emitir projeções.

## Output
Objeto canônico do Mapa-OS com posição operacional, evidências, bloqueios, horizontes e próxima ação.

## Invariants
- passagem do tempo não muda estado;
- calendário é projeção;
- inferência não vira fato;
- `existente ≠ completo ≠ aprovado ≠ implementado ≠ testado ≠ verificado ≠ publicado`;
- item bloqueado não pode ser `next_action`.
