# CienciadeDados_Wine
base de bados utilizada: https://archive.ics.uci.edu/ml/machine-learning-databases/wine/wine.data
## Compreensão do Negócio
### Objetivo de Negócio

1.  Identificação de Perfis de Vinho: Analisar os dados para identificar padrões exclusivos de composição química que caracterizam os vinhos produzidos por cada produtor.

2.  Otimização da Produção: Identificar fatores específicos na composição química que estão correlacionados com a qualidade do vinho. Isso pode ajudar os produtores a otimizar seus processos de produção para melhorar a consistência e qualidade do produto final.

3.  Classificação de Produtores: Desenvolver modelos preditivos para classificar automaticamente os vinhos de acordo com o produtor com base em suas características químicas. Isso pode ser útil para autenticação e certificação.

Obs: Decidimos, neste momento, realizar o item 3, que trata da Classificação de Produtores/Classes, devido ao tempo disponível para a conclusão do projeto.
## Objetivo de Mineração:
### Que tarefa de mineração será realizada para atingir o objetivo de Negócio?

Para atingir o objetivo de negócio de "Classificação de Produtores" com base nas características químicas dos vinhos, uma tarefa de mineração comumente realizada é a Classificação. A Classificação é uma técnica de aprendizado de máquina supervisionado, na qual um modelo é treinado para categorizar instâncias em classes ou categorias predefinidas.

### Aqui estão os passos geralmente seguidos para realizar a tarefa de Classificação neste contexto:  

1. Preparação dos Dados:  
    Organize os dados de forma que cada instância represente um vinho e suas características químicas. Atribua rótulos (classes) aos vinhos com base nos produtores.

2. Divisão dos Dados:  
    Separe os dados em conjuntos de treinamento e teste. O conjunto de treinamento é usado para treinar o modelo, enquanto o conjunto de teste é usado para avaliar a precisão do modelo.

3. Seleção de Características:  
    Identifique as características relevantes para a classificação dos produtores. Isso pode envolver uma análise exploratória para entender a importância de cada característica.

4. Escolha do Modelo de Classificação:  
    Seleção de um modelo de classificação adequado.

5. Treinamento do Modelo:
  Utilização do conjunto de treinamento para treinar o modelo, ajustando os parâmetros para otimizar o desempenho.

6. Avaliação do Modelo:
  Avaliação do modelo usando o conjunto de teste para medir a precisão da classificação. Métricas como acurácia, precisão, recall e F1-score podem ser utilizadas dependendo das características específicas do problema.

7. Interpretação dos Resultados:  
    Analise os resultados para entender como o modelo está classificando os vinhos em relação aos produtores. Isso pode incluir a análise de matrizes de confusão para identificar os erros mais comuns.

## Critérios de Sucesso Mineração:

Definimos como critério primário de sucesso a obtenção de uma devida classificação entre os produtores de vinhos presentes do dataset, nosso objetivo de negócio, que resulte em boa acurácia e níveis aceitáveis de erros.

A acurácia do modelo será a métrica essencial para determinar se este atribui corretamente as classes pré-determinadas aos vinhos e consequentemente se é de boa qualidade.

Idealmente optaríamos por um benchmarking externo, analisando modelos que utilizam a mesma base de dados e compartilham das mesmas intenções quanto ao critério de sucesso para traçar pontos de referência, porém dada a aparente ausência de exemplos com o mesmo critério de sucesso, a classificação entre os produtores, optaremos por um benckmarking interno, comparando os resultados individuais do critério de sucesso entre os cinco algoritmos utilizados.
2.Compreensão dos dados

## Introdução aos Dados:

A base de dados utilizada é uma base de dados com 178 instâncias diferentes de vinhos, divididas em três grandes classes e mais 13 atributos que representam características químicas dos exemplares e incluem diversas medidas como teor alcoólico, ácido málico, cinzas, alcalinidade das cinzas, magnésio, fenóis totais, flavonoides, fenóis não flavonoides, proantocianidinas, intensidade de cor, matiz e OD280/OD315 de vinhos diluídos.

### Dicionário dos dados:

    Alcohol: Álcool  
    Malic acid: Ácido málico  
    Ash: Cinzas  
    Alcalinity of ash: Alcalinidade das cinzas  
    Magnesium: Magnésio  
    Total phenols: Fenóis totais  
    Flavanoids: Flavonoides  
    Nonflavanoid phenols: Fenóis não flavonoides  
    Proanthocyanins: Proantocianinas  
    Color intensity: Intensidade da cor  
    Hue: Matiz  
    OD280/OD315 of diluted wines: OD280/OD315 de vinhos diluídos  
    Proline: Prolina  
    
### Tipos de dados:


Possuímos no total quatorze variáveis. Três delas, "níveis de magnésio, proline e classe", são representadas de forma qualitativa utilizando distinção por classes numéricas de tipo int64, e outra, "intensidade de cor", representada em um tipo object.  

As demais dez variáveis são de tipo numérico float64. Não possuímos dados faltantes de tipo null ou NaN.

