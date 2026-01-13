## Relationship Design Logic

DimDate[Date] → FactSales[OrderDate]  
DimProduct[ProductKey] → FactSales[ProductKey]  
DimCustomer[CustomerKey] → FactSales[CustomerKey]  
DimRegion[Region] → DimCustomer[Region]  

### Cardinality
All relationships are One-to-Many from Dimension to Fact.

### Filter Direction
Single direction from Dimension to Fact to:
- Avoid ambiguity
- Prevent double counting
- Maintain DAX correctness

### Grain Alignment
- FactSales: Transaction grain
- Dimensions: Master data grain

This structure guarantees:
- Stable Time Intelligence
- Correct target alignment
- RLS compatibility
- Performance optimization
