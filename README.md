# LSTM-Based Price Prediction and Trading Strategy

## Overview
This project uses a Long Short-Term Memory (LSTM) neural network to predict the price of an underlying asset in the derivatives market and simulate a simple trading strategy based on those predictions. 
It incorporates market data, volatility estimates, and moving average features to train the model and backtest a trading approach.

## Features
- Collects historical financial data using Yahoo Finance (yfinance)
- Generates technical features such as moving averages, returns, and short-term volatility
- Prepares sequential data for training an LSTM time-series forecasting model
- Builds and trains an LSTM neural network for close price prediction
- Evaluates prediction accuracy with RMSE
- Estimates volatility from predicted price series
- Simulates a simple trading strategy: Buy when predicted price > today’s price; Sell otherwise
- Plots evaluation metrics, predictions, volatility, and strategy equity curve

## Requirements
- Python 3.8+
- Libraries:
  - numpy
  - pandas
  - matplotlib
  - yfinance
  - scikit-learn
  - tensorflow (Keras API included)

Install libraries via:
pip install numpy pandas matplotlib yfinance scikit-learn tensorflow


## How It Works
1. **Data Collection**
   - Downloads historical data for SPY (S&P 500 ETF) as the underlying asset.
   - Downloads VIX index as a proxy for market volatility.
2. **Feature Engineering**
   - Calculates daily returns, 10-day moving average, and 10-day volatility.
   - Merges features into a dataset and scales them using MinMaxScaler.
3. **Model Training**
   - Creates sequences of historical data (30 days) as LSTM input.
   - Splits into training and test sets.
   - Builds a two-layer LSTM with dropout for regularization.
   - Trains for 20 epochs.
4. **Evaluation**
   - Generates predictions on test data.
   - Inverse-transforms predictions to original scale and computes RMSE.
5. **Volatility Forecasting**
   - Calculates rolling standard deviation of predicted returns as forecasted volatility.
6. **Strategy Simulation**
   - Creates a simple long/short strategy based on predicted vs actual prices.
   - Computes cumulative returns and plots equity curve.

## Usage
1. Save the Python code (`main.py`) with the provided script.
2. Install required dependencies.
3. Run: python main.py

4. The program will output:
   - Prediction RMSE
   - Plots: actual vs predicted prices, predicted volatility, equity curve.

## Next Steps / Extensions
- Replace SPY data with **real option chain data** from Yahoo Finance or paid APIs.
- Use **implied volatility** directly from options data instead of VIX proxy.
- Incorporate **Black-Scholes**, **Heston**, or Neural SDE pricing models.
- Apply **Reinforcement Learning** (Stable-Baselines3) for optimized trade decision-making.
- Enhance risk management via Value-at-Risk (VaR) or CVaR models.

## Disclaimer
This project is for educational purposes only.  
It is **not** intended for live trading or financial advice.  
Historical performance does not guarantee future results.

