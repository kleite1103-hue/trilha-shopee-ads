# DIAGNÓSTICO OPERACIONAL — TIME DE ADS
### Análise de gestão para reestruturação
**Efeito Vendas · agosto 2026**

**Base:** 53.783 execuções de checklist · 18 semanas · 153 contas ativas
**Recorte principal:** 30 dias úteis (16/jul a 26/ago)
**Quadro atualizado com contexto de RH:** Ana em licença-maternidade · Beatriz e Gabriel desligados · Christian realocado para outro setor

---

# PARTE 1 — CORREÇÃO METODOLÓGICA IMPORTANTE

Antes dos números: **encontrei um erro de dados que invalidaria toda a análise anterior de ads.**

O campo `cargo` do checklist não reflete a ação executada. Ele registra o **papel principal da pessoa**, não o tipo de trabalho feito.

| Ações de ads executadas | Registradas sob qual cargo |
|---|---|
| **12.881** ações de ads no total | analista_ads: 8.612 |
| | **consultor_conta: 2.812** |
| | gerente_ads: 1.413 |
| | gerente_conta: 44 |

**O caso mais grave é o Ewerton.** Ele tem três cadastros no sistema (analista_ads, consultor_conta e gerente_conta) e o sistema registra **92% do trabalho dele sob "consultor_conta"** — inclusive quando ele está fazendo otimização de orçamento e reajuste de meta de ROAS.

Resultado prático: numa análise por cargo, o Ewerton aparecia com **0,3 dias de otimização em 30** e **25 contas zeradas**. Corrigindo para analisar **por ação executada**, ele aparece com **4,8 dias de média e zero contas abandonadas**.

> **Se a reunião usar o relatório por cargo, o Ewerton será acusado injustamente.** Toda a análise abaixo usa ação executada, não cargo registrado.

**Ação corretiva necessária:** unificar os cadastros duplicados (Ewerton tem 3, Maysa 2, Gustavo 2) e permitir que uma execução registre o tipo de trabalho, não o cargo da pessoa.

---

# PARTE 2 — A DESCOBERTA CENTRAL: NÃO HÁ PADRÃO DE OPERAÇÃO

Este é o achado que mais importa para a reestruturação. Os quatro analistas operam de formas **radicalmente diferentes**, e não existe um padrão definido que diga qual é a certa.

## 2.1 Cobertura de otimização diária

*"Otimização Diária de Orçamento" é a ação nº1 do time de ads — 3.033 execuções. Se é diária, cada conta deveria receber ~30 toques em 30 dias úteis.*

| Analista | Contas | Média de dias com otimização (de 30) | Contas com 20+ dias | Contas zeradas |
|---|---|---|---|---|
| **Kaua** | 44 | **26,9** | **40** | 1 |
| Leonardo | 47 | 7,8 | 0 | 2 |
| Ewerton | 37 | 4,8 | 0 | 0 |
| Luiz *(gerente)* | 16 | 3,1 | 0 | **5** |
| Raissa | 3 | 6,7 | 0 | 0 |

**O contraste é de 9 para 1.** Kaua toca praticamente toda a carteira todo dia útil. Leonardo, com carteira maior, toca cada conta ~8 vezes em 30 dias. Ewerton, ~5.

**Como um gestor deve ler isso — três hipóteses, todas plausíveis:**

1. **Kaua trabalha mais** e os outros estão abaixo do esperado
2. **Kaua registra com mais granularidade** — marca cada ajuste, enquanto os outros marcam uma vez por sessão de trabalho
3. **Kaua faz intervenção excessiva** — e, à luz do que sabemos sobre o algoritmo (fase de aprendizado de 7 a 14 dias), pode estar prejudicando as contas dele

**Os dados de checklist sozinhos não distinguem essas três hipóteses.** A forma de descobrir está na Parte 6.

## 2.2 Disciplina diária individual

Em quantos dos 30 dias úteis a pessoa executou alguma ação diária:

| Pessoa | Dias com ação | Cobertura |
|---|---|---|
| Kaua | 30 de 30 | **100%** |
| Leonardo | 23 de 30 | 77% |
| Luiz | 7 de 30 | 23% |
| Ewerton | 2 de 30 *(sob cargo de ads)* | — |
| Raissa | 0 de 30 | 0% |

