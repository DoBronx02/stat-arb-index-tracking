This repository contains the full code and analysis for an index-tracking study based on the Dow Jones Industrial Average (DJIA). The project compares two modelling approaches: Cointegration (price-based, long-term equilibrium) and Tracking Error Variance (TEV) (return-based, short-run matching), and evaluates their performance under different rolling-window rebalancing frequencies.
The study is divided into two main components:

1. Long-Run vs Short-Run Tracking Models

Cointegration:
Uses log-prices to test whether the DJIA and its constituents share a stable long-run equilibrium.

Stationarity of residuals is evaluated using the Augmented Dickey–Fuller (ADF) test.

TEV (Tracking Error Variance):
Uses log-returns to match short-horizon movements by minimizing the variance of the daily tracking error.

Both models are estimated on an in-sample

Dynamic Rolling-Window Rebalancing

After estimating weights in each 3-year calibration window:
The weights are held fixed for a chosen rebalancing frequency (fortnightly, monthly, quarterly, semi-annual).

Over each holding period, the portfolio returns are computed and compared against the index.

The next window rolls forward, new weights are estimated, and the process repeats.

Performance metrics include:

Average annual TE

Annual tracking error volatility

Tracking error skewness

Tracking error excess kurtosis

ADF statistics


Both unconstrained weights (raw regression coefficients) and constrained weights (long-only, sum-to-one, solved via CVXPY) are evaluated.

stat-arb-index-tracking/
│
├── index_tracking_project.ipynb     
└──README.md                        

Data

Historical daily prices are automatically downloaded using yfinance for:
30 DJIA constituent stocks
The DJIA index (^DJI) for the period 2015–2025.

Results Summary

Cointegration spreads are strongly stationary, confirming a long-run price equilibrium.

TEV spreads display weak or no stationarity, capturing only short-run co-movement.

TEV yields smoother short-run behaviour but exhibits persistent fat-tailed errors (high kurtosis).



Author
Anirban Sen — M.Sc. Data Science


