
# ZIP-Level Home Price Forecasting & Risk Signal

## Overview
This project builds a **1-month-ahead ZIP-level home price forecast** and converts it into a **downside-risk alert** designed for mortgage lenders.

The objective is not to predict prices perfectly, but to **surface early warning signals** that help lenders manage collateral risk in underwriting and portfolio monitoring.

---

## Business Problem
Mortgage lenders are exposed to changes in collateral value.  
Even small short-term declines can materially impact:

- Loan-to-Value (LTV) ratios  
- Pricing and approval decisions  
- Portfolio-level geographic exposure  

This project provides a **consistent, ZIP-level signal** that flags areas requiring closer review *before* risk materializes.

---

## Key Outputs
1. **Next-Month Price Forecast**  
   Estimated home value for the coming month by ZIP code.

2. **Material Decline Alert**  
   A binary risk signal triggered when the forecasted next-month return is ≤ **−1%**, emphasizing downside protection.

---

## Modeling Approach (Business-Aligned Summary)
- Start with a simple baseline ("next month = last month")
- Incrementally add structure only when it improves validation performance:
  - Short-term dynamics
  - Trend awareness
  - Seasonal market behavior
- Select models using **validation RMSE / MAE**
- Perform final evaluation on a **true holdout test set** using rolling one-step forecasts

This mirrors how lenders reassess risk **month-by-month** in practice.

---

## Why This Signal Is Trustworthy
- Chronological train / validation / test splits  
- No future data used during training or model selection  
- Walk-forward evaluation that mirrors real decision cycles  
- Final performance measured on unseen historical periods  

---

## Stakeholder Use Cases
- **Underwriting:** adjust pricing or LTV thresholds where downside risk is elevated  
- **Portfolio Monitoring:** scan ZIPs and prioritize geographic reviews  
- **Risk Management:** add an objective, data-driven early-warning layer  

---

## Dataset
The home price data used in this project comes from Zillow-style monthly ZIP-level home values:

- **Source:** Kaggle  
- **Dataset:** Zillow Housing Prices  
- **Link:** https://www.kaggle.com/datasets/zhenyufan/zillow-housing-price

The data provides long-horizon monthly price histories suitable for trend and seasonal analysis.

---

## Repository Structure
```
├── notebook.ipynb        # Full Jupyter notebook (code + analysis)
├── notebook.pdf         # Rendered, shareable notebook output
├── presentation.pdf     # Static presentation (PDF)
├── presentation.pptx    # Editable presentation deck
├── zillow_data.csv      # ZIP-level monthly home price data
└── ~$presentation.pptx  # Temporary PowerPoint lock file
```

---

## Reproducibility Notes
- Expected data file: `zillow_data.csv`  
- Run order: **Restart Kernel → Run All**  
- Notebook is designed to run end-to-end without manual intervention  

---

## Future Enhancements
- Add macroeconomic drivers (interest rates, unemployment)
- Incorporate loan-level attributes (LTV, DTI)
- Calibrate alert thresholds to portfolio risk tolerance
- Track signal performance over time as a risk control

---

## Summary
This project demonstrates a **leakage-safe, business-aligned time-series forecasting system** that scales from individual ZIP analysis to portfolio-level risk monitoring for mortgage lenders.
