---
id: UNIT-ECON-001
type: unit_economics_model
status: pre_approved
version: 0.9.0
owner: null
market: Brazil
as_of: 2026-09-09
related:
  - BUS-MODEL-001
  - PRICING-001
  - UNIT-ECON-DATA-001
---
# EXECUTAR — Unit Economics Brasil

## 1. Objetivo

Testar sustentabilidade econômica dos preços propostos para o Brasil sem confundir hipótese com desempenho observado.

## 2. Fontes externas — CORPUS_DIRECT

### OpenAI API
Preços vigentes consultados em 2026-09-09:

- GPT-5.6 Luna: US$0,20 / 1M input; US$1,20 / 1M output.
- GPT-5.6 Terra: US$2,00 / 1M input; US$12,00 / 1M output.
- GPT-5.6 Sol: US$4,00 / 1M input; US$20,00 / 1M output; preço promocional informado como disponível pelo menos até 2026-11-21.

Fonte: https://openai.com/pt-BR/api/

### Câmbio
PTAX venda USD/BRL de 2026-09-08: **R$5,0856/US$**.

Fonte: https://ptax.bcb.gov.br/ptax_internet/consultarUltimaCotacaoDolar.do

### Stripe Brasil
- cartão nacional: 3,99% + R$0,39 por transação;
- Pix: 1,19% por Pix pago;
- Stripe Billing: 0,7% do volume no Billing.

Fonte: https://stripe.com/br/pricing

### WhatsApp via Twilio
- Twilio: US$0,005 por mensagem enviada ou recebida;
- tarifa Meta varia por categoria, país e janela de atendimento;
- utilidade dentro da janela de atendimento pode não ter cobrança Meta, enquanto outras categorias/regras variam.

Fonte: https://www.twilio.com/pt-br/whatsapp/pricing

### Simples Nacional
Para receitas de licenciamento/cessão de uso de software sujeitas ao fator R:

- fator R ≥ 0,28 → Anexo III;
- fator R < 0,28 → Anexo V.

Limite de receita bruta anual do Simples: R$4,8 milhões.

Fontes:
- https://www8.receita.fazenda.gov.br/SimplesNacional/Arquivos/manual/PerguntaoSN.pdf
- https://normas.receita.fazenda.gov.br/sijut2consulta/link.action?idAto=92278

## 3. Premissas de modelagem — PROPOSED

### Mix de contas pagantes

- 55% Solo;
- 35% Pro;
- 10% Business Workspace.

### Preços

- Solo: R$49,90/mês.
- Pro: R$89,90/mês.
- Business: R$499/mês, 5 seats incluídos.

### Pagamentos

- 75% cartão nacional;
- 25% Pix;
- uso de Stripe Billing.

### IA

#### Solo
- 700k input tokens/mês;
- 120k output tokens/mês;
- routing: 85% Luna / 12% Terra / 3% Sol.
- COGS estimado: **R$3,75/mês**.

#### Pro
- 1M input;
- 200k output;
- routing: 75% Luna / 20% Terra / 5% Sol.
- COGS estimado: **R$8,19/mês**.

#### Business — por seat
- 1M input;
- 200k output;
- routing: 60% Luna / 30% Terra / 10% Sol.
- COGS estimado: **R$12,12/seat/mês**.

### WhatsApp

Para modelagem conservadora de provider/canal, usar:

- Solo: 0 mensagens incluídas no baseline;
- Pro: COGS reservado de R$3,63/mês;
- Business: COGS reservado de R$6,04/seat/mês.

Esse valor é **PROPOSED** e não representa tarifa fixa da Meta; deve ser substituído por telemetria real do provider escolhido.

### Infra/suporte variável

- Solo: R$3/mês;
- Pro: R$5/mês;
- Business: R$8/seat/mês.

### OPEX fixo para break-even

**PROPOSED: R$50.000/mês** como cenário-base de planejamento. Não é custo observado.

### CAC alvo

- Solo: R$90;
- Pro: R$160;
- Business Workspace: R$1.200/conta.

## 4. Unit economics por plano

### Pagamentos estimados

Com mix 75% cartão / 25% Pix + Billing:

- Solo: ~R$2,28/mês.
- Pro: ~R$3,88/mês.
- Business Workspace R$499: ~R$20,20/mês.

### Contribuição antes de tributação

| Plano | Receita | Gateway/Billing | IA | WhatsApp | Infra/suporte | Contribuição pré-imposto |
|---|---:|---:|---:|---:|---:|---:|
| Solo | 49,90 | 2,28 | 3,75 | 0,00 | 3,00 | 40,87 |
| Pro | 89,90 | 3,88 | 8,19 | 3,63 | 5,00 | 69,20 |
| Business Workspace | 499,00 | 20,20 | 60,62 | 30,20 | 40,00 | 347,98 |

Business considera 5 seats incluídos.

## 5. Tributação: não usar uma alíquota fixa em toda escala

