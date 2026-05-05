# Recession-Indicator-Analysis

## Overview
This project builds a logistic regression model to predict US recessions 
6 months in advance using macroeconomic indicators sourced from the 
Federal Reserve Economic Data (FRED) API. The model achieves an AUC of 
0.725 on out of sample data from 2010 onward.

## Research Question
Can macroeconomic indicators (the yield curve, unemployment, industrial production, 
and the federal funds rate) available in real time predict US recessions before they 
are officially declared?

## Key Finding
The model correctly distinguishes recession from non-recession periods 
72.5% of the time on held-out data. The yield curve inversion is
serving as the strongest predictive signal. Performance is stronger for 
severe recessions (1980s, 2008) compared to mild contractions, reflecting a 
known limitation of models trained on historically severe episodes.

## Data
- Source: Federal Reserve Economic Data (FRED) via fredapi
- Series used: Unemployment Rate (UNRATE), 10yr-2yr Treasury Spread 
  (T10Y2Y), Industrial Production Index (INDPRO), CPI Inflation 
  (CPIAUCSL), Federal Funds Rate (FEDFUNDS), NBER Recession Indicator 
  (USREC)
- Period: 1960–present

## Methodology
- 6-month lagged features to simulate real-time forecasting conditions
- Train/test split at 2010 to evaluate out-of-sample performance
- Logistic regression with standardized features
- SQLite database built in Python to store and query indicator data
- Evaluation metric: AUC-ROC

## Tools
- Python (pandas, fredapi, scikit-learn, matplotlib, seaborn)
- SQLite via sqlite3
- Jupyter Notebook

## Files
- analysis.ipynb - full notebook reproducing all results
- indicators_chart.png - macroeconomic indicators with recession shading
- recession_probability.png - predicted recession probability over time
- recession_indicators.db - SQLite database of all indicator data

## Limitations
- Small number of recession events limits model complexity
- Model performs better on severe recessions than mild contractions
- Yield curve data resampled from daily to monthly introduces noise
