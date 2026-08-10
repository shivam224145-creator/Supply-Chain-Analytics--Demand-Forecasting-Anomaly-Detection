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

# Day 4 - Exploratory Data Analysis (EDA)

## Objective

Performed comprehensive Exploratory Data Analysis (EDA) on the cleaned supply chain dataset to understand demand patterns, inventory behavior, regional performance, supplier lead time, promotional impact, feature relationships, and data distribution. The insights generated during this phase will support Demand Forecasting and Anomaly Detection in the upcoming stages.

## Tasks Completed

- Imported required Python libraries.
- Loaded the cleaned supply chain dataset.
- Verified dataset structure and data types.
- Converted the `Date` column to datetime format.
- Analyzed daily demand trends using a time-series line chart.
- Explored average daily inventory levels over time.
- Performed region-wise demand analysis.
- Evaluated the impact of promotional campaigns on sales.
- Analyzed supplier lead time versus average units sold.
- Compared Actual Units Sold with Demand Forecast.
- Generated a Correlation Heatmap for numerical features.
- Visualized the distribution of Units Sold using a histogram.
- Examined potential outliers using a boxplot.
- Interpreted business insights from every visualization.

## Key Business Insights

- Daily demand remained relatively stable with normal fluctuations.
- Inventory levels followed a consistent trend throughout the year.
- Regional demand showed slight variations across all four regions.
- Promotional activities resulted in higher average units sold.
- Supplier lead time had minimal impact on average sales.
- Actual demand closely followed the generated demand forecast.
- Strong correlations were observed between selected inventory and demand-related variables.
- The distribution of Units Sold appeared close to normal with a few high-demand observations.
- Boxplot confirmed the presence of valid business outliers suitable for anomaly detection rather than removal.

## Visualizations Created

- Daily Demand Trend
- Inventory Trend
- Region-wise Sales Analysis
- Promotion Impact Analysis
- Supplier Lead Time Analysis
- Actual vs Forecast Demand
- Correlation Heatmap
- Units Sold Distribution (Histogram)
- Units Sold Boxplot

## Outcome

EDA successfully identified important demand patterns, inventory behavior, feature relationships, promotional effects, and potential anomalies. These insights establish a strong foundation for Feature Engineering, Time Series Forecasting, and Machine Learning-based Anomaly Detection.

## Status

**Exploratory Data Analysis (EDA) Completed Successfully**

---

# Day 5 - Feature Engineering & Time-Series Preparation

### 1. Date-Based Features
- Extracted Year, Month, Week, Day, Day_of_Week and Day_of_Year from Date.
- Created Is_Weekend indicator for weekend-based demand analysis.

### 2. Demand Lag Features
- Created Demand_Lag_1, Demand_Lag_7, Demand_Lag_14 and Demand_Lag_30.
- Generated lag features separately for each SKU-Warehouse combination to preserve time-series structure.

### 3. Rolling Demand Features
- Created 7-day, 14-day and 30-day rolling demand averages.
- Used previous observations with shift(1) to avoid data leakage.

### 4. Supply Chain Derived Features
- Created Inventory_Demand_Ratio to measure inventory coverage against recent demand.
- Created Inventory_Gap to measure inventory position relative to reorder point.
- Created Forecast_Error and Absolute_Forecast_Error to evaluate demand forecast performance.

### 5. Missing Value Handling
- Identified expected NaN values generated by lag and rolling features.
- Removed incomplete initial historical records instead of artificially filling them with zero.
- Removed 7,500 incomplete records.

### 6. Final Validation
- Final Dataset Shape: 83,750 rows × 33 columns
- Missing Values: 0
- Infinite Values: 0
- Duplicate Rows: 0
- Date Range: 2024-01-31 to 2024-12-30

### 7. Final Output
- Saved the feature-engineered dataset to:
  `data/processed/supply_chain_feature_engineered.csv`

### Project Progress
Raw Data → Data Understanding → Data Cleaning → EDA → Feature Engineering → Anomaly Detection

---

# Day 6 - Anomaly Detection Analysis

Today, the project focused on identifying and analyzing unusual supply-chain observations using statistical anomaly detection techniques.

### Work Completed

- Selected key anomaly detection variables:
  - Units_Sold
  - Inventory_Level
  - Demand_Forecast
  - Forecast_Error
- Applied **IQR-based anomaly detection** and created anomaly flags.
- Applied **Z-Score-based anomaly detection** using a threshold of 3.
- Compared IQR and Z-Score results to validate anomaly patterns.
- Created a **Combined Anomaly Score** using both detection methods.
- Identified **396 confirmed anomalies** from 83,750 feature-engineered observations.
- Created a separate confirmed anomaly dataset for investigation.
- Performed anomaly analysis by:
  - SKU
  - Warehouse
  - Region
  - Date
  - Anomaly severity
  - Detection driver
- Created visualizations for anomaly trends, severity, and major anomaly drivers.
- Added business interpretation to identify operational areas requiring further investigation.

### Key Findings

- Total Confirmed Anomalies: **396**
- Normal Observations: **83,354**
- Highest SKU anomaly count: **SKU_29 – 17**
- Highest Warehouse anomaly count: **WH_2 – 92**
- Highest Region anomaly count: **North – 104**
- Highest anomaly date: **2024-03-25 – 7 anomalies**
- Major anomaly driver: **Forecast Error – 229 signals**
- Highest combined anomaly score observed: **5**

### Output

Confirmed anomalies were prepared as a separate dataset for downstream investigation and supply-chain decision support.

---

