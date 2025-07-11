# June 2025 Stock Data Analysis 📈

This repository contains an in-depth analysis of stock market data from June 2025, covering data exploration, relationships between financial indicators, and predictive modeling using machine learning algorithms.

## Dataset Features

The dataset includes the following features:

  * **Date**: Trading date in YYYY-MM-DD format.
  * **Ticker**: Stock symbol identifier.
  * **Open**: Opening price for the trading day.
  * **Close**: Closing price for the trading day.
  * **High**: Highest price reached during the day.
  * **Low**: Lowest price reached during the day.
  * **Volume**: Number of shares traded.
  * **Market Cap**: Total market capitalization.
  * **PE Ratio**: Price-to-Earnings ratio for valuation analysis.
  * **Dividend Yield**: Annual dividend as a percentage of stock price.
  * **EPS**: Earnings Per Share.
  * **52 Week High**: Highest price in the past 52 weeks.
  * **52 Week Low**: Lowest price in the past 52 weeks.

-----

## Project Structure

  * `stock_market_june2025.csv`: The original dataset used for the analysis.
  * `stock_analysis.ipynb` (or similar): A Jupyter Notebook containing all the code for analysis, visualization, and modeling.

-----

## Installation

Ensure you have Python 3.x installed. You can install all the necessary libraries using pip:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```

-----

## Analysis & Findings

### Initial Data Exploration

The dataset is clean, with 2550 entries and 13 columns, and no missing values. The `Date` column was converted to datetime format for time-based analysis.

### Stock Price and Trading Volume Relationship

  * **Open prices** showed market volatility throughout June 2025, with wider "blur" areas indicating significant price variations among stocks.
  * Most transactions occurred at **low volumes**. However, there were **extreme trading volume spikes in mid-June** (around June 9, 2025) affecting multiple stocks simultaneously.
  * The **correlation between closing price (`Close`) and volume (`Volume`) was very weak (0.06)**. This suggests that volume spikes don't always mean price increases; market sentiment (positive or negative) can be the primary driver behind intense trading activity. This market appears less susceptible to single-volume manipulation.

### Financial Characteristics & Company Size

  * **PE Ratio Distribution**: Most stocks had a PE Ratio between 15-35 (healthy valuation), peaking at 20-25. Some stocks with high PEs (40-45) might be anticipating high future growth or be considered overvalued.
  * **Dividend Yield Distribution**: There were two main groups at 2-3% and 4-5%, as well as a peak at 0% (no dividends paid).
  * **Market Cap Distribution**: The dataset is dominated by small or nascent companies (low capitalization), but also includes a few "giant" companies with very large market caps, consistent with general stock market patterns.
  * **Inter-indicator Correlations**:
      * **PE Ratio vs. Dividend Yield**: There's **no clear linear relationship**. Stock valuation does not directly determine the dividend paid.
      * **Market Cap vs. EPS**: A **positive relationship**. Larger companies tend to have higher Earnings Per Share (EPS) due to economies of scale.

-----

## Predictive Modeling

Two powerful regression models, **Random Forest** and **XGBoost**, were used to predict stock **Closing Prices (`Close`)**.

### Data Preparation

  * Target feature: `Close`
  * Predictor features: `Open`, `High`, `Low`, `Volume`, `Market Cap`, `PE Ratio`, `Dividend Yield`, `EPS`, `52 Week High`, `52 Week Low`, and `Ticker` (after one-hot encoding).
  * Data was split 80% for training and 20% for testing.

### Model Evaluation Results

| Model         | MSE   | RMSE | R-squared |
| :------------ | :---- | :--- | :-------- |
| Random Forest | 6.15  | 2.48 | 1.00      |
| XGBoost       | 41.90 | 6.47 | 0.99      |

### Model Comparison

**Random Forest** showed **exceptionally strong performance**, with an R-squared near 1.00 and very low errors. This indicates that the model was able to explain almost all the variance in actual closing prices and provided highly accurate predictions.

**XGBoost** also performed **very robustly**, with an R-squared of 0.99. While slightly below Random Forest in these metrics (higher MSE and RMSE), XGBoost still demonstrated excellent predictive capability.

Visually, both models produced predictions that clustered very closely around the perfect line ($y=x$), confirming their high accuracy.

-----

## Conclusion

This analysis confirms that:

1.  **Stock closing prices in June 2025 can be predicted with very high accuracy** using the available features.
2.  **Random Forest is marginally superior** in this scenario based on numerical metrics, though XGBoost is a highly competitive alternative.
3.  It's crucial to note that **trading volume is not always linearly correlated with price changes**, suggesting that market sentiment plays a significant role.
4.  Investors can leverage the understanding that **stock valuation (PE Ratio) doesn't always correlate with dividends**, and that **larger companies tend to have higher EPS**.

The developed predictive models can serve as valuable tools for investors to make more informed decisions in the stock market.
