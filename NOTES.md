# Copilot Notes

## Average Order Value

- Copilot suggestion:
  `DIVIDE ( [Total Sales], [Total Transactions] )`

- Correction:
  Used the Copilot suggestion without modification because it correctly calculates average sales per transaction.

  ## MoM Sales Growth %

- Copilot suggestion:

```DAX
MoM Sales Growth % =
VAR CurrentSales =
    SUM ( Fact_Sales[sales_amount] )
VAR PreviousMonthSales =
    CALCULATE (
        SUM ( Fact_Sales[sales_amount] ),
        PREVIOUSMONTH ( Dim_Date[date] )
    )
RETURN
    DIVIDE ( CurrentSales - PreviousMonthSales, PreviousMonthSales )