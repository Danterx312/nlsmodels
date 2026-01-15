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
import numpy as np
import pandas as pd
import nlsmodels as nlm

# Create sample data
np.random.seed(42)
x = np.linspace(0, 10, 100)
y = 2.5 * np.exp(0.3 * x) + np.random.normal(0, 0.2, 100)
df = pd.DataFrame({'x': x, 'y': y})

# Fit nonlinear model
model = nlm.nonreg("y ~ a * exp(b * x)", df)
model.fit()

# View results
print(model.summary())
# Output:
# ============================================================
# NONLINEAR LEAST SQUARES REGRESSION
# ============================================================
# Dep. Variable: y           R-squared:    0.987
# Model:        NLS         Adj. R-squared: 0.987
# Method:       Least Squares F-statistic: 7452.34
# Date:         2024-01-15  Prob (F-statistic): 0.000
# Time:         14:30:22    Log-Likelihood: 45.231
# No. observations: 100     AIC: -86.462
# Df Residuals:     98      BIC: -81.251
# Df Model:          2
# ============================================================
#          coef   std err     t      P>|t|    [0.025   0.975]
# ------------------------------------------------------------
# a      2.501***  0.023   108.742   0.000    2.456    2.546
# b      0.298***  0.002   149.003   0.000    0.294    0.302
# ============================================================
