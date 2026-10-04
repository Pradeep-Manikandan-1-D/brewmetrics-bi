# BrewMetrics BI

A version-controlled Power BI solution for analyzing BrewMetrics Coffee Co.'s sales performance across cities, store formats, products, and time.

## 1. Project Overview

BrewMetrics Coffee Co. operates Flagship, Kiosk, and Drive-Thru stores across four cities. This Business Intelligence project uses Power BI to analyze sales performance and identify important patterns across time, cities, store formats, and products.

The project is developed as a version-controlled Power BI Project (`.pbip`) and maintained in GitHub to track the development of the semantic model, DAX measures, dashboard, and documentation.

## 2. Data Model

The solution follows a star-schema structure consisting of one fact table and three dimension tables.

### Fact Table

**Fact_Sales**

Contains the transactional sales data, including:

- Sale ID
- Date
- City
- Store Format
- Category
- Item
- Quantity
- Unit Price
- Sales Amount

### Dimension Tables

**Dim_Date**

Contains date-related information:

- Date
- Year
- Month
- Quarter
- Day

**Dim_City**

Contains the unique cities in the dataset.

**Dim_Product**

Contains product and category information.

### Relationships

The dimension tables are connected to the central `Fact_Sales` table through one-to-many relationships:

- `Dim_Date[date]` → `Fact_Sales[date]`
- `Dim_City[city]` → `Fact_Sales[city]`
- `Dim_Product[item]` → `Fact_Sales[item]`

This structure allows the dashboard to analyze sales across different dimensions while maintaining a clear semantic model.

## 3. DAX Measures

The project includes the following DAX measures:

### MoM Sales Growth %

Calculates month-over-month sales growth by comparing current sales with the previous month's sales.

### Running Total Sales

Calculates cumulative sales over time.

### Product Sales Rank

Uses `RANKX` to rank products based on total sales, with the highest-selling product receiving rank 1.

### Average Order Value

Calculates the average sales value per transaction using total sales and total transactions.

The DAX measures were developed with GitHub Copilot assistance. Copilot suggestions were reviewed and documented in `NOTES.md`.

## 4. Dashboard

The BrewMetrics dashboard provides an interactive view of sales performance.

The dashboard includes:

- Total Sales KPI
- Running Total Sales KPI
- Average Order Value KPI
- Total Quantity KPI
- Cold Brew Sales Trend
- Sales Performance by City
- Sales Distribution by Category
- City slicer for interactive filtering
- City → Store Format → Category drill-down analysis

The dashboard is designed to highlight seasonal sales patterns and differences in performance across cities.

## 5. Key Insights

### 1. Cold Brew Seasonal Pattern

The Cold Brew sales trend shows a noticeable pattern across the analysis period. Monitoring this trend can help BrewMetrics plan inventory, promotions, and product availability during periods of higher demand.

### 2. City Performance Gap

Sales performance differs across the four cities. Bengaluru demonstrates stronger sales performance compared with the other cities, highlighting an opportunity to investigate the factors contributing to its performance.

### 3. Category Contribution

The category-level sales distribution shows that different product categories contribute differently to overall sales. This can help BrewMetrics identify stronger categories and areas requiring further attention.

## 6. Version Control

The Power BI solution is maintained as a `.pbip` project inside the GitHub repository.

The development history includes separate commits for:

- Initial project setup
- Star-schema development
- MoM Sales Growth measure
- Running Total Sales measure
- Product Sales Rank measure
- Dashboard and project documentation

The complete Git history is preserved to demonstrate the development process.

## 7. Project Files

| File / Folder | Description |
|---|---|
| `BrewMetrics_BI.pbip` | Power BI project |
| `BrewMetrics_BI.pbip.Report` | Power BI report definition |
| `BrewMetrics_BI.pbip.SemanticModel` | Power BI semantic model |
| `NOTES.md` | Copilot suggestions and corrections |
| `REFLECTION.md` | Reflection on Copilot and version-controlled development |

## 8. Tools Used

- Power BI Desktop
- Power BI Project (`.pbip`)
- Power Query
- DAX
- GitHub
- GitHub Desktop
- Visual Studio Code
- GitHub Copilot

