# O PRINCÍPIO DO LEILÃO REVERSO
### Manual técnico do Shopee Ads oCPM
**Efeito Vendas · versão 2.0 · julho 2026**

---

# PARTE 0 — COMO USAR ESTE DOCUMENTO

Este documento tem dois leitores.

**Para o time:** é material de treinamento e base de decisão. Cada conceito é explicado antes de virar regra, e cada regra diz o que fazer na prática.

**Para uma IA de análise:** é especificação. Toda regra tem limiar numérico explícito, toda afirmação tem origem declarada, e a Parte 9 traz a lógica de decisão em forma executável.

## 0.1 Sistema de proveniência

Cada afirmação deste documento carrega uma etiqueta. Ela existe para que ninguém — nem pessoa nem máquina — afirme com mais força do que a evidência sustenta.

| Etiqueta | Significa | Como tratar |
|---|---|---|
| **[MEDIDO]** | Calculado sobre os dados da operação. Traz o n da amostra | Afirmar com confiança, citando o n |
| **[DOCUMENTADO]** | Publicado pela Shopee ou literatura técnica da indústria | Afirmar com confiança, é fato externo |
| **[DERIVADO]** | Consequência algébrica de definições | Sempre verdadeiro, mas não prova nada sobre o algoritmo |
| **[HIPÓTESE]** | Inferência plausível ainda não testada diretamente | Apresentar como hipótese, nunca como fato |

**Regra de ouro:** nada neste documento é [MEDIDO] sem o número de observações. Se não tem n, não é medição.

## 0.2 Instruções para a IA que ler este documento

Se você é um modelo construindo o motor de análise da Efeito Vendas, siga estas diretrizes:

1. Use as fórmulas da Parte 2 e os limiares da Parte 3 exatamente como escritos
2. Antes de emitir qualquer diagnóstico sobre um produto, verifique a **Lei 1 (Legibilidade)** — abaixo do limiar, não emita julgamento de desempenho
3. Aplique o **ROAS Ajustado** (Parte 4.1) antes de classificar qualquer produto
4. Nunca conclua nada da lista de anti-regras (Parte 9.5)
5. Calibre a força da afirmação pela etiqueta de proveniência
6. A Parte 9 contém a especificação executável completa

---

# PARTE 1 — O MECANISMO

## 1.1 O que mudou de fato na transição

Em maio de 2026 a Shopee migrou o modelo de cobrança dos anúncios de CPC (custo por clique) para oCPM (custo otimizado por mil impressões).

O mercado tratou isso como catástrofe. Os dados não confirmam.

**[MEDIDO]** Comparando novembro/2025 (CPC maduro) com julho/2026 (oCPM maduro), carteira agregada, 167 contas:

| Métrica | Nov/2025 (CPC) | Jul/2026 (oCPM) | Variação |
|---|---|---|---|
| ROAS | 8,54× | 8,81× | +3% |
| CPM | R$4,26 | R$5,13 | **+20%** |
| CTR | 2,82% | 3,17% | **+12%** |
| Conversão | 2,51% | 2,93% | +17% |
| Ticket | R$51 | R$49 | −4% |

**A leitura correta:** o CPM subiu 20% e foi integralmente absorvido pela melhora de CTR e conversão. O algoritmo passou a entregar impressões para público mais bem casado com o produto, e cobra mais caro por essa qualidade. Para o vendedor, o resultado líquido foi neutro a levemente positivo.

**[MEDIDO]** A distribuição do ROAS entre produtos permaneceu estável nos 9 meses: p10 em torno de 2,7×, mediana em torno de 7×, p90 em torno de 13×. A amplitude p90÷p10 nunca saiu da faixa de 4 a 5 vezes.

**Correção importante em relação a versões anteriores deste manual:** a afirmação de que houve um "vale" em maio, com ROAS caindo para 7,8×, era artefato de cálculo — vinha de calcular a média simples dos ROAS de cada conta, em vez de ponderar por gasto. No cálculo correto (GMV total ÷ gasto total), maio fechou em 8,81×, dentro da faixa normal.

**A lição estratégica permanece, e fica mais forte:** o mercado entrou em pânico com uma transição que, nos números, foi suave. Quem reagiu ao pânico — cortando orçamento, pausando produtos, revertendo métodos de lance — se machucou sozinho. A turbulência era percebida, não real.

## 1.2 O que significa o "o" de otimizado

**[DOCUMENTADO]** O Brasil opera em oCPM, não CPM puro. A diferença é fundamental e quase ninguém no mercado a entende.

**CPM puro** é um contrato de preço sem inteligência: o anunciante paga um valor fixo por mil impressões, independentemente de quem vê. É usado em campanhas de marca, onde o objetivo é alcance.

**oCPM** é um sistema de otimização. O anunciante não declara preço — declara intenção (meta de ROAS e orçamento). O sistema calcula, **para cada impressão individual**, quanto aquela oportunidade vale.

### Os cinco passos do oCPM

**Passo 1 — Você declara intenção, não lance.**
No GMV Max você informa a meta de ROAS e o orçamento diário. Nunca digita um valor de lance.

**Passo 2 — O sistema traduz a meta em valor por conversão.**
Se o ticket do produto é R$80 e a meta de ROAS é 8×, o sistema deduz que você aceita pagar até R$10 por venda (80 ÷ 8). Esse é o seu lance por conversão implícito.

**Passo 3 — Dois modelos preveem, naquele instante, para aquele comprador.**
Toda vez que existe uma impressão disponível, dois modelos de aprendizado de máquina rodam:
- **pCTR** — probabilidade daquele comprador específico clicar no seu anúncio
- **pCVR** — probabilidade de, clicando, ele comprar

Os modelos consideram quem é o comprador, o que ele viu antes, o histórico do seu produto e o contexto da tela.

**Passo 4 — Converte para lance por impressão.**

```
lance_por_impressão = pCTR × pCVR × (ticket ÷ ROAS_alvo) × 1000 × fator_de_controle
```

**Passo 5 — O leilão ordena e cobra.**
Maior lance por impressão vence. A cobrança é por impressão entregue, mesmo que ninguém clique.

### O fator de controle

**[DOCUMENTADO]** É um multiplicador que ajusta o ritmo de gasto. Ele considera o consumo do orçamento diário e o quanto o custo real está se aproximando do custo-alvo. É o mecanismo que espalha o orçamento ao longo do dia em vez de gastar tudo pela manhã, e que aperta ou solta o lance conforme o desempenho versus a meta.

### A implicação prática

**Seu lance muda a cada impressão.** O mesmo produto, no mesmo dia, com a mesma configuração, recebe lance alto para um comprador que o modelo julga quente e lance baixo — ou nem participa do leilão — para um comprador frio.

