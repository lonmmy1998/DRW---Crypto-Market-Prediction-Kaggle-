#  DRW Crypto Market Prediction (Kaggle)

This repository contains our complete end-to-end modeling pipeline for the [DRW Crypto Market Prediction](https://www.kaggle.com/competitions/drw-crypto-market-prediction) competition on Kaggle. The goal is to forecast short-term price movement of various cryptocurrencies using high-frequency market data.

custom feature engineering, time-based analysis, PCA dimensionality reduction, and final modeling with LightGBM.

<br>

## 📌 Project Overview

- **Competition Goal**: Predict future crypto price movement using historical market data.
- **Data Source**: `train.parquet` and `test.parquet` files provided by Kaggle.
- **Key Approach**: EDA → Feature Engineering → Feature Selection → PCA → Modeling → Submission

<br>

## 📓 Notebook Summary

All 9 modeling stages — including EDA, feature creation, PCA, and submission — are implemented in a **single Kaggle Notebook**.

| Part | Description |
|------|-------------|
| 1 | Data Loading & Cleaning |
| 2 | Baseline Modeling with LightGBM |
| 3 | Custom Features & Domain Knowledge |
| 4 | Integration of Anonymous Features |
| 5 | Lag & Rolling Time Features |
| 6 | Feature Importance Visualization |
| 7 | Feature Selection by Importance |
| 8 | PCA on X-features |
| 9 | Final Model Training & Submission |

🔗 **Kaggle Notebook**: [View Full Pipeline on Kaggle](https://www.kaggle.com/code/lonmmylai/drw-crypto-pipeline)  
📁 GitHub Notebook: [`drw_crypto_pipeline.ipynb`](./files/drw_crypto_pipeline.ipynb)



<br>

## 📈 Final Feature List

We used a total of **17 final features**, combining custom logic and PCA components:

| Category | Features |
|----------|----------|
| Ratio & Domain Features | `buy_ratio`, `spread`, `volume_change` |
| Time-based Features | `buy_qty_lag_1`, `buy_qty_lag_5`, `buy_qty_lag_10`, `buy_qty_ma_3`, `buy_qty_ma_5`, `buy_qty_ma_10`, `buy_qty_ma_15`, `volume_lag_5`, `volume_ma_10` |
| PCA Components | `PCA1`, `PCA2`, `PCA3`, `PCA4`, `PCA5` |

> PCA was applied to the anonymized `X1 ~ X30` features after standardization.

<br>

## 📌 Key Insights

- **Lag & Rolling mean features** helped capture market microstructure trends.
- **Anonymous features (X1~X30)** were effectively reduced using PCA.
- **Feature filtering based on LightGBM importance** removed noise and improved model consistency.
- Final predictions were generated using a 17-feature LightGBM model.

<br>

## 📌 Final Submission

- LightGBM trained on full dataset with 17 features.
- Predictions generated on test set and saved as `submission.csv`.
- Final result ready for submission to Kaggle.

<br>

## 📌 Future Work

- Add `asset_id`-based segmentation or embeddings.
- Apply SHAP for deeper interpretability.
- Use TimeSeriesSplit or walk-forward validation.
- Try advanced architectures (e.g. Transformer or TabNet).

---

This project demonstrates an effective pipeline for high-frequency financial prediction with interpretability and modeling best practices.

