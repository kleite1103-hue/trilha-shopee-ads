# TRILHA SHOPEE ADS — DOCUMENTO-MESTRE
### Estrutura completa, conteúdo, avaliações e material de apoio
**Efeito Vendas · versão 1.0 · julho 2026**

---

## COMO USAR ESTE DOCUMENTO

Este é o documento-fonte do curso. Ele contém tudo que é necessário para produzir qualquer aula sem depender de contexto externo: o que ensinar, em que ordem, com quais números, qual exercício e qual material entregar.

Para produzir uma aula específica, use a seção dela na Parte 3 junto com a Parte 2 (base de dados). Tudo que aparece como número no curso está na Parte 2 e vem de dados reais da operação — nada é estimado ou copiado de terceiros.

---

# PARTE 1 — PRINCÍPIOS DE PROJETO

Cinco decisões definem a ordem do curso. Elas existem porque a sequência errada produz aluno que decora em vez de entender, ou pior: aluno que age antes de saber ler.

### 1. Margem antes de ROAS
Ensinar ROAS antes de margem cria aluno perseguindo número arbitrário. Ele acha que 5× é bom, quando para margem de 15% o ponto de empate é 6,7× — ou seja, ele está tendo prejuízo achando que vai bem. Sem margem, todo ROAS é chute. Por isso a economia do produto vem antes de qualquer coisa de anúncio.

### 2. Funil antes de métrica
Métrica isolada não se fixa. "CTR é cliques dividido por impressões" o aluno decora e esquece. "O funil perde gente em cada etapa, e o CTR mede a primeira perda" ele entende e nunca mais esquece. Toda métrica é ensinada como etapa de um processo, nunca como definição solta.

### 3. Ler antes de agir
Os dados mostram que o maior prejuízo da operação vem de ação errada, não de inação: cortar orçamento destrói 39% do GMV sem ganhar eficiência, e 45% dos produtos considerados ruins se recuperam sozinhos. Aluno que aprende a agir antes de aprender a ler vira destruidor de conta. A seção de leitura vem antes da seção de operação.

### 4. A ferramenta por último
Ensinar a ferramenta cedo cria apertador de botão que não sabe pensar. O aluno precisa conseguir fazer o diagnóstico no braço primeiro. Aí a ferramenta vira aceleração, não muleta — e ele consegue perceber quando a ferramenta está errada.

### 5. Um módulo inteiro sobre o que não fazer
Raro em curso, essencial aqui. Os erros mais caros do Shopee Ads são contraintuitivos: pausar parece prudente e destrói receita, CPM alto parece problema e é sinal de confiança, ROAS alto parece vitória e pode ser volume minúsculo.

---

# PARTE 2 — A BASE DE DADOS

Todos os números do curso saem daqui. Origem: operação real, 167 contas, 15.764 registros de produto-mês, 31.947 dias de faturamento, período novembro/2025 a julho/2026.

## 2.1 Benchmarks da carteira

| Métrica | p25 (ruim) | Mediana | p75 (bom) |
|---|---|---|---|
| ROAS por produto | 5,0× | 7,2× | 9,5× |
| Conversão | 1,27% | 2,50% | 4,65% |
| CTR | — | 2,71% | — |
| Ticket | — | R$47 | — |
| CPM | — | R$4,60 | — |
| Lance | — | R$0,176 | — |

**Carteira agregada, julho/2026:** ROAS 8,81× · CTR 3,17% · conversão 2,93% · ticket R$49 · CPM R$5,13

## 2.2 A transição CPC → oCPM

| | Nov/2025 (CPC) | Jul/2026 (oCPM) | Variação |
|---|---|---|---|
| ROAS | 8,54× | 8,81× | +3% |
| CPM | R$4,26 | R$5,13 | **+20%** |
| CTR | 2,82% | 3,17% | **+12%** |
| Conversão | 2,51% | 2,93% | +17% |
| Ticket | R$51 | R$49 | −4% |

**Leitura:** o CPM subiu 20% e foi absorvido pela melhora de CTR e conversão. O algoritmo passou a entregar para público mais bem casado com o produto e cobra mais caro por isso. Para o vendedor, o resultado líquido foi neutro.

A distribuição do ROAS entre produtos ficou estável nos 9 meses (p10 ~2,7× · mediana ~7× · p90 ~13×). A amplitude nunca saiu da faixa de 4 a 5 vezes.

## 2.3 As 8 leis

Estas são as descobertas próprias da operação. Não existem em nenhum material público.

**Lei 1 — Legibilidade.** A confiabilidade da leitura do ROAS depende do volume de conversões. Medida como correlação do ROAS de um mês com o mês seguinte, validada nos 8 pares de meses:

| Conversões/mês | Confiabilidade | Tradução |
|---|---|---|
| menos de 10 | 0,38 | 62% do que você vê é sorte |
| 10 a 30 | 0,53 | metade é sorte |
| 30 a 100 | 0,71 | leitura utilizável |
| mais de 100 | 0,85 | leitura confiável |

Limiar operacional: **30 conversões**. Abaixo disso não há gestão, há aposta.

**Lei 2 — Preço e conversão se opõem.** Elasticidade medida: ticket +10% → conversão −6,4%. Efeito líquido no lance: +0,36. Kit funciona, mas 64% do ganho é devorado pela queda de conversão.