É por isso que "otimizar lance" deixou de existir como atividade. O lance não é mais um parâmetro que você controla; é uma saída calculada milhares de vezes por dia.

## 1.3 O algoritmo como investidor

Esta é a lente conceitual do método.

Pare de pensar no algoritmo como leiloeiro que entrega ao maior lance. Pense nele como **investidor de risco**. Ele tem um recurso escasso — impressões — e quer alocá-lo onde o retorno é maior.

Como todo investidor, ele avalia quatro coisas antes de apostar:

| O que ele avalia | Métrica | Pergunta que ele faz |
|---|---|---|
| Taxa de execução | Conversão | De cada clique, quantos viram venda? |
| Tamanho da aposta | Ticket | Cada venda sua vale quanto? |
| Poder de atração | CTR | De cada impressão, quantos clicam? |
| Histórico | Dados acumulados | Você já provou antes? |

Daí o nome **Leilão Reverso**: no leilão comum você dá o lance. Aqui, a Shopee dá o lance em você.

### A consequência mais mal compreendida do mercado

**CPM alto não é castigo.** Quando a Shopee cobra mais caro para exibir seu produto, é porque o modelo prevê que ele converte bem — e por isso aquela impressão vale mais.

**[DERIVADO]** Isso decorre diretamente da fórmula do passo 4: o CPM que você paga é o produto de pCTR × pCVR × valor por conversão. Se o CPM subiu sem que você mexesse em nada, foi porque o modelo elevou a previsão de desempenho do seu produto.

**Regra prática:** CPM subindo com ROAS estável ou subindo é sinal positivo. A ação correta é escalar, não pausar.

## 1.4 Calibração: por que produto novo sofre

**[DOCUMENTADO]** Num sistema de leilão, a saída do modelo de previsão não é um ranking — é um preço. A plataforma cobra contra aquela probabilidade prevista.

Isso impõe uma exigência técnica severa: o modelo precisa ser **calibrado**, não apenas ordenar corretamente. Se ele prevê 3% de conversão, o produto precisa converter perto de 3% na realidade. Um modelo que ordena bem mas está descalibrado em 20% cobra a mais ou entrega a menos de todos os anunciantes.

**Consequência para o vendedor:** produto sem histórico tem previsão malcalibrada, e malcalibração custa dinheiro à plataforma. Por isso o sistema é conservador com produtos novos — ele entrega pouco até ter dados suficientes para prever com confiança.

**[DOCUMENTADO]** A fase de aprendizado dura de 7 a 14 dias após configurar ou alterar significativamente um anúncio. Durante esse período o desempenho flutua enquanto o modelo calibra.

**Regra prática:** não tocar no produto nos primeiros 7 dias. Cada alteração relevante reinicia a calibração e joga fora o trabalho estatístico já feito.

## 1.5 A janela de atribuição

**[DOCUMENTADO]** A Shopee atribui conversões em até **7 dias após o clique** e 1 dia após a visualização.

**A consequência é crítica e quase ninguém opera considerando ela:**

Uma venda de hoje pode ser creditada a um anúncio de seis dias atrás. Portanto, **o ROAS dos últimos 7 dias está sempre subestimado** — as conversões daquele período ainda não terminaram de chegar.

**[DOCUMENTADO]** A literatura de sistemas de lance automatizado trata isso explicitamente: confiar em conversões rastreadas em tempo real como sinal para a estratégia de lance superestima o custo por conversão e leva a estratégias excessivamente conservadoras.

**Regra prática, obrigatória:**
- Nenhuma decisão baseada em janela menor que 7 dias
- Toda avaliação de desempenho **exclui os últimos 7 dias**
- Mês corrente nunca se compara com mês fechado

**Impacto estimado na operação:** boa parte das decisões de "pausar produto ruim" provavelmente foi tomada sobre números que se completariam dias depois.

---

# PARTE 2 — A ANATOMIA DO ROAS

## 2.1 A identidade

```
ROAS = Ticket × Conversão × CTR × 1000 ÷ CPM

Lance = Ticket × Conversão ÷ ROAS_alvo
```

**[DERIVADO]** Esta é uma identidade algébrica. Abrindo as definições:

```
Ticket    = GMV ÷ Conversões
Conversão = Conversões ÷ Cliques
CTR       = Cliques ÷ Impressões
ROAS      = GMV ÷ Gasto
```

Substituindo e cancelando os termos, sobra `Gasto ÷ Impressões × 1000` — que é a definição de CPM. A equação é verdadeira em qualquer plataforma de anúncios, em qualquer época, inclusive no modelo CPC antigo.

**Por que isso importa para o documento:** versões anteriores deste manual apresentavam esta fórmula como descoberta validada em 10.263 produtos com erro de 0,0005%. Isso era um erro conceitual — o "erro de 0,0005%" era arredondamento de ponto flutuante, não validação. Qualquer pessoa que abrisse a álgebra poderia desmontar a afirmação.

## 2.2 O que a identidade dá e o que não dá

**Ela dá — e isso é valioso:**
- Existem **exatamente quatro alavancas**: ticket, conversão, CTR e o custo
- Elas se **multiplicam**, não somam. Melhorar duas ao mesmo tempo tem efeito composto
- O ROAS alvo aparece como **denominador** na fórmula do lance — exigir mais derruba a competitividade

**Ela não dá:**
- Não prevê comportamento (não diz o que acontece quando você mexe numa alavanca, porque as alavancas se afetam mutuamente)
- Não prova nada sobre o algoritmo da Shopee especificamente
- Não é diferencial competitivo — qualquer um chega nela

**O diferencial real da Efeito Vendas está na Parte 3:** as leis de comportamento, que só se medem com volume de dados.

## 2.3 Viabilidade competitiva

**[HIPÓTESE]** Lance calculado abaixo de R$0,15 indica que o produto opera predominantemente em inventário residual — as sobras de impressão de baixa disputa.

**Base da hipótese:** **[MEDIDO]** o lance mediano da carteira é R$0,176 (n=1.585 produtos, junho). Produtos abaixo de R$0,15 concentram-se em faixas de GMV baixo.

**Ressalva de honestidade:** este limiar não foi validado contra dados de posicionamento da Shopee, porque a plataforma não expõe essa informação. Use como sinalizador, não como veredito.

**Os três caminhos de resgate, quando o lance é insuficiente:**

```
ticket_necessário    = 0,15 × ROAS_alvo ÷ conversão
conversão_necessária = 0,15 × ROAS_alvo ÷ ticket
ROAS_alvo_máximo     = ticket × conversão ÷ 0,15
```

---

# PARTE 3 — AS LEIS MEDIDAS

Esta é a parte proprietária do método. Cada lei foi medida sobre os dados da operação e não existe em nenhum material público.