*Nota: o número do Ewerton está distorcido pelo problema de cargo descrito na Parte 1. O volume real dele nos últimos 30 dias é de 1.627 ações de ads.*

## 2.3 Volume real de trabalho de ads (por ação, 30 dias)

| Pessoa | Ações de ads |
|---|---|
| Kaua | 2.768 |
| Leonardo | 1.930 |
| Ewerton | 1.627 |
| Luiz | 315 |
| Janaina *(consultora)* | 129 |
| Patricia *(consultora)* | 58 |

**Observação de gestão:** consultores estão executando ações de ads (Janaina, Patricia, Elisandra, Mariana, Ketylyn somam ~260 ações). Isso é bom ou é falta de fronteira? Precisa ser definido.

---

# PARTE 3 — EVIDÊNCIA E RASTREABILIDADE

## 3.1 O time de ads praticamente não anexa print

| Cargo | Execuções | % com print | % com produto | % com detalhe |
|---|---|---|---|---|
| assistente_shopee | 6.398 | **97%** | 0% | 100% |
| consultor_conta | 33.025 | **29%** | 6,6% | 20% |
| gerente_conta | 3.399 | 28% | 1,6% | 6% |
| **analista_ads** | 9.531 | **1%** | 1,0% | **0%** |
| **gerente_ads** | 1.430 | **0%** | 0% | 2% |

**Este é o problema de governança mais sério do time de ads.**

Enquanto Sthefany anexa print em 98% das execuções e Janaina em 44%, o time de ads inteiro está em **0 a 1%**.

Por pessoa:

| Pessoa | Cargo | Execuções | Prints | % |
|---|---|---|---|---|
| Sthefany | assistente | 5.210 | 5.089 | 98% |
| Janaina | consultora | 7.816 | 3.464 | 44% |
| Mariana Ramos | consultora | 2.988 | 1.134 | 38% |
| Patricia | consultora | 8.159 | 2.990 | 37% |
| Ketylyn | gerente conta | 2.535 | 652 | 26% |
| **Kaua** | **analista ads** | 5.483 | **62** | **1%** |
| **Leonardo** | **analista ads** | 3.452 | **2** | **0%** |
| **Luiz** | **gerente ads** | 1.430 | **3** | **0%** |
| **Raissa** | **analista ads** | 283 | **1** | **0%** |

**Consequências práticas:**
- Não há como auditar se a otimização foi feita ou apenas marcada
- Não há memória: se um analista sai, o sucessor não vê o que foi ajustado nem por quê
- Cliente que questiona "o que vocês fizeram na minha conta?" não tem resposta documentada
- Não é possível ligar uma ação a um resultado

**Única exceção:** "Criação de Imagens Otimizadas" tem 97% de print — porque a entrega *é* a imagem.

## 3.2 ID de produto quase nunca é informado

Apenas **1% das ações de ads** registram qual produto foi trabalhado. As exceções fazem sentido: "Criação de Anúncio de Produto" (13%) e "Descontinuidade de Campanhas Ruins" (7%).

**Curiosidade:** Raissa é a única com 28% de preenchimento de produto — a maior taxa do time.

**Por que isso importa:** sem `produto_id`, "Reajuste de Meta de ROAS" registra que *algo* foi ajustado em *alguma* campanha. Não dá para saber qual produto, nem medir se o ajuste funcionou. **É o elo que falta para fechar o ciclo entre ação e resultado.**

---

# PARTE 4 — O QUE O TIME DE ADS FAZ

## 4.1 Distribuição do esforço

| Ação | Execuções | % do total |
|---|---|---|
| Otimização Diária de Orçamento | 3.033 | 28% |
| Monitoramento Diário da Performance | 1.682 | 15% |
| Ajuste de Campanha Existente | 1.235 | 11% |
| Reajuste de Meta de ROAS | 1.018 | 9% |
| Comunicação com Cliente | 752 | 7% |
| Análise Semanal de Desempenho | 677 | 6% |

**43% do trabalho de ads é rotina diária** (otimizar + monitorar). Ações de análise e estratégia ficam com o restante.

## 4.2 Rotina versus análise, por pessoa

