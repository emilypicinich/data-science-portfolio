🛒 Predicting Purchase Conversion Through Behavioral Analytics

A machine learning project mapping the customer journey and identifying the behaviors that lead to purchases

📌 Overview

This project analyzes customer journey behavior to determine which user actions most strongly predict whether a visitor will complete a purchase. Using a dataset of 12,719 e-commerce sessions, the project investigates engagement patterns, funnel progression, and behavioral signals such as page activity, device usage, time spent on pages, and cart interactions.
Through exploratory analysis and machine learning modeling, Logistic Regression emerged as the most accurate and interpretable model for predicting purchase likelihood, achieving a ROC-AUC of 0.959 and an accuracy of 86.9%. These results provide actionable insights for optimizing e-commerce marketing, checkout design, and conversion strategies.

📁 Dataset

Source: Customer Journey – Click to Conversion (Kaggle, 2025)

Rows: 12,719 sessions

Columns: 10 behavioral variables

Key fields include:
- PageType — home, product_page, cart, checkout, confirmation
- DeviceType — desktop, tablet, mobile
- ReferralSource — Google, Email, Social Media, Direct
- ItemsInCart — count of items added
- TimeOnPage_seconds — duration spent on the page
- Country — 7 international markets
- Purchased — target variable (0 = no, 1 = yes)
- The dataset contained no missing values and no duplicates.

🧹 Data Cleaning & Preparation

✔️ Checked for nulls — none found

✔️ Confirmed no duplicate rows

✔️ Identified numeric vs. categorical features
- Numeric: TimeOnPage_seconds, ItemsInCart, Purchased
- Categorical: all other fields

✔️ Added engagement feature (optional)
- An engagement_score was engineered using normalized time/click/page variables.

✔️ Train/test split
- 80% training
- 20% testing
- Stratified by Purchased to maintain class balance

📊 Exploratory Data Analysis
1. Funnel Drop-Off
- The bar chart shows dramatic drop-off between home → product → cart → checkout → confirmation.
- This represents the biggest obstacle to conversions.
2. Time on Page

As shown in the histogram:
- Engagement time is evenly distributed
- No dominant viewing duration
- Suggests time alone does not predict purchases
3. Items in Cart

The bar chart shows:
- ~8,000 users added zero items
- Small group added 1–5 items
- This variable became the strongest indicator of buying intent
4. Purchases
- ~7,700 did not purchase vs. ~5,000 who did.
- A moderate class imbalance but still well-suited for modeling.
5. Categorical Behavior Patterns

Plots show:
- Device usage evenly split across desktop, tablet, mobile
- Country sessions evenly distributed
- Referral sources nearly balanced across Google, Email, Social Media, Direct
6. Statistical Findings

From Pearson correlation:
- ItemsInCart → r = 0.155, p < 0.001
- TimeOnPage_seconds → r ≈ 0, no significance

From Cramér’s V:
- PageType → 0.576 (strongest predictor)
- Country, ReferralSource → small but significant
- DeviceType → no effect

🤖 Modeling

Two classification models were trained:
1. Logistic Regression

Performance:
- ROC-AUC: 0.959
- Accuracy: 86.9%
- F1-score: 0.82
- Precision (buyers): 0.905
- Recall (buyers): 0.748
- Confusion matrix and ROC curve show excellent discrimination between buyers and non-buyers.
2. Random Forest Classifier

Performance:
- ROC-AUC: 0.858
- Lower recall (0.595) and weaker calibration
- Underperformed compared to Logistic Regression

🟩 Best Model

Logistic Regression was selected:
- Higher accuracy
- Best recall/precision trade-off
- More interpretable for business teams
- Most stable with categorical and numerical mix

🧠 Key Insights

Based on EDA + modeling results:
- Adding items to the cart is the strongest behavioral predictor of purchase.
- Time on page does not matter — length of session ≠ buying intent.
- PageType is the most powerful categorical variable, as deeper funnel stages massively increase conversion likelihood.
- Device type has no relationship with buying behavior.
- A simple, interpretable model (Logistic Regression) outperformed Random Forest, proving that complex models aren’t always better.

💼 Business Implications

As summarized in the slides:
- Encourage users to add anything to their cart early (prompts, small incentives).
- Reduce friction between product viewing → cart → checkout.
- Personalize messaging for high-intent users deeper in the funnel.
- Regularly measure and optimize funnel drop-off at every stage.

🚀 Future Extensions
- Expand to churn or subscription retention prediction
- Integrate real-time scoring for dynamic marketing
- Build a dashboard showing funnel health and intent signals
- Incorporate session-level clickstream and landing-page data
