
# Price-Volume-Mix (PVM) Revenue & Profit Analysis

**Interactive Power BI dashboard for revenue and profit variance decomposition in a manufacturing and distribution company.**

🔗 **[View Live Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMzQ0MmMyZWUtMWE3Yi00Njg0LWFjYWQtNTc5NDdjODM4MTgyIiwidCI6ImI5ZWY1NjYzLWM3MjktNDg1Mi1hMGI1LTQ5YmQ2M2M1OWJjOSIsImMiOjR9)**

---

## Business Problem

In manufacturing and distribution companies, revenue can change between periods for very different reasons: selling more units, changing prices, shifting the product mix, gaining new customers, or losing existing ones. Without decomposing these effects, management cannot identify where to act.

This dashboard answers the key question: **Why did revenue (and profit) change between two selected periods — and exactly how much did each factor contribute?**

---

## What the Dashboard Does

The model decomposes the variance between any two selected periods into five distinct effects:

| Effect | What it measures |
|---|---|
| **Volume** | Impact of selling more or fewer units at base-period prices |
| **Price** | Impact of price changes on the same product mix |
| **Mix** | Impact of shifting sales toward higher or lower margin products |
| **Lost Products** | Revenue lost from products sold in the base period but not in the current period |
| **New Products** | Revenue gained from products not present in the base period |

---

## Dashboard Pages

### Page 1 — PVM Revenue
- Revenue waterfall: Base Period → Volume → Price → Mix → Lost → New → Current Period
- PVM decomposition by product type (bar charts)
- KPI cards: Revenue, Units, Avg Price, and total Variation vs base period
- Dynamic filters: Actual Period, Base Period, Product Line, Customer

### Page 2 — PVM Profit
- Same structure applied to gross profit
- Enables margin analysis alongside revenue analysis

---

## Data Model

```
FactSales ──── DimProducts (ProductId → Type, Serie, Source)
    │
    └────────── DimCustomers (CustomerId → Territory, Customer Type)
    │
    └────────── Dim_CY_Dates / Dim_PY_Dates (flexible period selection)

Bridge_PVM_Revenue / Bridge_PVM_Profit (effect sorting and labeling)
```

**Data source:** Originally extracted from SAP Business One (SAP B1) — the ERP system used for sales and inventory management in the source company. Data was exported, transformed in Power Query, and loaded into the Power BI model. Customer names and IDs have been anonymized for this public version.

**Industry context:** Industrial distribution — casters, wheels, tires, rigs, and material handling accessories.

---

## Key DAX Patterns Used

- Dynamic period selection via disconnected date tables (CY/PY)
- PVM decomposition using CALCULATE + FILTER combinations
- Waterfall chart ordering via bridge table with Sort column
- Conditional formatting for positive/negative variance

---

## Tools & Skills Demonstrated

- **Power BI Desktop** — data model design, DAX measures, report layout
- **Power Query (M)** — data transformation from SAP B1 export
- **DAX** — advanced measures for PVM decomposition logic
- **SAP B1** — source ERP system for transactional data extraction
- **Business acumen** — FP&A framework applied to manufacturing and distribution context

---

## Why PVM Matters in Manufacturing

Standard revenue reports tell you *what* happened. PVM tells you *why*. In industrial distribution, this distinction is critical:

- A volume drop masked by a price increase looks like flat revenue — PVM exposes both
- Lost products (SKU churn) are invisible in aggregate reports — PVM surfaces them explicitly
- Mix shifts between high and low margin product lines directly impact profitability — PVM quantifies this

This dashboard was built to support management decisions at the GM and commercial director level, not just for reporting purposes.

---

*Built by Juan José García M. | [LinkedIn](https://www.linkedin.com/in/jjgarciam0610) | juan.j.garcia@outlook.com*
