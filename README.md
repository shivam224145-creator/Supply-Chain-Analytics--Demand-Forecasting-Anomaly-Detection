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

# Day 3 - Data Cleaning

## Objective
Performed comprehensive data cleaning and validation to prepare the dataset for Exploratory Data Analysis (EDA), Demand Forecasting, and Anomaly Detection.

## Tasks Completed

- Imported required Python libraries.
- Loaded the raw supply chain dataset.
- Performed basic dataset validation (rows, columns, data types).
- Checked for missing values.
- Checked and validated duplicate records.
- Converted the `Date` column from string to datetime format.
- Validated all numerical columns for negative values.
- Verified binary columns (`Promotion_Flag` and `Stockout_Flag`).
- Performed initial outlier screening using the IQR method.
- Applied business rule validation (cost, price, inventory consistency).
- Verified final dataset integrity after cleaning.
- Saved the cleaned dataset for future analysis.

## Cleaning Summary

| Validation | Result |
|------------|--------|
| Missing Values | 0 |
| Duplicate Rows | 0 |
| Negative Values | 0 |
| Invalid Business Rules | 0 |
| Date Conversion | Completed |
| Outlier Screening | Completed |
| Final Dataset Shape | (91,250, 15) |

## Output

- Cleaned dataset saved successfully:
  - `data/processed/supply_chain_cleaned.csv`

## Status

**Data Cleaning Completed Successfully**

The dataset is now validated, consistent, and ready for Exploratory Data Analysis (EDA), Feature Engineering, Demand Forecasting, and Anomaly Detection.

---

