# Convolutional Neural Networks for Market Prediction

## Model 1
Our dataset consists of 5 years of daily stock data of multiple symbols. We have to use as much symbols as possible to ensure sufficient size of dataset. 

On each day, we have OHLC (open, high, low, close) and volume info for each stock so in total we have 5 values at each time step. We use z-score to standardize the data. Moving average (over last 20) and simple standard deviation (over entire history) are used for standardization. 

The 10 (L) most recent daily data for each stock is used to predict its risk/reward ratio over the next 5 days (P). Therefore input data has the dimension of 5 x 10. Risk is defined as maximum drawdown; reward is the maximum return relative to the mean of 10 most recent closes.