**Lei 3 — Saturação de audiência.** Dobrar impressões: CTR +4,5%, conversão −7,2%. Escalar dilui a qualidade do público, mas o custo é pequeno.

**Lei 4 — Escala é barata.** Elasticidade do GMV ao gasto: 1,03 (R² = 0,85, n = 3.517 observações). Dobrar o gasto dobra o GMV. Efeito no ROAS: +2%. Produtos que mais que dobraram o gasto tiveram GMV +209% e ROAS +5%.

**Lei 5 — Cortar é destruição pura.** Cortar gasto acima de 20%: GMV −39%, ROAS −2%. Cortar não melhora eficiência, só encolhe o negócio.

**Lei 6 — Reversão.** 45% dos produtos com ROAS abaixo de 2× voltaram acima de 4× no mês seguinte, sem intervenção.

**Lei 7 — O campeão nasce grande.** Correlação entre métricas do primeiro mês e o GMV futuro acumulado:

| Métrica do mês 1 | Poder preditivo |
|---|---|
| GMV | 0,65 |
| Conversões | 0,57 |
| ROAS | 0,50 |
| CTR | 0,27 |
| Conversão % | 0,19 |
| Ticket | 0,16 |

Campeões no primeiro mês: 130 conversões e R$7.159 de GMV. Demais produtos: 10 conversões e R$453.

**Lei 8 — A probabilidade se define cedo.**

| ROAS no mês 1 | Chance de virar campeão | GMV futuro mediano |
|---|---|---|
| menos de 4× | 1% | R$661 |
| 4 a 8× | 7% | R$2.768 |
| 8 a 15× | 19% | R$8.223 |
| mais de 15× | 40% | R$21.241 |

**Ressalvas de honestidade intelectual:** as Leis 4 e 6 são observacionais. Quem recebeu aumento de orçamento foi escolhido por já estar performando, então existe seleção embutida — o que os dados provam é que escalar na prática desta operação não destruiu ROAS, não que escalar aleatoriamente seria gratuito. A Lei 6 mistura recuperação natural com intervenção do time, não é possível separar.

## 2.4 Retrato da carteira

- 6,2% dos produtos geram 50% do GMV
- 39% dos produtos faturam menos de R$500/mês
- 27% dos produtos aparecem em um único mês e somem
- 25 a 28% da base de produtos é trocada todo mês
- Produtos que somem carregam apenas 2 a 10% do GMV
- Apenas 6,2% dos produtos sobrevivem nove meses
- Elasticidade agregada: R$1 a mais em ads gerou R$16 de GMV (maio→junho)
- Concentração da carteira: HHI 202 (saudável), top 5 contas = 23% do faturamento

## 2.5 Comissões e custos

**Comissão Shopee por faixa de preço:**

| Faixa | Comissão |
|---|---|
| até R$79,99 | 20% + R$4 |
| R$80 a R$99,99 | 14% + R$16 |
| R$100 a R$199,99 | 14% + R$20 |
| R$200 ou mais | 14% + R$26 |

**Atenção ao degrau:** um produto a R$79,99 paga R$20 de comissão. A R$80,00 paga R$27,20. Sete reais e vinte centavos a mais por um centavo de preço.

**Antecipação de recebíveis:** 1% (Loja Oficial) · 2,5% (Vendedor Indicado) · 3,5% (demais)

**ROAS mínimo = 100 ÷ margem%**

| Margem líquida | ROAS de empate |
|---|---|
| 10% | 10,0× |
| 15% | 6,7× |
| 20% | 5,0× |
| 25% | 4,0× |
| 30% | 3,3× |
| 40% | 2,5× |

## 2.6 Mecânica do oCPM

O Brasil opera em oCPM (CPM otimizado), não CPM puro. Documentado pela própria Shopee.

**Como funciona, passo a passo:**
1. O anunciante declara intenção (meta de ROAS e orçamento), não lance
2. O sistema traduz a meta em valor por conversão: ticket ÷ ROAS alvo
3. Para cada impressão disponível, dois modelos preveem: probabilidade de clique (pCTR) e probabilidade de conversão (pCVR), para aquele comprador específico
4. Converte para lance por impressão: pCTR × pCVR × valor por conversão × 1000 × fator de controle
5. Maior lance por impressão vence. Cobrança por impressão entregue

**O fator de controle** ajusta o ritmo de gasto ao longo do dia e aperta ou solta conforme o desempenho versus a meta.

**Calibração:** a saída do modelo não é um ranking, é um preço. A plataforma cobra contra aquela probabilidade prevista. Por isso o sistema é conservador com produtos sem histórico — previsão malcalibrada custa dinheiro à plataforma.

**Fase de aprendizado:** 7 a 14 dias após configurar ou alterar significativamente. Durante esse período o desempenho flutua enquanto o modelo calibra.

**Janela de atribuição:** 7 dias por clique, 1 dia por visualização. Consequência crítica: o ROAS dos últimos 7 dias está sempre subestimado, porque as conversões ainda não terminaram de chegar.

## 2.7 A anatomia do ROAS

```
ROAS = Ticket × Conversão × CTR × 1000 ÷ CPM

Lance = Ticket × Conversão ÷ ROAS alvo
```

