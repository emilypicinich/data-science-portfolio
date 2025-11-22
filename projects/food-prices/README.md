🥘 Pakistan Food Prices Analysis & Market Segmentation (2025)

📌 Overview

This project analyzes 1,100 food price observations across 10 major Pakistani cities, covering 35 unique food items across 9 categories, to understand how prices vary geographically and across product types. The analysis explores distribution patterns, price drivers, market segmentation, and predictive modeling to explain and visualize inflation-related trends in 2025.
Using statistical exploration, clustering, and machine learning models, the project reveals strong item- and category-driven price structures, major differences across cities, and clear segmentation in Pakistan’s food markets.

📁 Dataset

Source: Pakistan Food Prices 2025 (local market surveys, retailer listings, wholesale markets).

Dataset includes the following columns:
- Item – 35 food items
- Category – 9 food categories (e.g., Dairy, Meat, Pulses, Fruit)
- City – 10 major markets
- Price_per_Kg – numeric target variable
- Month – 12-month coverage
- Source – 5 reporting sources
- All 1,100 rows contained no missing values and no duplicates.

🧹 Data Preparation

✓ Validation Checks
- Confirmed all columns had valid values
- Verified consistent formatting of categorical fields
- Identified 35 items, 9 categories, 10 cities, 12 months

✓ Encoding
- Categorical fields (Item, Category, City, Month, Source) were encoded with:
-- OneHotEncoder for regression models
-- Category codes for correlation analysis

✓ Aggregations

Created grouped datasets for:
- Average price by city
- Average price by category
- Item-level averages

📊 Exploratory Data Analysis

Distribution of Food Prices
- The histogram shows a right-skewed distribution with strong clustering between 100–300 PKR/kg and a long tail stretching above 1,000 PKR/kg for premium items like mutton and pomfret fish. 

Average Price by City

The bar chart reveals substantial geographic variation:
- Highest-cost markets: Karachi, Hyderabad, Rawalpindi, Quetta
- Lowest-cost markets: Peshawar, Multan
- These differences suggest localized supply chain and demand pressures. 

Average Price by Category

From the category bar chart:
- Most expensive: Beverages (tea), Meat, Oil
- Mid-range: Condiments, Dairy
- Least expensive: Pulses, Fruit, Grain, Vegetables
- This reflects the cost burden of protein-rich and imported items. 

Item-Level Price Structure

The long bar chart of item averages clearly separates items into three price tiers:
- Premium: Mutton, Pomfret, Ghee, Tea, Cheese
- Mid-price: Spices, chicken, fish (Rohu), premium grains
- Low-cost staples: Vegetables, fruits, grains, pulses

Price Distribution by Category
- The boxplot highlights wide spreads in high-cost categories (meat, oil, condiments) and tight, low-cost distributions in vegetables and grains. 

Monthly Patterns
- The monthly bar chart shows short-term fluctuations but no strong seasonal cycles, as prices peak in June but stabilize in the second half of the year. 

📈 Correlation Analysis

A Spearman correlation heatmap shows:
- Weak correlations for City, Month, Source
- Moderate negative correlations between price and item/category codes
- Conclusion: Price is primarily driven by what the item is, not where/when it was recorded.

🤖 Predictive Modeling
1. Linear Regression
- RMSE: 37.14
- R²: 0.989
- The model explains nearly all variance due to the strong price structure encoded in items and categories.

2. Random Forest Regressor
- RMSE: 16.12
- R²: 0.998
- Best performance, capturing complex nonlinear interactions between food types and prices.

Feature Importance

Top predictors include:
- Category_Meat
- Item_Ghee
- Item_Cheese (Local)
- Item_Spices (Mixed)
- Item_Tea (Loose)
- These confirm that premium, high-cost items exert the strongest influence on price.

🗺️ Clustering & Market Segmentation

Item Clustering (K-Means)
- Cluster 0: Low-cost staples (vegetables, pulses, basic grains)
- Cluster 1: High-cost premium items (mutton, ghee, tea, pomfret)
- Cluster 2: Mid-cost essentials (chicken, spices, Rohu fish)

City Clustering (K-Means + PCA)
- Cluster 0: Lowest-cost cities (Hyderabad, Quetta, Sialkot)
- Cluster 1: High-cost markets (Karachi, Multan)
- Cluster 2: Mid-range urban centers (Islamabad, Lahore, Faisalabad, Rawalpindi)
- Cluster 3: Unique outlier (Peshawar)

Heatmap & Radar Chart
- Visualizations compare category-level profiles across clusters, confirming large differences in affordability for beverages, grains, vegetables, oil, and premium proteins.

🧠 Key Insights
- Food prices in Pakistan exhibit strong category and item-driven variation.
- Meat, tea, oil, and dairy items dominate the high-price tier.
- Cities show clear economic segmentation, enabling actionable market grouping.
- Predictive models reveal that item type alone can explain nearly all price variation.
- Premium items have a disproportionate impact on household food budgets.

💼 Business & Policy Implications
- Improve price transparency in high-cost cities.
- Monitor inflation impacts in premium categories (meat, oil, beverages).
- Target subsidies or interventions in cities with rapidly rising prices.
- Use clusters to tailor regional market policies.

🚀 Future Extensions
- Add forecasting models (ARIMA, Prophet)
- Integrate multi-year data for trend analysis
- Build an interactive dashboard for policymakers
- Include wholesale vs. retail price comparisons
