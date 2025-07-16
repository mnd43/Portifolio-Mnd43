# Análise de Fornecedores  

## Objetivo  
Este projeto teve como objetivo realizar uma análise geral dos fornecedores, atentando-se à integridade do saldo contábil, à concentração e representatividade de terceiros e à identificação de possíveis inconsistências no controle da empresa.  

## Ferramentas utilizadas  
Utilizei a biblioteca Faker do Python para criar a base fictícia, determinando alguns parâmetros para que se aproximasse minimamente das bases reais utilizadas em empresas. Posteriormente, desenvolvi o dashboard utilizando o Power BI.

## Tratamento de Dados  
Como a base foi criada, não houve necessidade de grandes tratamentos em relação a formatos e limpeza. Apenas desmembrei a base maior nas tabelas de dimensões: **D_Fornecedores**, **D_Moeda**, **D_Tempo**; e a tabela fato **F_Transações**, para treinar modelagem e facilitar as análises.  

## Gráficos utilizados e Insights extraídos  

### Gráfico de pizza  
Como o intuito era comparar os itens por anos e havia apenas dois anos na base, optei por essa visualização. Nesse gráfico, é possível observar valores do ano anterior, o que pode indicar inconsistências no ERP ou ausência de conciliação na contabilidade. No entanto, esses registros também podem estar corretos caso se refiram a itens com prazos de negociação mais longos, itens importados destinados a projetos específicos em construção, ou casos de renegociação de prazo. Cabe uma análise de negócio mais aprofundada para entender o real motivo.  

### Tabela  
Nesta tabela de representatividade, é possível identificar que a base de fornecedores da empresa é bastante pulverizada, sem uma grande concentração ou dependência de apenas um terceiro. Isso reduz os riscos e pode ser um indicativo positivo para a continuidade do negócio. Os dez maiores valores somam menos de 5% do total global. Além disso, há um fluxo constante de transações com os fornecedores, principalmente os de maior representação monetária, o que sugere que não há uma relação de exclusividade ou compras muito específicas de alto valor com um único terceiro.  

### Gráfico de colunas  
Cabe um questionamento sobre o motivo dos valores à vista estarem registrados na base de contas a pagar, visto que essa rubrica é destinada a obrigações futuras. Esses valores deveriam ser lançados com contrapartida em caixa e equivalentes, refletindo corretamente a saída imediata de recursos financeiros. Essa situação pode indicar erro na parametrização do ERP ou falta de rastreabilidade na empresa.  

### Mapa preenchido  
O fato de haver fornecedores externos com transações em moeda estrangeira indica que a empresa precisa manter o controle da variação cambial, o que afeta diretamente outras contas do balanço. Dependendo da natureza e do motivo dessas compras, essa informação pode ser útil para o cálculo de **Transfer Pricing**.  

### Gráfico de linhas  
Neste gráfico, é possível observar que, de maneira geral, a conta não variou significativamente ao longo do ano, com exceção do mês de fevereiro. Isso não indica erro ou inconsistência, mas levanta um questionamento de negócio para entender se essa variação é sazonal ou resultado de algum evento pontual ocorrido no mês.  

## 📸 Visualização do Dashboard



[⬅️ Voltar para o início](index.md)
