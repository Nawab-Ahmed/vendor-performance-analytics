# Annual Vendor Performance & Profitability Analysis (2024–2025)

This project is an end-to-end, portfolio-grade analytics case study focused on evaluating **vendor profitability, pricing efficiency, and inventory performance** for a retail / wholesale business.  
The objective is to move beyond reporting and deliver **clear, finance-driven insights and actionable recommendations** for management.

## Business Objectives
This analysis answers four executive-level questions:
- Which vendors drive profit at scale?
- Where is margin being destroyed and why (pricing power vs pricing leakage)?
- How efficiently is inventory converting into sales (working capital usage)?
- What actions should management take (renegotiate, scale, maintain, or exit)?

## Data Sources
Raw datasets (cleaned and processed using Python):
- `sales.csv` (large dataset processed via chunking)
- `purchases.csv`
- `purchase_prices.csv`
- `begin_inventory.csv`
- `end_inventory.csv`
- `vendor_invoice.csv`
Final modeled dataset:
- `vendor_performance.csv` (vendor–year grain)
All analysis is performed at **year level (2024–2025)** with no monthly granularity.

## Feature Engineering (Vendor–Year Level)
The final dataset includes the following engineered features:
- PurchaseQty  
- SalesQty  
- PurchaseDollars  
- SalesDollars  
- AvgPurchasePrice  
- AvgSalesPrice  
- PriceGap = AvgSalesPrice − AvgPurchasePrice  
- Profit = SalesDollars − PurchaseDollars  
- MarginPct = Profit / SalesDollars  
- AvgInventory  
- InventoryTurnover = SalesQty / AvgInventory  
### Vendor Segmentation
Vendors are segmented into four business-relevant categories:
- High Profit • High Volume  
- High Profit • Low Volume  
- Low Profit • High Volume  
- Low Profit • Low Volume  
Additional operational flags:
- IsDeadStock  
- IsFastMover  
- IsSlowMover  
## Dashboard Overview (Power BI)
The Power BI dashboard is structured into four pages for executive storytelling.
### Page 1 — Executive Overview (What is happening?)
- Total Sales, Total Purchases, Gross Profit, Vendor Count, Overall Margin %
- Top 10 vendors by total profit (profit concentration risk)
- Vendor segmentation scatter (Sales vs Profit)
**Key takeaway:**  
Profit is highly concentrated among a small group of vendors, exposing dependency risk.
### Page 2 — Pricing & Margin Drivers (Why is it happening?)
- Price Gap analysis (pricing power vs pricing leakage)
- Margin vs Volume scatter using a cleaned margin measure for stability
**Key takeaway:**  
Margin erosion is concentrated among a small number of vendors, indicating the need for **targeted repricing**, not broad cost-cutting.
### Page 3 — Inventory & Operations Efficiency (How efficiently is capital used?)
- Inventory turnover distribution with threshold at turnover = 1
- Fastest-moving vs slowest-moving vendors
- Dead / slow stock risk table with operational actions
**Key takeaway:**  
A large portion of inventory does not complete a full turnover cycle, indicating **working capital inefficiency**.
### Page 4 — Strategic Actions & Recommendations (What should management do?)
- Strategic Action Matrix filtered to vendors requiring intervention
- Vendors prioritized by **financial impact**
- Rule-based strategic recommendations by vendor segment
**Key takeaway:**  
Profitability and inefficiency are highly concentrated, enabling **focused and surgical management actions**.
## Key Insights (Executive Summary)
- Profit is driven by a small subset of vendors, increasing dependency risk.
- Pricing leakage is localized, not systemic.
- Inventory inefficiency is widespread among slow- and no-movement vendors.
- Clear vendor-level actions can improve profitability and working capital efficiency.
## Methodology
### Data Engineering (Python)
- Chunked ingestion for large datasets
- Data cleaning, joins, and aggregation to vendor–year level
- Feature engineering and validation checks
### Business Intelligence (Power BI)
- Executive-focused dashboard design
- Stable metric handling (cleaned margins, capped display values)
- Action-oriented storytelling
## Assumptions & Limitations
- Analysis is performed at **annual level only** (no monthly trends).
- Gross Margin % is **left blank** for vendors with no sales during the period, as margin is not defined in such cases.
- Extremely high inventory turnover values can occur when average inventory is very low (edge-case behavior).
- Displayed margin values are capped at ±100% for executive readability while preserving raw values in the model.
## Files & Structure
- `powerbi/` — Power BI dashboard (`.pbix`)
- `data/` — Final modeled dataset and data dictionary
- `notebooks/` — Python notebooks for data processing and feature engineering
- `screenshots/` — Dashboard screenshots
- `docs/` — Methodology, assumptions, and documentation
## Tools Used
- Python (pandas, numpy)
- Power BI (DAX, data modeling, dashboarding)
- CSV / Excel data sources
## Author
**Nawab Ahmed**  
Data Analyst  