**Base de dados comum:** 15.764 registros de produto-mês, 167 contas, novembro/2025 a julho/2026.

---

## LEI 1 — LEGIBILIDADE
### A confiabilidade da leitura depende do volume de conversões

**[MEDIDO]** n = 8 pares de meses consecutivos. Método: correlação do ROAS de um mês com o mês seguinte, para o mesmo produto, segmentada por volume de conversões.

| Conversões/mês | Confiabilidade | Tradução |
|---|---|---|
| menos de 10 | **0,38** | 62% do que você vê é ruído |
| 10 a 30 | **0,53** | metade é ruído |
| 30 a 100 | **0,71** | leitura utilizável |
| mais de 100 | **0,85** | leitura confiável |

A relação é monotônica e se manteve em **todos** os 8 pares de meses, sem exceção.

**O que é "confiabilidade":** é a fração do ROAS observado que se repete no período seguinte. Confiabilidade 0,38 significa que se um produto mostrou ROAS 20× este mês, apenas 38% desse desvio em relação à média é sinal real — o resto é sorte e vai desaparecer.

**LIMIAR OPERACIONAL: 30 conversões acumuladas.**

Abaixo disso, o produto está em **zona de ruído**. Não existe decisão de desempenho válida — nem pausar, nem escalar, nem reformular. As únicas ações permitidas são:
- alimentar o produto com orçamento até gerar volume
- esperar acumular dados

**Por que isso acontece tecnicamente:** [HIPÓTESE, apoiada em [DOCUMENTADO]] o oCPM precisa de conversões para calibrar as previsões de pCTR e pCVR. Produto sem volume nunca calibra bem, e fica preso num limbo onde nem o algoritmo aprende, nem o gestor consegue avaliar.

**Impacto na carteira:** **[MEDIDO]** 39% dos produtos ativos faturam menos de R$500/mês. A maior parte da carteira está, a qualquer momento, na zona ilegível.

---

## LEI 2 — ESCALA É BARATA
### Aumentar o gasto não destrói o ROAS

**[MEDIDO]** n = 3.517 observações de produto-mês com variação de gasto. Método: regressão da variação logarítmica do GMV contra a variação logarítmica do gasto, dentro do mesmo produto.

```
Δlog(GMV) = 1,03 × Δlog(gasto)        R² = 0,85
```

**Elasticidade de escala = 1,03.** Dobrar o gasto dobra o GMV. Efeito no ROAS ao dobrar: **+2%**.

Por faixa de variação:

| Movimento de gasto | n | Variação de GMV | Efeito no ROAS |
|---|---|---|---|
| subiu mais de 100% | 341 | +209% | +5% |
| subiu 50 a 100% | 412 | +91% | +3% |
| subiu 25 a 50% | 508 | +42% | +2% |
| subiu 5 a 25% | 703 | +16% | +1% |

**Isto contradiz o consenso do mercado.** A ideia de que "escalar derruba o ROAS" não se sustenta nesta carteira, na faixa de gasto praticada.

**Ressalva metodológica obrigatória:** esta é uma medição **observacional**, não experimental. Os produtos que receberam mais orçamento foram escolhidos pelos gestores justamente por já estarem performando bem — existe seleção embutida. O que os dados provam é que **escalar como esta operação escala não destruiu ROAS**. Não provam que escalar aleatoriamente seria gratuito.

**Regra prática:** escalar é a ação padrão para produto legível com margem saudável, não a exceção. Os limites de escala são estoque, margem e capacidade operacional — não o ROAS.

---

## LEI 3 — CORTAR É DESTRUIÇÃO PURA
### Reduzir orçamento encolhe a receita sem ganhar eficiência

**[MEDIDO]** mesma base da Lei 2.

| Movimento | n | Variação de GMV | Efeito no ROAS |
|---|---|---|---|
| cortou mais de 20% | 486 | **−39%** | **−2%** |
| cortou 5 a 20% | 397 | −14% | −1% |

Cortar orçamento **não melhora o ROAS**. Ele piora levemente. O único efeito consistente é a perda proporcional de receita.

**Consequência direta:** a prática de "reduzir investimento para melhorar a eficiência" não tem base nos dados. É destruição de receita sem contrapartida.

---

## LEI 4 — REVERSÃO À MÉDIA
### Quase metade dos produtos ruins se recupera sozinha

**[MEDIDO]** n = 1.237 produtos rastreados de junho para julho, com gasto acima de R$30.

**45% dos produtos com ROAS abaixo de 2× em um mês apresentaram ROAS acima de 4× no mês seguinte**, sem intervenção registrada.

**O que isso significa:** o candidato típico a ser pausado tem chance próxima de moeda de se curar sozinho. Pausar produto por ROAS baixo é, na prática, uma aposta com quase 50% de chance de estar destruindo um produto viável.

**Ressalva:** a medição não consegue separar recuperação natural (reversão à média estatística) de intervenções feitas pelo time e não registradas no sistema. O número real de recuperação espontânea pode ser menor.

---

## LEI 5 — O TICKET NÃO MULTIPLICA O ROAS
### Correção importante em relação a versões anteriores

**[MEDIDO]** n = 1.325 produtos com 5 ou mais conversões, junho/2026.

```
log(ROAS) = 1,14 + 0,226 × log(ticket)        R² = 0,091
```

**Ticket +10% → ROAS +2,2%.** O ticket explica apenas **9,1%** da variação do ROAS entre produtos.

**Por que o efeito é fraco — a decomposição:**

| Efeito de ticket +10% | Variação | R² |
|---|---|---|
| sobre a conversão | **−5,7%** | 0,269 |
| sobre o CPM | **+2,4%** | 0,080 |
| sobre o CTR | +0,9% | 0,024 |

O ticket sobe o lance, mas a conversão cai e o CPM sobe. Os efeitos quase se cancelam.

### O efeito kit também estava errado

**[MEDIDO]** n = 518 produtos identificados como kit versus 1.067 unidades, junho.

Comparação direta: ROAS ponderado de kits 9,29× versus unidades 9,34× — **diferença de −1%**.

Controlando por faixa de ticket:

| Faixa de ticket | Kit | Unidade | Diferença |
|---|---|---|---|
| R$0-50 | 6,80× | 6,63× | +3% |
| R$50-100 | 7,58× | 7,48× | +1% |
| R$100-200 | 7,34× | 7,30× | +1% |

**A afirmação de "+37% de ROAS para kits", presente em versões anteriores deste manual, era resultado de confundimento** — kits têm ticket maior, e a comparação não controlava por isso. O efeito real do formato kit sobre o ROAS é de 1 a 3 pontos percentuais, dentro da margem de ruído.

