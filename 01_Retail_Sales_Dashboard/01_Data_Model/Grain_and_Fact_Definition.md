# Fact Table Grain – Retail Sales Model

This document defines the grain and structural rules of the FactSales table used in the Retail Sales Power BI data model.

---

## Fact Table

FactSales

---

## Grain Definition

One row represents **one sales transaction**
(One Product × One Invoice × One Date × One Customer × One Region)

---

## Keys

DateKey
ProductKey
CustomerKey
RegionKey
InvoiceNumber

---

## Measures (Additive at Transaction Grain)

Sales Amount
Quantity
Cost
Profit

---

## Why Grain Is Fixed at Transaction Level

Enables accurate MTD, QTD, YTD, YoY calculations
Supports drill-down from Year → Month → Day → Invoice
Prevents aggregation errors in Target vs Actual analysis
Ensures correct filter propagation from all Dimensions

---

## Grain Alignment Rules

FactSales: Transaction-level grain
DimDate: One row per calendar date
DimProduct: One row per product
DimCustomer: One row per customer
DimRegion: One row per region

All relationships follow **higher grain (Dimension) → lower grain (Fact)**.

---

## Grain Mismatch Handling (Target Example)

Sales: Transaction grain
Targets: Monthly-Region grain (separate FactTarget table)
Comparison is performed using shared dimensions (DimDate, DimRegion), not row-level joins.
