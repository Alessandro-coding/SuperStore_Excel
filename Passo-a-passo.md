# Banco de dados

A primeira tarefa que iremos realizar será a de juntar todos os dados em uma planilha única. Realizaremos esse processo através do comando PROCV, onde iremos usar os valores das colunas em comum para extrair os valores das colunas que não possuímos ainda, como: estado do pedido, cidade do pedido, nome do cliente, etc. Assim, a partir da planilha *orders* criaremos uma *planilha total* com todas as informações dos pedidos.

# Desempenho de Produtos e Localizações

Após agrupar todas as informações em uma planilha só, iremos criar tabelas dinâmicas e posteriormente alguns gráficos para analisar as seguintes requisições:

- Quais produtos geram maior receita e quais possuem baixo desempenho?

- Existe uma relação entre o desempenho das lojas e as regiões em que estão localizadas?

Primeiramente, para realizarmos a primeira análise, iremos criar duas tabelas dinâmicas com o *nome dos produtos* nas linhas e o *valor de profit* na soma. Após isso, iremos ordenar as tabelas com base na coluna *soma de profit*, uma ordenada pelos maiores valores da coluna *soma de profit*, já a outra ordenada pelos menores valores, nos permitindo verificar quais produtos são os responsáveis pelos maiores lucros das vendas e os maiores prejuízos delas. É interessante a construção de gráficos simples, no caso foram feitos 2 gráficos de barras, para visualizar melhor a proporção dos profits dos produtos e obter insights mais facilmente.

Os 3 produtos que retornaram maiores lucros são 

| Nome do Produto | Soma de Profit | % do Total das vendas 
| --- | --- | --- |
| Canon imageCLASS 2200 Advanced Copier | 25199,928 | 8,80 |
| Fellowes PB500 Electric Punch Plastic Comb Binding Machine with Manual Bind | 7753,04 | 2,71 |
| Hewlett Packard LaserJet 3310 Copier | 6983,88 | 2,44 |

Os 3 produtos que retornaram maiores prejuízos são 

| Nome do Produto | Soma de Profit | % do Total das vendas 
| --- | --- | --- |
| Cubify CubeX 3D Printer Double Head Print | -8879,9704 | -3,10 |
| Lexmark MX611dhe Monochrome Laser Printer | -4589,973 | -1,60 |
| Cubify CubeX 3D Printer Triple Head Print | -3839,9904 | -1,34 |

Em seguida, para analisarmos os desempenhos das lojas por região (Cidades) também iremos criar uma tabela dinâmica onde a *city* será as linhas e o *profit* será a soma. Assim, obteremos as principais cidades que mais vendem. As 3 cidades que retornaram mais lucro são

| Nome da Cidade | Soma de Profit | % do Total das vendas 
| --- | --- | --- |
| New York City | 62036,9837 | 21,66 |
| Los Angeles | 30440,7579 | 10,63 |
| Seattle | 29156,0967 | 10,18 |

**Recomendações**

Em relação aos produtos, deve-se focar na investigação de estratégias para potencializar ainda mais a venda desses produtos “carro chefe” que trazem maiores lucros para a empresa. Já no caso dos produtos que estão gerando prejuízos, são necessárias medidas para aumentar a venda desses produtos ou descartá-los das vendas.

Em relação as regiões que mais vendem, existem cidades que concentram grande parte do capital das vendas. Assim, abrir novas lojas nessas cidades ou aplicar um marketing mais persuasivo para pessoas dessas regiões são opções de estratégias a serem estudadas. 

# Análise de Cohort

# Segmentação RFM
