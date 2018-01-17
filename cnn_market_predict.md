# Convolutional Neural Networks for Market Prediction

## Model 1
Our dataset consists of M daily stock data of N symbols. 

On each day, we have OHLC (open, high, low, close) and volume. In total, we have 5 values for each time step. We use z-score to standardize the data.


The 10 (L) most recent daily data for each stock is used to predict risk/reward ratio of the same stock over the next 5 days (P). 
