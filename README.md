# 🏥 Hospital Admissions Forecasting  
*Time Series Forecasting in Healthcare*

---

## 📘 Project Overview

This project presents a **time series forecasting case study in the healthcare domain**, focused on predicting **daily hospital admissions** to support efficient **resource planning and decision-making**.

Hospitals often face challenges related to **bed availability, staff scheduling, and medical supply management** due to fluctuating patient inflow. Using historical admission data, this study applies **classical time series models and machine learning techniques** to forecast future demand and evaluate their effectiveness.

This README summarizes the complete forecasting workflow and findings documented in the accompanying report :contentReference[oaicite:0]{index=0}.

---

## 🎯 Objectives

- Analyze historical hospital admission data as a time series  
- Identify **trend**, **seasonality**, and **short-term dependencies**  
- Apply multiple forecasting models for comparison  
- Evaluate models using standard error metrics  
- Recommend the most effective approach for healthcare planning  

---

## 🗂️ Dataset Description

- **Source**: Hospital Admissions Dataset  
- **Time Period**: 2017 – 2020  
- **Records**: 1,064 daily observations  
- **Target Variable**: Daily number of patient admissions  
- **Key Columns**:
  - Date of Admission (D.O.A)
  - Admissions count  

### 🔧 Exogenous Features (Engineered)
- Temperature (synthetic seasonal proxy)  
- Rainfall (synthetic monsoon proxy)  
- Holiday indicator (weekend flag)  

---

## 🔍 Exploratory Data Analysis (EDA)

The following analyses were performed:

- **Admissions over time** to observe variability and spikes  
- **Distribution analysis** revealing right-skewed admissions  
- **Boxplot analysis** highlighting extreme outliers  
- **Monthly average trend** indicating seasonal effects  
- **ACF & PACF plots** identifying strong weekly seasonality  
- **Lag analysis** confirming dependence on previous-day admissions  

---

## ⚙️ Data Preprocessing

- Converted admission dates to a continuous daily time series  
- Filled missing dates with zero admissions  
- Created lag-based features (lag_1 to lag_7)  
- Added calendar features (day of week, month)  
- Integrated synthetic exogenous variables  

---

## 🤖 Forecasting Models Implemented

### 📌 Baseline and Statistical Models
- **Moving Average (MA)** – Simple baseline  
- **Holt-Winters Exponential Smoothing** – Trend and seasonality  
- **ARIMA (1,1,1)** – Trend modeling  
- **SARIMA (1,1,1)(1,1,1,7)** – Weekly seasonality  
- **SARIMAX** – Seasonal ARIMA with exogenous variables  

### 📌 Machine Learning Model
- **Random Forest Regressor**  
  - Uses lag features and exogenous variables  
  - Captures nonlinear and irregular admission patterns  

---

## 📏 Evaluation Metrics

Models were evaluated using:

- **MAE (Mean Absolute Error)**  
- **RMSE (Root Mean Square Error)**  
- **MAPE (Mean Absolute Percentage Error)**  

These metrics assess both absolute and relative forecasting accuracy.

---

## 📊 Model Performance Summary

| Model           | MAE  | RMSE | Performance |
|-----------------|------|------|-------------|
| Moving Average  | 13.16 | 13.33 | Weak baseline |
| Holt-Winters    | 15.05 | 15.37 | Over-smoothed |
| ARIMA           | 12.37 | 12.52 | Misses spikes |
| SARIMA          | 14.00 | 14.25 | Seasonal but lagging |
| SARIMAX         | 92.09 | 108.59 | Poor exogenous fit |
| **Random Forest** | **6.78** | **7.60** | **Best overall** |

---

## 🔮 Key Insights

- Strong **weekly seasonality** (7-day cycle)  
- Increased admissions during **monsoon months**  
- **Lag-1 admissions** is the most influential predictor  
- Weather variables (rainfall, temperature) significantly affect demand  
- Random Forest adapts best to **nonlinear spikes and irregular patterns**  

---

## 🧠 Feature Importance (Random Forest)

- **lag_1** — ~63% importance  
- Rainfall — ~8%  
- Temperature — ~6%  
- Remaining lag features — moderate influence  

**Interpretation**: Yesterday’s admissions and weather conditions are the strongest predictors of next-day demand.

---

## 🏥 Managerial Implications

Forecasting insights can support:

- **Bed management** during high-admission periods  
- **Staff scheduling** to handle workload surges  
- **Medical supply planning** based on demand trends  
- **Emergency preparedness** for outbreaks or epidemics  
- **Cost optimization** by avoiding overstaffing  

---

## 🏁 Conclusion

The forecasting framework demonstrates that while classical time series models capture general trends and seasonality, the **Random Forest Regressor** delivers the highest predictive accuracy due to its ability to learn nonlinear relationships.

With real-world exogenous inputs (weather APIs, official holiday calendars, outbreak indicators), forecasting performance can be further improved, making the system suitable for **practical hospital decision support**.

---

## 🔮 Future Enhancements

- Department-level forecasting (Emergency, Pediatrics, Cardiology)  
- Time-series cross-validation  
- Integration of real weather and holiday datasets  
- Forecast confidence intervals  
- Deployment of an interactive decision-support dashboard  

---

## 📜 License

This project is intended for **academic and educational purposes**.  
Reuse is permitted with appropriate attribution.

---
