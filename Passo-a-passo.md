# Dataset

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

Nessa etapa, nosso objetivo será responder às seguintes perguntas:

- Qual é a retenção de clientes ao longo dos meses?
- Quais cohorts apresentam maior retenção?
- Existem fatores sazonais que impactam a retenção?

Para montar a análise cohort da retenção dos clientes, precisaremos separar as informações que serão usadas nessa análise. Essas informações serão separadas em 4 colunas, usaremos o ID do cliente de cada pedido, a data do pedido, a data do primeiro pedido do cliente e a quantidade de meses decorridos desde o primeiro pedido do cliente até a data desse pedido do mesmo cliente. Vale ressaltar que nessa nova análise estarão os dados dos pedidos, assim, existirão IDs de clientes repetidos, pois esses podem ter feito mais de 1 compra na loja.

A ideia será fazer uma tabela do mês/ano pela quantidade de meses decorridos, gerando as "safras" dos clientes que permaneceram comprando na SuperStore. Essa análise ajuda a entender quais as tendências de compra no ano e quais estratégias de marketing ou vendas se provaram mais eficientes para a retenção dos clientes.

Primeiramente, iremos criar uma planilha chamada *Análise_Cohort*, onde iremos copiar toda a coluna de ID do cliente e toda a coluna de data do pedido da *Planilha total* para esta nova planilha. A data do pedido será transformada do formato DD/MM/AAAA para AAAA-MM, com o intuito de tornar os cálculos das funções mais fáceis. Em seguida, iremos usar a função PROCV para procurar as datas dos pedidos do ID da linha e retornar a data mínima dos pedidos desse ID, conseguindo a data da primeira compra do cliente de determinado ID. Por fim, iremos realizar um cálculo de meses decorridos através das colunas data do pedido e data do primeiro pedido, usando a função ESQUERDA iremos subtrair o ano da data do pedido pelo ano da data do primeiro pedido e multiplicar esse resultado por 12. Com esse resultado, iremos usar a função DIREITA para realizar a subtração do mês da data do pedido pelo mês da data do primeiro pedido e com isso somar ao resultado que conseguimos anteriormente, conseguindo a quantidade de meses decorridos da primeira compra até a compra atual.

Logo, criamos uma tabela dinâmica usando a data da compra como linhas pelos meses decorridos como colunas e a soma distinta dos IDs dos clientes. Colocamos a soma para mostrar a % do total geral e obteremos um gráfico semelhante a esse:

![](/Imagens/analise_cohort)

**Recomendações**



# Segmentação RFM