A simulação inicial de 9% é útil como aproximação local, mas não deve ser usada como modelo de escala.

Assumindo **Anexo III** e fator R ≥28%, a alíquota efetiva depende da RBT12.

Fórmula simplificada:

`aliquota_efetiva = (RBT12 × aliquota_nominal - parcela_deduzir) / RBT12`

Se o fator R ficar abaixo de 28%, o enquadramento muda para Anexo V e o cenário precisa ser recalculado.

## 6. Cenário-base por número de contas pagantes

Mix: 55% Solo / 35% Pro / 10% Business Workspace.

ARPA ponderado mensal: **R$108,81 por conta pagante**.

Custos variáveis não tributários ponderados: **R$27,31/conta/mês**.

| Contas | MRR | ARR | Simples/Anexo III | Contribuição mensal pós-imposto* | OPEX fixo base | Resultado operacional antes de CAC |
|---:|---:|---:|---:|---:|---:|---:|
| 100 | R$10.881 | R$130.572 | 6,00% | ~R$7.497 | R$50.000 | ~-R$42.503 |
| 500 | R$54.405 | R$652.860 | ~10,80% efetivo | ~R$34.874 | R$50.000 | ~-R$15.126 |
| 1.000 | R$108.810 | R$1.305.720 | ~13,27% efetivo | ~R$67.057 | R$50.000 | ~R$17.057 |
| 5.000 | R$544.050 | R$6.528.600 | **fora do limite do Simples** | **GAP** | R$50.000+ | **GAP tributário** |

`*` contribuição = receita - gateway/Billing - IA - WhatsApp - infra/suporte - tributo modelado.

O cenário de 5.000 contas exige modelagem de regime tributário fora do Simples; não é correto extrapolar Anexo III além de R$4,8 milhões.

## 7. Break-even

Com OPEX fixo de R$50 mil/mês e ignorando mudança de faixa tributária, um cálculo estático com contribuição ponderada de ~R$71,70/conta indicaria ~697 contas.

Porém, com tributação progressiva real, o ponto de equilíbrio fica acima desse cálculo simplificado. A tabela mostra que:

- 500 contas ainda não cobrem R$50 mil de OPEX;
- 1.000 contas já cobrem no cenário Anexo III base.

Portanto, o break-even operacional modelado está **entre 500 e 1.000 contas**, devendo ser recalculado por faixa tributária e OPEX real.

## 8. CAC e payback

CAC ponderado proposto pelo mix:

`0,55×90 + 0,35×160 + 0,10×1200 = R$225,50 por conta adquirida`.

Com contribuição simplificada de R$71,70/conta/mês, payback teórico ≈ **3,1 meses**.

Esse número é um guardrail de planejamento e não desempenho observado.

## 9. Caixa de aquisição — cenário simples

CAC de coorte, sem considerar timing de recebimento, churn ou parcelamento:

| Contas adquiridas | Caixa de CAC alvo |
|---:|---:|
| 100 | R$22.550 |
| 500 | R$112.750 |
| 1.000 | R$225.500 |
| 5.000 | R$1.127.500 |

No cenário de OPEX fixo de R$50 mil/mês, uma estimativa simples de 6 meses de runway + CAC da coorte seria aproximadamente:

- 100 contas: ~R$279,5 mil;
- 500 contas: ~R$203,5 mil usando a contribuição tributária corrigida da faixa;
- 1.000 contas: CAC domina o caixa incremental, pois a operação já supera OPEX no cenário-base;
- 5.000 contas: **não modelar sem regime tributário, estrutura de equipe e capital de giro específicos**.

## 10. Stress conditions

Recalcular imediatamente se:

- Sol perder preço promocional ou houver aumento relevante de API;
- consumo médio de tokens exceder 2× a premissa;
- fator R ficar abaixo de 28%;
- mix de cartão aumentar de forma relevante;
- WhatsApp aumentar mensagens iniciadas pela empresa/fora da janela;
- suporte variável subir acima das premissas;
- Business exigir implantação humana intensiva.

## 11. Métricas obrigatórias desde o primeiro pagante

- MRR / ARR;
- paid users / paid workspaces;
- ARPU / ARPA;
- plan mix;
- annual mix;
- AI COGS por usuário e por plano;
- WhatsApp COGS;
- gateway/payment COGS;
- infra/suporte variável;
- contribution margin;
- CAC;
- CAC payback;
- logo churn;
- revenue churn;
- LTV;
- LTV/CAC;
- credit overage rate;
- upgrade/downgrade rate.

## 12. Estado epistemológico

### CORPUS_DIRECT
Tarifas públicas e regras tributárias citadas nas fontes acima.

### CORPUS_DERIVED
Fórmulas, COGS de IA e tabelas calculadas a partir das premissas.

### PROPOSED
Preços, mix, CAC, consumo, OPEX, uso de WhatsApp e targets de margem.

### GAP
Todos os indicadores reais do EXECUTAR e o regime tributário pós-Simples.