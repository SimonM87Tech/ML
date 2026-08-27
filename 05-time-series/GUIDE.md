# Time Series

Predicting the future from the past: sales, demand, prices, server load. Deceptively different from other ML — the data is ordered, and that changes everything.

## Keywords decoded

- **Forecasting horizon** — how far ahead you predict. Accuracy decays fast with distance; pin the client down on the horizon they actually need.
- **Trend / seasonality / noise** — the classic decomposition: long-term direction + repeating cycles (weekly, yearly) + randomness. Plot these before modeling anything.
- **Stationarity** — statistical properties not changing over time. Classical methods assume it; real data usually isn't (hence differencing — modeling the *changes* instead of the values).
- **Autocorrelation** — how much the series correlates with its own past. Tells you which **lag features** (value 1 day ago, 7 days ago...) will help.
- **ARIMA / exponential smoothing** — classical statistical forecasters. Still strong baselines; often unbeaten on short, clean series.
- **Gradient boosting on lag features** — turn forecasting into tabular ML: features = lags, rolling means, day-of-week, holidays. The pragmatic industry workhorse (see `01-classical-ml`).
- **Prophet / NeuralProphet, N-BEATS, TFT** — packaged and deep forecasters. Worth knowing by name; reach for them only when simpler methods plateau.
- **Walk-forward validation** — the only honest evaluation: train on the past, test on the future, slide forward. **Random train/test splits are data leakage here** — you'd be training on the future. Most common time-series mistake.
- **Backtest** — running the model over history as if live. You know this from distinct-baguette.

## What to master

1. Decompose and plot a series before modeling.
2. The lag-features + gradient boosting recipe.
3. Walk-forward validation, reflexively.
4. Baselines: "predict yesterday's value" and "predict same day last week" are brutally hard to beat. Report every model against them.

## Advisor lens

Forecasting clients usually want the impossible ("predict our sales next quarter within 2%"). Reframe deliverables around *decisions*: is the forecast good enough to order inventory, staff shifts, set budgets? A forecast with honest uncertainty bands that improves a decision beats a precise-looking number that can't be trusted.