**Importante para o ensino:** esta é uma identidade algébrica, não uma descoberta sobre a Shopee. Abrindo as definições (ticket = GMV ÷ conversões, conversão = conversões ÷ cliques, CTR = cliques ÷ impressões, ROAS = GMV ÷ gasto), todos os termos se cancelam e sobra a definição de CPM. Ela é verdadeira em qualquer plataforma de anúncios.

**O valor dela é anatômico:** mostra que existem exatamente quatro alavancas e que elas se multiplicam entre si. Melhorar duas ao mesmo tempo tem efeito composto, não somado. Ensinar assim é honesto e igualmente poderoso. Ensinar como "fórmula secreta descoberta" expõe a autoridade do curso a quem abrir a álgebra.

**Viabilidade competitiva:** lance ≥ R$0,15 compete em inventário premium. Abaixo disso, o produto opera em inventário residual — as sobras baratas, onde o ROAS parece alto porque custou quase nada, mas o volume é minúsculo.

## 2.8 Hierarquia das alavancas

| Ordem | Alavanca | Por quê |
|---|---|---|
| 1ª | Conversão | Entra duas vezes: no lance e na nota de qualidade. Efeito quase quadrático |
| 2ª | Ticket | Multiplica a conversão no cálculo do lance |
| 3ª | CTR | Transforma o lance em preço de impressão |
| 4ª | ROAS alvo | É freio e filtro de público, não acelerador |

## 2.9 Palavras-chave, categoria e formato

**Palavras-chave no GMV Max:** não existe mais seleção manual. A correspondência é automática, baseada em três insumos: o título do produto e conteúdo do anúncio, a intenção de busca do comprador, e os sinais históricos do anúncio. O título deixou de ser assunto de SEO orgânico e virou ativo de mídia paga.

**O ROAS alvo como dial de amplitude:** com ROAS alvo alto, o sistema direciona para público de nicho e alta intenção — melhora eficiência, limita alcance. Com ROAS alvo baixo, expande para faixa mais ampla — aumenta alcance, reduz precisão. É o equivalente moderno da correspondência exata versus ampla do modelo antigo, onde a Shopee cobrava 1,2× o lance pela correspondência ampla.

**Categoria — três papéis:**
- Filtro de elegibilidade: define em quais leilões o produto entra
- Insumo de relevância: categoria errada ou atributos incompletos prejudicam a correspondência
- Alvo direto no Discovery: a segmentação é por categoria de interesse, com lance dinâmico até 2×

**Categoria é irreversível.** É o único campo que não pode ser editado depois da publicação. E cadastrar em categoria não correspondente é infração de spam de categorias, com risco de banimento e exclusão permanente do item.

**Formatos e inventário:**

| Formato | Inventário |
|---|---|
| Busca | máximo 60 anúncios por palavra-chave; 2 primeiros resultados + 1 a cada 3 listagens |
| Daily Discover | até 26 anúncios nas primeiras 55 posições |
| You May Also Like | até 12 anúncios nas primeiras 35 posições |

Escassez diferente produz preço de equilíbrio diferente. Busca é movida por intenção, descoberta por afinidade. O CPM observado por produto é média ponderada entre inventários distintos.

## 2.10 Métodos de lance

- **Lance Automático:** produtos novos, de 0 a 100 cliques. Não tocar por 7 dias
- **Meta de ROAS:** produtos maduros, 200+ cliques e 20+ conversões
- **Lei da Âncora:** nunca reverter de Meta de ROAS para Automático. Caso documentado na operação: 11,89× caiu para 4,41× após reversão
- Na turbulência de maio, produtos em Meta de ROAS ficaram estáveis enquanto Automático caiu 32%

## 2.11 Classificações

**Curvas:**

| Curva | Critério | Ação |
|---|---|---|
| A | ROAS > 8× e CTR > 2% | Replicar e escalar |
| B | ROAS 4 a 8× | Otimizar conversão |
| C | ROAS 2 a 4× | Reformular oferta |
| Pausar | ROAS < 2× e CTR < 1% | Pausar, nunca apagar |

**Quadrantes** (cortes: ROAS 8× e GMV R$5.000/mês):

| Quadrante | ROAS | Volume | Ação |
|---|---|---|---|
| OURO | alto | alto | Manter e replicar |
| ESCALA | baixo | alto | Consertar conversão — maior oportunidade |
| NICHO | alto | baixo | Ampliar orçamento |
| FRACO | baixo | baixo | Reformular ou pausar |

## 2.12 Mix de fontes de faturamento

**Sobre o GMV bruto, ponderado** (603 registros conta-mês com os campos preenchidos):

| Fonte | % do GMV bruto |
|---|---|
| Ads | 53,7% |
| Orgânico | 22,3% |
| Afiliado | 10,4% |
| Live | 1,1% |
| Vídeo | 0,4% |
| Não classificado | 12,2% |

**Na conta típica (mediana por conta):** Ads 62% · Orgânico 17% · Afiliado 5,3%

A diferença entre ponderado e mediana importa: as contas grandes são mais dependentes de ads, então a média ponderada puxa o número para cima. A conta típica depende menos de ads do que o agregado sugere.

**Distribuição da dependência de afiliado:**