### Compreendendo as colunas de dados:

  1. Alcool:  
    Alcool apresenta uma distribuição normal com concentração dos valores próximos a média
    Possui alta correlação com Prolina e Classe, onde valores menores de Alcool tendem a classe 1 e valores menores tendem a classe 3.
    Distribui-se de forma quase uniforme entre as classes, sendo a classe 1 majoritária.  

  2. Ácido Málico:  
    Acido Málico apresenta uma distribuição unimodal enviesada a esquerda.
    Possui alta correlação com Tonalidade ...

  3. Cinzas:  
    Cinzas apresenta uma distribuição normal e unimodal.

  4. Alcanilidade de cinzas:  
    Alcalinidade de cinzas apresenta uma distribuição normal e unimodal.

  5. Magnésio:  
    Marnésio apresenta uma disbribuição unimodal enviesada a esquerda.
    Possui alta correlação com Prolina.

  6. Total de Fenois:  
    Total de Fenois apresenta uma distribuição unimodal.
    Possui alta correlação com Flavonoides, Proantocianinas, OD280/OD315 e Classe.

  7. Flavanoides:  
    Flavonoides apresenta uma distribuição bimodal enviesada a esquerda. Possui alta correlação negativa com Fenois não Flavanoides e correlação positiva com OD280/OD315, total de Fenois, Tonalidade e Classe.

  8. Fenois não Flavanoides:  
    Fenois não flavanoides apresenta uma distribuição unimodal levemente enviesada a esquerda.
    Possui alta correlação negativa com Flavanoides, OD280/OD315, Total de Fenois e Classe. 

  9. Proantocianinas:  
    Proantocianinas apresenta uma distribuição unimodal enviesada a esquerda.
    Possui alta correlação com Flavonoides, OD280/OD315 e Total de Fenois. 

  10. Cor Intensidade:  
    Cor Intensidade apresenta uma distribuição bimodal. ...

  11. Tonalidade:  
    Tonalidade apresenta uma distribuição bimodal levemente enviesada a direita.
    Possui uma alta correlação com ácido malico e flavanoides.

  12. OD280/OD315:  
    OD280/OD315 apresenta uma distribuição bimodal levemente enviesada a direita.
    Possui alta correlação com flavanoides, proantocianinas, total de fenois e classe.

  13. Prolina:  
    Prolina apresenta uma distribuição unimodal enviesada a esquerda.
    Possui alta correlação com álcool, magnésio e classe.

  14. Classe:
    A distribuição de classes segue uma distribuição normal, com a classe 2 sendo predominante.

### Correlação
Podemos concluir dessa análise que existe uma forte relação entre a quantidade de fenóis em um vinho e sua classificação.

![grafico de correlação]()


### Distribuição entre as 3 categorias.  

Abaixo esboçamos gráficos e com eles observamos a distribuição de variáveis em relação as classes quanto a seus valores: Verificamos qual classe contem os valores mais altos e/ou baixos de cada variável, podendo cruzar essa relação com a diferença/correlação entre variáveis, váriancia e desvio padrão de cada variável. Dito isso, algumas observações que chamam atenção, a exemplo de:  

  1. Os valores acima de 2.0~ de ácido málico pertendem a classe 3  
  2. Em flavonoides os valores pertencentes a classe 3 não passam de 1.0  
  3. Em tonalidade há um grande desbalanceamento nas classes, com tons acima de 1~ pertencentes a classe 2 exclusivamente.  
  4. Em prolina todos os valores acima de 700 pertencem a classe 1

![grafico de distribuição]()


![histograma]()

### Preparação dos Dados  

Durante a fase de preparação dos dados fez-se necessário a conversão dos valores de cor intensidade para tipos numéricos que possam ser compreendidos e utilizados pelos algoritmos assim como no processo consistênte de análise de dados.  

Como investigado anteriormente, não foram encontrados valores ausentes de qualquer tipo e ainda que existam distibuições não-gausseanas e enviesadas tampouco ocorreu a necessidade de normalização.  

Quanto os valores fora de escopo, ou outliers, da forma que foram encontrados, foram considerados como ocorrências naturais e não como erros. Devido a baixa ocorrência acreditamos que não haverão impactos negativos significativos ao modelo.  

## Modelagem

Dado que temos um problema de classificação, escolhemos as seguintes abordagens que atendem a este propósito:

1. Random Forest

Técnica que costuma apresentar boa acurácia em problemas de classificação, permite avaliar o impacto das variáveis independentes, é explicável e de fácil compreensão. Por ser uma abordagem que funciona a partir da avaliação e seleção de vários classificadores, tem um custo computacional maior que técnicas mais simples, no entanto, justamente por se utilizar de várias classificações costuma ser mais asssertiva.

Os dados foram divididos em conjuntos de treinamento(70%) e teste (30%) e obtivemos 0.96 de acuácia


![boxplot]()

