Ferramentas utilizadas
Primeirament foi realizado a tentativa de leitura do arquivo de dados em um jupyter notebook local. Foram utilizadas as seguintes ferramentas:
pandas, pyspark, pyarrow efastparquet. No entanto, mesmo a leitura sendo realizada em outros arquivos, o arquivo em questão, estava retornando vazio.
Devido a isso, foi utilizado a ferramenta Databricks, onde foi possível ler o arquivo com pypark.


Como apenas visualizar
Por meio do link : https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/3538777167072494/1341609434325299/17316877167626/latest.html

Como executar
Utilizar o DataBricks. (é possível criar uma conta gratuitamente na versão comunidade:https://community.cloud.databricks.com/login.html)
Fazer upload da base de dados no Databricks(https://docs.microsoft.com/en-us/azure/databricks/ingestion/add-data/).
Importar o notebook (https://docs.databricks.com/notebooks/notebooks-manage.html#import-a-notebook).
Associar o notebook a um cluster. (Se necessário, é possivel criar um cluster: https://docs.databricks.com/clusters/create.html)
Ao ler o arquivo, é preciso colocar substituir o caminho /FileStore/tables/desafio/dataset_cdjr_parquet.gzip pelo diretório correto.

Análise exploratória e preparação dos dados
Passo 1: Verificação geral nos dados retornando informações como valores máximos, mínimos, desvio padrão e média.
Passo 2: Avaliação da existência de valores nulos.
Passo 3: Análise de distribuição dos dados.
Passo 4: Análise de correlação entre as variáveis. As variáveis com maior correlação umas com as outras foram selecionadas para fazerem parte da classificação.
Passo 5: Avalição e remoção de outliers.


Modelagem
Passo 1: divisão entre os dados 
Treino:80%
Teste:20%
Passo 2 : Escolha dos algoritmos (SVM e Regressão logística foram escolhidos, pois são algoritmos bastante aplicados em classificações dicotômica.)

Avaliação da performance do modelo

Primeiro foi realizado um teste sem a remoção de outliers onde foram utilizadas as colunas 'feature0','feature2','feature15','feature10','target','feature1','feature6','feature9'.
Utilizando o SVM, temos:
Matriz de confusão:
[[ 25 108]
 [ 20 173]]
A especificidade : 0.18796992481203006
A sensibilidade : 0.8963730569948186
A acurácia : 0.6073619631901841

Utilizando regressão logística:
Matriz de confusão:
[[ 24 109]
 [ 15 178]]
A especificidade : 0.18045112781954886
A sensibilidade : 0.9222797927461139
A acurácia : 0.6196319018404908


Posteiormente foi realizada a análise de outliers e posteriormente os modelos foram aplicados novamente.
Utilizando o SVM, temos:
Matriz de confusão:
[[11  4]
 [ 4  7]]
A especificidade é 0.7333333333333333
A sensibilidade é 0.6363636363636364
A acurácia é 0.6923076923076923

Utilizando regressão logística:
Matriz de confusão:
[[10  5]
 [ 5  6]]
A especificidade é 0.6666666666666666
A sensibilidade é 0.5454545454545454
A acurácia é 0.6153846153846154



Referências
https://www.amazon.com.br/M%C3%A3os-Obra-Aprendizado-Scikit-Learn-TensorFlow/dp/8550803812


