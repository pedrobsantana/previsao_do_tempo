# Consumo de Dados para Previsão do Tempo das Cidades do Rio de Janeiro

**Objetivo**   
Na engine de processamento Apache Spark, utilizar as linguagens Python e SQL.   

**Descrição**   
Extrair dados de previsão do tempo das cidades do Rio de Janeiro. Para consultar todas as cidades dessa região, utilizaremos a API do IBGE. No caso, basta realizar uma requisição HTTP com o método GET, utilizando a URL abaixo:   

https://servicodados.ibge.gov.br/api/v1/localidades/microrregioes/33001|33002|33003|33004|33005|33006|33007|33008|33009|33010|33011|33012|33013|33014/municipios

Com esses dados, gerar um dataframe e a partir dele uma temp view: "cities".   

Utilizando os nomes das cidades, foi consultado os dados de previsão de tempo para cada cidade. Para realizar essa consulta, foi utilizada a API da API da WeatherAPI.   

Com os dados consultados, gerar um dataframe e partir dele outra temp view: "forecasts".   

Com as temp views geradas, foi utilizado o Spark SQL para criar queries e gerar dataframes das seguintes tabelas:   

**Tabela 1: dados de previsão do tempo para os próximos cinco dias, para cada data e cidade consultadas.**   

As colunas dessa tabela serão:   

. Cidade   
. CodigoDaCidade   
. Data   
. Regiao   
. Pais   
. Latitude   
. Longigute   
. TemperaturaMaxima   
. TemperaturaMinima   
. TemperaturaMedia   
. VaiChover   
. ChanceDeChuva   
. CondicaoDoTempo   
. NascerDoSol   
. PorDoSol   
. VelocidadeMaximaDoVento   

Observações:    
. preencher os valores da coluna "VaiChover" com "Sim" ou "Não";   
. a coluna "CodigoDaCidade" é o ID retornado junto com os nomes da cidades na API do IBGE.   

**Tabela 2: quantidade de dias com chuva e sem chuva para os dias consultados, para cada data consultada.**   

As colunas dessa tabela serão:   

. Cidade   
. QtdDiasVaiChover   
. QtdDiasNaoVaiChover   
. TotalDiasMapeados   

Ao final, as duas tabelas foram exportadas em formato .csv
