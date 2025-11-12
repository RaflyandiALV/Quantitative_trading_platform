# Quantitative Trading & Backtesting Platform

> [In Active Development] A comprehensive Python-based backend for algorithmic trading, featuring a custom-built backtesting engine and a FastAPI service to support a front-end iOS portfolio application.

## 1. Project Overview

This project is the core logic and backend for a personal quantitative trading system designed for cryptocurrency markets. The primary goal is to create a robust environment to research, build, and rigorously backtest various trading strategies before deploying them.

The system is architected as a decoupled backend service. The Python engine handles all data processing, strategy logic, and performance analytics, while a **FastAPI** layer serves this data to a front-end client (an iOS application currently in development).

## 2. Core Features

* **Custom Backtesting Engine:** Built from scratch to simulate trade execution, risk management (Stop Loss/Take Profit), commission fees, and detailed P&L tracking.
* **Strategy Implementation Framework:** A modular structure that allows for new strategies to be easily developed and tested.
* **Performance Analytics Dashboard:** Generates key financial metrics (Sharpe Ratio, Max Drawdown, Win Rate, Volatility) and equity curves, comparing strategy performance against a "Buy & Hold" benchmark.
* **Data Acquisition & Cleaning:** Scripts to fetch, clean, and resample historical market data from multiple sources (via `ccxt` and `yfinance`) and augment it with technical indicators.
* **API-Driven Backend:** A secure RESTful API using FastAPI to serve data and manage strategy execution.

## 3. Strategies Implemented & Researched

This platform has been used to implement and validate four primary trading strategies from scratch:

1.  **Grid Trading:** A bot that automatically places Buy and Sell limit orders at predefined price intervals to profit from market volatility.
2.  **Mean Reversal (Bollinger Bands & RSI):** Identifies potential entry points by triggering Buy orders on *oversold* conditions (price hitting lower Bollinger Band, confirmed by low RSI) and Sell orders on *overbought* conditions.
3.  **Momentum (Breakout):** Identifies high-momentum breakout signals where price breaks a key historical resistance level, confirmed by high volume and a bullish MACD crossover.
4.  **Multi-Timeframe Analysis (MTA):** A complex hierarchical strategy:
    * **D1 (Daily):** Confirms the overall bullish trend.
    * **H4 (4-Hour):** Identifies momentum alignment within that trend.
    * **H1 (1-Hour):** Executes precise entries on pullbacks to key moving averages.

## 4. Technical Architecture

The system is designed with a clear separation of concerns:

* **Data Layer:** Handles all data fetching (`ccxt`, `yfinance`) and data processing/indicator calculation (`Pandas`, `NumPy`).
* **Strategy & Backtesting Layer:** The core Python engine where strategy logic is defined and executed against historical data.
* **Analysis Layer:** Generates performance metrics and visualizations (`Matplotlib`, `Seaborn`).
* **API Layer (In Development):** A `FastAPI` server that provides secure endpoints for:
    * `GET /market_data`: Fetching live or historical data.
    * `GET /portfolio`: Retrieving current portfolio status, balance, and open positions.
    * `GET /trade_history`: Fetching historical trade logs.
    * `POST /strategy/start`: Sending commands to initiate or stop a specific trading bot.

## 5. Technology Stack

* **Core & Backend:** `Python`, `FastAPI`
* **Data Analysis & Manipulation:** `Pandas`, `NumPy`
* **Data Acquisition:** `ccxt`, `yfinance`
* **Visualization:** `Matplotlib`, `Seaborn`
* **Development Environment:** `Jupyter Notebook`, `VS Code`, `Git`
