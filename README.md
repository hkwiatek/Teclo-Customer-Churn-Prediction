# Teclo-Customer-Churn-Prediction
Project for IBM data

## Project Overview
Customer retention is one of the most critical KPIs for any telecommunications company, as acquiring a new customer is significantly more expensive than retaining an existing one. 

This project goes beyond a simple predictive model. It focuses on identifying the root causes of customer churn using the **IBM Telco Customer Churn dataset** and deploying optimized Machine Learning algorithms to proactively flag at-risk customers while maximizing business ROI.

##  Key Highlights & Advanced Practices
What makes this project stand out from standard ML tutorials?

* **Preventing Data Leakage:** The dataset was strictly split into training and testing sets (`train_test_split`) *before* applying One-Hot Encoding to ensure the model was evaluated on completely unseen data.
* **Handling Class Imbalance:** Instead of using synthetic data generation, the severe class imbalance was handled natively using `class_weight='balanced'` in Random Forest and dynamic `scale_pos_weight` calculation in XGBoost.
* **Preventing Overfitting:** Implemented the `early_stopping_rounds` mechanism with an evaluation set in XGBoost to find the optimal number of trees dynamically.
* **Business-Driven Metrics:** Shifted focus from standard Accuracy to **Recall (Sensitivity)** and managed the **Precision-Recall Trade-off**. The model was tuned to capture 81% of actual churners, accepting a higher False Positive rate because the cost of a retention discount is lower than the cost of losing a customer.

## Tech Stack
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn (RandomForestClassifier), XGBoost (XGBClassifier)

## Exploratory Data Analysis (EDA) Insights
Extensive EDA revealed several critical business insights:
1. **The Contract Trap:** Customers on *Month-to-month* contracts have a massive churn rate compared to those on 1-year or 2-year contracts.
2. **The Fiber Optic Paradox:** Paradoxically, the premium *Fiber optic* service generates the highest churn rate (>40%), indicating potential technical issues or aggressive local competition.
3. **Crucial First Months:** The highest risk of losing a customer occurs during the first few months of tenure. 

## Model Performance
Two models were trained and compared:
1. **Random Forest (Baseline):** Achieved good overall accuracy but struggled to identify the minority class (Recall for churners: ~45%).
2. **XGBoost (Optimized):** By applying `scale_pos_weight` and tuning hyperparameters, the model's ability to identify churning customers skyrocketed (**Recall increased to 81%**), making it a highly effective tool for the retention team.

## Final Business Recommendations
Based on the *Feature Importance* extracted from the models, the following strategic actions are recommended:
* **Incentivize Long-Term Contracts:** Shift marketing budgets to offer heavy discounts for the first month if a user commits to a 12- or 24-month contract.
* **Proactive Engagement:** Implement a check-in call or loyalty discount for new customers with high `MonthlyCharges` around their 3rd month.
* **Technical Audit:** Conduct an urgent audit of the *Fiber optic* infrastructure to investigate the root cause of the high cancellation rates.
