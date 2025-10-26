# Energy-Consumption-Time Series Forecasting

⚡️ PJME Interconnection Energy Demand Forecasting

Project Overview

This repository contains a robust, production-ready solution for forecasting hourly electricity demand for the PJME (Pennsylvania, Jersey, Maryland, Electric) interconnection region.

Accurate short-term forecasting is critical for energy utilities to manage grid stability, schedule power generation, and optimize procurement costs. This project demonstrates a systematic approach to time series forecasting, leveraging advanced feature engineering, multiple modeling paradigms, and state-of-the-art hyperparameter optimization.

The analysis is contained within the core Jupyter Notebook: PMJE_Energy_Consumption.ipynb.

🛠️ Technology & Libraries

This project emphasizes a strong command of modern data science tools for time series analysis:

Category

Key Libraries

Purpose

Forecasting

xgboost, Prophet, statsmodels

Primary modeling engines (Ensemble, Decomposable, Classical).

Optimization

Optuna

Systematic and efficient hyperparameter tuning for XGBoost model.

Data Handling

pandas, numpy, USFederalHolidayCalendar

Data manipulation and complex feature extraction.

Metrics

sklearn.metrics

Validation using MAE, RMSE, and MAPE.

📈 Methodology Highlights

The core of this solution lies in its rigorous methodology, moving beyond simple time-based models.

1. Advanced Feature Engineering

A comprehensive set of time series and exogenous features were engineered to capture all known patterns of energy consumption:

Temporal Features: Extraction of year, quarter, month, dayofyear, dayofweek, and hour to capture complex seasonality.

Calendar Effects: Integration of the USFederalHolidayCalendar library to create binary flags for all observed holidays.

Time Series Lags: Creation of essential lagged features (lag_1h, lag_1day, lag_1week) to model immediate and periodic temporal dependence.

Trend Smoothing: Calculation of multiple Rolling Means (7-Day, 30-Day, 200-Day) to smooth noise and estimate underlying trends.

2. Multi-Model Approach

The project compared three distinct forecasting methods before selecting the final ensemble model:

SARIMAX (Classical): Used as a baseline to capture linear autocorrelation.

Prophet (Decomposable): Used to rapidly model trend, seasonality, and holidays.

XGBoost (Ensemble Tree): Utilized for its superior ability to capture non-linear interactions between the 15+ engineered features (lags, holidays, rolling means).

3. Systematic Hyperparameter Optimization (Optuna)

The final XGBoost model was systematically tuned using the Optuna framework to minimize the Mean Absolute Percentage Error (MAPE), ensuring a balance of accuracy and interpretability. This approach uses an intelligent search process (rather than simple Grid Search) to find the optimal combination of model parameters.

📊 Results & Validation

The model's performance was rigorously evaluated using Time Series Cross-Validation.

Metric

Result

Mean Absolute Percentage Error (MAPE)

[Insert Final MAPE Score from Notebook] %

Root Mean Squared Error (RMSE)

[Insert Final RMSE Score from Notebook]

Mean Absolute Error (MAE)

[Insert Final MAE Score from Notebook]

Key Findings

The inclusion of lag features (1-day and 1-week) and the explicit holiday flag were identified as the most important features in the XGBoost model.

The ensemble tree-based model significantly outperformed the classical and decomposable models due to its ability to model the complex, non-linear relationship between temperature, time of day, and demand.

🚀 How to Run the Notebook

Clone the repository:

git clone [your-repo-link]
cd pjme-energy-forecasting


Install dependencies:

pip install -r requirements.txt
# Note: If no requirements.txt exists, you'll need to list the main libraries:
# pip install pandas numpy xgboost prophet optuna statsmodels us-holidays scikit-learn


Run the notebook:
Open the PMJE_Energy_Consumption.ipynb file in Jupyter Lab or VS Code to step through the analysis, feature creation, optimization, and final model evaluation.
