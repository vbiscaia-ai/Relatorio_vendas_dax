Projeto Star Schema — Financial Sample
🎯 Objetivo
Este projeto tem como finalidade transformar a tabela única Financial Sample em um modelo dimensional (esquema em estrela), estruturado para análises eficientes no Power BI. A modelagem inclui tabelas dimensão e fato, criação de calendário via DAX, medidas agregadas e um relatório extra comparativo entre produtos.
- [📊 Dax_Starschema.pbix (download)](https://github.com/vbiscaia-ai/Dax-Starschema/raw/master/Dax_Starschema.pbix)

🧠 Escopo da Análise
O modelo permite responder perguntas como:
• Total de vendas por produtos em determinado período
• Qual a evolução de vendas por mês e ano
• Como as vendas de um produto específico se comparam às dos demais

🏗️ Estrutura do Star Schema
🟨 Tabela Fato: F_Vendas
Contém os eventos de venda por produto e data.
Campos principais:
• SK_ID
• DateKey / Date
• ProdutoKey / ID_produto
• Sale Price
• Units Sold
• Sales
• Profit
• Discount Band
• Segment
• Country
• Salers
![Star Schema - Modelo Dimensional](https://github.com/vbiscaia-ai/Dax-Starschema/blob/master/Star_schema_vendas.png)

📘 Tabelas Dimensão
D_Produtos
• Id_produto
• Media_manufaturada
• Media_valor_vendas
• Mediana_Valor_Vendas
• Valor_maximo_vendas
• Valor_minimo_vendas
• Soma_unidade_vendida
• Product
D_Produtos_Detalhes
• Id_produto
• Discounts
• Product
• Discount Band
• Sale Price
• Units Sold
• Manufacturing Price
D_Descontos
• Id_produto
• Discounts
• Discount Band
D_Detalhes
• COGS
• Country
• Date
• Discount Band
• Discounts
• Id_produto
• Manufacturing Price
• Product
• Profit
• Sale Price
• Sales
• Segment
• Units Sold
D_Calendário
Criada via DAX com CALENDARAUTO() para gerar automaticamente um intervalo contínuo de datas com base nas tabelas do modelo.
Campos principais:
• DateKey
• Date
• Year
• MonthNumber
• NomeDoMes
• MesOrdem (criado para ordenar os meses no visual)
• DayOfWeek
• DayOfWeekName

📊 Relatório Extra
Foi desenvolvido um relatório adicional no Power BI que permite comparar as vendas do produto Paseo com as vendas de todos os outros produtos. Utiliza medidas DAX para isolar o contexto e calcular percentuais de participação.
![Relatório Power BI](https://github.com/vbiscaia-ai/Dax-Starschema/blob/master/relatorio.jpeg)

🛠️ Tecnologias Utilizadas
• Power BI Desktop
• Power Query / DAX
• GitHub (versionamento e documentação)
• Markdown (README e fórmulas)

📁 Estrutura do Repositório
• projeto.pbix — arquivo do Power BI
• star_schema.png — imagem do modelo em estrela
• README.md — este documento
• dax-formulas.md — arquivo com todas as fórmulas DAX utilizadas

📌 Exemplo de Fórmula DAX
Total Sales
Total Sales = SUM(F_Vendas[Sales])
Essa medida calcula o total de vendas agregando o campo Sales da tabela fato F_Vendas.

- [📄 funções_dax.md](https://github.com/vbiscaia-ai/Dax-Starschema/blob/master/funções_dax.md)
- [📄 tabela_date_dax.md](https://github.com/vbiscaia-ai/Dax-Starschema/blob/master/tabela_date_dax.md)

Para ver todas as fórmulas utilizadas no projeto, acesse o arquivo completo:
🔗 dax-formulas.md
- [📄 dax_formulas.md](https://github.com/vbiscaia-ai/Dax-Starschema/blob/master/dax_formulas.md)

✅ Boas Práticas Aplicadas
• Criação de surrogate keys no ETL para estabilidade dos relacionamentos
• Uso da fórmula DAX CALENDARAUTO() para geração automática da dimensão de tempo
• Ordenação de colunas categóricas de produtos por atributos numéricos (ex.: Id)
• Separação de medidas e colunas calculadas para melhor performance
• Documentação clara e acessível para reuso e revisão técnica

Autor: Victor Biscaia
Local: Salvador, Bahia – Brasil
LinkedIn: https://www.linkedin.com/in/victor-biscaia-097603371/




