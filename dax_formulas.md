📅 D_Calendário (criada com CALENDARAUTO)
A tabela de calendário foi criada com CALENDARAUTO(12), que gera automaticamente um intervalo contínuo de datas com base nas tabelas do modelo.

Table_date = CALENDARAUTO(12)

DayWeekName = FORMAT('Table_date'[Date], "DDDD")

Mês = MONTH('Table_date'[Date])

MêsOrdenado = FORMAT(MONTH('Table_date'[Date]), "00") & " - " & FORMAT('Table_date'[Date], "MMMM")
// Medida criada para agregar número do mês e nome do mês, permitindo ordenação correta no visual

WeekNumber = WEEKNUM('Table_date'[Date])

Year = YEAR('Table_date'[Date])



📈 Medidas para Relatórios
Medidas agregadas para uso em visuais, KPIs e comparações.

🎯 Média de vendas por produto (exceto Paseo)
MediaSemPaseo =
CALCULATE(
    AVERAGEX(
        VALUES(F_Vendas[Product]),
        CALCULATE(SUM(F_Vendas[Sales]))
    ),
    F_Vendas[Product] <> "Paseo"
)


Essa medida calcula a média das vendas totais por produto, excluindo Paseo da avaliação.


📊 Percentual que Paseo representa no total de vendas
PercentualPaseo =
DIVIDE(
    CALCULATE(SUM(F_Vendas[Sales]), F_Vendas[Product] = "Paseo"),
    CALCULATE(SUM(F_Vendas[Sales]), ALL(F_Vendas[Product]))
)


Ideal para KPIs que mostram a participação de Paseo nas vendas totais.


💰 Total de todas as vendas
TotalVendas =
SUM(F_Vendas[Sales])



💰 Total de vendas de Paseo
TotalVendasPaseo =
CALCULATE(SUM(F_Vendas[Sales]), F_Vendas[Product] = "Paseo")




