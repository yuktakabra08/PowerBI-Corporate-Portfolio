# ETL Documentation – Retail Sales Project

## Data Sources
- Sales Transactions (CSV)
- Product Master (AdventureWorks)

## Data Issues Identified
- Inconsistent size values (S, M, L, 0, null)
- Extra spaces and casing issues in text fields
- Missing product styles

## Cleaning Steps
1. Standardized data types
2. Applied Trim, Clean, Proper Case
3. Replaced invalid categories with 'Unknown'
4. Created Date Dimension
5. Validated keys and removed duplicates

## Final Output
- FactSales (transaction grain)
- DimProduct (clean master)
- DimDate (time intelligence ready)
