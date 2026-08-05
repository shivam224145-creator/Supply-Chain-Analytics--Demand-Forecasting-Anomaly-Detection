# Supply-Chain-Analytics--Demand-Forecasting-Anomaly-Detection
# DAY 1
Searching and Selecting the right dataset for Project.

In day 1 we are seaching and selecting the right dataset for the project in which all required things are present, to achieve project Goal.  finally we find a right and useful dataset for Project on kaggle - https://www.kaggle.com/datasets/ziya07/high-dimensional-supply-chain-inventory-dataset 

---

# Day 2 - Data Understanding Summary

## Dataset Overview

- Dataset contains **91,250 records** and **15 columns**.
- The dataset represents daily supply chain transactions across multiple products, warehouses, suppliers, and regions.
- Data covers **365 days (2024-01-01 to 2024-12-30)**.

## Key Findings

- No missing values were observed during the initial inspection.
- Dataset includes **50 SKUs**, **5 Warehouses**, **10 Suppliers**, and **4 Regions**.
- Inventory levels, unit cost, and unit price appear realistic.
- Order_Quantity is zero for most records, indicating orders are placed only when inventory reaches the reorder threshold.
- Promotion_Flag is a binary feature with approximately 10% promotional records.
- Stockout_Flag contains only zero values and will be evaluated further during feature engineering.
- The Date column is currently stored as a string and will be converted to datetime during data cleaning.

## Conclusion

The dataset is well-structured, lightweight, and suitable for demand forecasting, anomaly detection, inventory analysis, Power BI dashboard development, and Streamlit deployment.

---
