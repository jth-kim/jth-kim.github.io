# Copula-Optimized DCC-GARCH

<br>

Python, Econometrics, Copulas, Dynamic Volatility, Dynamic correlation, SARIMA, Cross Correlation

<br>

This project showcases a custom implementation of DCC-GARCH models with copula optimization, applied to both financial (AAPL/SPX) and non-traditional space weather (sunspots/solar wind speed) datasets, alongside a foundational GARCH(1,1) applied to simulated data with (VaR) analysis. While GARCH and its multivariate innovations are from and primarily used in the world of econometrics, I think adapting these techniques to diverse contexts is interesting for novel interpretation. At the very least its a way to test my abilities and ensure a thorough understanding of the underlying methodology and statistical artefacts utilised.

## Objective
Develop and validate a DCC-GARCH framework from scratch to model dynamic correlations and volatilities, with copula optimization for flexible dependence structures. Apply to:

- Financial data (AAPL/SPX) to ensure correctness against standard benchmarks in its typical context.
- Space weather data (sunspots/solar wind speed) to explore an unorthodox application.
- Include a basic GARCH(1,1) applied to simulated data to investigate parameter variability’s impact on VaR and forecast skill, building foundational understanding and intuition.

## Method
All models are implemented in Python. Further details are contained in the relevant notebooks.

GARCH(1, 1) is vanilla:

<img width="458" height="111" alt="garch11_latex" src="https://github.com/user-attachments/assets/7ff90f7c-f351-4090-896b-1dcf1081b972" />

The DCC-GARCH(1, 1) model is in principle doing the same thing, but requires some extra matrix related step to break down the H matrix:

<img width="415" height="251" alt="dcc11_latex" src="https://github.com/user-attachments/assets/7e943ba7-3e00-4626-b7a3-bda3c68848fc" />

- Toy GARCH(1,1) with VaR: Implements a basic GARCH(1,1) model with manual log-likelihood optimization, using Monte Carlo simulations to assess parameter variability impact on volatility forecasts and VaR. This warmup toy project was to ensure I had clarity on the method before tackling DCC complexity.
- Applying DCC to financial data (AAPL x SPX) ensures I've done the implementation correctly, since using the model in this context is well understood, providing me with answers to check against.
- Since the Space Weather project is not a typical use of DCC, I spend a bit more time investigating how the model digests the data under different manipulations. It has inspired some other directions I could take going forward too.



## Plots:
See notebooks

## Findings 

See notebooks


Other notes:

The decomposition of the H matrix lends itself to interesting interpretations. The R is interpreted as a dynamic correlation. I suspect monitoring that R matrix would make for an interesting regime-change detecting tool. Surely there's existing literature on that. I'll look into it once i've developed my own thoughts on the idea.

## Tools

Python: pandas, numpy, scipy, statsmodels, arch, copulas, matplotlib, seaborn.
Data: AAPL/SPX (Yahoo Finance), sunspots (NOAA/SIDC), solar wind (NASA/OMNIWeb).
Reference: [Orskaug, E. (2009). Multivariate DCC-GARCH Model - With Various Error Distributions](http://hdl.handle.net/11250/259296)
