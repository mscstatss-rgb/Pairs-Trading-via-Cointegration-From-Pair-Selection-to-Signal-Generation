# Pairs-Trading-via-Cointegration-From-Pair-Selection-to-Signal-Generation

Overview

Rather than forecasting individual stock prices, this project looks at relationships between stocks in the same sector. If two stocks are cointegrated, the spread between them tends to revert to a stable long-run mean — even though each stock's own price is close to unpredictable on its own. That mean-reverting spread is what gets traded.

Methodology
1)Data collection — daily adjusted close prices for a set of NSE-listed stocks across two sectors (Banking, Automobile), ~3 years of history.

2)Stationarity testing — Augmented Dickey-Fuller (ADF) test confirms each individual price series is non-stationary (I(1)), a precondition for cointegration.

3)Cointegration testing — Engle-Granger test run pairwise across all sector candidates to find pairs whose spread is stationary.

4)Regression direction check — both regression directions (A on B, B on A) tested, since Engle-Granger is not symmetric; the direction producing the more stationary residual was used.
5)Spread modeling — hedge ratio estimated via OLS, spread computed and visually/statistically validated for mean reversion.

6)Z-score signal generation — spread converted to a rolling z-score (rolling mean and rolling std, not a single fixed value) to account for volatility clustering observed in the data.

7)Position signals — simple threshold-based entry/exit rules (enter at |z| > 2, exit near z = 0).