| Faixa | % das contas |
|---|---|
| quase zero | 6% |
| 1 a 5% | 41% |
| 5 a 15% | 42% |
| 15 a 30% | 8% |
| mais de 30% | 2% |

**Ressalva metodológica importante.** A segunda fonte de dados (métricas diárias, junho) dá números diferentes: Ads 68% · Afiliado 13% · Orgânico 20% · Live 2,3%. E soma 103,8%, o que indica sobreposição — uma mesma venda pode ser atribuída a mais de uma fonte.

Além disso, os campos têm cobertura desigual: `gmv_ads` está preenchido em 78% dos registros, `gmv_afiliados` em 64%, `gmv_organico` em 66%. Tratar campo vazio como zero subestima sistematicamente as fontes menos preenchidas — foi esse erro que produziu, numa primeira análise, o número falso de "83% ads".

**Como ensinar isso:** dizer que ads fica entre 54% e 68% e afiliado entre 10% e 13%, dependendo do critério de atribuição. Não apresentar número único — a honestidade sobre a faixa é parte do que diferencia este material.

---

# PARTE 3 — AS 40 AULAS

Cada aula: 15 a 25 minutos, uma ideia central, termina em ação.

---

## SEÇÃO 1 · FUNDAMENTOS
**Módulos 01 a 08 — A linguagem**
*Objetivo: o aluno lê um relatório sem se perder*

### 01 · Por que anunciar
**Ensina:** o que muda quando você paga por tráfego. A diferença entre esperar ser encontrado e comprar atenção. Por que quase todo crescimento em marketplace passa por mídia paga.
**Conteúdo:** o mix real da carteira (seção 2.12) como retrato do mercado. Ads é a maior fonte, mas não é a única — e a dependência varia muito entre contas. O risco da concentração e por que ela existe.
**Exercício:** identificar quanto do próprio faturamento vem de cada fonte.

### 02 · O funil
**Ensina:** impressão → clique → conversão → receita. Cada seta perde gente. Onde cada métrica mora.
**Conteúdo:** a estrutura visual do funil. Números reais: de 100.000 impressões, ~3.000 cliques, ~90 vendas.
**Exercício:** desenhar o próprio funil com números reais de um produto.

### 03 · As três moedas
**Ensina:** impressão, clique e conversão como unidades de medida diferentes. O que cada uma custa e o que cada uma vale.
**Conteúdo:** por que a plataforma precisa converter tudo para uma moeda única. Introdução conceitual ao leilão, sem entrar na mecânica ainda.

### 04 · CTR
**Ensina:** de cada 1.000 pessoas que viram, quantas clicaram.
**Conteúdo:** fórmula, exemplo real (105.752 impressões, 3.166 cliques, 2,99%), benchmarks (carteira 3,17%, mediana 2,71%, piso de atenção 1,5%). O que CTR revela: foto principal (maior fator), preço na vitrine, título, avaliações visíveis. A armadilha do CTR alto com conversão baixa.
**Exercício:** listar os 10 produtos que mais gastaram, marcar os abaixo de 1,5%, avaliar a foto de cada um.

### 05 · Taxa de conversão
**Ensina:** a alavanca soberana. Por que ela pesa duas vezes.
**Conteúdo:** fórmula, benchmarks (p25 1,27%, mediana 2,50%, p75 4,65%). Por que entra duas vezes no algoritmo (lance e nota de qualidade) e o efeito quase quadrático. As cinco alavancas de conversão: preço competitivo, foto clara, avaliações, cupom, frete grátis.
**Exercício:** identificar os produtos abaixo da mediana e listar qual das cinco alavancas está faltando em cada.

### 06 · Ticket médio e GMV
**Ensina:** o tamanho de cada venda e o total.
**Conteúdo:** ticket = GMV ÷ conversões. Mediana da carteira R$47. Por que ticket baixo tem dificuldade estrutural (o custo de anunciar é o mesmo, a margem é menor).
**Exercício:** calcular o ticket real de cada produto.

### 07 · ROAS e ACOS
**Ensina:** as duas faces da mesma moeda.
**Conteúdo:** ROAS = retorno por real investido. ACOS = percentual do faturamento gasto em ads. Um é o inverso do outro. Benchmarks: p25 5,0× · mediana 7,2× · p75 9,5×. Aviso: ROAS bom depende da margem, que vem no módulo 12.
**Exercício:** calcular ROAS e ACOS dos 10 principais produtos.

### 08 · CPM e CPC
**Ensina:** o que você realmente paga.
**Conteúdo:** CPM = custo por mil impressões (modelo atual). CPC = custo por clique (modelo antigo). Mediana atual R$4,60 a R$5,13. **CPM alto não é castigo** — é sinal de que o algoritmo acredita no produto. Primeira menção ao Leilão Reverso, sem aprofundar.
**Exercício:** calcular o CPM de cada produto e identificar os mais caros — e perguntar se o ROAS deles justifica.

**AVALIAÇÃO DA SEÇÃO 1:** entregar o relatório da própria conta com cada métrica identificada, calculada e comentada em uma linha.

---

## SEÇÃO 2 · ECONOMIA DO PRODUTO
**Módulos 09 a 14 — Conhecer os próprios números antes de gastar**
*Objetivo: o aluno sabe qual ROAS ele precisa, não qual gostaria*

