# Retail Demand Forecasting

## Overview
This project predicts daily sales for retail stores using historical sales data, 
promotions, and calendar features.  
Built to understand the exact problem Tajir is solving — predicting what a 
shopkeeper needs before they run out of stock.

## Dataset
- Source: [Kaggle Store Sales Time Series Forecasting](https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data)
- Features include:
  - `store_nbr`, `family`, `date`, `sales`, `onpromotion`
- Data was cleaned and structured with **calendar features, lag features, and rolling averages**.

## Features Engineered
- Calendar: day_of_week, is_weekend, month, week_of_year
- Lag features: sales_lag_1 (yesterday), sales_lag_7 (last week)
- Rolling features: rolling_7 (7-day moving average)
- Promotions: onpromotion

## Model
- Random Forest Regressor (sklearn)
- Target: `sales`
- Train/Test split: Time-based (older dates for training, recent dates for testing)
- Performance metric: RMSE

## Results
- RMSE: 389.02
- Actual vs Predicted Sales plot: see `notebooks/03_modeling.ipynb`

## Limitations
Model performs well on regular sales patterns but underestimates sudden demand 
spikes — a known limitation of tree-based models on time series data. Next step 
would be trying Facebook Prophet or LSTM for better spike detection.

## How to Run
1. Clone repo
2. Install requirements: `pip install -r requirements.txt`
3. Run notebooks in order:
   - `01_eda.ipynb`
   - `02_feature_engineering.ipynb`
   - `03_modeling.ipynb`

## Insights
- Sales have **weekly seasonality**, higher on weekends for many families.
- Lag and rolling features significantly improve prediction accuracy.
- This pipeline can be extended for **SKU-level demand forecasting**, which is 
exactly what Tajir needs for logistics and inventory optimization.
