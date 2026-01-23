# ZIP-Level Home Price Forecasting & Risk Signal (CRISP-DM)

## 1. Business Understanding
Mortgage lenders face collateral risk when home values decline. Even short-term drops can impact LTV ratios, pricing, and portfolio exposure.

**Objective:**  
Forecast next-month ZIP-level home prices and generate a **material downside risk alert** (≥ −1% expected decline) to support underwriting and portfolio risk monitoring.

**Primary Stakeholders**
- Mortgage underwriters
- Portfolio risk managers
- Credit policy teams

**How They Use This**
- Adjust LTV thresholds or pricing
- Flag ZIP codes for enhanced review
- Monitor geographic concentration risk

---

## 2. Data Understanding
**Source:** Zillow-style monthly ZIP-level home values - [Kaggle](https://www.kaggle.com/datasets/zhenyufan/zillow-housing-price)  
**Granularity:** ZIP × Month  
**Target:** Next-month home value

The dataset provides long historical coverage, making it suitable for trend and seasonality modeling.

**Limitations**
- No property-level attributes
- Aggregated ZIP-level behavior may mask micro-trends
- External macro factors not included

---

## 3. Data Preparation
- Chronological sorting by ZIP and month
- Log transformations to stabilize variance
- Differencing to achieve stationarity where required
- Strict train / validation / test splits to prevent leakage

All preparation steps are fully reproducible and justified based on time-series best practices.

---

## 4. Modeling
**Baseline Model:** ARMA  
Chosen as a statistically grounded baseline capturing short-term dynamics.

**Model Iteration**
- ARMA (baseline)
- ARIMA (trend-aware)
- SARIMA / SARIMAX (seasonality-aware)

Each iteration is justified based on validation RMSE/MAE improvements.

---

## 5. Evaluation
**Metrics**
- RMSE: penalizes large forecast errors (tail risk)
- MAE: interpretable average error

**Process**
- Model selection using validation data
- Final evaluation on a true holdout test set
- Walk-forward forecasting to mirror real lender decision cycles

---

## 6. Deployment & Use
Outputs include:
- Next-month price forecast
- Binary downside-risk alert

These outputs can be operationalized into underwriting tools or portfolio dashboards.

---

## Repository Navigation
```
├── notebook.ipynb        # Full analysis notebook
├── notebook_updated.ipynb# Updated notebook (ARMA baseline, currency-aware plots)
├── presentation.pdf     # Executive presentation
├── data/                # Raw data
└── README.md
```

## Presentation
[Executive Presentation (PDF)](https://github.com/rahroy82/home_price_forecast/blob/main/presentation.pdf)

## Reproducibility
- Restart Kernel → Run All
- All results regenerate end-to-end

---

## Summary
This project demonstrates a **leakage-safe, business-aligned forecasting workflow** using CRISP-DM, designed for real-world mortgage risk management.