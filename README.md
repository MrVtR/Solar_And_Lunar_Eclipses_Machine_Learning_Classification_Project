# Repositório para Análise de dados, Treinamento de Modelo preditivo e Análise de Resultados para dados obtidos da NASA sobre Eclipses Lunares e Solares
## Fonte para os datasets criados pela NASA: 
https://www.kaggle.com/datasets/nasa/solar-eclipses

## Fonte para as informações de Documentação e Conclusão escritas por mim com base no dataset da NASA:
https://eclipse.gsfc.nasa.gov

## Bibliotecas utilizadas
- Pandas
- Numpy
- Matplotlib
- Seaborn
- Sklearn
- Pycaret
- Figlet

## Checklist do projeto:
### Eclipse Lunar:
- [x] Análise exploratória e Pré Processamento dos dados
- [x] Verificação de Outliers e tratativa caso exista
- [x] Treinamento de Modelo Preditivo inicial
- [x] Comparação de Modelos Preditivos em busca do melhor resultado
- [x] Validação Cruzada para comprovar a estabilidade do Modelo escolhido
- [x] Escrita de Conclusão
- [x] Criação/Melhoria de Documentação
### Eclipse Solar:
- [x] Análise exploratória e Pré Processamento dos dados
- [x] Verificação de Outliers e tratativa caso exista
- [x] Treinamento de Modelo Preditivo inicial
- [x] Comparação de Modelos Preditivos em busca do melhor resultado
- [x] Validação Cruzada para comprovar a estabilidade do Modelo escolhido
- [x] Escrita de Conclusão
- [x] Criação/Melhoria de Documentação

## Conclusão para o modelo de Eclipses Lunares
Para a etapa de exploração e pré-processamento, fiz uma verificação inicial dos possíveis problemas: Valores nulos em algum lugar do DataFrame, dados não normalizados, dados uplicados, Variáveis categóricas, correlação baixa entre os dados e outliers.

Destes problemas,encontrei que havia algumas conversões de dados para serem feitas, como String para Float e String para DateTime, com o objetivo de verificar as correlações destes dados com os demais,onde a correlação destes dados convertidos se mostraram baixas e portanto, os dados foram removidos do modelo de treinamento. Além disso, também verifiquei que os dados de classificação estavam em formato de String, então serializei a classificação do dataset e fiz com que as informações fossem classificadas como números inteiros, onde cada número está atrelado a uma classificação única dos dados

Sabendo que o problema era de classificação, explorei os modelos KNN e Naive Bayer, sem uso de hiperparâmetros neles, definido o número de K-vizinhos como 5 também. O algoritmo Naive Bayer teve um score de 0.86, enquanto o KNN 0.89.

Em estudos passados sobre Machine Learning, vi que alguns estavam usando uma biblioteca chamada PyCaret e fui atrás da documentação dela pra implementar aqui. Se trata de uma biblioteca que automatiza testes com diversos modelos e encontra o melhor com seus hiperparâmetros já definidos em pouco tempo(Para este dataset, questão de 10seg mais ou menos), meu objetivo aqui no caso seria tentar subir ainda mais o score, utilizando outros algoritmos. De todos os analisados pela biblioteca, foi retornado o Random Forest Classifier como sendo o de maior score, plotei sua Matriz de confusão e o Report de Classificação para ver se não estava dando nenhum caso de Overfitting e aparentemente ficou estável, tendo um score final de 0.971.

Por fim, adotei o método de validação cruzada, usando 10 iterações para ser um pouco mais rigoroso com os dados e comparando tanto o KNN que fiz sua implementação manualmente quanto a sugestão do PyCaret, onde foi obtido o resultado de que realmente o algoritmo do PyCaret é ligeiramente mais eficiente nos resultados, tendo uma média de Score em 0.9015, enquanto o KNN teve 0.8944, pouco menos de 1% a menos de média.

## Conclusão para o modelo de Eclipses Solares
Para o modelo de classificação Solar, fiz as mesmas verificações na exploração e pré-processamento de dados: Busca por Valores nulos em algum lugar do DataFrame, dados não normalizados, dados uplicados, Variáveis categóricas, correlação baixa entre os dados e outliers.

Como no modelo anterior foi evidenciado que as conversões de dados String -> Float e String -> DateTime não tinham uma correlação boa com os dados, aqui já os descartei de imediato

Sabendo que o problema era de classificação, explorei os modelos KNN e Naive Bayer, sem uso de hiperparâmetros neles, definido o número de K-vizinhos como 5 também. O algoritmo Naive Bayer teve um score de 0.933, enquanto o KNN 0.915.

Em estudos passados sobre Machine Learning, vi que alguns estavam usando uma biblioteca chamada PyCaret e fui atrás da documentação dela pra implementar aqui. Se trata de uma biblioteca que automatiza testes com diversos modelos e encontra o melhor com seus hiperparâmetros já definidos em pouco tempo(Para este dataset, questão de 10seg mais ou menos), meu objetivo aqui no caso seria tentar subir ainda mais o score, utilizando outros algoritmos. De todos os analisados pela biblioteca, foi retornado o Random Forest Classifier como sendo o de maior score, plotei sua Matriz de confusão e o Report de Classificação para ver se não estava dando nenhum caso de Overfitting e aparentemente ficou estável, tendo um score final de 0.973.

Por fim, adotei o método de validação cruzada, usando 10 iterações para ser um pouco mais rigoroso com os dados e comparando tanto o KNN que fiz sua implementação manualmente quanto a sugestão do PyCaret, onde foi obtido o resultado de que o algoritmo do PyCaret se saiu ligeiramente menos eficiente nos resultados, tendo uma média de Score em 0.9351, enquanto o KNN teve 0.9367, cerca de 0.0016 de diferença apenas no score obtido.
