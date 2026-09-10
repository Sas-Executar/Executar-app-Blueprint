# SRC-SCANNER-RUNTIME-FOLLOWUP-001

| Campo | Valor |
|---|---|
| `SOURCE_ID` | `SRC-SCANNER-RUNTIME-FOLLOWUP-001` |
| `source_name` | `visao.md` |
| `date_received` | `2026-09-09` |
| `type` | Follow-up operacional de engenharia / Scanner Visual |
| `epistemic_classification` | `D · INTERNAL` |
| `sha256` | `afbcf7b7b63f395a50f2312bb4c02b7209536c9414e06376d9e617e8d788cd1d` |
| `normalization_status` | `CLASSIFIED` |
| `raw_location` | Upload da conversa; original preservado pelo hash acima |

## Roteamento

Apesar do nome `visao.md`, esta fonte **não é uma Product Vision**. Ela descreve um follow-up de implementação para o Visual Symbol Scanner V2.

Ela registra requisitos operacionais específicos, entre eles:

- Scanner visual sem QR e sem OCR;
- reconhecimento físico de símbolos;
- `Chat → OPEN_CHAT`;
- `Selector → OPEN_SELECTOR`;
- `Done → COMPLETE_LATEST_OPEN_TASK` + Undo;
- ausência de etapa de confirmação no fluxo especificado;
- inferência ONNX on-device;
- rejeição de `UNKNOWN`;
- sessão de modelo reutilizada;
- testes físicos/offline e métricas de latência;
- separação entre reconhecimento e execução do comando.

## Destino

Esta fonte é relevante para capabilities Scanner e execução omnicanal, mas **não deve contaminar o Core Domain geral com detalhes de runtime**. Seus contratos específicos serão normalizados nos workflows de Contracts / Agents / Integration e, no WF-02, usados apenas para registrar a capability e sua relação com o estado canônico.

## Não promover no WF-02

- branch/PR históricos;
- URL de artefato ONNX ainda ausente;
- SHA de modelo ainda ausente;
- afirmações de implementação não revalidadas no runtime atual.