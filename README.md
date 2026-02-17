# Predicting Next-Day S&P 500 Direction Using Machine Learning

## 📌 Project Overview

This project investigates whether **next-day directional movement of the S&P 500 index** can be predicted using historical price data and machine learning.

Financial time series are noisy, weakly predictive, and highly prone to overfitting. The objective is **not** to claim market inefficiency, but to:

- Build a realistic ML pipeline for financial time series  
- Avoid common sources of leakage and bias  
- Evaluate performance using proper temporal validation  
- Assess whether any predictive signal survives out-of-sample testing  

---

## 🎯 Research Question

> Can historical price-based features provide statistically meaningful predictive power for next-day S&P 500 direction?

Target variable:

- **1** → Next-day close > today’s close  
- **0** → Next-day close ≤ today’s close  

This is framed as a **binary classification problem**.

---

## ⚠️ Why This Problem Is Difficult

Equity markets are close to informationally efficient. Predictive modeling in this domain faces several structural challenges:

- Low signal-to-noise ratio  
- Non-stationarity  
- Regime shifts  
- Look-ahead bias risk  
- Data leakage via improper cross-validation  
- Overfitting due to flexible models  

Most “stock prediction” notebooks fail because they ignore these issues.

This project explicitly addresses them.

---

## 📊 Data

**Instrument:** S&P 500 Index (^GSPC)  
**Source:** Yahoo Finance (via `yfinance`)  
**Frequency:** Daily OHLCV  

### Feature Categories

**Price-Based Features**
- Daily returns
- Rolling returns
- High-low spreads
- Volatility proxies
- Volume dynamics

**Technical Indicators**
- Simple & Exponential Moving Averages
- RSI
- MACD
- Momentum-based signals
- Rolling trend indicators

All features are constructed using only historical data available at time *t*.

---

## 🧠 Modeling Approach

### Model Used

- **Random Forest Classifier**

Chosen for:
- Non-linear pattern detection
- Robustness to noisy inputs
- Reduced sensitivity to scaling
- Built-in feature importance estimation

---

## 🔬 Backtesting & Validation Framework

To prevent leakage and inflated performance:

- Temporal train-test split (no shuffling)
- Walk-forward style validation
- Out-of-sample evaluation
- No future information in feature construction
- Target alignment strictly shifted forward

This simulates realistic deployment conditions.

---

## 📈 Evaluation Metrics

Given the classification framing:

- Precision

More importantly:

- Out-of-sample performance stability
- Comparison against naive baseline (50% directional accuracy)

In financial prediction, even small edges (~52–55%) can be meaningful — but must be stable.

---

## 📊 Results (Replace With Your Actual Numbers)

Performance remains close to random baseline, consistent with market efficiency literature.

Key observation:  
Feature complexity does not necessarily translate into robust predictive power once leakage is eliminated.

---

## 🧩 Key Lessons

1. Backtesting methodology matters more than model complexity  
2. Many apparent “edges” disappear under proper temporal validation  
3. Technical indicators alone provide limited predictive power  
4. Financial ML requires extreme discipline around leakage  

---

## 🔁 Reproducibility

1. Clone repository  
2. Install dependencies  
3. Run Jupyter notebook sequentially
