# PCA + Custom Feature Engineering for Crypto Market Forecasting

This notebook is my first submission to a [Kaggle Playground Competition](https://www.kaggle.com/competitions/drw-crypto-market-prediction), focused on predicting crypto market behavior. It highlights my practical skills in:

- Custom feature engineering (domain-informed)
- Dimensionality reduction using PCA
- LightGBM regression modeling

While the current result is a baseline, the notebook reflects my efforts to explore and apply effective preprocessing techniques.

---

## 📁 Notebook Overview

The core notebook includes:

1. **Data Loading**
   - Uses `polars` and `pandas` to efficiently load and manipulate large `.parquet` files.

2. **Feature Engineering**
   - Introduced custom features such as:
     - `buy_ratio` = `buy_qty / (buy_qty + sell_qty)`
     - `spread` = `ask_qty - bid_qty`
     - `volume_change` = Percentage change of volume
     - Multiple lag and rolling mean features

3. **PCA Transformation**
   - Applied PCA to `X1 ~ X30` anonymous features
   - Retained the **top 5 principal components** for better model generalization

4. **Model Training**
   - Used `LightGBM Regressor` with time series split cross-validation
   - Evaluated performance based on Pearson correlation

5. **Submission**
   - Generated a `.csv` submission compatible with the competition requirements

---

##  Final Feature Set (17 features)

| Category              | Features                                                                 |
|-----------------------|--------------------------------------------------------------------------|
| Custom Engineered     | `buy_ratio`, `spread`, `volume_change`                                   |
| Lag & Rolling Stats   | `buy_qty_lag_1`, `buy_qty_lag_5`, `buy_qty_lag_10`, `buy_qty_ma_3`, `buy_qty_ma_5`, `buy_qty_ma_10`, `buy_qty_ma_15`, `volume_lag_5`, `volume_ma_10` |
| PCA Components        | `PCA_1`, `PCA_2`, `PCA_3`, `PCA_4`, `PCA_5`                               |

---

## Notes

- The current score is preliminary and serves as a baseline.
- This project focuses on demonstrating **data preprocessing and feature thinking**, not leaderboard performance.
- Further steps may include:
  - Time-aware rolling windows
  - Ensemble models
  - Feature selection or SHAP analysis

---

## 🧑‍💻 About Me

I am a graduate student transitioning into machine learning engineering. This is part of my portfolio to showcase hands-on skills in:

- Feature engineering
- Dimensionality reduction
- Model evaluation and deployment

➡️ Feel free to check out other ML projects on my GitHub!

