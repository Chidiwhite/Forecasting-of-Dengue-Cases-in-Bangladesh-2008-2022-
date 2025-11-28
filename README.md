# Forecasting-of-Dengue-Cases-in-Bangladesh-2008-2022
This time-series forecasting project analyzed over a decade of Dengue-Climate data from Bangladesh (2008–2022) to build a predictive model for disease outbreaks.This project wasn't just about fitting a line; it was a lesson in statistical rigor, feature engineering, and the importance of model parsimony. Here is a breakdown of the project:

Data Loading & Transformation: Started by merging discrete year/month columns to create a continuous datetime index, transforming raw records into a structured time-series dataset ready for analysis.

Exploratory Data Analysis (EDA) & The 2019 Anomaly:Visualization revealed the strong seasonal nature of the disease, but one year stood out. I isolated and plotted the 2019 data specifically, uncovering a massive, atypical outbreak peak that dwarfed historical trends. This anomaly became a critical focal point for understanding the limitations of standard forecasting models.

Feature Engineering (The "Lag" Effect):Mosquito-borne diseases don't react to weather instantly. I engineered lagged variables (t-1 to t-3 months) for Rainfall, Temperature, and Humidity to capture the biological delay between environmental changes and reported cases.

Stationarity Check (ADF Test):A critical step in time series. I performed the Augmented Dickey-Fuller test, which yielded a p-value of 1.72e-09, confirming the data was stationary. This allowed me to set the differencing parameter ($d=0$) with confidence.

Modeling (SARIMAX ➡️ SARIMA):I initially built a SARIMAX model to include climate drivers. However, rigorous P-value testing revealed a surprising insight: the historical momentum and seasonality were such dominant predictors that the climate variables were statistically insignificant. I pivoted to a pure, parsimonious SARIMA(1, 0, 0) x (0, 1, 0, 12) model.

Prediction & Evaluation:Testing on the last 24 months (2022-2023), the model achieved an MAE of 3,716. While accurate for baseline months, the high RMSE (6,815) highlighted the challenge of predicting extreme "black swan" outbreak events using historical patterns alone.This project reinforced that sometimes, the simplest model is the most robust—and that detecting outliers like 2019 is just as important as the forecast itself.
