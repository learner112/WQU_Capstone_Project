# WQU Capstone Project: Index Narrowing application on NIFTY50 index

A comprehensive quantitative finance project analyzing the NIFTY 50 index constituents, calculating risk metrics, and developing portfolio optimization strategies with backtesting capabilities.

## Project Overview

This capstone project focuses on:
- **Data Collection**: Gathering historical price data for NIFTY 50 constituents and index prices from 2015-2025
- **Risk Analysis**: Computing beta, volatility, Sharpe ratio, and Signal-to-Noise Ratio (SNR) metrics
- **Index Composition Tracking**: Monitoring NIFTY 50 constituent changes and weightages over time (semi-annual rebalancing)
- **Portfolio Construction**: Building optimized portfolios based on risk-adjusted returns
- **Backtesting**: Evaluating portfolio performance against the NIFTY 50 benchmark index
- **Performance Analysis**: Comparing strategy returns vs. buy-and-hold index returns

## Project Structure

```
WQU_Capstone_Project/
├── README.md                                # This file
├── requirements.txt                         # Python dependencies
│
├── Notebooks/
│   ├── data_loader.ipynb                   # Downloads and prepares raw market data
│   ├── data_preperation.ipynb              # Cleans and processes data for analysis
│   ├── main.ipynb                          # Core portfolio optimization and analysis
│   └── performance_analysis.ipynb          # Backtesting and strategy evaluation
│
├── Data Files/
│   ├── all_price_data.csv                  # Combined price history for all stocks
│   ├── nifty50_cons.csv                    # All NIFTY 50 constituents over time
│   ├── nifty50_cons_with_risk_metrics.csv  # Constituents + risk metrics (beta, vol, Sharpe)
│   ├── nifty50_index_prices_2015_2025.csv  # NIFTY 50 daily index prices
│   ├── portfolio_vs_nifty50_index.csv      # Strategy portfolio returns vs benchmark
│   └── NIFTY50_Index Prices_2016_2020.csv  # Historical index prices (2016-2020)
│
├── price_history/                          # Individual stock price files
│   ├── ACC.csv, ADANIENT.csv, ADANIPORTS.csv, ... (50+ stock files)
│   └── [All NIFTY 50 constituent stocks]
│
├── Rebalance files/                        # Index rebalancing records
│   ├── forward_index_narrowing_by_rebalance_2016-03-31.csv
│   ├── forward_index_narrowing_by_rebalance_2016-09-30.csv
│   └── [Semi-annual rebalancing records from 2016-2025]
│
└── Nifty50/                                # Source NIFTY 50 constituent data
    ├── nifty50_combined.csv
    ├── mcwb_mar16/, mcwb_mar17/, ..., mcwb_mar25/
    ├── mcwb_sep16/, mcwb_sep17/, ..., mcwb_sep25/
    └── [NIFTY 50 composition snapshots by rebalance date]
```

## Key Data Files

| File | Description |
|------|-------------|
| `all_price_data.csv` | Combined daily prices for all NIFTY 50 constituents with daily returns |
| `nifty50_cons.csv` | Historical constituent list with weightages from 2016-2025 |
| `nifty50_cons_with_risk_metrics.csv` | Constituents + Beta, Volatility, Sharpe Ratio metrics |
| `nifty50_index_prices_2015_2025.csv` | Daily NIFTY 50 index open/high/low/close prices |
| `portfolio_vs_nifty50_index.csv` | Cumulative returns comparison: portfolio strategy vs benchmark |
| `price_history/` | 50+ individual stock CSV files with adjusted close prices |

## Technologies & Dependencies

The project uses:
- **Data Processing**: pandas, numpy
- **Data Collection**: yfinance (Yahoo Finance API)
- **Statistical Analysis**: statsmodels
- **Visualization**: matplotlib, seaborn
- **Jupyter**: Interactive notebooks for analysis

See `requirements.txt` for complete dependency list.

## Workflow

### 1. Data Loading (`data_loader.ipynb`)
- Downloads NIFTY 50 constituent data from periodic rebalancing files (March/September)
- Fetches historical price data from Yahoo Finance for all constituents
- Downloads daily NIFTY 50 index prices (2015-2025)
- Handles missing data and download failures

### 2. Data Preparation (`data_preperation.ipynb`)
- Consolidates individual stock price files into `all_price_data.csv`
- Calculates daily returns for each security
- Merges constituent information with risk metrics
- Handles outliers and data validation

### 3. Main Analysis (`main.ipynb`)
- Computes risk metrics (Beta, Volatility, Sharpe Ratio, SNR)
- Implements portfolio optimization algorithms
- Applies transaction costs (20 bps) for realistic modeling
- Performs portfolio rebalancing based on risk-adjusted metrics
- Generates portfolio composition over time

### 4. Performance Analysis (`performance_analysis.ipynb`)
- Backtests strategies across the entire time period
- Compares portfolio returns vs NIFTY 50 benchmark
- Calculates performance metrics (Sharpe Ratio, Maximum Drawdown, Win Rate)
- Visualizes cumulative returns and performance analysis

## Key Metrics

- **Beta (β)**: Measures stock sensitivity to market movements
- **Volatility (σ)**: Annualized standard deviation of returns
- **Sharpe Ratio**: Risk-adjusted return metric
- **Signal-to-Noise Ratio (SNR)**: Beta / Volatility² - captures information efficiency
- **Transaction Costs**: 20 basis points (0.2%) per trade

## Installation & Setup

### Requirements
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Installation Steps

1. Clone/download the project
2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Open Jupyter and run notebooks in order:
```bash
jupyter notebook
```

4. Execute notebooks in this sequence:
   - `data_loader.ipynb` (data collection)
   - `data_preperation.ipynb` (data cleaning)
   - `main.ipynb` (core analysis)
   - `performance_analysis.ipynb` (results)

## Key Features

✅ **Comprehensive Data Coverage**: 10 years of historical data (2015-2025)
✅ **Real-world Constraints**: Transaction costs and semi-annual rebalancing
✅ **Risk Metrics**: Beta, volatility, Sharpe ratio, and custom metrics
✅ **Backtesting Framework**: Performance evaluation with proper alignment to historical index composition
✅ **Multiple Strategies**: Portfolio optimization using Signal-to-Noise Ratio ranking
✅ **Visualization**: Performance charts, cumulative returns, and risk analysis

## Output & Analysis

The project produces:
- **Portfolio Composition Files**: CSV files showing which stocks to hold at each rebalance date
- **Performance Report**: `portfolio_vs_nifty50_index.csv` comparing strategy vs benchmark returns
- **Risk Metrics**: Historical beta, volatility, and Sharpe ratios
- **Visualizations**: Return curves, drawdown analysis, performance comparisons

## Notes

- NIFTY 50 rebalances semi-annually (March and September of each year)
- Analysis uses 1-year rolling windows for risk metric calculations
- Minimum 200 observations required for statistical estimation
- Data sourced from Yahoo Finance (adjusted close prices)
- All prices are in Indian Rupees (INR)

## Author
Siddhartha Datta

## License
This project is part of the WQU (WorldQuant University) Capstone Project program.
