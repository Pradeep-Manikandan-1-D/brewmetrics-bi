# BrewMetrics Coffee Co. Power BI Notes

## Summary

This chat covered four DAX measures for the BrewMetrics semantic model. The examples use the existing `[Total Sales]` and `[Total Transactions]` measures where appropriate, plus the `Fact_Sales` and `Dim_Date`/`Dim_Product` columns.

## Average Order Value

```DAX
Average Order Value =
DIVIDE ( [Total Sales], [Total Transactions] )
```

Calculates average sales value per transaction in the current filter context. `DIVIDE` returns blank when there are no transactions, avoiding a divide-by-zero error.

## MoM Sales Growth %

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
```

Compares sales in the current date context with sales in the previous month, then divides the difference by previous-month sales. Format the measure as a percentage. Include Year with Month in visuals so the same month from different years is not combined.

## Running Total Sales

```DAX
Running Total Sales =
CALCULATE (
    [Total Sales],
    FILTER (
        ALL ( Dim_Date[date] ),
        Dim_Date[date] <= MAX ( Dim_Date[date] )
    )
)
```

Calculates cumulative sales through each date on the visual's time axis. It clears the current date filter to include earlier dates while retaining other filters, such as city or product.

## Product Sales Rank

```DAX
Product Sales Rank =
RANKX (
    ALL ( Dim_Product[item] ),
    [Total Sales],
    ,
    DESC,
    DENSE
)
```

Ranks items by `[Total Sales]` in descending order, giving the highest-selling item rank 1. Ties share a rank, and `DENSE` leaves no gaps after tied ranks.

## Date Table Note

For reliable time-intelligence results such as `PREVIOUSMONTH`, `Dim_Date` should contain a continuous range of dates and be configured as the model's date table. The current model's `Dim_Date` is generated from distinct dates found in `Fact_Sales`, so verify its date coverage before relying on month-over-month results.