### O que continua verdadeiro sobre o ticket

- Ticket maior **aumenta o lance** e portanto a competitividade no leilão (isso é [DERIVADO] da fórmula)
- Kit continua fazendo sentido por **margem, logística e valor percebido** — não por ROAS
- Produtos de ticket muito baixo têm dificuldade estrutural, porque o custo fixo por venda (comissão fixa de R$4 a R$26) pesa proporcionalmente mais

**Como comunicar isso ao cliente ou aluno:** kit é uma estratégia de margem e de ticket médio da loja, não uma alavanca de ROAS. Prometer ganho de ROAS via kit é prometer o que os dados não entregam.

---

## LEI 6 — SATURAÇÃO DE AUDIÊNCIA
### Escalar dilui a qualidade do público, mas pouco

**[MEDIDO]** n = 1.325 produtos, junho.

| Efeito de dobrar impressões | Variação |
|---|---|
| sobre o CTR | +4,5% |
| sobre a conversão | **−7,2%** |

Ao ampliar o alcance, o algoritmo alcança compradores progressivamente menos qualificados. O efeito existe e é mensurável, mas é pequeno o suficiente para não invalidar a Lei 2.

---

## LEI 7 — O CAMPEÃO NASCE GRANDE
### Volume no primeiro mês prevê sucesso; eficiência não

**[MEDIDO]** n = 892 produtos com nascimento identificado e ao menos 3 meses de vida. Método: correlação logarítmica entre métricas do primeiro mês e GMV acumulado nos meses seguintes.

| Métrica do mês 1 | Poder preditivo |
|---|---|
| **GMV** | **0,65** |
| **Conversões** | **0,57** |
| ROAS | 0,50 |
| CTR | 0,27 |
| Conversão % | 0,19 |
| Ticket | 0,16 |

Comparando os 10% de maior GMV futuro com a metade inferior, no **primeiro mês**:

| | Campeões | Demais |
|---|---|---|
| Conversões | 130 | 10 |
| GMV | R$7.159 | R$453 |

**Interpretação:** campeão não é construído por otimização — é detectado por volume inicial. Métricas de eficiência (CTR, taxa de conversão, ticket) quase não preveem o futuro.

**Implicação estratégica:** o trabalho de maior retorno não é otimizar produto medíocre, é identificar cedo qual produto tem tração e alimentá-lo.

---

## LEI 8 — A PROBABILIDADE SE DEFINE CEDO
### O ROAS do primeiro mês determina a chance de sucesso

**[MEDIDO]** mesma base da Lei 7.

| ROAS no mês 1 | Chance de virar campeão | GMV futuro mediano |
|---|---|---|
| menos de 4× | **1%** | R$661 |
| 4 a 8× | 7% | R$2.768 |
| 8 a 15× | 19% | R$8.223 |
| mais de 15× | **40%** | R$21.241 |

**Produto que abre abaixo de 4× tem 1% de chance de virar campeão.** Insistir em otimização de campanha nesse produto é a alocação de esforço mais cara da operação — o problema não está no anúncio, está na oferta.

**Ressalva:** o primeiro mês pode conter fase de aprendizado incompleta. Aplicar a triagem apenas após o produto ter acumulado ao menos 30 conversões (Lei 1) ou 30 dias corridos, o que vier primeiro.

---

# PARTE 4 — LEITURA DE DADOS

## 4.1 ROAS Ajustado

A Lei 1 diz que o ROAS observado de produto de baixo volume é majoritariamente ruído. O ROAS Ajustado corrige isso, aproximando o valor observado de uma referência confiável na proporção do ruído.

```
ROAS_ajustado = C × ROAS_observado + (1 − C) × ROAS_referência

onde C = confiabilidade, pela tabela da Lei 1:
    conversões < 10    →  C = 0,38
    10 ≤ conversões < 30  →  C = 0,53
    30 ≤ conversões < 100 →  C = 0,71
    conversões ≥ 100   →  C = 0,85

ROAS_referência = ROAS agregado da conta (GMV total ÷ gasto total)
                  ou, na ausência, ROAS mediano da faixa de ticket
```

**Exemplo trabalhado:**
Produto com 8 conversões, ROAS observado 18×, numa conta que roda 7× no agregado.
```
ROAS_ajustado = 0,38 × 18 + 0,62 × 7 = 6,84 + 4,34 = 11,2×
```
A leitura correta desse produto é 11,2×, não 18×. A diferença define se ele entra ou não na lista de escala.

**[MEDIDO] Validação:** testado contra a realidade em 1.237 produtos (junho → julho):
- **9,4% menos erro de previsão** que o ROAS cru
- **12% menos erros de classificação** de curva

## 4.2 Janelas válidas de avaliação

| Situação | Regra |
|---|---|
| Últimos 7 dias | **Nunca avaliar** — atribuição incompleta |
| Mês corrente | **Nunca comparar** com mês fechado |
| Produto com menos de 7 dias | **Nunca julgar** — fase de aprendizado |
| Comparação entre períodos | Ambos fechados, mesma duração |
| Janela mínima recomendada | 28 dias, excluindo os últimos 7 |

## 4.3 As sete armadilhas de leitura

Estas são as interpretações erradas mais comuns e mais caras.

**1. CPM alto lido como problema.**
Errado: "o CPM subiu, o anúncio está caro, vou pausar."
Certo: CPM alto com ROAS estável significa que o algoritmo elevou a previsão de desempenho do produto. É sinal de confiança. Ação correta: escalar.

**2. Lance baixo com ROAS alto lido como eficiência.**
Errado: "esse produto tem ROAS 15×, é o melhor da conta."
Certo: verificar o GMV absoluto. ROAS alto sobre faturamento minúsculo indica operação em inventário residual, não eficiência superior.

**3. ROAS alto sem volume tratado como sucesso.**
Um ROAS de 15× sobre R$3 mil não constrói operação. Um ROAS de 9× sobre R$100 mil constrói. O objetivo é lucro absoluto, não percentual.

**4. Julgar mês incompleto contra mês fechado.**
Comparar os 6 primeiros dias de um mês contra o mês anterior fechado produz queda aparente de 70 a 80% que não existe.

**5. Julgar os últimos 7 dias.**
A atribuição não terminou. O ROAS está sistematicamente subestimado.

**6. Julgar produto abaixo de 30 conversões.**
Lei 1. Não há leitura confiável.

**7. Pedir ROAS alvo alto demais.**
O ROAS alvo é denominador na fórmula do lance. Exigir 15× de um produto que converte 1,5% derruba o lance a ponto de o produto sumir dos leilões.

---

# PARTE 5 — A ECONOMIA DO PRODUTO

Nenhuma meta de ROAS faz sentido sem conhecer a margem. Esta parte vem antes de qualquer decisão de anúncio.

