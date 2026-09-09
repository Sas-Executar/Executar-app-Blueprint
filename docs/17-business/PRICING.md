---
id: PRICING-001
type: pricing_strategy
status: pre_approved
version: 0.9.0
owner: null
market: Brazil
currency: BRL
related:
  - BUS-MODEL-001
  - UNIT-ECON-001
---
# EXECUTAR — Pricing Brasil

## 1. Estado

Os valores abaixo são **preços de teste `PROPOSED`**. `pre_approved` significa que a arquitetura de cobrança está autorizada para experimentação e modelagem; não significa preço publicado, contrato comercial ativo ou release.

## 2. Estrutura recomendada

| Plano | Mensal | Anual de teste | Unidade | Papel |
|---|---:|---:|---|---|
| Trial | R$0 | — | 14 dias | ativação |
| Solo | R$49,90 | R$499/ano | 1 executor | sistema de execução |
| Pro | R$89,90 | R$919/ano | 1 executor | automação + omnicanal |
| Business | R$499/mês | R$5.390/ano | workspace, 5 seats incluídos | governança e gestão multiusuário |
| Enterprise | custom | custom | contrato | integrações, SLA e implantação |

Seat Business adicional: **PROPOSED R$89/mês**, ainda sujeito a teste de disposição a pagar e custo real de suporte.

## 3. Solo

Inclui como proposta de teste:

- projetos/tarefas/ações;
- WIP 1:1, Lista e Kanban;
- Agora/Hoje/Amanhã;
- Copiloto;
- planejamento/replanejamento dentro de franquia;
- Status Report;
- Mapa-OS;
- Scanner;
- onboarding;
- franquia básica de IA.

Princípio: Copiloto, Mapa-OS e Scanner não devem ser escondidos no plano mais caro, porque compõem o produto central.

## 4. Pro

Além do Solo:

- Rotinas;
- automações;
- Remix multi-project;
- maior franquia de IA;
- Email/WhatsApp conforme franquia;
- MCP quando implementado e autorizado;
- workflows;
- Reports avançados;
- personalização de símbolos/ações do Scanner conforme policy;
- histórico e integrações ampliadas.

Preço-base recomendado para teste: **R$89,90/mês**. R$79,90 permanece apenas como variante experimental de preço, não baseline econômico.

## 5. Business

Modelo recomendado: **workspace como contrato**, não um único seat como contrato.

Baseline:

- R$499/mês;
- 5 seats incluídos;
- governança, permissões, auditoria, workflows compartilhados e controles organizacionais quando implementados;
- expansão por seats adicionais;
- Enterprise separado para requisitos de implantação/SLA/SSO específicos.

Alternativa de experimento: R$129–149/seat/mês com mínimo de 5 seats. Esta alternativa não é o baseline deste documento.

## 6. Annual

Política proposta:

- Solo: desconto aproximado de 16–17%;
- Pro: desconto aproximado de 15%;
- Business: desconto aproximado de 10%.

A redução é menor nos planos de maior COGS porque IA, canais e infraestrutura continuam sendo consumidos mensalmente.

## 7. Usage layer

### Execution Credits

- franquia incluída por plano;
- top-up/overage após franquia;
- não expor tokens de modelo ao usuário;
- não cobrar por operações simples de estado quando puderem ser executadas com COGS marginal mínimo.

### WhatsApp

- franquia incluída no Pro/Business quando o canal estiver implementado;
- excedente por uso;
- preço final depende do provider/BSP, categoria da mensagem e janela de atendimento.

## 8. Pagamentos

**PROPOSED**:

- cartão nacional;
- Pix;
- boleto para Business quando aplicável;
- cobrança mensal e anual;
- NF e faturamento empresarial quando a operação estiver constituída para isso.

## 9. Guardrails de pricing

Não publicar uma promessa de `IA ilimitada` ou `WhatsApp ilimitado` antes de observar consumo real.

Reavaliar preço quando qualquer condição persistir por 2 ciclos de faturamento:

- margem de contribuição Solo <70%;
- Pro <65%;
- Business <60%;
- AI COGS acima do limite do plano;
- CAC payback acima dos limites definidos em `BUS-MODEL-001`;
- suporte variável maior que a premissa de `UNIT-ECON-001`.

## 10. Métrica primária

- Solo/Pro: `active_executor_month`.
- Business: `active_workspace_month` + expansão por seats.

A cobrança não deve transformar tarefa, scan, Mapa-OS ou comando simples em unidade principal de preço.