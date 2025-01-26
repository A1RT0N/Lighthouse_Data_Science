### Desafio de Previsão de Precificação - Plataforma de Aluguéis Temporários

#### Introdução
O objetivo do desafio era construir um modelo preditivo que é capaz de prever preços de casas de aluguel temporário com base nos dados fornecidos e ter respostas para o seguinte:

1. Análise Exploratória de Dados (EDA - Exploratory Data Analysis)
2. Responder perguntas específicas sobre variáveis que têm algum efeito sobre o preços.
3. Modelando e testando um modelo preditivo. 
4. Sugestões de valores para um exemplo aleatório de preço para um apartamento

---

### EDA

#### Características Gerais:
- **16 colunas** relativas ao ambiente de propriedade, à orientação de anfitrião, ao tempo de estadia desses aluguéis.

- Algumas colunas continham valores ausentes, como `ultima_avalicao_e_reviews_por_mes`.

#### Insights Principais:
1. **Gráfico de Distribuição de Preços**:
   - A maior parte dos preços está abaixo de $300 por noite.
   - Outliers altos foram identificados e tratados ($10.000).

2. **Preço por Grupo de Bairro**:
   - **Manhattan** tem a maior média de preço ($178,94), seguido por **Brooklyn** (117,81).
   - **Bronx** apresenta preços mais baixos ($85,28).

3. **Correlação**:
   - `disponibilidade_365`: Tem uma moderada correlação positiva com o preço (0.23).
   - Outras variáveis numéricas com baixa correlação direta com os preços.

---

### 2. Respostas às Perguntas do Desafio

#### a. Onde seria mais indicado investir em um apartamento para alugar?
- **Manhattan**: um lugar muito promissor devido aos preços mais altos.
- Dentro de Manhattan, **os lados de Midtown e do Upper East Side** são mais procurados, mas disponibilidade é alta. 

O número mínimo de noites resultou em um menor impacto, mas os valores que eram exorbitantes (>30 noites) haviam sido tratados para evitar distorções.

c. Há algum padrão no texto do local para ḍots de valor mais alto?
"os nomes incluem as palavras 'luxury, 'penthouse' e 'entire', parecem estar associados a preços mais altos.

3. Modelado Preditivo

Modelos Testados:

Regressão Linear (Baseline):

MSE: 13.325,61

MAE: 76,97

R²: 0,032

O desempenho é limitado devido à incapacidade de capturar relações não lineares.

Gradient Boosting Regressor:

MSE: 11.909,65

MAE: 71,47

R²: 0,135

Melhor desempenho, capturando relações mais complexas entre as variáveis.

Melhor Modelo:

O Gradient Boosting Regressor foi escolhido por apresentar melhor desempenho geral, explicando 13,5% da variância do preço e reduzindo o erro absoluto médio para $71,47.

4. Sugestão de Preço para o Apartamento Exemplo

Características do Apartamento:

Localidade: Midtown, Manhattan

Tipo: Entire home/apt

Disponibilidade: 355 dias por ano

Número de reviews: 45

Previsão de Preço: $178,79 por noite

5. Conclusão

Embora em maior medida em comparação com a regressão linear, o modelo Gradient Boosting conseguiu capturar relações importantes entre as variáveis. A previsão para o apartamento exemplo está alinhada aos preços observados em Manhattan.