## 5.1 Comissões Shopee

**[DOCUMENTADO]**

| Faixa de preço | Comissão |
|---|---|
| até R$79,99 | 20% + R$4 |
| R$80,00 a R$99,99 | 14% + R$16 |
| R$100,00 a R$199,99 | 14% + R$20 |
| R$200,00 ou mais | 14% + R$26 |

**O degrau perigoso:** produto a R$79,99 paga R$20,00 de comissão. A R$80,00 paga R$27,20. Sete reais e vinte centavos a mais por um centavo de preço.

**Antecipação de recebíveis:** 1% (Loja Oficial) · 2,5% (Vendedor Indicado) · 3,5% (demais)

## 5.2 ROAS mínimo

```
ROAS_mínimo = 100 ÷ margem_líquida_percentual
```

| Margem líquida | ROAS de empate |
|---|---|
| 10% | 10,0× |
| 15% | 6,7× |
| 20% | 5,0× |
| 25% | 4,0× |
| 30% | 3,3× |
| 40% | 2,5× |

**Este é o número mais importante da operação e o menos usado.** Sem ele, toda meta de ROAS é arbitrária. Um ROAS de 5× é excelente para margem de 30% e prejuízo para margem de 15%.

## 5.3 Estrutura de custo completa

```
margem_líquida = preço
               − custo_do_produto
               − comissão (tabela 5.1)
               − antecipação (se aplicável)
               − frete_e_embalagem
               − custo_de_ads
```

**Erro comum:** calcular margem sem incluir o custo de ads, e depois comparar com o ROAS. Isso conta o custo de anúncio duas vezes ou nenhuma, dependendo de como a conta é feita. Definir claramente qual margem está em uso.

---

# PARTE 6 — AS ALAVANCAS

## 6.1 Hierarquia

| Ordem | Alavanca | Mecanismo | Evidência |
|---|---|---|---|
| 1ª | Conversão | Entra no lance e na nota de qualidade | [DOCUMENTADO] + [DERIVADO] |
| 2ª | CTR | Converte lance em preço de impressão | [DERIVADO] |
| 3ª | Ticket | Aumenta o lance, mas derruba conversão | [MEDIDO] Lei 5 |
| 4ª | ROAS alvo | Freio e filtro de amplitude de público | [DOCUMENTADO] |

**Nota sobre a ordem:** versões anteriores colocavam o ticket em segundo lugar. A Lei 5 mostrou que o efeito líquido do ticket sobre o ROAS é fraco (+2,2%, R²=0,09), enquanto o CTR entra diretamente na conversão do lance em CPM. A ordem foi corrigida.

## 6.2 Conversão

**[DOCUMENTADO]** A conversão entra duas vezes no sistema: no cálculo do lance por impressão (como pCVR) e na avaliação de qualidade do anúncio.

**[HIPÓTESE]** Por entrar duas vezes, o efeito de melhorar a conversão seria mais que proporcional.

**Ressalva importante:** não é possível medir esse efeito duplo diretamente com os dados disponíveis, porque a conversão faz parte da própria definição de ROAS — qualquer correlação entre as duas é parcialmente circular. A afirmação de "efeito quase quadrático", presente em versões anteriores, era precisão não medida e foi removida.

**O que se pode afirmar:** a conversão é a alavanca de maior impacto porque atua em dois pontos documentados do sistema. A magnitude exata não está medida.

**As cinco alavancas práticas de conversão:**
1. Preço competitivo dentro da faixa do mercado
2. Foto principal clara e honesta
3. Avaliações (prova social)
4. Cupom de desconto
5. Frete grátis

## 6.3 CTR

**[MEDIDO]** Benchmarks, junho/2026:
- Mediana por produto: 2,71%
- Carteira agregada, julho: 3,17%
- Piso de atenção: 1,5%

**O que determina o CTR**, em ordem de peso prático: foto principal, preço visível na vitrine, título, avaliações visíveis na listagem.

**Armadilha:** CTR alto com conversão baixa indica anúncio que atrai e decepciona — a vitrine promete o que a página não entrega. As duas métricas devem ser lidas em par.

## 6.4 ROAS alvo como dial de amplitude

**[DOCUMENTADO]** A Shopee documenta explicitamente: com ROAS alvo alto, o GMV Max direciona os anúncios para público de nicho, filtrando compradores de alta intenção — melhora a eficiência de conversão e limita o alcance. Com ROAS alvo mais baixo, expande a entrega para faixa mais ampla de compradores, aumentando alcance e exposição.

**Isso significa que o ROAS alvo tem duas funções simultâneas:**
1. **Freio de custo** — está no denominador do lance
2. **Filtro de amplitude de público** — define quão restrito é o alvo

É o equivalente moderno da correspondência exata versus ampla do modelo manual antigo. **[DOCUMENTADO]** Naquele modelo, a Shopee cobrava 1,2× o lance quando a correspondência ampla era acionada, e o lance sugerido para ampla era 20% maior que para exata — a diluição de relevância sempre teve preço explícito.

| ROAS alvo | Equivale a | Efeito |
|---|---|---|
| Alto | Correspondência exata | Nicho, alta intenção, pouco volume |
| Baixo | Correspondência ampla | Amplo, mais volume, menos precisão |

## 6.5 Título — o ativo de mídia esquecido

**[DOCUMENTADO]** No GMV Max não existe mais seleção manual de palavras-chave. A Shopee documenta que a correspondência é automática e se baseia em três insumos:
1. O título do produto e o conteúdo do anúncio
2. A intenção de busca do comprador
3. O desempenho e sinais históricos do anúncio

A orientação oficial é direta: focar no título do produto e na qualidade do anúncio, porque palavras-chave relevantes no título ajudam o algoritmo a fazer a correspondência com as buscas certas.

**Implicação:** o título deixou de ser assunto de SEO orgânico e virou **entrada de palavras-chave da campanha paga**. Antes, título fraco era compensado escolhendo boas palavras-chave. Agora não existe essa compensação — título ruim limita os leilões em que o produto sequer entra, e nenhuma otimização de lance corrige isso.

**É um gargalo invisível:** não aparece em nenhuma métrica de ROAS, porque o produto simplesmente não participa dos leilões que perdeu.

## 6.6 Categoria — a decisão irreversível

**[DOCUMENTADO]** A categoria opera em três camadas:

1. **Filtro de elegibilidade** — define em quais leilões o produto entra. É anterior ao ranqueamento
2. **Insumo de relevância** — categoria errada ou atributos incompletos prejudicam a correspondência
3. **Alvo direto no Discovery** — a segmentação de descoberta é por categoria de interesse, com lance dinâmico aumentado em até 2×

