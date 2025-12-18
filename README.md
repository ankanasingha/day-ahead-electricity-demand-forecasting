# Day-Ahead Electricity Load Forecasting

## Project Overview

Accurate short-term electricity load forecasting is essential for power system reliability, energy trading, and operational planning. This project focuses on **day-ahead (24-hour) electricity load forecasting** using **hourly demand data** from the PJM interconnection, sourced via the U.S. Energy Information Administration (EIA) API.

The project compares a **traditional statistical time-series model (SARIMA)** with a **modern machine learning approach (XGBoost)** to evaluate forecasting accuracy, robustness, and computational efficiency under realistic operational constraints.

---

## Objectives

- Build a **reproducible pipeline** for hourly electricity load forecasting  
- Analyze **daily, weekly, and seasonal demand patterns**  
- Compare **statistical vs. machine learning models**  
- Evaluate models using **MAE, RMSE, and runtime performance**  
- Provide insights relevant to **energy trading and system operations**

---

## Data Description

- **Source:** U.S. Energy Information Administration (EIA) API  
- **Region:** PJM Interconnection  
- **Frequency:** Hourly  
- **Time Span:** January 2024 – December 2024  
- **Target Variable:** System load (MW)

### Data Processing Steps
- Conversion of string-based load values to numeric format  
- Aggregation of duplicate timestamps using mean values  
- Enforcement of strict hourly frequency  
- Time-based interpolation for missing observations  
- Validation of seasonality and demand consistency  

---

## Exploratory Data Analysis

Key patterns identified:
- Strong **intra-day seasonality** (morning ramp-up, evening peaks)
- Clear **weekday vs. weekend differences**
- Weekly seasonality justifying a **168-hour cycle**
- Approximately **2% extreme values**, retained as genuine demand events

---

## Modeling Approaches

### 1. SARIMA (Statistical Baseline)
- Captures linear trends and seasonal patterns
- Weekly seasonality explicitly modeled
- Serves as an interpretable benchmark

### 2. XGBoost (Machine Learning)
- Uses lagged load values (1, 24, 168 hours)
- Rolling statistics for short- and long-term smoothing
- Calendar features (hour of day, day of week)
- Captures nonlinear demand dynamics efficiently

---

## Evaluation Metrics

Models are evaluated on a **24-hour day-ahead forecast horizon** using:

- **MAE (Mean Absolute Error)**
- **RMSE (Root Mean Squared Error)**
- **Runtime (seconds)**

| Model   | MAE (MW) | RMSE (MW) | Runtime (s) |
|--------|----------|-----------|-------------|
| XGBoost | ~566 | ~686 | ~1.3 |
| SARIMA  | ~1927 | ~2140 | ~3413 |

---

## Key Findings

- XGBoost significantly outperforms SARIMA in both **accuracy and speed**
- Machine learning models are better suited for **large-scale, high-frequency load data**
- SARIMA remains useful as a **transparent statistical baseline**
- Extreme demand events should be retained for realistic operational forecasting

---

## Technologies Used

- Python  
- Pandas, NumPy  
- Matplotlib  
- Statsmodels (SARIMAX)  
- XGBoost  
- Scikit-learn  
- EIA Open Data API  

---


