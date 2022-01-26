# Vendas Rossmann
Projeto de Previsão de Vendas das Farmácias Rossmann

Todo o cenário a seguir é completamente fictício. A empresa, o contexto, o CEO e as hipóteses de negócio foram criadas apenas para simular um ambiente real em que um ciêntista de dados está inserido.

Os dados referente a este projeto fazem parte de um desafio lançado no **kaglle**. Para acessá-los [clique aqui.](https://www.kaggle.com/c/rossmann-store-sales).  


# 1. Problema de negócio
A rede de farmácias Rossmann está presente em 7 países da Europa e possue mais de 4.000 lojas. O CFO da empresa solicitou aos seus gerentes a previsão de vendas de cada loja nas próximas seis semanas para que pudesse definir um orçamento para a reformas das lojas. Diversos fatores podem influenciar as vendas das lojas, incluindo promoções, concorrentes próximos, localização das lojas, feriados e sazonalidade.

Com milhares de gerentes prevendo as vendas com base em suas circunstâncias individuais, as previsões podem variar muito. Neste contexto, foi solicidado ao time de ciência de dados a criação de um modelo para prever as vendas das lojas com base nos dados. 

# 2. Premissas do negócio

- Lojas fechadas não nos dão informações sobre vendas, sendo assim, foram removidas de nossa análise; 
- Foram consideradas apenas lojas com vendas maiores que zero;  
- Para lojas que não possuiam informação sobre o concorrente mais próximo, concluímos que não há competição ou que não há concorrentes próximos. Neste caso, foi considerado um valor bem acima da distância observada no conjunto de dados. 

## 2.1 Descrição dos atributos

Foram fornecidas as seguintes informações de vendas para cada loja:

- **Id** - um Id que representa um (Store, Date) duplo dentro do conjunto de teste  
- **Store** - um ID único para cada loja  
- **Sales** - o volume de negócios em qualquer dia (isto é o que você está prevendo)  
- **Customers** - o número de clientes em um determinado dia  
- **Open** - um indicador para saber se a loja estava aberta: 0 = fechada, 1 = aberta  
- **StateHoliday** - indica um feriado estadual. Normalmente todas as lojas, com poucas exceções, fecham nos feriados estaduais. Observe que todas as escolas fecham nos feriados e finais de semana. a = feriado, b = feriado da Páscoa, c = Natal, 0 = Nenhum  
- **SchoolHoliday** - indica se (loja, data) foi afetado pelo fechamento de escolas públicas  
- **StoreType** - diferencia entre 4 modelos de loja diferentes: a, b, c, d  
- **Assortment** - descreve um nível de sortimento: a = básico, b = extra, c = estendido  
- **CompetitionDistance** - distância em metros até a loja concorrente mais próxima  
- **CompetitionOpenSince[Month/Year]** - fornece o ano e mês aproximados em que o concorrente mais próximo foi aberto  
- **Promo** - indica se uma loja está fazendo uma promoção naquele dia  
- **Promo2** - Promo2 é uma promoção contínua e consecutiva para algumas lojas: 0 = a loja não está participando, 1 = a loja está participando  
- **Promo2Since[Year/Week]** - descreve o ano e a semana em que a loja começou a participar da Promo2  
- **PromoInterval** - descreve os intervalos consecutivos em que a Promo2 é iniciada, nomeando os meses em que a promoção é reiniciada. Por exemplo. "Fev, maio, agosto, novembro" significa que cada rodada começa em fevereiro, maio, agosto, novembro de qualquer ano para aquela loja  

# 3. Estratégias para a solução

Para dar velocidade ao projeto e entregar valor para o negócio no menor tempo possível, foi utilidado o método cíclico CRISP-DS, aplicando os passos a seguir:

**Passo 01. Descrição dos dados:** Nesta etapa foi utilizado métodos estatísticos para descrever os dados, como: média, mediana, desvio padrão, máximo, mínimo, intervalo, knewness e kurtosis. Além disso foi resolvido o problema de dados faltantes levando em conta as questões do negócio.

**Passo 02. Engenharia de Atributos:** Neste passo, o objetivo foi criar novos atributos a partir dos atributos já existentes para descrever melhor o fenômeno a ser previsto. 

**Step 03. Data Filtering:**

**Step 04. Exploratory Data Analysis:**

**Step 05. Data Preparation:**

**Step 06. Feature Selection:**

**Step 07. Machine Learning Modelling:**

**Step 08. Hyperparameter Fine Tunning:**

**Step 09. Convert Model Performance to Business Values:**

**Step 10. Deploy Modelo to Production:**

# 4. Top 3 insights


# 5. Modelos de machine learning aplicados

- Average Model (baseline para comparação)
- Linear Regression Model
- Linear Regression Regularized Model (Lasso)
- Random Forest Regressor
- XGBoost Regressor

# 6. Performance dos modelos de machine learning

# 7. Business Results

# 8. Conclusions

# 9. Lessons Learned

# 10. Next Steps to Improve







# 5. Modelos de machine learning aplicados



# 6. Performance dos modelos de machine learning

De modo a respeitar a ordem cronológica dos dados, foi utilizada a técnica de Time Series Cross-Validation para cada modelo, avaliando o Erro Médio Absoluto (MAE), o Erro Médio Absoluto Porcentagem (MAPE) e o Erro Quadrático Médio Raiz (RMSE).  
A performance real dos modelos é dada pela média dos erros +/- o desvio padrão do erro, representados na tabela abaixo:  

|    Model Name        |     MAE CV      |    MAPE CV    |     RMSE CV       |
|:--------------------:|:------------:|:----------:|:--------------:|
| Random Forest Regressor	    | 839.51 +/- 217.12	  | 11.64 +/- 2.32	| 1259.03 +/- 317.32 |
| XGBoost Regressor	          | 1048.45 +/- 172.04	| 14.48 +/- 1.74	| 1513.27 +/- 234.33 |
| Linear Regression	          | 2081.73 +/- 295.63	| 30.26 +/- 1.66	| 2952.52 +/- 468.37 |
| Linear Regression - Lasso	  | 2116.38 +/- 341.5	  | 29.2 +/- 1.18	  | 3057.75 +/- 504.26 |

Embora o modelo Random Forest Regressor tenha apresentado melhor desempenho, este modelo geralmente requer uma grande quantidade de espaço no servidor na etapa de implantação, gerando um aumento significativo de custo para a empresa. Portanto, optei pela utilização do modelo XGBoost Regressor, que após o ajuste fino dos hiperparâmetros apresentou desempenho semelhante e requer menos espaço no servidor, gerando menor custo para a empresa.

# 7. Performance após ajuste fino dos hiperparâmetros (Hyperparameter Fine Tuning)

Entendendo as métricas:
- MAE: o modelo apresenta em média um valor de erro de $652.
- MAPE: esse erro médio representa 9.5%, ou seja, para cada valor predito do modelo ele pode subestimar ou superestimar o resultado em 9.5%.
- RMSE: apresenta um erro médio de 938 unidades, sendo que essa métrica é mais sensível a outliers e com isso, se essa métrica estiver bastante discrepante da MAE, deverão serem feitos outros ajustes nos dados. No entanto, a RMSE foi utilizada como métrica de melhoria para o modelo.

|    Model Name        |     MAE      |    MAPE    |     RMSE       |
|:--------------------:|:------------:|:----------:|:--------------:|
|  XGBoost Regressor   |   652.623    |   9.53     |   938.783      |

![](reports/figures/final_model_performance.png)

# 8. Tradução do erro em métricas de negócio

Em termos de negócios, MAE significa o quanto a previsão está errada, definindo limites superior e inferior. MAPE significa o percentual em que os valores previstos são diferentes em relação aos valores alvo, sendo, portanto, uma métrica de fácil interpretação.  
A tabela abaixo mostra as piores previsões da loja, explicando que algumas lojas são mais desafiadoras de se prever. O campo previous_scenario é calculado subtraindo o MAE do campo de previsões e o campo best_scenario é calculado adicionando o campo MAE.  

|   store |   predictions |   worst_scenario |   best_scenario |      MAE |     MAPE |
|--------:|--------------:|-----------------:|----------------:|---------:|---------:|
| 292 |	106105.304688	| 102793.176257 |	109417.433118	| 3312.128431 |	56.627257 |
| 909 |	246366.156250	| 238776.324686 |	253955.987814	| 7589.831564 |	53.281534 |
| 876 |	210235.625000	| 206231.893629 |	214239.356371	| 4003.731371 |	30.846828 |
| 722 |	348907.000000	| 347013.004421 |	350800.995579	| 1893.995579 |	24.936654 |
| 274 |	199582.671875	| 198315.597168 |	200849.746582	| 1267.074707 |	21.853904 |

No entanto, as lojas  que apresentaram grandes erros no resultado das previsões são minorias, podendo ser identificadas como os pontos discrepantes no gráfico abaixo:

![](reports/figures/mape_outliers.png)

Por fim, a tabela abaixo mostra a soma de todas as lojas, bem como os piores e melhores cenários:

| Scenario       | Values           |
|:---------------|:-----------------|
| predictions    | $285,507,228.42 |
| worst_scenario | $284,775,307.37 |
| best_scenario  | $286,239,149.47 |

# 9. Como acessar e obter as previsões
## 9.1 Telegram

- Cadastre-se no Telegram e crie uma conta.
- Para acessar as previsões via Telegram, clique no link abaixo:  
[<img alt="Telegram" src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white"/>]( 
https://t.me/ederson_rossmann_bot)

## 9.2 Como obter a predição

- Envie o número de identificação da loja (um de cada vez) acompanhado de barra no início (ex: /22) e obtenha a previsão de vendas para as próximas seis semanas da loja escolhida.
- Caso o número da loja não exista, receberá em resposta a mensagem: "Store Not Available".

![](reports/figures/telegram.png)

# 10. Conclusões

Considerando o primeiro ciclo do projeto, o modelo final apresentou um desempenho satisfatório, considerando uma margem de erro de 9,53% do valor predito para mais ou para menos.  
Verificou-se também que o modelo final tem uma tendência a subestimar as previsões em 1,3%.

# 11. Lições aprendidas

- Projeto completo de Regressão Linear do tipo "end-to-end" de Ciência de Dados.
- Disponibilizar em nuvem o modelo de manchine learning para produção.

# 12. Próximos passos

Pode ser realizado um novo ciclo do método CRISP-DM de modo a buscar melhorar a performance do modelo, através de nova engenharia de variáveis, nova técnica de seleção de variáveis para o modelo, testar outros algoritmos e assim por diante.

# Autor

Ederson de Moraes  

[<img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>]( https://www.linkedin.com/in/ederson-moraes/)
