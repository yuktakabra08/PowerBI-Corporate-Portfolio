# Data Model – Retail Sales (Star Schema)

This folder contains the enterprise-grade data model built in Power BI following Kimball Star Schema principles.

## Objective
Design a clean analytical model to support:
- Time Intelligence (MTD, QTD, YTD, YoY)
- Target vs Actual
- Region, Product, Customer slicing
- High performance DAX

## Tables

### Fact Table
**FactSales**
- Grain: One row per sales transaction
- Keys:
  - DateKey
  - ProductKey
  - CustomerKey
- Measures:
  - Sales Amount
  - Quantity
  - Cost

### Dimension Tables

**DimDate**
- One row per calendar date
- Attributes: Year, Quarter, Month, MonthNumber, Day, Weekday
- Marked as official Date Table for Time Intelligence

**DimProduct**
- One row per product
- Attributes: Category, Subcategory, Brand, Size, Color

**DimCustomer**
- One row per customer
- Attributes: Gender, City, State, Country, Region

**DimRegion**
- One row per region
- Hierarchy: Country → Region

## Relationships

All relationships follow:
- One-to-Many (Dimension → Fact)
- Single direction filter flow
- No many-to-many
- No bi-directional filters

## Why Star Schema

This design ensures:
- Correct filter propagation
- Accurate aggregations
- Reliable Time Intelligence
- Scalable performance
- Interview-ready modeling architecture

## Business Use Cases Supported

- Sales trend analysis
- Regional performance
- Product profitability
- Customer segmentation
- Executive KPI dashboards
