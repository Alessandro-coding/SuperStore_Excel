# Dataset

A primeira tarefa que iremos realizar será a de juntar todos os dados em uma planilha única. Realizaremos esse processo através do comando PROCV, onde iremos usar os valores das colunas em comum para extrair os valores das colunas que não possuímos ainda, como: estado do pedido, cidade do pedido, nome do cliente, etc. Assim, a partir da planilha *orders* criaremos uma *planilha total* com todas as informações dos pedidos.

# Desempenho de Produtos e Localizações

Após agrupar todas as informações em uma planilha só, iremos criar tabelas dinâmicas e posteriormente alguns gráficos para analisar as seguintes requisições:

- Quais produtos geram maior receita e quais possuem baixo desempenho?
- Existe uma relação entre o desempenho das lojas e as regiões em que estão localizadas?

Primeiramente, para realizarmos a primeira análise, iremos criar duas tabelas dinâmicas com o *nome dos produtos* nas linhas e o *valor de profit* na soma. Após isso, iremos ordenar as tabelas com base na coluna *soma de profit*, uma ordenada pelos maiores valores da coluna *soma de profit*, já a outra ordenada pelos menores valores, nos permitindo verificar quais produtos são os responsáveis pelos maiores lucros das vendas e os maiores prejuízos delas. É interessante a construção de gráficos simples, no caso foram feitos 2 gráficos de barras, para visualizar melhor a proporção dos profits dos produtos e obter insights mais facilmente.

Os 3 produtos que retornaram maiores lucros são 

| Nome do Produto | Soma de Profit | % do Total das vendas |
| --- | --- | --- |
| Canon imageCLASS 2200 Advanced Copier | 25199,928 | 8,80 |
| Fellowes PB500 Electric Punch Plastic Comb Binding Machine with Manual Bind | 7753,04 | 2,71 |
| Hewlett Packard LaserJet 3310 Copier | 6983,88 | 2,44 |

Os 3 produtos que retornaram maiores prejuízos são 

| Nome do Produto | Soma de Profit | % do Total das vendas |
| --- | --- | --- |
| Cubify CubeX 3D Printer Double Head Print | -8879,9704 | -3,10 |
| Lexmark MX611dhe Monochrome Laser Printer | -4589,973 | -1,60 |
| Cubify CubeX 3D Printer Triple Head Print | -3839,9904 | -1,34 |

Em seguida, para analisarmos os desempenhos das lojas por região (Cidades) também iremos criar uma tabela dinâmica onde a *city* será as linhas e o *profit* será a soma. Assim, obteremos as principais cidades que mais vendem. As 3 cidades que retornaram mais lucro são

| Nome da Cidade | Soma de Profit | % do Total das vendas |
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

![](/Imagens/analise_cohort.png)

**Recomendações**

O ano de 2014 é o mais representativo para se fazer a análise Cohort, pois foi onde a grande parte dos dados estão concentrados. Levando em conta esse contexto, os meses de maio, julho e setembro mostram uma retenção de clientes que se destaca em 2014, maior que 10%. 

Eu recomendo que as estratégias utilizadas pelas áreas de marketing e vendas nos 2 períodos mencionados anteriormente sejam revisitadas, pois demonstram uma eficácia maior com base na análise Cohort feita com os dados. 

# Segmentação RFM

Na análise RFM, temos como objetivo responder as seguintes perguntas:

- Quem são os “Campeõesˮ e “Clientes em Riscoˮ?
- Como os clientes estão distribuídos entre os segmentos RFM?
- Quais ações podem ser tomadas para fidelizar clientes ou recuperar os em risco?

A análise RFM consiste em classificar os clientes em grupos com base no seu comportamento de compra. Essa análise levará em conta 3 fatores, a compra mais recente do cliente, a quantidade de compras que o mesmo já fez na loja e o valor monetário total que esse já gastou em compras. Assim, usando como base a segmentação do [Blog G4 informação](https://g4educacao.com/blog/o-que-e-matriz-rfm), iremos utilizar os valores e intervalos para segmentar os clientes em 11 grupos: Campeões, Clientes em risco, Clientes fiéis, Clientes hibernando, Clientes perdidos, Clientes promissores, Clientes quase dormentes, Clientes que não posso perder, Clientes que precisam de atenção, Fiéis em potencial e Novos clientes. Conforme a seguinte imagem retirada do blog mencionado anteriormente.

![](/Imagens/matriz_rfm.png)

Para montar a análise RFM, precisaremos dos seguintes dados dos clientes: IDs dos clientes não repetidos, dias desde a compra mais recente do cliente, quantidade de compras realizadas pelo cliente, total gasto pelo cliente.

Os IDs dos clientes conseguiremos através da planilha *customers* onde não há repetição de IDs.

Os dias desde a compra mais recente serão calculados através de uma fórmula, onde usaremos o dia atual da análise como o dia da compra mais recente da *planilha total*. A fórmula será calculada utilizando a função MÁXIMO para calcular a data de pedido mais recente da *planilha total* menos a data de pedido mais recente do cliente na *planilha total* (usamos a função SE aninhada dentro da MÁXIMO para encontrar essa data comparando o ID do cliente com o da *planilha total*).

A quantidade de compras realizadas pelo cliente será calculada através do aninhamento das funções CONT.VALORES, UNIQUE e FILTER. A ideia é filtrar as compras através da comparação de ID e contar quantas dessas são únicas.

Por fim, a última coluna de total gasto pelo cliente será calculada através da função SOMASE que irá somar as vendas de acordo com a comparação de IDs dos clientes na *Análise_RFM* e na *planilha total*.

Após conseguirmos as informações anteriores dos clientes, iremos transformar elas em notas que vão de 1 a 5 para poder realizar a classificação dos clientes. Assim, criaremos uma tabela representando as notas com base nos intervalos de valores do Blog G4 informação.

|  | Recência | Frequência |
| --- | --- | --- |
| Nota 5 | 1 a 72 dias | 13 a 15 compras |
| Nota 4 | 73 a 145 dias | 10 a 12 compras |
| Nota 3 | 146 a 218 dias | 7 a 9 compras |
| Nota 2 | 219 a 292 dias | 4 a 6 compras |
| Nota 1 | 293 a 365 dias | 1 a 3 compras |

As notas serão adicionadas como novas colunas através da função SES ou IFS para comparar o valor da informação do cliente com a da tabela.

Vale ressaltar que a análise RFM no blog não utiliza as notas dos valores monetários dos clientes, mas iremos utilizar aqui e fazer uma média da nota de frequência e da nota de valor monetário para encontrarmos a classificação do cliente na matriz RFM. Dessa forma, a nota do valor monetário será dada com base em que percentil esse se encontra comparado às vendas da *planilha total*.

Após criar a tabela das notas com o nome da classificação do cliente, iremos fazer a média das notas da frequência e da nota valor monetário como uma nota só. E criaremos uma última coluna para a tabela através das funções ÍNDICE e CORRESP, comparando as notas do cliente com o valor da tabela e retornando o nome da sua classificação.

Por fim, montamos uma tabela dinâmica para verificar como estão distribuídos os clientes nos segmentos RFM.

![](/Imagens/tabela_rfm.png)

**Recomendações**

Eu recomendo que os segmentos mais expressivos sejam abordados primeiramente, com o objetivo de melhorar esses segmentos através de ofertas mais persuasivas para os clientes de cada segmento.  

O segmento de clientes em risco gera uma urgência maior, visto que representa um grupo que pode avançar para clientes fiéis caso a recência do cliente aumente. Assim, uma estratégia que vise vender ticket menor pode ser interessante para esse grupo.  

O segmento de cliente fiéis em potencial mostra uma ótima oportunidade, visto que representam um grupo que pode avançar para clientes fiéis caso aumente a frequência e o valor monetário do cliente. Assim, uma estratégia que vise vender um ticket maior pode ser interessante para esse grupo. 
