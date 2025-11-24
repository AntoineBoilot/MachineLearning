# Cross-Sectional Equity Return Prediction with Gradient Boosting

## Overview

This project applies supervised Machine Learning to predict next-month cross-sectional equity returns and builds a long-short portfolio based on the model's predictions.

I use daily price data for a universe of liquid stocks, build simple factor-like features (momentum, volatility, etc.), train a Gradient Boosting model, and backtest a market-neutral strategy that goes long the top predicted names and short the bottom ones.

The goal is not to produce a production-ready trading system, but to show the full research pipeline:
data → features → model → backtest → performance analysis.

## Methodology

1. Data
   • Daily close prices for a fixed universe of stocks  
   • Monthly returns and realised volatility  

2. Features
   • 1M, 3M, 6M past returns  
   • 1M and 3M realised volatility  
   • Simple technical indicators  

3. Target
   • Next 1M forward return per stock  

4. Model
   • GradientBoostingRegressor (scikit-learn)  
   • Train / test split based on time  
   • Evaluation using MSE and cross-sectional correlation (Information Coefficient)  

5. Strategy
   • Each month, rank stocks by predicted return  
   • Go long the top X per cent and short the bottom X per cent  
   • Equal weights, no transaction costs (for simplicity)  

## Results

• Positive Information Coefficient on the test period  
• Long-short strategy with positive Sharpe ratio and limited drawdowns  

Plots and detailed results are available in the `notebooks` folder.

## How to run

```bash
pip install -r requirements.txt

# Example usage (data preparation, model training, backtest)
python src/data_download.py
python src/run_experiment.py
