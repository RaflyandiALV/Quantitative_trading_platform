# Quantitative Trading & Backtesting Platform

> [In Active Development] A comprehensive Python-based backend for algorithmic trading, featuring a custom-built backtesting engine and a FastAPI service to support a front-end iOS portfolio application.

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.26-4D77CF?logo=numpy&logoColor=white)
![yfinance](https://img.shields.io/badge/yfinance-0.2-318CE7)
![ccxt](https://img.shields.io/badge/ccxt-4.x-brightgreen)
![TA-Lib](https://img.shields.io/badge/TA--Lib-0.4-orange)
![Jupyter](https://img.shields.io/badge/JupyterLab-4.x-F37626?logo=jupyter&logoColor=white)

---

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
* **Data Analysis & Manipulation:** `Pandas`, `NumPy`, `SciPy`
* **Data Acquisition:** `ccxt`, `yfinance`
* **Visualization:** `Matplotlib`, `Seaborn`
* **Development Environment:** `Jupyter Notebook`, `VS Code`, `Git`

---

## 6. How to Run (Step-by-Step Guide)

This project consists of several Jupyter Notebooks. The recommended way to run this project is by using **Conda** for environment management, as it simplifies the complex installation of `TA-Lib`.

### A. Get the Code

1.  Open your terminal (CMD, PowerShell, or Git Bash).
2.  Clone the repository:
    ```bash
    git clone [https://github.com/RaflyandiALV/Quantitative_trading_platform.git](https://github.com/RaflyandiALV/Quantitative_trading_platform.git)
    cd Quantitative_trading_platform
    ```

### B. Setup Environment (Requires Conda/Miniconda)

1.  **Create a new Conda environment:**
    This command creates a new environment named `quant_platform` with Python 3.13.
    ```bash
    conda create -n quant_platform python=3.13 -y
    ```

2.  **Activate the environment:**
    ```bash
    conda activate quant_platform
    ```
    *(Your terminal prompt will now show `(quant_platform)`)*

### C. Install Dependencies

Installation is a two-step process to ensure TA-Lib is installed correctly.

1.  **Install TA-Lib (Required via Conda):**
    This is the most stable way to install `TA-Lib` on both Windows and macOS.
    ```bash
    (quant_platform) C:\...> conda install -c conda-forge ta-lib -y
    ```

2.  **Install all other libraries:**
    Use the provided `requirements.txt` file to install the remaining packages.
    ```bash
    (quant_platform) C:\...> pip install -r requirements.txt
    ```

### D. Launch the Project

1.  **Start Jupyter Lab:**
    From inside the project folder, run:
    ```bash
    (quant_platform) C:\...> jupyter lab
    ```

2.  **Open a Notebook:**
    Your browser will open automatically. From the file navigator on the left, click on any notebook (e.g., `multitimeframe.ipynb` or `grid_trading.ipynb`) to get started.

3.  **Run the Analysis:**
    Execute the code cells in the notebook one by one from top to bottom to see the analysis and backtest results.

---

## 7. Dependencies (`requirements.txt`)

This repository includes a `requirements.txt` file listing all necessary Python packages.
*(**Note:** `TA-Lib` is intentionally omitted from this file as it must be installed via Conda as shown in Step C1).*
