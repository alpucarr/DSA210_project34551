# DSA210: 5 may deadline 

## 📌 Project Overview
This project investigates potential insider trading activities among US Congress members. By analyzing historical stock transactions, market trends, and relationship networks, this project aims to mathematically distinguish between lucky investments and information asymmetry.

## Key Features & Methodology
We employed a multi-layered data science pipeline to extract signal from noise:

1. **Anomaly Detection (Isolation Forest):** Filtered out routine trades to isolate massive, irregular transaction volumes.
2. **Relative Performance Analysis (Alpha):** Calculated the true success of trades by neutralizing the S&P 500 (SPY) market trend, exposing trades that massively outperformed or escaped market crashes.
3. **Event-Driven Timing:** Measured the exact days between a Senator's trade and a subsequent massive stock crash (e.g., escaping a 20% drop just 48 hours prior).
4. **Machine Learning Classifier (Random Forest):** Trained a predictive model to assign a "Suspicion Probability Score" (0-100%) to each transaction based on Alpha, Market Trend, and Transaction Type.
5. **Proxy Trading Analysis:** Cross-referenced highly suspicious trades with account ownership (Self vs. Spouse/Joint) to expose proxy trading.
6. **Statistical A/B Testing (SciPy):** Conducted Independent T-Tests to determine if Proxy accounts statistically outperformed Self accounts.
7. **Network Graph Visualization (NetworkX):** Generated a "Crime Board" topology connecting Senators, their Proxies, and the target assets.

## Major Findings
* **The PayPal Exodus:** The ML model assigned a **94% Suspicion Score** to Senator John Hickenlooper's massive dump of PYPL stock, occurring mere days before a historic market crash for the company. Senator Ron Wyden exhibited identical behavior.
* **The Proxy Shield:** A significant portion of >80% suspicious trades were executed via "Spouse" or "Joint" accounts, revealing a consistent pattern of bypassing direct ethical scrutiny.
* **Brazen Execution (P-Value: 0.4832):** Our T-Test revealed no statistically significant difference in returns between Self and Proxy accounts. Conclusion: Senators do not exclusively hide their highly profitable/suspicious trades in proxy accounts; they execute them openly under their own names with equal frequency.

## Technologies Used
* **Data Manipulation:** `pandas`, `numpy`
* **Financial Data Engine:** `yfinance`
* **Machine Learning:** `scikit-learn` (Random Forest Classifier)
* **Statistical Analysis:** `scipy`
* **Visualization:** `matplotlib`, `networkx`

## ⚙️ How to Run the Project
1. Clone the repository: `git clone [your-repo-link]`
2. Install required dependencies: 
   ```bash
   pip install pandas numpy yfinance scikit-learn scipy networkx matplotlib