### 09 · A estrutura de custo real
**Ensina:** tudo que sai do preço até sobrar lucro.
**Conteúdo:** preço − custo do produto − comissão − frete − embalagem − antecipação − ads = lucro. Cada linha explicada. O erro comum de esquecer o custo de ads na conta de margem.
**Exercício:** montar a estrutura de custo de um produto.

### 10 · As comissões e os degraus
**Ensina:** a tabela de comissões e as armadilhas de faixa.
**Conteúdo:** as quatro faixas com fórmula. O degrau de R$79,99 para R$80,00 (R$20 vira R$27,20). Antecipação: 1%, 2,5% e 3,5%.
**Exercício:** identificar produtos precificados logo acima de um degrau.

### 11 · Calcular a margem líquida
**Ensina:** a conta completa, na prática.
**Conteúdo:** passo a passo com um produto real. Margem bruta versus líquida. O que é margem de contribuição.
**Exercício:** planilha de margem dos 10 principais produtos.

### 12 · ROAS mínimo = 100 ÷ margem%
**Ensina:** o número que só você tem.
**Conteúdo:** a fórmula e a tabela de referência. Margem 15% → ROAS 6,7× para empatar. Por que "ROAS 5× é bom" é uma frase sem sentido sem saber a margem. Como definir a meta acima do empate.
**Exercício:** calcular o ROAS mínimo de cada produto e comparar com o ROAS real. Marcar os que estão dando prejuízo.

### 13 · Precificação estratégica
**Ensina:** onde posicionar o preço dentro das faixas.
**Conteúdo:** usar os degraus a favor. Preço psicológico versus preço de faixa. Como o preço afeta conversão e CTR ao mesmo tempo.
**Exercício:** simular reposicionamento de três produtos.

### 14 · Kit e ticket: a matemática real
**Ensina:** por que kit funciona, e quanto ele realmente entrega.
**Conteúdo:** **Lei 2** — ticket +10% derruba conversão em 6,4%. Efeito líquido no lance: +0,36. Subir ticket em 50% não dá 50% de lance a mais, dá cerca de 18%. Kit continua valendo a pena, mas com expectativa calibrada. Tipos de agrupamento: kit de quantidade, combo complementar, kit temático, produto com brinde.
**Exercício:** escolher três produtos de ticket baixo e projetar o kit com expectativa realista.

**AVALIAÇÃO DA SEÇÃO 2:** planilha de margem e ROAS mínimo dos 10 principais produtos, com marcação de quais estão abaixo do ponto de empate.

---

## SEÇÃO 3 · COMO O LEILÃO FUNCIONA
**Módulos 15 a 21 — A máquina por dentro**
*Objetivo: o aluno para de "otimizar lance" e passa a alimentar o algoritmo*

### 15 · A virada: do CPC ao oCPM
**Ensina:** o que mudou e por que as táticas antigas pararam de funcionar.
**Conteúdo:** no CPC você comprava tráfego e controlava o lance. No oCPM o algoritmo avalia e precifica. Os números reais da transição (tabela 2.2): CPM +20%, CTR +12%, ROAS estável. Por que quem continuou mexendo no lance estava girando um volante desconectado.

### 16 · O Princípio do Leilão Reverso
**Ensina:** a tese central. A Shopee dá o lance em você.
**Conteúdo:** o algoritmo como investidor, não leiloeiro. Ele tem impressões escassas e as investe onde o retorno é maior. As quatro coisas que ele avalia: conversão, ticket, CTR, histórico. **CPM alto é elogio, não castigo.**

### 17 · O que o algoritmo prevê e como cobra
**Ensina:** a mecânica do oCPM, passo a passo.
**Conteúdo:** os 5 passos da seção 2.6. Os dois modelos de previsão rodando a cada impressão. O lance recalculado para cada comprador. Calibração: por que a saída é um preço, não um ranking. O fator de controle.

### 18 · A anatomia do ROAS
**Ensina:** as quatro alavancas e por que se multiplicam.
**Conteúdo:** a fórmula como anatomia (seção 2.7 — ensinar honestamente como identidade, não como descoberta). A hierarquia das alavancas (2.8). Viabilidade: lance ≥ R$0,15. O paradoxo do lance baixo: inventário residual versus premium.
**Exercício:** usar a calculadora de viabilidade em cinco produtos.

### 19 · Título e categoria
**Ensina:** as duas entradas que você controla.
**Conteúdo:** palavras-chave são automáticas e vêm do título — o título virou ativo de mídia. Categoria: três papéis, irreversível, risco de banimento por spam de categoria. Atributos obrigatórios como insumo de relevância.
**Exercício:** auditoria de título e categoria de 20 produtos.

### 20 · Métodos de lance e a Lei da Âncora
**Ensina:** quando usar Automático e quando usar Meta de ROAS.
**Conteúdo:** Automático para produtos novos (0-100 cliques), Meta de ROAS para maduros (200+ cliques, 20+ conversões). Nunca reverter — o caso de 11,89× para 4,41×. O ROAS alvo como dial de amplitude (nicho versus alcance), equivalente moderno da correspondência exata versus ampla.
**Exercício:** listar produtos maduros que ainda estão em Automático.

