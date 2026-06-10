# 📈 Trade Bot — Time Series Analyst

A time series analysis bot that processes market data to identify patterns, generate signals, and support trading decisions.

---

## Features

- Ingests OHLCV (Open, High, Low, Close, Volume) data from market feeds or CSV
- Time series decomposition: trend, seasonality, and residual analysis
- Technical indicator computation (moving averages, RSI, MACD, Bollinger Bands, etc.)
- Signal generation based on configurable strategy rules
- Backtesting engine to evaluate strategy performance on historical data
- Visualization of price series, indicators, and trade signals

---

## Requirements

- Python 3.9+
- Dependencies:

```bash
pip install -r requirements.txt
```

Key libraries: `pandas`, `numpy`, `scikit-learn`, `statsmodels`, `ta`, `matplotlib`, `ccxt` (or `yfinance` for stock data)

---

## Project Structure

```
trade-bot/
├── data/               # Raw and processed market data
├── src/
│   ├── ingestion.py    # Data fetching and loading
│   ├── features.py     # Indicator and feature engineering
│   ├── model.py        # Time series models (ARIMA, LSTM, etc.)
│   ├── strategy.py     # Signal generation logic
│   ├── backtest.py     # Backtesting engine
│   └── visualize.py    # Plotting utilities
├── config.yaml         # Strategy and API configuration
├── main.py             # Entry point
├── requirements.txt
└── README.md
```

---

## Configuration

Edit `config.yaml` to set your data source, strategy parameters, and credentials:

```yaml
data:
  source: yfinance          # yfinance | ccxt | csv
  symbol: BTC-USD
  interval: 1d              # 1m, 5m, 1h, 1d
  start: "2022-01-01"
  end: "2024-12-31"

strategy:
  short_window: 20
  long_window: 50
  rsi_threshold: 30

api:
  key: YOUR_API_KEY
  secret: YOUR_API_SECRET
```

> ⚠️ Never commit your API keys. Use environment variables or a `.env` file and add it to `.gitignore`.

---

## Usage

**Fetch data and run analysis:**
```bash
python main.py --mode analyze
```

**Run backtest:**
```bash
python main.py --mode backtest
```

**Live signal monitoring:**
```bash
python main.py --mode live
```

---

## Time Series Models

The bot supports multiple modeling approaches:

| Model | Use Case |
|---|---|
| ARIMA / SARIMA | Classical statistical forecasting |
| Exponential Smoothing | Trend + seasonality decomposition |
| LSTM / GRU | Deep learning on sequential price data |
| Prophet | Multi-seasonality with holiday effects |

Switch models via the `model.type` field in `config.yaml`.

---

## Backtesting

Backtest results include:
- Total return and annualized return
- Sharpe ratio and max drawdown
- Win rate and average trade P&L
- Equity curve plot

---

## Disclaimer

This bot is for **educational and research purposes only**. It does not constitute financial advice. Always do your own due diligence before trading with real capital.

---

## License

MIT
