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


    ## Running Total Sales

- Copilot suggestion:

```DAX
Running Total Sales =
CALCULATE (
    [Total Sales],
    FILTER (
        ALL ( Dim_Date[date] ),
        Dim_Date[date] <= MAX ( Dim_Date[date] )
    )
)

## Product Sales Rank

- Copilot suggestion:

```DAX
Product Sales Rank =
RANKX (
    ALL ( Dim_Product[item] ),
    [Total Sales],
    ,
    DESC,
    DENSE
)

# BrewMetrics BI

A version-controlled Power BI solution for analyzing BrewMetrics Coffee Co.'s sales performance across cities, store formats, products, and time.

## Project Overview

This project analyzes BrewMetrics Coffee Co. sales data using Power BI. The solution uses a star schema with a central Fact_Sales table and supporting date, city, and product dimension tables.

## Data Model

The Power BI semantic model contains:

- **Fact_Sales** — sales transactions, quantity, unit price, and sales amount
- **Dim_Date** — date, year, month, quarter, and day information
- **Dim_City** — city information
- **Dim_Product** — product and category information

The model uses one-to-many relationships from the dimension tables to Fact_Sales.

## DAX Measures

The project includes:

- MoM Sales Growth %
- Running Total Sales
- Product Sales Rank
- Average Order Value

These measures were developed with GitHub Copilot assistance and documented in `NOTES.md`.

## Dashboard

The dashboard provides:

- Cold Brew sales trend over time
- Sales performance comparison across cities
- Sales distribution by category
- KPI cards for sales and order metrics
- City filtering through a slicer
- City → Store Format → Category drill-down analysis

## Key Insights

1. **Cold Brew sales show a noticeable seasonal pattern across the analysis period**, making time-based monitoring useful for planning inventory and promotions.

2. **Bengaluru is the strongest-performing city**, while the other cities show a performance gap that can be investigated further using the drill-down analysis.

3. **Product categories contribute differently to overall sales**, allowing BrewMetrics to identify stronger and weaker category-level performance.

## Version Control

The Power BI project is maintained as a `.pbip` project in GitHub. Development was completed through separate commits for schema development and DAX measures, preserving the project history.

## Files

- `BrewMetrics_BI.pbip` — Power BI project
- `NOTES.md` — Copilot suggestions and corrections
- `REFLECTION.md` — project reflection