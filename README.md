# S&P 500 Next-Day Direction Prediction (Walk-Forward Backtest)

## Overview
This project tests whether simple market features contain **predictive signal** for the **next-day direction** (up/down) of the S&P 500 index.

The goal is *not* to claim market-beating performance — it is to build a **robust, bias-aware research workflow**:
- correct time-series validation
- realistic baselines
- simple strategy translation with transaction costs
- diagnostics that highlight regime sensitivity and feature instability

## What’s Inside
- **Data ingestion**: S&P 500 historical prices (via `yfinance`)
- **Feature engineering**: lagged returns / price-derived signals
- **Models**
  - Naive baselines (e.g., always-up / persistence)
  - Logistic regression baseline
  - Random Forest classifier
- **Evaluation**
  - Walk-forward / rolling backtest (no shuffling)
  - Accuracy and baseline comparison
  - Simple strategy returns translation + transaction cost sanity check
  - Feature importance snapshot + overfitting diagnostics

## Key Enhancements (Iteration Notes)
Recent improvements focus on realism and research discipline:
- Added **naive + linear baselines** for proper benchmarking
- Added **transaction-cost-adjusted** strategy returns to avoid “paper alpha”
- Added **feature importance** snapshot to check stability
- Added **train vs test gap** diagnostics to surface overfitting/regime effects

## How to Run
1. Open the notebook in Google Colab
2. Run cells top-to-bottom
3. Optional: tune feature set or model parameters and re-run backtest

## Repository Structure
- `*.ipynb` — main research notebook
- `README.md` — project overview

## Notes / Disclaimer
This is for educational and research purposes only. It is not investment advice.
Markets are non-stationary; results may not hold across regimes.
