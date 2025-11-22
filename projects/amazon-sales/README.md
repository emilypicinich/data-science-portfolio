📦 Amazon Sales Trends & Consumer Behavior Analysis

A 42K-product study of pricing, promotions, ratings, badges, and purchase behavior on Amazon

📌 Overview

This project analyzes 42,675 Amazon product listings to identify what drives consumer purchases and long-term engagement. The dataset includes detailed product attributes, ratings, reviews, pricing, badges, coupons, sustainability labels, sponsorship status, and recent sales ("bought in last month").

Using exploratory data analysis, hypothesis testing, and machine learning models, the project evaluates how pricing, promotions, visibility badges, and product attributes influence sales. It also develops predictive models to estimate purchasing volume.

The full analysis is documented in the Jupyter notebook, amazon-sales, and summarized in the slide deck, amazon-sales-slides.

📁 Dataset

Source: Kaggle (Amazon Product Sales Dataset, 2025 release)

- Rows: ~42,675
- Columns: 20+, including:
  - Product metadata: title, URLs, category proxies, sustainability badges
  - Engagement metrics: ratings, number_of_reviews, bought_in_last_month
  - Pricing: listed_price, price_on_variant, discounted price
  - Promotions: sponsorship status, coupons, Best Seller badges, Amazon’s Choice

Key characteristics:
- Ratings are stored as strings and cleaned into floats
- Review counts contain commas and require numeric conversion
- Purchase counts contain textual variants (e.g., "10K+") and require extraction + scaling
- Many price fields contain currency symbols requiring parsing
- Some features (sustainability badges, coupons, Best Seller categories) are sparse and imbalanced

🧹 Data Cleaning & Feature Engineering
- Ratings → cleaned from text ("4.6 out of 5 stars") to float
- Number of reviews → stripped commas → integer
- Bought in last month → extracted numeric value + K/M/B suffix scaling
- Discounted price + listed price → extracted numeric currency values
- Coupon indicator → converted into Boolean (has_coupon)
- Sustainability badges → collapsed into "No Badge" vs specific badge labels
- Best Seller categories → left as categorical strings for analysis
- Outliers → retained due to business relevance (e.g., high-price luxury electronics)

Missing values were imputed, but key variables were handled conservatively to preserve distribution integrity.

📊 Exploratory Data Analysis

⭐ Ratings
- Ratings cluster tightly between 4.0 and 5.0, with a spike near 4.5–4.8.
- Negative ratings are extremely rare → ratings are not useful as a prediction target.

📝 Number of Reviews
- Review counts range from 1 to 865,598, but most products fall between 10–10,000, displaying a clear winner-takes-most dynamic.

🛒 Purchases ("bought in last month")
- Distribution is extremely skewed, from near-zero up to 100,000+.
- Substantive log-log relationships exist between reviews ↔ purchases (Spearman r = 0.593).

💲 Pricing
- Most items are priced between $10–$100, with a long right tail exceeding $5,000.
- Log transformation produces a cleaner distribution.

🏷️ Promotions & Badges
- Sponsored products account for only ~7K listings
- Coupons are extremely rare (4.6%)
- Sustainability badges appear in <10% of products
- Best Seller badges are rare but extremely influential when present

🔍 Statistical Tests & Behavioral Insights

▶ Sponsorship
- Sponsored products sell far more in the last month (Cohen’s d = 1.22)
- Only small differences in reviews (d = 0.08)
- Sponsored items have slightly lower ratings (d = –0.064)
- Interpretation: Sponsorship boosts visibility and purchases short-term, but may reduce perceived quality.

▶ Sustainability Badges
- No meaningful effect on purchases (Cohen’s d ≈ 0.00)
- Moderate effect on review counts (Cohen’s d ≈ 0.42)
- Very small effect on ratings (Cohen’s d ≈ 0.15)
- Interpretation: Badges increase trust and long-term engagement, not sales.

▶ Coupon Availability
- Median purchases:
  - Coupon: 50
  - No coupon: 100
- Cohen’s d (log scale) = 0.21 (small effect)
- Interpretation: Coupons do NOT consistently boost sales; non-coupon items often perform better.

▶ Best Seller Badges
- Strong boosts in both purchases and reviews for Best Seller items
- Median purchases for Best Sellers = 5,000–6,000
- No Badge median = 100
- Best Seller = dominant credibility marker

📈 Modeling

🔹 Linear Regression
- R² = 0.10
- RMSE ≈ 5,478
- Conclusion: Linear models cannot capture nonlinear consumer behavior.

🔹 Random Forest Regressor
- Train R² = 0.97, Test R² = 0.91
- RMSE ≈ 1,699
- Top Predictors (Feature Importance):
  - Current/discounted price
  - Listed price
  - Ratings
  - Sponsorship & Best Seller categories
- Interpretation: Pricing is the strongest driver of purchases.

🔹 Gradient Boosting
- Train R² = 0.86, Test R² = 0.82
- More stable, less overfitting than Random Forest
- Lower raw accuracy
- Offers robustness when stability > accuracy.

🧠 Key Insights
- Pricing dominates as the strongest driver of sales.
- Sponsorship drives short-term purchases but slightly reduces ratings.
- Sustainability badges influence reviews, not sales.
- Coupons are not reliable sales boosters.
- Best Seller badges are the most powerful credibility signal.
- Ratings are too skewed to be a meaningful prediction target.
- Non-linear models (e.g., Random Forest) outperform linear ones dramatically.

🚀 Future Improvements
- Build category-specific predictive models
- Add time-series analysis if future snapshots are available
- Run SHAP explainability on tree models
- Explore price elasticity modeling per category
- Build a Tableau or Streamlit dashboard for executive insights
