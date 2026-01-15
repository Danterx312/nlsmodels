# nlsmodels
nlsmodels: Python package for nonlinear least squares regression with R-like formula syntax (`y ~ a*exp(b*x)`). Features auto-initialization for logistic/exponential/Michaelis-Menten models, complete statistical diagnostics (AIC, BIC, R²), confidence intervals, and professional output. Perfect for data scientists and researchers.

<h1 align="center">
  <br>
  <img src="https://raw.githubusercontent.com/Danterx312/nlsmodels/main/docs/logo.png" alt="nlsmodels logo" width="200">
  <br>
  nlsmodels
  <br>
</h1>

<h4 align="center">Nonlinear Regression Models for Python with R-like Formula Syntax</h4>

<p align="center">
  <a href="https://pypi.org/project/nlsmodels/">
    <img src="https://img.shields.io/pypi/v/nlsmodels?color=blue&label=PyPI" alt="PyPI Version">
  </a>
  <a href="https://pepy.tech/project/nlsmodels">
    <img src="https://static.pepy.tech/badge/nlsmodels/month" alt="Monthly Downloads">
  </a>
  <a href="https://www.python.org/">
    <img src="https://img.shields.io/badge/python-3.8+-blue.svg" alt="Python Version">
  </a>
  <a href="https://github.com/Danterx312/nlsmodels/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License">
  </a>
  <a href="https://github.com/Danterx312/nlsmodels/actions">
    <img src="https://github.com/Danterx312/nlsmodels/actions/workflows/tests.yml/badge.svg" alt="Tests Status">
  </a>
</p>

<p align="center">
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-features">Features</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-documentation">Documentation</a> •
  <a href="#-examples">Examples</a> •
  <a href="#-api-reference">API</a> •
  <a href="#-contributing">Contributing</a> •
  <a href="#-license">License</a>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/Danterx312/nlsmodels/main/docs/demo.gif" alt="nlsmodels demo" width="600">
</p>

## 🚀 Quick Start

```python
import nlsmodels as nlm
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Logistic growth data
x = np.linspace(0, 20, 100)
y = 10 / (1 + np.exp((5 - x) / 2)) + np.random.normal(0, 0.5, 100)
df = pd.DataFrame({'x': x, 'y': y})

# Fit using special function (auto-initializes)
model = nlm.nonreg("y ~ SSlogis(x, Asym, xmid, scal)", df)
model.fit()

# View results
print(model.summary())
# Output:

#           NONLINEAR LEAST SQUARES REGRESSION             
# ============================================================
#    Dep. Variable:             y           Pseudo-R:    0.976
#            Model:           NLS      Adj. Pseudo-R:    0.975
#           Method: Least Squares        F-statistic: 1313.159
#             Date:    2026-01-14 Prob (F-statistic):    0.000
#             Time:      23:24:34     Log-Likelihood:  -71.856
# No. observations:           100                AIC: -134.122
#     Df Residuals:            97                BIC: -126.307
#        Df Model:             3
# ==========================================================
#       coef   std err     t      P>|t|    [0.025   0.975] 
# ----------------------------------------------------------
# Asym    9.990    0.081  123.682    0.000    9.830   10.151
# xmid    4.932    0.091   54.163    0.000    4.751    5.113
# scal    1.964    0.083   23.636    0.000    1.799    2.129
# ----------------------------------------------------------

# Notes:
# Pseudo-R² and F-statistic are reported as descriptive measures.
# Inference is based on local linearization of the nonlinear model.


Example 2
# Linear Regression Analysis: Puromycin Experiments

This project performs a linear regression analysis using the puromycin experiment data presented in the book **"Introduction to Linear Regression Analysis"** by Montgomery, Peck, and Vining.

## Reference

Montgomery, D. C., Peck, E. A., & Vining, G. G. (2021). *Introduction to Linear Regression Analysis*. Wiley.


## Experiment Data

The data corresponds to **Table 12.1** from the book, which shows the relationship between substrate concentration and enzymatic reaction velocity in the presence of puromycin.

### Table 12.1: Reaction Velocity vs. Substrate Concentration

| Substrate Concentration (ppm) | Velocity [(counts/min)/min] |
|---|---|
| 0.02 | 47, 76 |
| 0.06 | 97, 107 |
| 0.11 | 123, 139 |
| 0.22 | 152, 159 |
| 0.56 | 191, 201 |
| 1.10 | 200, 207 |

**Note:** Each concentration has two replicated velocity measurements.

## Analysis Objectives

1. Fit a simple linear regression model: `Velocity ~ Concentration`
2. Evaluate model fit using R² and residual analysis
3. Verify linear model assumptions
4. Make predictions for new concentrations

## 🛠 Technologies Used

- **Python 3.9+**
- Main libraries:
  - Python: `pandas`, `numpy`, `statsmodels`, `matplotlib`,

