# Fraud_Detection

## Overview
This project focuses on detecting fraudulent financial transactions using machine learning techniques. The dataset consists of 50,000 transactions with multiple features related to senders, receivers, transaction types, and balances.

The project covers:
- Data cleaning and preparation, including handling missing values, outliers, and feature engineering.
- Model building using various classifiers, notably Random Forest and XGBoost.
- Evaluation of models using precision, recall, confusion matrices, and classification reports.
- Insights into key factors predicting fraudulent transactions.
- Recommendations for fraud prevention infrastructure and validation strategies.

## Dataset
The dataset used contains transactional data with the following:
- Transaction amounts
- Account balances
- Transaction types (e.g., TRANSFER, CASH_OUT)
- Flags indicating merchants and large transactions
- Sender and receiver IDs

Missing values were handled carefully, especially where merchant balances were zero but actually unknown.

- **[Dataset Link](https://www.kaggle.com/code/benroshan/transaction-fraud-detection/input)**

## Data Cleaning and Feature Engineering
- Zero merchant balances were treated as missing to prevent bias.
- Outliers in transaction amounts were flagged using binary indicators instead of removal, preserving important fraud signals.
- Features engineered included:
  - Amount mismatch flags (`amount_diff_orig`, `amount_diff_dest`)
  - Large transaction flags (`orig_flag`, `dest_flag`)
  - One-hot encoding of transaction types
  - Label encoding for sender and receiver IDs
  - Merchant account flags

## Models Used
- **Random Forest Classifier**: An ensemble of decision trees trained on random subsets of data and features.
- **XGBoost Classifier**: A gradient boosting approach building sequential trees to correct prior errors.
- Other baseline models like Logistic Regression, Naive Bayes, SVM, and Decision Trees were also explored.

The training data was balanced using SMOTE (Synthetic Minority Over-sampling Technique) to address class imbalance.

## Model Performance
- Random Forest achieved nearly perfect accuracy.
- XGBoost also showed excellent precision and recall, especially on the fraud class.
- Evaluation metrics focused on precision, recall, and F1-score for the minority fraud class due to the imbalance in data.
- Confusion matrices were used to visualize true vs predicted labels.

## Key Fraud Indicators
- Mismatches between transaction amount and balance changes.
- Transaction sequences involving TRANSFER followed by CASH_OUT.
- Large transaction amounts flagged by binary indicators.
- Accounts receiving funds from many unrelated senders.
- Merchant account flags helping to differentiate business transactions.

## Recommendations for Fraud Prevention
- Implement real-time transaction scoring with model predictions.
- Detect suspicious transaction sequences rapidly.
- Introduce limits and additional verifications for unusually large transactions.
- Monitor inflows to accounts from multiple unrelated senders.
- Handle missing or unknown merchant balances carefully.
- Maintain feedback loops with fraud analysts for model updates.
- Regular audits to detect data leakage or feature drift.

## How to Use This Project

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/fraud-detection.git
   cd fraud-detection
2. Install required libraries
   ```bash
   pip install -r requirements.txt
4. Run the notebook or script to train and evaluate models:
   ```bash
   jupyter notebook Fraud_Detection.ipynb

## Dependencies
- Python 3.7+
- pandas
- numpy
- scikit-learn
- imbalanced-learn
- xgboost
- matplotlib
- seaborn
- plotly
