
## Overview of AI Collaboration

In my project the AI was strictly employed as an advanced pair programming assistant, a syntax debugger, and a sounding board for data science methodologies. The conceptual direction, hypothesis formulation, and final conclusions were entirely comes from me.

## Chronological Breakdown of Prompts and Generated Outputs

### Phase 1: Data Enrichment & Alpha Calculation (Relative Performance)
**My Intent:** To move beyond simple ROI and calculate true "Information Asymmetry" by comparing a Senator's trade performance against the broader market (S&P 500) over a 30-day window.
*   **Prompt/Direction provided to AI:** "I have a dataset of congressional stock trades. I need to calculate the 'Alpha' for each trade. Write a Python script using the `yfinance` library that fetches the 30-day historical performance of the specific stock ticker starting from the transaction date, fetches the S&P 500 (SPY) performance for the exact same timeframe, and calculates the difference (Alpha). Handle timezone inconsistencies and missing ticker errors."
*   **AI Output & Contribution:** The LLM generated a robust iterative function that utilized `yf.Ticker().history()`. It successfully handled `DatetimeIndex` timezone stripping and calculated `alpha = ticker_perf - spy_perf`. 
*   **My Review:** Integrated the generated function into the main DataFrame, effectively creating the `alpha_table` which served as the foundation for all subsequent machine learning.

### Phase 2: Event-Driven Timing (The Earnings "Guillotine" Test)
**My Intent:** To determine if highly profitable trades were executed suspiciously close to unreleased corporate earnings reports.
*   **Prompt/Direction provided to AI:** "Write a script to cross-reference our highly suspicious trades with historical earnings dates. Use `yfinance` to find the very next earnings call date after a Senator's transaction date. Calculate the days remaining until the news broke."
*   **AI Output & Contribution:** Generated a loop using `stock.get_earnings_dates()`, filtering for `future_earnings.index > txn_date`. 
*   **My Decision:** The script executed correctly, but revealed limitations in the free tier of the `yfinance` API regarding historical earnings data. I instructed the LLM to abandon this approach and pivot to "Disclosure Delay" and "Account Ownership" analysis.

### Phase 3: Machine Learning & Predictive Modeling (Random Forest)
**My Intent:** To build an algorithmic system that objectively flags "Insider Trading" based on market parameters, removing human bias.
*   **Prompt/Direction provided to AI:** "Let's build a Predictive ML Model. Create a target variable `Is_Suspicious` where 1 equals a 'Sale' followed by a massive negative Alpha, or a 'Purchase' followed by a massive positive Alpha. Then, train a `RandomForestClassifier` from `scikit-learn` using features: `Is_Buy`, `Market_Trend`, `30_day_perf`, and `alpha`. Output the feature importances and the top 10 transactions with the highest probability scores."
*   **AI Output & Contribution:** 
    *   Wrote the labeling function `is_suspicious(row)`.
    *   Structured the `train_test_split`.
    *   Implemented the ML model, crucially adding `class_weight='balanced'` to prevent the model from ignoring the minority class (suspicious trades).
    *   Generated code to extract `model.predict_proba()` and `model.feature_importances_`.
*   **Results Yielded:** The model successfully flagged Senator Hickenlooper and Tuberville with >94% suspicion scores.

### Phase 4: Proxy Trading Discovery & Statistical Significance (A/B Testing)
**My Intent:** To investigate the mechanism of these suspicious trades. Do Senators hide their most corrupt trades behind family members?
*   **Prompt/Direction provided to AI:** "Filter the original dataset for the trades the ML model scored >80% suspicious. Check the `owner` column to see if they were executed by 'Self', 'Spouse', or 'Joint'. Then, write an Independent T-Test using `scipy.stats` to mathematically prove if 'Proxy' accounts (Spouse/Joint) yield a statistically higher Alpha than 'Self' accounts."
*   **AI Output & Contribution:** 
    *   Created the proxy filtering logic.
    *   Generated the code for `stats.ttest_ind(proxy_returns, self_returns, equal_var=False)`.
*   **Results Yielded:** The outputted P-Value was 0.4832. This led to the profound project conclusion that there is no statistical difference; Senators are brazenly executing highly suspicious trades openly under their own names just as frequently as proxy accounts.

### Phase 5: Network Topology Visualization (The "Crime Board")
**My Intent:** To create a compelling, report-ready visual representation of the proxy trading network.
*   **Prompt/Direction provided to AI:** "Using Python, create a 'Crime Board' network graph. Connect the Senator nodes to their Account Ownership nodes, and connect those to the Target Stock Tickers. Use `NetworkX` and `Matplotlib`. Node colors should differentiate the entity type, and edge thickness should be dictated by the ML suspicion score."
*   **AI Output & Contribution:** Provided the complete topological layout code. Assisted in debugging MacOS environment pathing errors by suggesting `%pip install networkx` specific to the Jupyter kernel architecture. The graph compiled successfully, visually mapping the corruption network.

---
**Declaration:** All code generated by the AI was thoroughly read, conceptually understood, and integrated manually by the student. The AI served as an execution tool for my analytical hypotheses.
