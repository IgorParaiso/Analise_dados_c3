# Análise de Dados aplicada a computação - C3

## Componentes
-  Allan Jones da Silva Jesus
- Igor Paraiso Demuner
- José Carlos Vieira dos Santos Júnior

# Análise Exploratória
Nesse ponto, nós plotamos vários gráficos para entender melhor qual o relacionamento entre a variável target (Preço de venda) com as variáveis explicativas.

Pontos relevantes encontrados:
- A área do lote, não é proporcional ao preço, pois lotes de mesmo tamanho, costumam ter uma infinidade de valores diferentes.
- O ano de construção da casa, tem bastante influência no preço, podemos observar uma tedência crescente.
- A área de fundação da casa também não tem influência no preço
- A área de porão tem um efeito positivo no preço
- Quanto mais novo o ano de contrução da garagem, maior o preço
- A grande maioria dos preços de casa está entre 100.000 e 200.00
- Quando observamos a distribuição de preços por qualidade de material, também encontramos uma correlaçã opositiva.
- O ano da venda não tem impacto real no valor da venda

# Pré-processamento
O primeiro passo de pré-processamento, foi identificar a quantidade de missings (ou seja valores nulos), nós optamos por substituir os nulos de variáveis numéricas pra 0, e substituir os nulos de variáveis categoricas por Na, quando aplicável, substituímos, pela cartegoria mais relevantes, por exemplo o sistema elétrico, quando nulo substituímos pelo mais básico.
Utilizamos um Ordinal Encoder para transformar as variáveis categóricas em numéricas, para que o nosso regressor pudesse entende-las e interpreta-las

# Modelo Regressor
O modelo que escolhemos para prever o preço das casas foi o RandomForestRegressor, definimos 100 estimadores e separamos o conjunto em treino (70% dos registros) e teste (30% dos registros).
O modelo paresentou:
- R² de 0,89
- RMSE de 26974,62
- MAE de 26800,10

# Modelo para definir se uma casa é cara ou barata
Para esse definição, utilizamos o Kmeans divido em 2 clusters, considerando as principais variáveis que tem correlação com preço de venda, no caso são:
  - Nota da casa
  - Se é acima do nível do solo
  - Capacidade de carros

O grupo 0 que tem a média mais baixa de preço e portanto casas baratas
O grupo 1 que tem a média mais alta de preçoe e portanto casas caras

# Modelo de clusterização
Para esse caso também utilizamos o Kmeans com as principais variáveis correlacionadas ao target, utilizamos a regra do cotovelo e identificamos que o número de clusters ideal é 3 e por isso dividimos o dataset em 3 grupos
