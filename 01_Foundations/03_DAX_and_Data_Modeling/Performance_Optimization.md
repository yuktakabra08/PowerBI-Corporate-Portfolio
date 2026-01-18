# Performance Optimization – Power BI Data Model

This document outlines key performance optimization practices applied in the Retail Sales Power BI model.

---

## Data Model Optimization

Star Schema
FactSales at transaction grain
Conformed dimensions (Date, Product, Customer, Region)
Single-direction relationships (Dimension → Fact)
No many-to-many or bi-directional filters

Purpose
Ensures fast filter propagation
Reduces ambiguity
Improves DAX evaluation speed

---

## DAX Optimization

Use Measures Instead of Calculated Columns
Reduces memory footprint
Improves query-time performance

Avoid Iterators Where Possible
Prefer SUM over SUMX
Prefer COUNT over COUNTX

Use Variables
Reduces repeated calculations
Improves readability and performance

Example
DAX:
Sales YTD =
VAR CurrentYear = YEAR ( MAX ( DimDate[Date] ) )
RETURN
CALCULATE ( [Total Sales], DATESYTD ( DimDate[Date] ) )

---

## Filter Context Control

Avoid Bi-Directional Relationships
Use TREATAS or USERELATIONSHIP only when required

Minimize ALL() Usage
Remove only required filters, not entire tables

---

## Visual Optimization

Limit number of visuals per page
Avoid high-cardinality fields in slicers
Prefer Top N filters instead of full lists
Disable unnecessary interactions

---

## Performance Analyzer Usage

Measured visual load time using Performance Analyzer
Identified slow visuals with heavy DAX or high cardinality
Optimized measures and reduced visual-level filters

---
