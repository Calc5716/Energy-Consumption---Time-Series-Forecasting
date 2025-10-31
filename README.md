#  PMJE Energy Consumption Forecasting — Time Series Project

##  Overview
This project focuses on forecasting **hourly energy consumption** for the PJME region using multiple time series modeling techniques.  
The primary objective was to develop a **robust, accurate, and production-ready forecasting system** that leverages both classical and modern machine learning methods.

---

##  Workflow Summary

###  Data Preparation & Cleaning
- Loaded and explored the dataset, inspecting datatypes and timestamp consistency.  
- Converted the `Datetime` column to a proper `datetime` index and set hourly frequency to ensure no missing timestamps.  
- Checked and handled duplicate timestamps.  
- Renamed the target column to `y` and datetime index to `ds` for compatibility with Prophet.  
- Split the dataset into **training** and **testing** sets and visualized both for temporal validation.

---

###  Feature Engineering
- Created a **feature generation function** that engineered multiple exogenous predictors:
  - **Temporal features:** year, month, week, day of week, hour.
  - **Rolling statistics:** moving averages, lag features (1H, 1D, 1W).
  - **Seasonal indicators:** season flags, U.S. holidays, weekends.
- Imputed missing values using both **forward fill** and **backward fill**.
- One-hot encoded categorical variables using `OneHotEncoder` from scikit-learn.

---

###  Modeling & Evaluation
####  Model 1: SARIMAX
- Determined model parameters using ADFuller test, ACF/PACF plots, and seasonal decomposition.
- The SARIMAX model **failed to converge**, likely due to strong seasonality and numerous exogenous regressors.

####  Model 2: Prophet (Tuned with Optuna)
| Metric | Value |
|--------|--------|
| MAE | 603.06 |
| RMSE | 791.86 |
| MAPE | 1.9029% |

Achieved a **slightly improved but more stable model** through hyperparameter optimization.

####  Model 3: XGBoost Regressor
| Model | MAE | RMSE | MAPE |
|--------|--------|--------|--------|
| Tuned (Optuna) | 42.5086 | 159.453 | **0.1199 %** |

Although tuning improved performance, **Prophet remained the most accurate** for this dataset.

---

###  Final Outcome
- Selected **XGBooost (Optuna-tuned)** as the final model.
- Demonstrated strong generalization and forecasting precision, achieving a **MAPE of 0.1199 %**.

---

##  Key Tools & Libraries
`Python` | `Prophet` | `XGBoost` | `Optuna` | `scikit-learn` | `pandas` | `NumPy` | `matplotlib` | `seaborn`



---

## 📂 Author
**Paramesh Bandhu Banerjee**  
📧 parameshbbanerjee@gmail.com  
🎓 B.Sc. in Statistics | Presidency University, Kolkata