**[DOCUMENTADO]** **A categoria é o único campo que não pode ser editado após a publicação.** E cadastrar produto em categoria não correspondente configura infração de spam de categorias, com risco de banimento e exclusão permanente do item.

**Consequência operacional:** a escolha de categoria é decisão de arquitetura, não de operação. Merece etapa formal no cadastro, porque não tem correção posterior.

## 6.7 Formatos de exibição

**[DOCUMENTADO]** Inventário disponível por formato:

| Formato | Inventário |
|---|---|
| Busca | máximo 60 anúncios por palavra-chave; 2 primeiros resultados são anúncios, depois 1 a cada 3 listagens |
| Daily Discover | até 26 anúncios nas primeiras 55 posições |
| You May Also Like | até 12 anúncios nas primeiras 35 posições |

Escassez diferente produz preço de equilíbrio diferente. A lógica de disputa também difere: busca é movida por **intenção** (correspondência com a query), descoberta por **afinidade** (categoria e comportamento passado).

**[HIPÓTESE]** O CPM observado por produto é uma média ponderada entre inventários com preços distintos. Parte da variância de CPM entre produtos pode ser efeito de mix de posicionamento, não de qualidade do anúncio.

**Ação recomendada:** se a exportação da Shopee oferecer quebra de desempenho por posicionamento, essa é a próxima camada de refinamento do modelo.

## 6.8 Métodos de lance

**[DOCUMENTADO] + [MEDIDO]**

| Método | Quando usar |
|---|---|
| Lance Automático | Produto novo, 0 a 100 cliques |
| Meta de ROAS | Produto maduro, 200+ cliques e 20+ conversões |

**A Lei da Âncora:** nunca reverter de Meta de ROAS para Lance Automático.

**[MEDIDO]** Caso registrado na operação: produto que rodava 11,89× caiu para 4,41× após reversão de método. **[MEDIDO]** Durante a turbulência percebida de maio, produtos em Meta de ROAS mantiveram desempenho enquanto os em Lance Automático caíram 32%.

**Mecanismo [HIPÓTESE, apoiada em [DOCUMENTADO]]:** a reversão descarta o histórico de calibração acumulado, devolvendo o produto à fase de aprendizado.

---

# PARTE 7 — CLASSIFICAÇÃO

**Regra que precede toda classificação:** aplicar a Lei 1. Produto abaixo de 30 conversões recebe o rótulo **ILEGÍVEL** e fica fora das listas de ação, independentemente do ROAS.

## 7.1 Curvas

| Curva | Critério | Ação |
|---|---|---|
| A | ROAS_ajustado > 8× **e** CTR > 2% | Replicar e escalar |
| B | ROAS_ajustado entre 4× e 8× | Otimizar conversão |
| C | ROAS_ajustado entre 2× e 4× | Reformular oferta |
| Pausar | ROAS_ajustado < 2× **e** CTR < 1% | Ver protocolo 8.4 antes de pausar |

## 7.2 Quadrantes

Cortes: ROAS ajustado 8× e GMV mensal R$5.000.

| Quadrante | ROAS | Volume | Ação |
|---|---|---|---|
| **OURO** | ≥ 8× | ≥ R$5k | Manter, escalar, replicar o padrão |
| **ESCALA** | < 8× | ≥ R$5k | Atacar conversão — maior oportunidade |
| **NICHO** | ≥ 8× | < R$5k | Ampliar orçamento |
| **FRACO** | < 8× | < R$5k | Verificar legibilidade antes de agir |

**Por que ESCALA é a prioridade:** o volume já existe, que é a parte difícil. Falta eficiência, que é a parte controlável.

**Cuidado com FRACO:** boa parte dos produtos deste quadrante está abaixo do limiar de legibilidade. Antes de qualquer ação, verificar a Lei 1.

---

# PARTE 8 — PROTOCOLOS DE DECISÃO

## 8.1 Protocolo de lançamento

```
Dias 0-7    → Lance Automático. NÃO TOCAR.
              Ignorar completamente os números deste período.

Dias 8-30   → Observar acúmulo de conversões.
              Nenhuma decisão de desempenho antes de 30 conversões.

Marco 30 conversões ou 30 dias → Aplicar TRIAGEM (Lei 8):
     ROAS mês 1 < 4×    → problema é a OFERTA, não a campanha.
                          Reformular preço, foto, proposta.
                          Não investir mais em mídia.
     ROAS 4× a 8×       → manter, otimizar conversão.
     ROAS 8× a 15×      → escalar moderado (+20%/semana).
     ROAS > 15×         → escalar agressivo. Alta probabilidade de campeão.

Marco 200 cliques e 20 conversões → migrar para Meta de ROAS.
                                    NUNCA reverter depois.
```

## 8.2 Protocolo de escala

**Pré-requisitos, todos obrigatórios:**
- Produto legível (≥ 30 conversões/mês)
- ROAS ajustado acima do ROAS mínimo da margem
- Estoque suficiente para o volume projetado
- Fora da fase de aprendizado

**Execução:**
```
incremento = +20% de orçamento por semana
aguardar   = 7 dias entre incrementos, sem outras alterações
projeção   = GMV_novo ≈ GMV_atual × (gasto_novo ÷ gasto_atual) ^ 1,03
```

**Quando parar:** ruptura de estoque, margem comprometida, limite operacional. **Não parar por queda de ROAS de até 5%** — é o efeito esperado pela Lei 6.

## 8.3 Protocolo de resgate

**Para produtos ESCALA (volume alto, ROAS baixo):**
1. Verificar ROAS mínimo da margem — o produto realmente dá prejuízo?
2. Auditar as cinco alavancas de conversão (6.2)
3. Auditar título (6.5) — o produto está entrando nos leilões certos?
4. Meta: conversão acima da mediana da faixa de ticket

**Para produtos FRACO:**
1. **Primeiro:** verificar legibilidade (Lei 1). Se ilegível, alimentar ou aguardar
2. Se legível e ROAS abaixo de 4× desde o lançamento: problema é a oferta (Lei 8)
3. Reformulação de oferta, não otimização de campanha

## 8.4 Protocolo de pausa

**Este protocolo existe para impedir a decisão mais cara da operação.**

**Critérios que NÃO justificam pausar:**
- ROAS baixo isoladamente (Lei 4: 45% se recuperam)
- CPM alto (armadilha 1)
- Desempenho ruim nos últimos 7 dias (atribuição incompleta)
- Produto abaixo de 30 conversões (Lei 1: não há leitura)
- Desejo de "melhorar o ROAS da conta" (Lei 3: não melhora)

**Critérios que justificam pausar:**
- Margem comprovadamente negativa após conta completa (Parte 5)
- Ruptura de estoque
- Problema de qualidade, reclamação ou risco reputacional
- Produto legível, com ROAS abaixo do mínimo da margem, por 3 meses consecutivos

**Regra absoluta:** pausar, **nunca apagar**. Apagar destrói o histórico de calibração permanentemente.

---

# PARTE 9 — ESPECIFICAÇÃO PARA A IA DE ANÁLISE

Esta parte é a camada executável. Uma IA construindo o motor de análise da Efeito Vendas deve implementar exatamente o que está aqui.

## 9.1 Campos de entrada necessários

**Por anúncio, por mês:**
```
conta_id, produto_id, nome_anuncio, mes_referencia
status_anuncio, metodo_lance
impressoes, cliques, conversoes, gmv, despesas
```

**Por conta (contexto):**
```
gmv_total, despesas_total  →  para calcular ROAS_referência
margem_liquida_percentual  →  se disponível; senão, solicitar
```

## 9.2 Cálculos derivados obrigatórios

```python
ctr        = cliques / impressoes
conversao  = conversoes / cliques
ticket     = gmv / conversoes
roas       = gmv / despesas
cpm        = despesas / impressoes * 1000
lance      = ticket * conversao / roas

# confiabilidade (Lei 1)
if conversoes < 10:    C = 0.38
elif conversoes < 30:  C = 0.53
elif conversoes < 100: C = 0.71
else:                  C = 0.85

roas_referencia = gmv_conta_total / despesas_conta_total
roas_ajustado   = C * roas + (1 - C) * roas_referencia

legivel = (conversoes >= 30)
```

## 9.3 Árvore de decisão por produto

```
1. VERIFICAR JANELA
   se periodo inclui os ultimos 7 dias:
       → EMITIR AVISO: "janela contem atribuicao incompleta"
       → NAO emitir diagnostico de desempenho
   se periodo é mes corrente:
       → NAO comparar com mes fechado

2. VERIFICAR LEGIBILIDADE
   se nao legivel (conversoes < 30):
       → classificar como ILEGIVEL
       → acao permitida: apenas "alimentar" ou "aguardar"
       → NAO emitir recomendacao de pausar, escalar ou reformular
       → ENCERRAR analise deste produto

3. VERIFICAR FASE DE APRENDIZADO
   se idade_do_anuncio < 7 dias:
       → classificar como EM APRENDIZADO
       → acao permitida: apenas "aguardar"
       → ENCERRAR

4. VERIFICAR VIABILIDADE ECONOMICA
   se margem disponivel:
       roas_minimo = 100 / margem_percentual
       se roas_ajustado < roas_minimo:
           → sinalizar PREJUIZO
   senao:
       → solicitar margem antes de recomendar meta de ROAS

5. CLASSIFICAR
   curva     = por 7.1, usando roas_ajustado
   quadrante = por 7.2, usando roas_ajustado e gmv

6. VERIFICAR METODO DE LANCE
   se metodo == "Lance Automatico" e cliques >= 200 e conversoes >= 20:
       → recomendar MIGRAR para Meta de ROAS
       → alertar: "nunca reverter depois"

7. GERAR RECOMENDACAO
   OURO   → escalar +20%/semana se estoque permite
   ESCALA → atacar conversao; listar as 5 alavancas; auditar titulo
   NICHO  → ampliar orcamento +20%/semana
   FRACO  → se roas < 4x desde o lancamento: reformular OFERTA
            senao: otimizar conversao

8. VERIFICAR SINAIS DE ESCALA
   se roas_ajustado > roas_minimo * 1.5 e legivel:
       → produto é candidato a escala
       → projetar: gmv_novo = gmv * (gasto_novo/gasto)**1.03
```

## 9.4 Calibração da linguagem por proveniência

A IA deve modular a força da afirmação conforme a origem do dado:

| Etiqueta | Linguagem permitida |
|---|---|
| [MEDIDO] | "Nos dados da operação, X" · "medido em n=Y produtos" |
| [DOCUMENTADO] | "A Shopee documenta que X" · "o sistema funciona assim" |
| [DERIVADO] | "Por definição, X" · "matematicamente, X" |
| [HIPÓTESE] | "Provavelmente X" · "a hipótese é que X" · "ainda não medido" |

**Nunca** apresentar [HIPÓTESE] como fato. **Nunca** apresentar [DERIVADO] como descoberta.

## 9.5 Anti-regras — o que a IA NUNCA deve concluir

```
1. NUNCA recomendar reduzir CPM como objetivo
   → CPM é resultado, não variável de controle

2. NUNCA recomendar pausar por ROAS baixo isolado
   → Lei 4: 45% se recuperam sozinhos
   → usar protocolo 8.4

3. NUNCA recomendar cortar orçamento para melhorar eficiência
   → Lei 3: não melhora, só destrói receita

4. NUNCA afirmar que escalar derruba o ROAS
   → Lei 2: elasticidade 1,03

5. NUNCA prometer ganho de ROAS via kit
   → Lei 5: efeito é de 1 a 3%, dentro do ruído

6. NUNCA classificar produto abaixo de 30 conversões
   → Lei 1: não há leitura confiável

7. NUNCA avaliar janela que inclui os últimos 7 dias
   → atribuição incompleta

8. NUNCA comparar mês corrente com mês fechado

9. NUNCA tratar ROAS alto com volume baixo como sucesso
   → verificar GMV absoluto

10. NUNCA recomendar reverter de Meta de ROAS para Automático

11. NUNCA apresentar a fórmula do ROAS como descoberta proprietária
    → é identidade algébrica

12. NUNCA afirmar magnitude do "efeito duplo" da conversão
    → não medido; afirmar apenas que atua em dois pontos
```

## 9.6 Estrutura de saída recomendada

```
DIAGNÓSTICO DE CONTA
├── 1. Sumário
│      ROAS agregado, GMV, gasto, período avaliado
│      Aviso explícito se alguma janela é incompleta
│
├── 2. Legibilidade da carteira
│      Quantos produtos são legíveis / ilegíveis
│      % do GMV concentrado nos legíveis
│
├── 3. Viabilidade econômica
│      ROAS mínimo da margem versus ROAS real
│      Produtos operando em prejuízo
│
├── 4. Classificação
│      Distribuição por quadrante (apenas produtos legíveis)
│      Distribuição por curva
│
├── 5. Oportunidades priorizadas em R$
│      ESCALA: ganho potencial de conversão
│      NICHO: ganho potencial de escala (elasticidade 1,03)
│      Migração de método de lance
│
├── 6. Alertas
│      Produtos em prejuízo real
│      Produtos maduros em Lance Automático
│      Títulos fracos (se auditado)
│
└── 7. Plano de ação
       Ordenado por impacto em reais
       Cada item com: o quê, por quê (qual lei), meta esperada
```

