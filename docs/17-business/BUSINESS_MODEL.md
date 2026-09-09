---
id: BUS-MODEL-001
type: business_model
status: pre_approved
version: 0.9.0
owner: null
market: Brazil
related:
  - PROD-001
  - PROD-FLOW-001
  - PRICING-001
  - UNIT-ECON-001
---
# EXECUTAR — Modelo de Negócio Brasil

## 1. Categoria

**PROPOSED** — O EXECUTAR é tratado comercialmente como `Adaptive Work Execution SaaS` / `AI-native Work Execution Platform`, com entrada `solo-first` e expansão posterior para contas Business.

A unidade de valor não é armazenamento de tarefas. O produto monetiza a capacidade de transformar objetivos, projetos e compromissos em execução contínua, com Copiloto, planejamento/replanejamento, Mapa-OS, Scanner, Reports, Rotinas e canais autorizados.

## 2. Motion de mercado

**PROPOSED**:

`Prosumer PLG → Solo/Pro self-service → expansão Business → Enterprise`.

- aquisição principal inicialmente self-service;
- trial para ativação;
- assinatura recorrente em BRL;
- expansão por plano, workspace/seats e consumo variável;
- implantação assistida somente nas camadas Business/Enterprise quando necessária.

## 3. Unidade econômica

### B2C / Prosumer

Unidade principal: `active_executor / month`.

### B2B

Unidade principal recomendada: `workspace / month`, com seats incluídos e expansão por seat.

Essa distinção evita tratar um contrato Business como se tivesse o mesmo CAC e custo de atendimento de um usuário Solo.

## 4. Fontes de receita

**PROPOSED**:

1. assinatura SaaS recorrente;
2. `Execution Credits` / uso adicional de IA;
3. uso adicional de canais com custo variável, especialmente WhatsApp;
4. expansão de seats/workspaces Business;
5. implementação/serviços Enterprise futuros;
6. add-ons futuros de integração, marketplace e produtos físicos, desde que aprovados em artefatos próprios.

## 5. O que não deve ser a métrica principal de cobrança

**PROPOSED** — não cobrar como unidade principal por:

- tarefa criada;
- tarefa concluída;
- projeto;
- scan;
- impressão de Mapa-OS;
- comando simples do Copiloto.

Essas operações formam a experiência central e não devem criar microfricção de pagamento.

## 6. Trial e free tier

**PROPOSED**:

- trial: 14 dias;
- acesso amplo ao Pro durante trial;
- sem `free forever` amplo no lançamento;
- eventual free tier futuro somente após dados reais de ativação, retenção e COGS.

## 7. Regra de IA

**PROPOSED**:

`assinatura → franquia incluída → overage/top-up`.

O usuário não compra tokens. A unidade comercial deve ser `Execution Credits` ou outra abstração equivalente.

Operações simples e de estado devem ser economicamente baratas; operações caras podem consumir franquia, por exemplo:

- engenharia de plano;
- replanejamento complexo;
- análise extensa de documentos;
- processamento multimodal;
- grandes sincronizações.

O roteamento técnico deve privilegiar modelo adequado ao trabalho, em vez de usar o modelo mais caro em todas as interações.

## 8. WhatsApp e canais variáveis

**PROPOSED** — WhatsApp não deve ser prometido como ilimitado sem medição. O custo depende de provider, categoria de mensagem e janela de atendimento. O modelo comercial deve suportar franquia + excedente.

## 9. Pagamentos Brasil

**PROPOSED**:

### Solo/Pro
- cartão;
- Pix;
- mensal e anual.

### Business
- cartão;
- Pix;
- boleto quando economicamente/operacionalmente adequado;
- faturamento anual/semestral futuro.

## 10. Guardrails

- `AI COGS / revenue` alvo: ≤8% Solo; ≤10% Pro; ≤10–12% Business.
- `Contribution Margin` alvo: ≥70% Solo; ≥65% Pro; ≥60% Business no estágio inicial.
- `CAC payback` alvo: <6 meses para Solo/Pro e <12 meses para Business; meta operacional preferida menor que isso.
- Não declarar `CAC`, `churn`, `LTV`, `ARPU` ou margem como observado até existir telemetria real.

## 11. Evidência e limites

### CORPUS_DIRECT
- tarifas públicas atuais de OpenAI API, Stripe, Twilio/WhatsApp e regras públicas do Simples Nacional usadas em `UNIT-ECON-001`.

### CORPUS_DERIVED
- cálculos unitários e cenários derivados das premissas registradas.

### PROPOSED
- planos, preços, CAC alvo, churn, mix de planos, consumo médio, OPEX e políticas de franquia.

### GAP
- CAC real;
- churn real;
- LTV real;
- custo real de suporte;
- consumo real de IA por usuário;
- custo real de WhatsApp por perfil;
- enquadramento tributário definitivo;
- margem realizada.

## 12. Decisão comercial

O modelo recomendado para teste é: `Trial → Solo → Pro → Business Workspace → Enterprise`, com assinatura recorrente como receita principal e uso variável como proteção de margem, não como pedágio sobre a execução básica.