Na relação de alcool e classes verificamos que os níveis mais altos de alcool estão presentes na classe 1 e os níveis mais baixos na classe 2 onde também observamos a ocorrência de dois possíveis outliers acima de seu limite máximo.
Na classe 3 se predominam os níveis relativamente mais equilibrados de alcool. os dados contidos no intervalo intermodal parecem distintos quanto a seu nível de álcool.

Observando a distribuição e a distinção das classes quanto ao nível de alcool, podemos considerar os níveis de alcool como um bom indicador para categorizar as classes.

![violin]()

No gráfico violino em todas as classes temos uma distribuição que podemos considerar unimodal. Observamos melhor onde se concentram a maior parte dos valores e adquirimos uma noção melhor sobre a relação de níveis de alcool e a categorização por classe.

Verificamos que, mesmo que a região do segundo quartil, que concentra a maior parte dos valores daquela classe, seja distinta entra as demais (quanto ao seu nível de álcool) temos uma presença significativa de valores entre duas ou mais classes apresentando os mesmos níveis de alcool, sinificando que, embora seja um bom indicador, o nível de alcool seria capaz de determinar com boa acurácia a classe dos vinhos.

![flavonoides]()

Verificamos a distribuição e relação da classe aos níveis de Flavonoides no vinho, similar ao que fizemos com os níveis de álcool.

Tal como nos níveis de álcool os limites intermodais também mostram a presença de uma distinção de classes para o nível de Flavonoides. Observando os limites superiores e inferiores observamos que os vinhos com maior valor de Flavonoides tendem a ser da classe 1 e os menores da classe 2

![grau de importancia]()

Por fim visualizamos o grau de importância das variáveis para a classificação. Evidenciamos que Alcool e Flavonoides possuem alta relevância para a determinação das classes, algo que pode ser verificado anteriormente.

Verificamos, por exemplo, que Total de Fenois possui uma importância relativamente baixa para a classificação, mesmo que possua alto grau de correlação com Flavonoides que tem alto grau de importância e alto grau de correlação negativa com classe, nosso Target.

Usando o grau de importância podemos identificar quais variáveis são realmente significativas para a classificação, podendo assim ter uma visão mais compreensiva dos dados e se necessário realizar seleção de atributos.
Por meio do que foi descrito e dos dados que conhecemos, concluímos que os níveis de alcool, prolina, flavonoides e OD280/OD320 são as principais variáveis necessárias para classificar vinhos entre as três classes de vinhos existentes.

### Outros modelos
Outros modelos também foram utilizados, como pode ser evidênciado no documento original. Abaixo tomamos o resultado desses modelos para nossa conclusão.

## Avaliação

Os algoritmos foram avaliados com base em suas acurácias, precisão, recall e F1-score, onde a Regressão Logística emerge como a melhor alternativa:  
### Acurácia

A acurácia é tida comumente como principal métrica de avaliação e nos fornece a taxa de acertos do modelo, a seguir listamos as acuácias de cada modelo:

Usando o Algoritmo de RandomForest obtivemos uma acurácia de 96% para a primeira iteração  
Usando o Algoritmo de KNN obtivemos uma acurácia de 87% para a primeira iteração  
Usando o Algoritimo Árvore de decisão obtivemos uma acurácia de 93% para a primeira iteração  
Usando o Algoritmo de Regressão Logística obtivemos uma acurácia de 98% para a primeira iteração  
Usando o Algoritmo de SMV ovtivemos uma acurácia de 96% para a primeira iteração  

O algoritmo de Regressão Logística obteve a mais alta acurácia, atingindo 98% na primeira iteração, atingindo também o maior grau de acurácia na segunda iteração. A acurácia representa a proporção de previsões corretas em relação ao total de previsões. No entanto, a acurácia por si só pode ser enganadora, especialmente em conjuntos de dados desbalanceados.  

### Precisão

A precisão é a proporção de verdadeiros positivos em relação ao total de predições positivas. A Regressão Logística apresentou a mais alta precisão em ambas as iterações, indicando que, quando prevê uma classe positiva, é mais provável que esteja correta. Isso é crucial em situações em que falsos positivos são indesejados.  
Recall

O recall representa a proporção de verdadeiros positivos em relação ao total de instâncias positivas no conjunto de dados. Mais uma vez, a Regressão Logística obteve o melhor desempenho em recall em ambas as iterações, indicando que consegue identificar uma alta proporção de exemplos positivos.  
F1-Score

O F1-score é a média harmônica entre precisão e recall. Fornece uma medida balanceada entre essas duas métricas. A Regressão Logística também apresentou o maior F1-score em ambas as iterações, o que reforça sua capacidade de equilibrar precisão e recall de maneira eficaz.  
### Finalmente.  

Em síntese, ao analisar métricas como Acurácia, Precisão, Recall e F1-Score, destaca-se que a Regressão Logística emerge como a opção mais apropriada para resolver este problema de classificação. Isso se deve ao seu notável desempenho e maior habilidade em explicar variações nos dados. Contudo, é crucial ponderar outros aspectos, como a complexidade do modelo, o tempo de treinamento e a interpretabilidade, no processo de escolha do modelo definitivo para uma dada problemática.