---

# PARTE 10 — TABELAS DE REFERÊNCIA

## 10.1 Benchmarks por produto
**[MEDIDO]** n=1.585 produtos com volume, junho/2026

| Métrica | p25 | Mediana | p75 |
|---|---|---|---|
| ROAS | 5,0× | 7,2× | 9,5× |
| Conversão | 1,27% | 2,50% | 4,65% |
| CTR | — | 2,71% | — |
| Ticket | — | R$47 | — |
| CPM | — | R$4,60 | — |
| Lance | — | R$0,176 | — |

## 10.2 Ticket × desempenho
**[MEDIDO]** medianas, junho/2026. Usar mediana e não média — a média é inflada por outliers.

| Faixa de ticket | n | ROAS mediano | Conversão mediana | CPM mediano |
|---|---|---|---|---|
| R$0-20 | 88 | 5,7× | 4,92% | R$4,30 |
| R$20-30 | 280 | 6,4× | 4,14% | R$4,33 |
| R$30-40 | 248 | 7,0× | 3,41% | R$4,39 |
| R$40-50 | 255 | 6,8× | 2,42% | R$4,56 |
| R$50-70 | 307 | 7,7× | 2,11% | R$4,58 |
| R$70-100 | 185 | 7,2× | 1,55% | R$5,16 |
| R$100-150 | 99 | 6,7× | 1,11% | R$6,52 |
| R$150-250 | 83 | 8,2× | 1,04% | R$6,60 |
| R$250+ | 40 | 12,0× | 1,02% | R$9,57 |

**Como ler:** o ROAS não sobe de forma limpa com o ticket. A relação é fraca (Lei 5). O padrão consistente é a **conversão caindo** conforme o ticket sobe, e o **CPM subindo**. Use esta tabela para calibrar expectativa de conversão por faixa de preço, não para prometer ROAS.

## 10.3 Mix de fontes de faturamento
**[MEDIDO]** n=603 registros conta-mês com campos preenchidos

| Fonte | % do GMV bruto (ponderado) | Mediana por conta |
|---|---|---|
| Ads | 53,7% | 62% |
| Orgânico | 22,3% | 17% |
| Afiliado | 10,4% | 5,3% |
| Live | 1,1% | — |
| Vídeo | 0,4% | — |
| Não classificado | 12,2% | — |

**Ressalva:** a segunda fonte de dados (métricas diárias) dá Ads 68%, Afiliado 13%, Orgânico 20%, somando 103,8% — o que indica sobreposição de atribuição. Comunicar como faixa: **ads entre 54% e 68%, afiliado entre 10% e 13%**.

## 10.4 Retrato da carteira
**[MEDIDO]**

| Fato | Valor |
|---|---|
| Produtos que geram 50% do GMV | 6,2% |
| Produtos que faturam menos de R$500/mês | 39% |
| Produtos que vivem um único mês | 27% |
| Turnover mensal da base de produtos | 25 a 28% |
| GMV carregado pelos produtos que somem | 2 a 10% |
| Produtos que sobrevivem 9 meses | 6,2% |
| HHI de concentração de contas | 202 (saudável) |

---

# ANEXO — REGISTRO DE CORREÇÕES DA VERSÃO 1

Este anexo existe para impedir que afirmações incorretas retornem ao material.

| Afirmação da v1 | Situação | Correção |
|---|---|---|
| "Fórmula validada com erro de 0,0005%" | **Falso** | É identidade algébrica; o erro era arredondamento. Reposicionada como anatomia |
| "Kits têm ROAS 37% maior" | **Falso** | Confundimento por ticket. Efeito real: +1 a +3% |
| "Ticket multiplica o ROAS" | **Muito exagerado** | Ticket +10% → ROAS +2,2%, R²=0,09 |
| "R$100-150 tem ROAS 29,3×" | **Falso** | Média inflada por outlier. Mediana: 6,7× |
| "Maio foi turbulência, ROAS caiu a 7,8×" | **Falso** | Artefato de média simples. Ponderado: 8,81× |
| "Conversão quase quadruplica o resultado" | **Não medido** | Removido. O efeito duplo é documentado, a magnitude não |
| "Mix: 83% ads, 11% orgânico, 6% afiliado" | **Falso** | Erro de campos vazios tratados como zero. Correto: 54-68% ads |
| Checklist mandava "pausar produto FRACO" | **Contradiz os dados** | Leis 3 e 4. Substituído pelo protocolo 8.4 |
| Gráfico "ROAS por decil de conversão" | **Circular** | Conversão está dentro da definição de ROAS. Removido |
| Case 2 projetava CPM fixo | **Inconsistente** | Contradiz a tese do próprio documento (o CPM reprecifica) |

---

# A TESE

> **O ROAS não é o objetivo. É o pedágio.**
>
> **O recurso escasso no oCPM é volume de conversão por anúncio — porque ele é, ao mesmo tempo, o que torna o produto legível para o gestor e o que o algoritmo usa para calibrar a previsão.**
>
> **A operação média gerencia ao contrário: dispersa orçamento entre muitos produtos (mantendo todos ilegíveis), corta os que parecem ruins (destruindo receita sem ganhar eficiência), e persegue ROAS alto — que é consequência, não causa.**

## O que este manual corrige no mercado

| O mercado ensina | Os dados mostram |
|---|---|
| Escalar derruba o ROAS | Elasticidade 1,03 — não derruba (Lei 2) |
| Pause o que está ruim | 45% se recuperam sozinhos (Lei 4); cortar tira 39% do GMV (Lei 3) |
| Kit aumenta o ROAS | Efeito de 1 a 3%, dentro do ruído (Lei 5) |
| Ticket multiplica o ROAS | +2,2% com R² de 0,09 (Lei 5) |
| CPM alto é problema | É sinal de confiança do algoritmo |
| Otimize cada anúncio | Abaixo de 30 conversões não há o que otimizar (Lei 1) |
| Persiga ROAS alto | ROAS é pedágio; o ativo é volume legível |

## Previsões falsificáveis

O que torna isto uma tese e não uma opinião. Testável em 60 dias com grupo de controle:

1. Contas que pararem de pausar por ROAS baixo terão GMV maior sem perda proporcional de ROAS
2. Contas que concentrarem orçamento em produtos acima de 30 conversões terão menor volatilidade de resultado
3. Produtos triados no mês 1 pela Lei 8 terão taxa de campeão superior aos 10% da base atual

---

*O Princípio do Leilão Reverso · versão 2.0 · Efeito Vendas · julho 2026*
*Base: 15.764 registros de produto-mês · 167 contas · 31.947 dias de faturamento · novembro/2025 a julho/2026*