| Pessoa | Total | Rotina diária | % | Análise semanal | % |
|---|---|---|---|---|---|
| Kaua | 5.483 | 2.661 | 49% | 534 | **10%** |
| Leonardo | 3.452 | 1.442 | 42% | 124 | 4% |
| Luiz | 1.430 | 429 | 30% | **0** | **0%** |
| Ewerton | 313 | 99 | 32% | **0** | **0%** |
| Raissa | 283 | 84 | 30% | 20 | 7% |

**Luiz e Ewerton não registram nenhuma análise semanal.** Kaua é quem mais equilibra rotina e análise.

## 4.3 Ações estratégicas — cada um faz uma coisa diferente

| Pessoa | Escala por ROAS | Estratégia de Funil | Descontinuidade | Análise de Funil | ROAS por Produto |
|---|---|---|---|---|---|
| **Leonardo** | **197** | **325** | 47 | 0 | 45 |
| **Kaua** | 0 | 84 | 22 | **356** | 0 |
| **Luiz** | 13 | 71 | 30 | 1 | **297** |
| Ewerton | 20 | 16 | 16 | 15 | 47 |
| Raissa | 2 | 37 | 12 | 4 | 40 |

**Leia esta tabela com atenção — ela é a prova de que não existe método padronizado.**

- Leonardo escala produtos (197 vezes). Kaua **nunca** escalou (zero).
- Kaua analisa funil (356 vezes). Leonardo **nunca** analisou funil (zero).
- Luiz olha ROAS por produto (297). Kaua **nunca** olhou (zero).

Três analistas, três metodologias completamente distintas, aplicadas a 128 contas de clientes. **Nenhum cliente recebe o mesmo tipo de trabalho que outro** — depende de quem pegou a conta.

---

# PARTE 5 — CONTAS EM RISCO

## 5.1 Contas sem otimização em 30 dias úteis

| Analista | Contas zeradas | Quais |
|---|---|---|
| **Luiz** | **5** | passion_boutique, ecocollor, alquiverde, looksalice, GMA STORE |
| Leonardo | 2 | SDLBELEZA, SDL IMPORTADORA |
| Kaua | 1 | LumaShopping |
| Ewerton | 0 | — |
| Raissa | 0 | — |

**Luiz tem 16 contas e 5 delas (31%) não receberam nenhuma otimização em 30 dias úteis.** Ele também zerou completamente nas últimas duas semanas do período.

**Pergunta de gestão:** o gerente de ads deve ter carteira própria? Hoje ele opera 16 contas com a menor cobertura do time e não faz análise semanal nenhuma. Ou ele é gestor e não deveria ter carteira, ou é operador e a carteira precisa de acompanhamento.

## 5.2 Distribuição de cobertura na carteira toda

De 148 contas com analista atribuído:

| Faixa | Contas |
|---|---|
| 21 a 30 dias de otimização | 40 |
| 11 a 20 dias | 9 |
| 6 a 10 dias | 31 |
| 1 a 5 dias | 32 |
| **Zero** | **36** |

**As 40 contas com cobertura alta são quase todas do Kaua.** As demais 108 recebem tratamento muito mais esparso.

---

# PARTE 6 — O TESTE QUE RESOLVE A DÚVIDA PRINCIPAL

A pergunta que este relatório **não consegue** responder: a alta frequência do Kaua é melhor, indiferente ou pior?

Isso importa porque as duas conclusões possíveis levam a decisões opostas:
- Se frequência ajuda → Leonardo, Ewerton e Luiz precisam aumentar o ritmo
- Se frequência atrapalha → Kaua está prejudicando 44 contas

**Há razão técnica para suspeitar que atrapalha:** o modelo oCPM tem fase de aprendizado documentada de 7 a 14 dias, e alterações significativas reiniciam a calibração. Otimizar orçamento todos os dias pode estar impedindo qualquer campanha de estabilizar.

**O teste:** comparar o desempenho das contas por faixa de frequência de otimização, controlando por tamanho de conta e segmento. Os dados para isso já existem — é cruzar o checklist com as métricas de ads.

**Isso deveria acontecer antes de qualquer decisão de padronizar frequência.** Posso rodar essa análise se você quiser levar a resposta para a reunião.

