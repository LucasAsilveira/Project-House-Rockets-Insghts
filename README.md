# Project-House-Rockets-Insights
#STATUS: EM DESENVOLVIMENTO...

# Contexto 
### Projeto de Insights de uma plataforma de compras e vendas de imóveis

House Rockets é uma plataforma digital de compras e vendas de imóveis. Possui no seu banco de dados 21613 imóveis catalogados com 21 atributos distintos.
Como Cientista de dados, fui contratado pela empresa para encontrar melhores oportunidades no mercado de imóvel. 

O contexto é fictício, e foi utilizado para praticar minhas habilidades de desenvolver um projeto de Insights na área de Dados. 


## 1. Questão de Negócio

### 1.1. Problema 

O CEO da empresa gsotaria de maximizar o lucro da empresa encontrando bons negócios. A estratégia usada é encontrar casas com bom preço para compra e conseguir lucro na venda. O time de compra não consegue tomar boas decises de compras com a atual organiazação e estruturação. 

### 1.2. Causas do Problema

Falta de um método para organizar, vizualizar e avaliar da melhor forma. Pois existem muitos atributos que as tornam mais ou menos atrativas aos compradores e vendedores e a localização e o período do ano também podem influenciar os preços. O portifólio é muito grande, levando muito tempo para fazer o trabalho de forma manual. 

### 1.3. Solução 
Será feita uma analise exploratória de dados, afim de analisar todos os atributos, podendo organizar em tabelas e gráficos para a analise. Tornar possível a visualização de todas as analises de maneira on-line. 


## 2. Descrição das Variáveis e Premissas

- Foi retirado imóvel registrado com 33 banheiros, após a analise foi definido que houve possível erro de digitalção. 
- Todos os imóveis do portifólio estão em boas condiçes. 


## 3. Planejamento da Solução:

### 3.1. O que será entregue:
A solução será entregue em forma de um aplicativo no Streamlit que será armazenada na plataforma Heroku, para poder ser acessada de maneira on-line, a qualquer hora. Esta plataforma terá gráficos e tabelas, afim de simplificar a exploração dos dados e irá conter: 
- Geolocalização em mapas para poder visualizar a localização dos imoveis e fazer analise dos mesmos.
- Gráficos com opções de filtro para poder filtrar e avaliar os imóveis conforme as caracteristícas desejadas. 
- Tabela com indicação de compra e score de precificação do imóvel.  

### 3.2. Ferramentas Usadas:

- Python 3.8;
- Jupyter Notebook;
- PyCharm
- Panda Enviroment;
- Git e Github;
- Streamlit;
- Heroku;


### 3.3. Processo :
- Coleta de dados: Os dados foram coletados do site Kaggle.
- Limpeza dos Dados: Organizar e Renomear colunas, descrever os tipos, dimensão, checar dados faltantes e realizar descrição estatística, criar hipóteses de negócio criando novas variáveis para exploração destas adiante.
- Exploração dos dados: Fazer análise gráfica das variáveis, validar as hipóteses levantadas.
- Criar modelo de Insiths: Estimar precificação através de um score usando principais Insights encontrados. 
- Tabela de indicação: Criar tabela com indicação de melhores oportunidades de compras. 
- Estimativas econômicas do negócio: Fazer avaliação econômica e previsão de lucro.  


## 4. Principais Insights dos Dados:
### 1. Imóveis com graduação('grade') mais elevada possuem preço em média mais alto. (VERDADEIRA)
A medida que aumenta o 'grade', que é uma medida quanto ao desigin do imóvel, o preço medio do imóvel sobe. Esta diferença é agravada acima da graduação 6.

-Insight Gerado: Este atributo referesse ao  design e fazendo uma avaliação de todos os atributos que indicam qualidade do imóvel este foi o que melhor indicou qualidade com relação ao preço, assim foi o usado na hora de classificar a qualidade para o score de preço feito no modelo.  

### 2. Imóveis com localização de frente para o mar('waterfront') possuem preço médio mais alto. (VERDADEIRA)
Em média os imóveis com localização 'waterfront' chegam a ter 3x mais o valor dos que não possuem esta localização. 

- Insight Gerado: Este atributo é muito relevante ao preço. Ao buscar oportunidades de imóveis com preços acessíveis que possuem este atributo positivo, pode-se encontrar boas oportunidades de lucro.

### 3. Imóveis que já foram reformados possuem preços mais alto. (VERDADEIRO)
Imóveis reformados tem preço em média 1.43 vezes maior.

- Insight Gerado: Podemos levantar dois pontos, primeiro usar este atributo para encontrar imóveis ja reformados, que estjam com preços bons para compra. O segundo é encontrar boas oportunidades de imóveis não reformados, podendo ao fazer uma boa reforma, conseguir uma valorização de em média 40%.

### 4. Imóveis que possuem porão possuem preço mais alto. (VERDADEIRO)
Imóveis que possuem porão possuem em médio preço maior que as que não possuem. Esta relação é de 1.28 vezes maior.

- Insight Gerado: Encontrar boas oportunidades em imóveis com porão, pois este atributo sendo positivo resulta em uma valorização média de quase 30%. 

## 5. Respondendo Questão de Negócio:

## QUESTÃO: Quais são os Imóvies que a House Rockets deveria comprar e por qual preço?

### 5.1. Estratégia utilizada:
#### Para encontrar boas oportunidades a partir dos insigths obtidos no estudo e exploração dos dados foi usado os seguintes critérios:   

-  Criar uma coluna chamada "score_price" onde será feita uma graduação levando em conta as principais features que valorizam um imóvel, estas definidas durante o processo de analise dos dados. 

-  Criar coluna com preço da mediana de cada região. 

-  Criar coluna o status de sugestão de compra ou não do imóvel. Onde os critérios é, score favorável e preço 10% menor que a mediana da região, status favorável a compra, se não não favorável a compra. 

### 5.2. Classificação por score de preço:
#### Para definir um score de potencial de preço para cada imóvel, foi definido valores a serem adicionadoas a este score dadas as carácteristica principais que valorizam um imóvel estas definidas com base nos estudo e analise dos dados e insghts, foram eles: 

- score_living: De 1 a 5, onde foram separados proporcionalmente em 5 grupos de tamanho de imóveis. Dando pontução maior para móveis com maior área interno.

- score_grade : De 0 a 2, onde foram definidos conforme analise que percebeu que valorizações eram maiores em grades superiores a 8 e mais baixas quando inferiores a 3. 

- score_waterfront: De 0 a 3 onde 0 para não ter vista para água e 3 para imóveis com vista. 

- score_renovated: De 0 a 2, onde 0 quando não teve reforma e 1 para imóveis reformados. 

- score_bedrooms: De 0 a 2 onde separou-se em menos de 4 quartos, 4 a 6 e 7 ou mais. 

- score_bathrooms: De 0 a 2 onde separou-se em menos de 3, 3 a 5 e 6 ou mais.

- score_basement: De 0 a 1, onde 0 para imóveis que não possuem porão e 1 para os que possuem. 

#### Segue a baixo uma amostra da tabela com a estimativa de score:
![image](https://user-images.githubusercontent.com/94136773/157046694-3629e860-a4c0-43fe-a7a3-32cd2693ce9a.png)


## 6. Resultados financeiros para o negócio:

## 7. Conclusão:

## 8. Próximos Passos:

## 9. Referências:
