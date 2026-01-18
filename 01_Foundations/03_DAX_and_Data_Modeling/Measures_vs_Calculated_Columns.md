# Measures vs Calculated Columns – DAX Design

This document explains when to use Measures and when to use Calculated Columns in an enterprise Power BI model.

---

## Measures

Definition
Calculated at query time based on filter context.

Example
DAX:
Total Sales = SUM ( FactSales[Sales Amount] )

Characteristics
Evaluated dynamically with slicers, filters, and visuals
Do not increase model size
Use VertiPaq compression efficiently
Always respond to Date, Product, Region, Customer context

Business Usage
KPIs (Sales, Profit, Margin)
Time Intelligence (MTD, YTD, YoY)
Target vs Actual
Rankings, Percentages, Growth Metrics

---

## Calculated Columns

Definition
Computed at data refresh and stored row by row in the table.

Example
DAX:
YearMonth = FORMAT ( DimDate[Date], "YYYY-MM" )

Characteristics
Increase model size
Do not respond to slicer context
Used for row-level logic and categorization
Available for relationships, sorting, grouping

Business Usage
Surrogate Keys
Bucketization (Age Group, Price Band)
Sorting columns (Month Number)
Row-level flags (IsWeekend, IsHoliday)

---

## Performance & Modeling Rule

Use **Measures** for all aggregations and business KPIs.
Use **Calculated Columns** only when:

* The value is required for relationships
* The value is required for sorting
* The value is required for grouping
* The value is required for RLS logic

Never replace a Measure with a Calculated Column for totals, ratios, or time intelligence.

---