---

# PARTE 7 — LEITURA DE GESTOR

## O que está funcionando

- **Cobertura geral é boa:** 149 de 153 contas ativas tiveram alguma execução nas últimas 4 semanas
- **Kaua mantém disciplina exemplar:** 100% dos dias úteis, 40 de 44 contas com alta frequência, e é o único que equilibra rotina com análise semanal (10%)
- **O time de consultoria documenta bem:** 29% de prints, contra 1% de ads
- **Sthefany sustenta sozinha a operação de assistente** — 98% de prints e cobertura de 158 contas distintas no histórico

## Os quatro problemas reais

**1. Ausência de método padronizado.** Três analistas com três metodologias incompatíveis. Um escala e nunca analisa funil; outro analisa funil e nunca escala. Não é diferença de estilo — é ausência de definição do que é o trabalho.

**2. Zero rastreabilidade em ads.** 0-1% de prints, 1% de produto identificado, 0% de detalhe. O trabalho mais técnico e caro da operação é o único sem evidência.

**3. Frequência de intervenção sem base.** Varia de 3 a 27 dias por mês entre analistas, sem que ninguém saiba qual é a correta. E há suspeita técnica de que a alta frequência prejudique.

**4. O gerente de ads opera em vez de gerir.** Luiz tem a menor cobertura, 5 contas abandonadas, zero análises semanais, e parou de registrar nas últimas 2 semanas.

## O buraco no quadro depois das saídas

Com Gabriel desligado e Christian realocado, o time de ads passou de 6 para **4 pessoas efetivas** (Kaua, Leonardo, Ewerton e Raissa, mais Luiz como gerente).

| Pessoa | Contas |
|---|---|
| Leonardo | 47 |
| Kaua | 44 |
| Ewerton | 37 |
| Luiz | 16 |
| **Raissa** | **3** |

**Raissa tem 3 contas enquanto três colegas carregam 40+.** Se ela está ativa e disponível, há capacidade ociosa evidente. Redistribuir 15 contas para ela aliviaria os outros três imediatamente.

E vale registrar: **Ewerton acumula 37 contas de ads + 5 de consultor + atendimento a cliente.** Ele é o mais sobrecarregado em variedade de função, e isso explica a cobertura menor.

---

# PARTE 8 — PAUTA PARA A REUNIÃO

### Decisões que não dependem de mais dados

1. **Redistribuir carteira de ads.** Raissa com 3 contas é desperdício de capacidade. Meta: equilibrar em ~33 contas por analista.
2. **Tornar print obrigatório** nas ações de ads que envolvem alteração: Ajuste de Campanha, Reajuste de Meta de ROAS, Descontinuidade, Escala. É o mesmo padrão que o time de consultoria já cumpre.
3. **Tornar `produto_id` obrigatório** nas ações que se referem a produto específico. Sem isso, nunca será possível medir se um ajuste funcionou.
4. **Definir o papel do gerente de ads.** Gestão ou operação? Se gestão, tirar a carteira. Se operação, acompanhar cobertura.
5. **Unificar cadastros duplicados** (Ewerton ×3, Maysa ×2, Gustavo ×2) e limpar os TESTE.
6. **Definir o método padrão de ads.** Qual é a sequência de trabalho semanal esperada de um analista? Hoje cada um inventou a sua.

### Decisões que precisam do teste da Parte 6

7. **Qual a frequência correta de otimização?** Não decidir antes de medir se frequência alta ajuda ou prejudica.
8. **Otimização diária deve continuar existindo como ação?** Se o teste mostrar que não ajuda, ela é 28% do esforço da equipe sendo gasto sem retorno.

### Perguntas de contexto para confirmar

9. Raissa está ativa e disponível para receber carteira?
10. Com Ana em licença, quem cobre as 36 contas dela? Hoje o registro mostra zero.
11. Kauane está ativa? Está cadastrada como assistente sem nenhuma conta.
12. As 88 contas sem assistente atribuído — quem faz oferta relâmpago nelas?

---

*Análise sobre 53.783 execuções · 18 semanas · dados de agosto/2026*
*Números medem registro de execução. A Parte 1 explica por que a análise por cargo é inválida e esta usa ação executada.*
