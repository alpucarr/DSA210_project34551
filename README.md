# Insider Trading Detection Among the U.S. Congress Members
**DSA 210 — Spring 2026**


Do U.S. senators trade stocks like they know something we don't? This project analyzes Senate STOCK Act disclosures to detect statistically abnormal trading patterns or potential insider trading, using market-adjusted returns, machine learning, and network analysis.





| # | Notebook | What it does |
|---|---|---|
| 1 | `EDA_and_Filtering.ipynb` | Exploratory analysis, data distributions, and baseline hypothesis tests. |
| 2 | `Data_prep_and_alpha.ipynb` | Data cleaning, dynamic 30-day alpha computation vs SPY, and feature engineering. |
| 3 | `machine_learning.ipynb` | Unsupervised anomaly detection (Isolation Forest), behavioral clustering (K-Means), and Random Forest classification. |
| 4 | `Network_and_Case_Studies.ipynb` | Tripartite transaction networks, quick-flip detection, and long-horizon co-investment (Syndicate) analysis via PageRank. |

## Data Sources

- **Kaggle (U.S. Senate Stock Trading Dataset)** — Raw congressional transaction disclosures (`senate_stock_disclosures.csv`)
- **Yahoo Finance API (`yfinance`)** — Historical equity prices & S&P 500 (SPY) benchmark data


## Setup

```bash
pip install -r requirements.txt
```

Place `senate_stock_disclosures.csv` in the project root, then run notebooks in order. Without the CSV, notebooks fall back to a synthetic dataset for pipeline validation.

---
