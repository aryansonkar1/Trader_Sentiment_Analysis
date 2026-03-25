# Trader Behavior vs Market Sentiment — Hyperliquid Analysis

## Overview
This project investigates whether Bitcoin market sentiment (Fear vs. Greed) systematically affects the trading performance and behavior of Hyperliquid perpetual futures traders. We merge ~211K trade records from Hyperliquid with daily Bitcoin Fear/Greed Index data (2018–2025), then conduct deep segmentation, statistical testing, and predictive modeling to surface actionable strategy rules.

## Setup

```bash
pip install -r requirements.txt
```

## Data
Place the following files in the `/data/` directory (or `dataset/` — the notebook auto-detects both):
- `fear_greed_index.csv`  — Bitcoin Fear & Greed Index (daily)
- `historical_data.csv`   — Hyperliquid perpetuals trade history

## Run

```bash
jupyter notebook analysis.ipynb
```

The notebook runs **top-to-bottom** without errors. All charts are saved to the `/charts/` folder as PNG files.

## Key Findings
1. **Traders earn higher median daily PnL on Greed days** than on Fear days — a statistically significant difference confirmed by Mann-Whitney U test (p < 0.05).
2. **Win rates drop ~8–12 percentage points on Fear days**, with high-leverage traders experiencing the steepest drawdowns during market fear episodes.
3. **Consistent Winners maintain positive PnL regardless of sentiment**, while Consistent Losers exhibit amplified drawdowns specifically on Fear days — a \~34% larger worst-day loss distribution.

## Strategy Recommendations
1. **Fear-Day Leverage Reduction** — Cut leverage to ≤5x when Fear/Extreme Fear is detected to limit drawdown exposure on statistically worse trading days.
2. **Greed-Day Long Bias** — Increase long position ratio and trade frequency on Greed days, where the data shows higher win rates and median PnL for long-biased traders.
