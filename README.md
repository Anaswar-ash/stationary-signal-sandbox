# Project 1: The "Stationary Signal" Sandbox 📈

## Overview
This project explores a foundational concept in quantitative finance and time-series machine learning: **Stationarity**. 

Financial price data is inherently non-stationary (it trends and drifts), which violates the core assumptions of most statistical models. To fix this, quants transform raw prices into stationary features (like returns). However, this transformation comes at a cost: the loss of the asset's "memory" or trend. This sandbox visualizes and mathematically proves this trade-off, often called the "Quant's Dilemma."

## The Goal
To learn how to engineer standard financial features from raw price data, test them for stationarity using the Augmented Dickey-Fuller (ADF) test, and visualize the cost of these transformations.

## Key Features Engineered
Using 1 year of daily BTC-USD data pulled via `yfinance`, the following features were calculated:
* **Simple Returns:** The day-to-day percentage change.
* **Log-Returns:** Time-additive returns favored in quantitative modeling.
* **20-Day Volatility:** The rolling standard deviation of log-returns to measure price explosion.
* **Body-to-Wick Ratio:** A custom metric measuring how decisive a daily candle's price action was (handling potential division-by-zero errors).

## The Lesson: Stationarity vs. Memory

By running the **Augmented Dickey-Fuller (ADF) Test** across the dataset, this project mathematically proves that:
1. **Raw Prices fail the ADF test (Non-Stationary):** They have a strong memory of previous prices and clear trends.
2. **Returns pass the ADF test (Stationary):** They revert to a mean of zero and have constant variance.

**The Catch:** When plotting the raw price against the stationary returns, the correlation is near zero. By making the data statistically "safe" for modeling, we destroyed the memory of the asset's actual price level. Finding predictive signals in this noisy, stationary data is the core challenge of algorithmic trading.

## How to Run This Project
1. Clone this repository.
2. Create a virtual environment and install the dependencies:
   ```bash
   pip install -r requirements.txt