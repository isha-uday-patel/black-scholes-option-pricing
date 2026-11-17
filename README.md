# Black-Scholes Option Pricing: Derivatives Valuation & Sensitivity Analysis

Python implementation of the Black-Scholes-Merton model to price European call and put options on Apple (AAPL), calculate the Greeks and test how option values respond to volatility and time to expiration.

## Inputs

| Parameter | Value | Note |
|---|---|---|
| Spot price (S) | $333.74 | Retrieved with yfinance when the notebook was run |
| Strike (K) | $334.00 | At-the-money, rounded to the nearest dollar |
| Time to expiration (T) | 0.25 years | Assumed 3-month contract |
| Risk-free rate (r) | 5.0% | Approximate US Treasury rate |
| Volatility (σ) | 19.95% | Annualized from AAPL daily returns for 2023 (historical, not implied) |

## Results

| | Call | Put |
|---|---|---|
| Price | $15.24 | $11.35 |
| Delta | 0.5665 | -0.4335 |
| Gamma | 0.0118 | 0.0118 |
| Vega (per 1%) | 0.6565 | 0.6565 |
| Theta (per day) | -0.0956 | -0.0504 |
| Rho (per 1%) | 0.4345 | -0.3901 |

## Checks

- Put-call parity: call minus put equals spot minus the discounted strike ($3.89)
- Delta: call delta minus put delta equals 1.0
- Gamma and vega are identical for the call and the put at the same strike

## Sensitivity analysis

Charts show option prices across volatility from 10% to 50% and time decay from 365 days to expiry.

## Limitations and extensions

- Uses historical volatility, so a next step is to compare with market-implied volatility
- Prices European options only; extend to American options with a binomial tree or Monte Carlo
- Assumes constant volatility, so it ignores the volatility smile and skew
- Backtest against historical option chain data to measure pricing accuracy

## Tools

Python 3, NumPy, SciPy (stats), Pandas, Matplotlib, yfinance

## How to run

```bash
pip install -r requirements.txt
jupyter notebook Black_Scholes_Option_Pricing.ipynb
```

Full write-up: `Black_Scholes_Report.pdf`

*Student project for educational purposes. Not investment advice.*# black-scholes-option-pricing
