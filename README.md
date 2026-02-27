# Retail Demand Forecasting

## Overview
This project predicts daily sales for retail stores using historical sales data, 
promotions, and calendar features.  
Built to understand the exact problem Tajir is solving — predicting what a 
shopkeeper needs before they run out of stock.

## Dataset
- Source: [Kaggle Store Sales Time Series Forecasting](https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data)
- Download `train.csv` and `test.csv` and place them in the same folder as the notebook
- Features include `store_nbr`, `family`, `date`, `sales`, `onpromotion`

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

## Limitations
Model performs well on regular sales patterns but underestimates sudden demand 
spikes — a known limitation of tree-based models on time series data. Next step 
would be trying Facebook Prophet or LSTM for better spike detection.

## How to Run
1. Clone repo
2. Download dataset from Kaggle link above and place in same folder
3. Install requirements: `pip install pandas numpy matplotlib seaborn scikit-learn`
4. Open and run `retail_demand_forecasting.ipynb`

## Insights
- Sales have **weekly seasonality**, higher on weekends for many families.
- Lag and rolling features significantly improve prediction accuracy.
- This pipeline can be extended for **SKU-level demand forecasting**, which is 
exactly what Tajir needs for logistics and inventory optimization.
