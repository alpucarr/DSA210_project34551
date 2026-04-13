# DSA210_project34551
dsa210 project of Alp Uçar

## Analysis of US Congress Stock Trades 
This project aims to investigate potential information asymmetry in the stock market transactions of US Congress members.

For the first milestone of 14 April, I have completed the following:
- **Data Collection:** Processed the Senate stock disclosure dataset.
- **EDA:** Performed exploratory data analysis to identify the most active senators and frequently traded stocks.
- **Hypothesis Testing:** Conducted a t-test to compare the average transaction volumes between "Purchase" and "Sale" operations.

## How to Run
1. Make sure you have the dependencies: `pip install -r requirements.txt`
2. Open the `.ipynb` file in a Jupyter environment.
3. Run the cells in order to see the analysis and plots.

4. ## Future Work & Data Enrichment
This is an initial exploratory phase. In the upcoming milestones, I plan to:
- **Integrate Yahoo Finance (yfinance) API:** To fetch historical price data and calculate actual returns (ROI) for each trade.
- **Add Political Affiliation:** Cross-referencing senator names with political party data to analyze potential partisan differences in trading success.
- **Benchmark Analysis:** Comparing individual performances against the S&P 500 index to detect "Alpha" or informational advantages.