### 21 · Fase de aprendizado e atribuição
**Ensina:** por que os primeiros dias mentem.
**Conteúdo:** fase de aprendizado de 7 a 14 dias. Janela de atribuição de 7 dias por clique. **Consequência: o ROAS dos últimos 7 dias está sempre subestimado.** Por que mexer no produto reinicia a calibração. A regra dos 7 dias sem tocar.

**AVALIAÇÃO DA SEÇÃO 3:** auditoria de título e categoria de 20 produtos, com proposta de novo título para os que estiverem fracos.

---

## SEÇÃO 4 · LEITURA DE DADOS
**Módulos 22 a 27 — Interpretar sem se enganar**
*Objetivo: o aluno sabe quando NÃO tem informação suficiente*

### 22 · Onde estão os dados
**Ensina:** exportar corretamente.
**Conteúdo:** os relatórios disponíveis (Anúncios de Produto, Anúncios de Loja, GMV Max Detail). O que cada coluna significa. Erros comuns de exportação: período errado, filtro de status, mês incompleto.

### 23 · A Lei da Legibilidade
**Ensina:** abaixo de 30 conversões você não sabe nada.
**Conteúdo:** **Lei 1** completa, com a tabela de confiabilidade. Por que produto com 5 conversões não tem ROAS, tem anedota. O conceito de zona de ruído. A única ação válida abaixo do limiar: alimentar até gerar volume, ou esperar.
**Exercício:** marcar quantos produtos da própria carteira estão na zona ilegível.

### 24 · ROAS Ajustado
**Ensina:** corrigir a leitura pelo ruído.
**Conteúdo:** a fórmula `C × ROAS observado + (1−C) × ROAS de referência`, com C da tabela de confiabilidade. Exemplo trabalhado: produto com 8 conversões e ROAS 18× numa conta que roda 7× → ROAS Ajustado 11,2×. Validação: 9,4% menos erro de previsão, 12% menos erro de classificação.
**Exercício:** recalcular o ROAS ajustado dos produtos de baixo volume e ver quais mudam de classificação.

### 25 · Curvas A, B, C e Pausar
**Ensina:** a primeira classificação.
**Conteúdo:** os quatro critérios e as ações correspondentes. Como classificar em escala.
**Exercício:** classificar a carteira inteira.

### 26 · Os quatro quadrantes
**Ensina:** cruzar eficiência com volume.
**Conteúdo:** OURO, ESCALA, NICHO, FRACO. Por que ESCALA é a maior oportunidade (o volume já existe, falta eficiência). Como priorizar entre quadrantes.
**Exercício:** montar a matriz da própria carteira e calcular a oportunidade em reais do quadrante ESCALA.

### 27 · As sete armadilhas de leitura
**Ensina:** o módulo do "não faça".
**Conteúdo:**
1. CPM alto lido como problema — é sinal de confiança do algoritmo
2. Lance baixo com ROAS alto — inventário residual, volume minúsculo
3. ROAS alto sem volume — não constrói operação
4. Julgar mês incompleto contra mês fechado
5. Julgar os últimos 7 dias (atribuição não terminou)
6. Julgar produto abaixo de 30 conversões
7. Pedir ROAS alvo alto demais achando que dá mais lucro — estrangula o lance e some do leilão

**AVALIAÇÃO DA SEÇÃO 4:** carteira classificada em curvas e quadrantes, com os produtos ilegíveis marcados separadamente e a oportunidade do quadrante ESCALA calculada em reais.

---

## SEÇÃO 5 · OPERAÇÃO
**Módulos 28 a 32 — Executar protocolos, não improvisar**
*Objetivo: o aluno opera por protocolo, não por instinto*

### 28 · Protocolo de lançamento
**Ensina:** os primeiros 30 dias de um produto.
**Conteúdo:** configuração inicial (Lance Automático, orçamento de teste). Os 7 dias intocáveis. O que observar na primeira semana e o que ignorar. Quando migrar para Meta de ROAS.
**Exercício:** lançar um produto seguindo o protocolo e documentar.

### 29 · Protocolo de escala
**Ensina:** escalar não derruba o ROAS.
**Conteúdo:** **Lei 4** — elasticidade 1,03. Dobrar o gasto dobra o GMV. Produtos que mais que dobraram tiveram ROAS +5%. O ritmo recomendado de +20% por semana e por que ele é conservador. **Lei 3** — a diluição existe mas é pequena (conversão −7,2% ao dobrar impressões). Quando parar: margem, estoque, não o ROAS.
**Exercício:** escolher três produtos legíveis e escalar seguindo o protocolo.

### 30 · Protocolo de resgate
**Ensina:** o que fazer com ESCALA e FRACO.
**Conteúdo:** para ESCALA, atacar conversão (as cinco alavancas do módulo 05). Para FRACO, decidir entre reformular oferta ou aceitar. Os três caminhos de resgate calculados: via ticket, via conversão, via ROAS alvo.
**Exercício:** montar plano de resgate para os cinco maiores ESCALA.

### 31 · Quando realmente pausar
**Ensina:** por que pausar quase nunca é a resposta.
**Conteúdo:** **Lei 5** — cortar 20% do gasto tira 39% do GMV e não melhora o ROAS. **Lei 6** — 45% dos produtos com ROAS abaixo de 2× se recuperam sozinhos. Os únicos critérios válidos para pausar: margem comprovadamente negativa, ruptura de estoque, problema de qualidade. Nunca pausar "para melhorar o ROAS". Pausar, nunca apagar — apagar destrói o histórico.

