# Retail Sales – Core DAX Measures (Day 4)

This file documents the core business measures created in Power BI.
These measures form the foundation for all analysis, KPIs, and dashboards.

---

## 1. Total Sales

DAX:

Total Sales = SUM ( FactSales[Sales Amount] )

Business Meaning:
Total number of units sold.

## 2. Total Quantity

DAX:

Total Quantity = SUM ( FactSales[OrderQuantity] )


Business Meaning:
Total number of units sold.

## 3. Total Orders

DAX:

Total Orders = DISTINCTCOUNT ( FactSales[SalesOrderNumber] )


Business Meaning:
Number of unique customer orders.

## 4. Average Order Value (AOV)

DAX:

Avg Order Value =
DIVIDE ( [Total Sales], [Total Orders] )


Business Meaning:
Average revenue generated per order.

## 5. Sales % of Total

DAX:

Sales % of Total =
DIVIDE(
    [Total Sales],
    CALCULATE( [Total Sales], ALL ( DimProduct ) )
)


Business Meaning:
Percentage contribution of each product (or region, customer, etc.)
to the overall company revenue.

Technical Note:
ALL(DimProduct) removes the product filter so the denominator
always represents the grand total, while the numerator changes
per row context.


Commit message:

