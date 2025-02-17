# Stock-Price-Prediction-Using-ARIMA-
Made a code for standard Prediction of stock price Using ARIMA Model by Python 
1. What is ARIMA?
ARIMA (AutoRegressive Integrated Moving Average) is a statistical model used for time series forecasting. It helps predict future stock prices by analyzing past price movements.

2. Why Use ARIMA for Stock Prediction?
Stock prices follow time series patterns, and ARIMA is effective in capturing trends.
It helps smooth out short-term noise and provides reliable forecasts.
It doesn’t require complex feature engineering—just historical price data.
3. How I Built the Model Using NSE Library
Instead of using a static dataset, I directly fetched live stock price data from the NSE (National Stock Exchange) using the nsepy or yfinance library.

🔹 Steps I Followed:

Fetched Stock Data

Used the NSE library (nsepy or yfinance) to extract historical stock prices.
Example: get_history(symbol="RELIANCE", start=date(2015,1,1), end=date(2023,12,31))
Preprocessed the Data

Checked for missing values.
Converted the date column to a time series index.
Ensured stationarity using the Augmented Dickey-Fuller (ADF) test.
Configured the ARIMA Model

Determined p, d, q using Autocorrelation (ACF) and Partial Autocorrelation (PACF) plots.
Example parameter selection:
p = 2 (AutoRegressive order)
d = 1 (Differencing for stationarity)
q = 2 (Moving Average order)
Trained the ARIMA Model

Used statsmodels' ARIMA function to fit the model.
Example:
python
Copy
Edit
from statsmodels.tsa.arima.model import ARIMA
model = ARIMA(stock_data['Close'], order=(2,1,2))
model_fit = model.fit()
Made Predictions

Forecasted future stock prices using .forecast()
Example:
python
Copy
Edit
forecast = model_fit.forecast(steps=30)  # Predict next 30 days
Evaluated Model Performance

Compared predicted prices with actual values.
Used metrics like RMSE (Root Mean Squared Error) to check accuracy.
4. Key Insights & Limitations
✅ Strengths:

Easy and efficient stock price forecasting without needing to collect and clean a dataset.
Can be automated for real-time predictions.
⚠️ Limitations:

ARIMA works well for short-term trends, but it doesn’t capture sudden market fluctuations or news impacts.
It assumes stock prices are linear, which is not always true.
5. Next Steps for Improvement
Experiment with SARIMA (Seasonal ARIMA) for better predictions.
Combine ARIMA with machine learning (LSTMs, Random Forest) for improved accuracy.
Incorporate trading volume, news sentiment, or macroeconomic indicators for a more robust model.