### 32 · A rotina semanal do gestor
**Ensina:** o ritmo de operação.
**Conteúdo:** o que se olha toda semana, o que se olha todo mês, o que não se olha nunca. A ordem de análise: precificação → funil → cadastro → ferramentas → afiliados → ads. Checklist da semana.
**Exercício:** executar uma semana completa da rotina.

**AVALIAÇÃO DA SEÇÃO 5:** um ciclo de 30 dias documentado — o que foi feito, com qual justificativa, e o que aconteceu.

---

## SEÇÃO 6 · A FERRAMENTA
**Módulos 33 a 36 — Acelerar o que já se sabe fazer**

### 33 · O que a ferramenta faz e o que não faz
**Ensina:** o escopo honesto.
**Conteúdo:** o que ela automatiza, o que ela sugere, e onde o julgamento humano continua obrigatório. Por que ela não substitui os módulos anteriores.

### 34 · Importando dados corretamente
**Ensina:** lixo entra, lixo sai.
**Conteúdo:** formatos aceitos, período correto, erros comuns de importação e como identificá-los.

### 35 · Lendo o diagnóstico
**Ensina:** cada bloco da saída e o que significa.
**Conteúdo:** percorrer um diagnóstico real, bloco por bloco, ligando cada um ao conceito já ensinado.

### 36 · Da análise à ação
**Ensina:** transformar saída em tarefa.
**Conteúdo:** como priorizar as recomendações, o que fazer primeiro, como registrar o que foi feito.

**AVALIAÇÃO DA SEÇÃO 6:** um diagnóstico completo gerado e interpretado por escrito, com plano de ação priorizado.

---

## SEÇÃO 7 · GESTÃO DE CARTEIRA
**Módulos 37 a 40 — Sair do produto e pensar no conjunto**

### 37 · Alocação de orçamento
**Ensina:** distribuir entre produtos, não otimizar um por um.
**Conteúdo:** a concentração real (6,2% dos produtos = 50% do GMV). Por que dispersar orçamento mantém tudo ilegível. Concentração como requisito matemático, não preferência.
**Exercício:** redistribuir o orçamento da carteira com justificativa.

### 38 · A assinatura do campeão
**Ensina:** campeão nasce grande, não é construído.
**Conteúdo:** **Lei 7** — o poder preditivo de cada métrica do primeiro mês. GMV e conversões preveem, CTR e ticket quase não. Campeões fizeram 130 conversões no mês 1 contra 10 dos demais.

### 39 · Triagem no mês 1
**Ensina:** decidir cedo, com probabilidade.
**Conteúdo:** **Lei 8** — a tabela de probabilidade por ROAS inicial. Produto que abre abaixo de 4× tem 1% de chance de virar campeão. Produto acima de 15× tem 40%. O protocolo de triagem: abaixo de 4× vai para reformulação de oferta, não para otimização de campanha. Acima de 15× recebe orçamento imediatamente.
**Exercício:** aplicar a triagem nos produtos lançados nos últimos 60 dias.

### 40 · Diagnóstico de conta completo
**Ensina:** juntar tudo.
**Conteúdo:** o roteiro completo, do zero ao plano de ação. Ordem de análise, o que priorizar, como apresentar o diagnóstico.
**Exercício:** diagnóstico completo de uma conta.

**AVALIAÇÃO DA SEÇÃO 7:** plano de alocação de orçamento da carteira com justificativa por produto.

---

## CERTIFICAÇÃO FINAL

Diagnosticar uma conta **que não é a sua**, com defesa das decisões.

É o único formato que prova domínio do método em vez de familiaridade com o próprio contexto. O aluno recebe uma exportação real anonimizada, produz o diagnóstico completo e defende as escolhas.

---

# PARTE 4 — MODELO DE AVALIAÇÃO

**Princípio: entregável, não questionário.**

Prova teórica mede memória. Entregável mede aplicação, gera resultado real para o aluno (ele termina o módulo com trabalho feito na própria conta) e produz casos reais que alimentam as próximas turmas.

| Seção | Entregável |
|---|---|
| 1 · Fundamentos | Relatório da conta com cada métrica identificada e comentada |
| 2 · Economia | Planilha de margem e ROAS mínimo dos 10 principais produtos |
| 3 · Leilão | Auditoria de título e categoria de 20 produtos |
| 4 · Leitura | Carteira classificada, ilegíveis marcados, oportunidade em reais |
| 5 · Operação | Um ciclo de 30 dias documentado |
| 6 · Ferramenta | Diagnóstico gerado e interpretado |
| 7 · Carteira | Plano de alocação com justificativa |
| Final | Diagnóstico de conta de terceiro, com defesa |

---

# PARTE 5 — MATERIAL DE APOIO

**Regra: no máximo um artefato por aula.** Mais que isso ninguém usa.

## 5.1 Por tipo de aula

| Tipo | Artefato |
|---|---|
| Conceito (CTR, ROAS, CPM) | Cartão de referência de uma página |
| Cálculo (margem, ROAS mínimo) | Calculadora interativa |
| Protocolo (lançamento, escala) | Checklist imprimível |
| Diagnóstico | Planilha modelo preenchida |
| Ferramenta | Vídeo de tela, sem PDF |

