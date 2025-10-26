# Energy-Consumption-Time Series Forecasting

# ⚡️ PJME Interconnection Energy Demand Forecasting

## 📘 Project Overview

This repository contains a **production-ready solution** for forecasting **hourly electricity demand** for the **PJME (Pennsylvania, Jersey, Maryland, Electric)** interconnection region.

Accurate short-term forecasting is critical for energy utilities to manage **grid stability**, **schedule power generation**, and **optimize procurement costs**.  
This project demonstrates a **systematic and data-driven approach** to time series forecasting, leveraging advanced **feature engineering**, **multiple modeling paradigms**, and **state-of-the-art hyperparameter optimization**.

The complete analysis is available in the notebook:  
📄 `PMJE_Energy_Consumption.ipynb`

---

## 🛠️ Technology & Libraries

This project leverages modern data science tools for **time series analysis** and **forecasting**.

| **Category** | **Key Libraries** | **Purpose** |
|---------------|-------------------|--------------|
| **Forecasting** | `xgboost`, `Prophet`, `statsmodels` | Primary modeling engines (Ensemble, Decomposable, Classical). |
| **Optimization** | `Optuna` | Systematic and efficient hyperparameter tuning for the XGBoost model. |
| **Data Handling** | `pandas`, `numpy`, `USFederalHolidayCalendar` | Data manipulation and complex feature extraction. |
| **Metrics** | `sklearn.metrics` | Validation using MAE, RMSE, and MAPE. |

---

## 📈 Methodology Highlights

The core of this solution lies in its **rigorous methodology**, going beyond traditional time-based models.

### 1. Advanced Feature Engineering

A comprehensive set of **time series** and **exogenous features** was engineered to capture known consumption patterns:

- **Temporal Features:** Year, quarter, month, dayofyear, dayofweek, and hour.  
- **Calendar Effects:** Integration of `USFederalHolidayCalendar` to create binary holiday flags.  
- **Time Series Lags:** Lagged features such as `lag_1h`, `lag_1day`, `lag_1week` to capture short and long temporal dependencies.  
- **Trend Smoothing:** Rolling means (7-day, 30-day, 200-day) for noise reduction and trend estimation.  

---

### 2. Multi-Model Approach

Three distinct forecasting methods were compared before finalizing the **ensemble model**:

| **Model** | **Type** | **Description** |
|------------|-----------|-----------------|
| **SARIMAX** | Classical | Baseline capturing linear autocorrelation. |
| **Prophet** | Decomposable | Models trend, seasonality, and holidays efficiently. |
| **XGBoost** | Ensemble Tree | Captures non-linear interactions between engineered features. |

---

### 3. Systematic Hyperparameter Optimization (Optuna)

The final **XGBoost** model was tuned using **Optuna**, optimizing the **Mean Absolute Percentage Error (MAPE)** through intelligent search — outperforming grid search in efficiency and accuracy.

---

## 📊 Results & Validation

Model performance was rigorously validated using **Time Series Cross-Validation**.

| **Metric** | **Result** |
|-------------|-------------|
| **MAPE** | [Insert Final MAPE Score] % |
| **RMSE** | [Insert Final RMSE Score] |
| **MAE** | [Insert Final MAE Score] |

### 🔍 Key Findings

- **Lag features** (`1-day` and `1-week`) and **holiday flags** were the most influential predictors.  
- The **XGBoost model** significantly outperformed the classical and decomposable models, effectively capturing **non-linear relationships** between temperature, time of day, and demand.  

---

## 🚀 How to Run the Notebook

### 1. Clone the Repository

```bash
git clone [your-repo-link]
cd pjme-energy-forecasting

pip install -r requirements.txt
If no requirements.txt is provided, install the main libraries manually:
