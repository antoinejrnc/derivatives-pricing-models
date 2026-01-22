# Derivatives Pricing Models (Python)

This repository implements a compact but rigorous **European option pricing and risk analytics** toolkit in Python.

It includes:
- **Black–Scholes–Merton pricing** (calls & puts, with dividend yield)
- **Analytical Greeks** (Δ, Γ, Vega, Θ, ρ)
- **Implied volatility** via numerical root-finding (Brent’s method)
- **Monte Carlo validation** under geometric Brownian motion (GBM)
- **Sensitivity analysis** (price vs volatility) with visualisation

---

## How to run

This project is designed to run in **Google Colab** (or locally in Jupyter).

1. Open `project1.ipynb`
2. Run all cells from top to bottom
3. Figures and outputs will be generated automatically

---

## Methods

### Black–Scholes framework
Under the Black–Scholes–Merton assumptions, the underlying follows a GBM process:

\[
dS_t = (r - q) S_t \, dt + \sigma S_t \, dW_t
\]

where:
- \( r \) = risk-free rate  
- \( q \) = dividend yield  
- \( \sigma \) = volatility  
- \( W_t \) = Brownian motion  

Closed-form solutions are implemented for European call and put prices.

### Numerical methods
- **Implied volatility** is obtained by inverting the Black–Scholes pricing function using **Brent’s root-finding method**.
- **Monte Carlo simulation** is used as an independent pricing approach to validate the analytical results.

---

## Validation (important)

This notebook validates results using multiple consistency checks:

- **Analytical vs Monte Carlo pricing:** Monte Carlo estimates converge close to Black–Scholes prices (up to sampling error).
- **Implied volatility recovery:** implied vol computed from a model-generated price returns the original volatility input.
- **Economic sanity checks:** option prices increase monotonically with volatility; Greeks exhibit expected signs and magnitudes.

These checks mirror best practice in quantitative model implementation: verify results using **independent methods**, not just one formula.

---

## Model limitations (important)

Black–Scholes is foundational but relies on simplifying assumptions that do not fully hold in real markets:

- **Constant volatility:** real markets exhibit volatility smiles/skews and time-varying volatility.
- **Lognormal returns:** empirical returns can have skewness and fat tails.
- **No jumps:** sudden price moves are not captured.
- **Frictionless hedging:** ignores discrete hedging, transaction costs, liquidity constraints, and funding spreads.

### Why this matters
These limitations motivate more advanced models such as:
- **Stochastic volatility (e.g., Heston)**
- Jump-diffusion models
- Local volatility models

This project is intentionally built as a clean baseline that can be extended to these frameworks.

---

## Reproducibility

Python libraries used:
- `numpy`
- `pandas`
- `scipy`
- `matplotlib`

Recommended environment:
- Python 3.9+ (works in Colab)

---

## Project purpose

This project was developed to demonstrate:
- correct implementation of core derivatives pricing theory,
- numerical methods (root finding, simulation),
- risk sensitivity computation (Greeks),
- and practical validation and interpretation of results.

It is intended as preparation for postgraduate study and quantitative finance applications.