## 5.2 O material-mãe

Um cartão único com tudo que o aluno consulta o tempo todo. É o que ele imprime e cola na parede:

- Anatomia do ROAS e fórmula do lance
- ROAS mínimo = 100 ÷ margem% (com a tabela)
- Tabela de comissões por faixa
- Limiar de legibilidade (30 conversões) e a tabela de confiabilidade
- Benchmarks: CTR, conversão, ROAS, ticket, CPM
- Critérios de curva e quadrante
- Viabilidade: lance ≥ R$0,15

## 5.3 Calculadoras necessárias

1. **Margem e ROAS mínimo** — preço, custo, faixa de comissão → margem líquida e ROAS de empate
2. **Viabilidade** — ticket, conversão, CTR, ROAS alvo → lance, CPM previsto, veredito
3. **ROAS Ajustado** — ROAS observado, conversões, ROAS de referência → ROAS corrigido
4. **Simulador de kit** — preço unitário, quantidade, desconto → ticket novo e ganho realista de lance
5. **Escala** — gasto atual, gasto novo → GMV projetado pela elasticidade 1,03

## 5.4 Checklists

- Lançamento de produto (30 dias)
- Auditoria de título e categoria
- Rotina semanal do gestor
- Critérios para pausar (os três únicos válidos)
- Diagnóstico de conta completo

## 5.5 Planilhas modelo

- Margem por produto
- Classificação de carteira (curvas + quadrantes + legibilidade)
- Plano de alocação de orçamento

---

# PARTE 6 — PRODUÇÃO

## 6.1 Formato das aulas

- 15 a 25 minutos cada. Acima disso a retenção cai e o aluno não volta
- Uma ideia central por aula
- Toda aula termina em ação, não em resumo
- Slides com revelação progressiva: o texto aparece conforme a fala avança, nunca antes

## 6.2 Ordem de produção recomendada

**Não começar pelo módulo 01.** Começar pela **Seção 4 (Leitura de Dados, módulos 22 a 27)** — é onde está o conteúdo mais original, são as leis próprias da operação, e serve para calibrar tom e profundidade antes de encarar o básico.

Depois: Seção 5 (Operação) → Seção 3 (Leilão) → Seção 2 (Economia) → Seção 1 (Fundamentos) → Seções 6 e 7.

**Produzir em lote por seção.** Escrever as 8 aulas de Fundamentos juntas mantém tom e vocabulário consistentes. Escrever a aula 3 hoje e a 4 daqui a duas semanas gera curso que parece costurado por pessoas diferentes.

## 6.3 Estrutura comercial sugerida

- **Seções 1 e 2 gratuitas ou de baixo custo** — são o funil. Quem chega na Seção 3 já está comprado
- **Trilha rápida de 6 aulas** para quem já opera: 23 (Legibilidade), 24 (ROAS Ajustado), 29 (Escala), 31 (Não pausar), 39 (Triagem), 19 (Título). São as que mudam resultado mais rápido

## 6.4 Distribuição

Fonte única em HTML, publicada no GitHub Pages, aparecendo em três lugares:
- Sistema Efeito Vendas → Ferramentas (time interno)
- Seller.IA Club → área de membros (alunos)
- Central de materiais → link direto (público e vendas)

Atualiza num lugar, atualiza em todos.

---

# ANEXO — A TESE DO CURSO

Se o curso tem uma frase, é esta:

> **O ROAS não é o objetivo. É o pedágio.**
>
> **O único recurso escasso no oCPM é volume de conversão por anúncio — porque ele é, ao mesmo tempo, o que torna o produto legível para você e o que o algoritmo usa para calibrar.**
>
> **A operação média gerencia ao contrário: espalha orçamento em muitos produtos (todos ilegíveis), corta os que parecem ruins (destruindo receita sem ganhar eficiência), e persegue ROAS alto — que é consequência, não causa.**

## O que o curso corrige no mercado

| O mercado ensina | Os dados mostram |
|---|---|
| "Escalar derruba o ROAS" | Elasticidade 1,03 — não derruba |
| "Pause o que está ruim" | 45% se recuperam sozinhos; cortar tira 39% do GMV e 0% de ganho |
| "Persiga ROAS alto" | ROAS é pedágio; o ativo é volume |
| "Otimize cada anúncio" | Abaixo de 30 conversões não há o que otimizar |
| "Kit aumenta o ROAS" | Aumenta, mas 64% do ganho é comido pela conversão |
| "CPM alto é problema" | É sinal de confiança do algoritmo |

## Previsões falsificáveis

O que torna isto uma tese e não uma opinião — pode ser testado em 60 dias:

1. Contas que pararem de pausar produtos por ROAS baixo terão GMV maior sem perda de ROAS
2. Contas que concentrarem orçamento em produtos acima de 30 conversões terão menos volatilidade
3. Produtos triados no mês 1 pela regra do módulo 39 terão taxa de campeão maior que os 10% da base atual

---

*Documento-mestre · Trilha Shopee Ads · Efeito Vendas · julho 2026*
*Todos os números vêm da operação real: 167 contas, 15.764 registros de produto-mês, 31.947 dias de faturamento, novembro/2025 a julho/2026.*
