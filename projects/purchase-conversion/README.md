🏙️ Predicting Housing Prices in NYC
A machine learning project using Linear Regression and Random Forests

📌 Overview
This project explores real estate listings across New York City to understand pricing patterns and build predictive models for estimating housing prices. Using a dataset sourced from Kaggle, the analysis includes data cleaning, feature engineering, exploratory data visualization, and the development of two predictive models—Linear Regression and Random Forest Regressor.
The Random Forest model ultimately achieved superior performance with high predictive accuracy, demonstrating the value of non-linear and ensemble methods for modeling complex real estate markets.

📁 Dataset
The dataset contains 4,801 NYC real estate listings and 20 features, including:
PRICE (target variable)
BEDS, BATH, PROPERTYSQFT
LATITUDE, LONGITUDE
Property categories such as TYPE, LOCALITY, ADDRESS, etc.
A full column breakdown appears in the notebook.
Source
Dataset from Kaggle:
https://www.kaggle.com/datasets/nelgiriyewithana/new-york-housing-market

🧹 Data Cleaning & Preparation
Several steps were taken to prepare the dataset for modeling:
✔️ Removed unnecessary or duplicate columns
Fields such as BROKERTITLE, MAIN_ADDRESS, LONG_NAME, and several variant location columns were dropped.
✔️ Handled missing values
Columns like SUBLOCALITY.1, LOCALITY.1, and STREET_NAME.1 contained 4,600–4,700+ null values and were removed.
✔️ Removed outliers
To improve model performance, I filtered outliers using the mean ± 3 standard deviations rule for:
PRICE
PROPERTYSQFT
✔️ Feature engineering
Added PRICE_PER_SQFT, which later became the strongest predictor.
✔️ Standardized numerical features
StandardScaler was applied before fitting models.

📊 Exploratory Data Analysis
1. Distribution of House Prices
Highly right-skewed
Majority of homes fall in lower price ranges
Long tail caused by luxury properties
2. Distribution of Price per Square Foot
Also strongly right-skewed
Reveals affordability patterns across neighborhoods
3. Scatterplot: PRICE vs. PROPERTYSQFT
Positive correlation between size and price
Significant variability showing factors like location
4. Boxplot: PRICE by TYPE
Townhouses exhibit highest median and largest variation
Co-ops and houses show lower medians and smaller ranges
These visualizations reflect the complexity and variability of NYC housing markets.

🤖 Modeling
1. Linear Regression
Features used:
PROPERTYSQFT
BEDS
BATH
PRICE_PER_SQFT
Linear Regression Performance
RMSE: 1,109,057
MAE: 610,946
R²: 0.903
Feature Importance (Coefficients):
PRICE_PER_SQFT — strongest positive predictor
PROPERTYSQFT — also strongly positive
BEDS and BATH — small negative coefficients

2. Random Forest Regressor
After scaling the features:
Random Forest Performance
RMSE: 580,255
R²: 0.973
This model reduced error by nearly half compared to Linear Regression and captured non-linear patterns more effectively.

🧠 Key Findings
NYC housing prices exhibit large variation and extreme outliers.
Price per square foot is the strongest single indicator of property value.
Removing outliers significantly improves model performance.
Random Forest clearly outperforms Linear Regression for this dataset.
Property type (townhouse vs. condo vs. co-op) strongly influences price distribution.

🚀 Future Improvements
Add geospatial clustering (e.g., KMeans based on lat/long)
Include neighborhood-level features (schools, transit, crime)
Test gradient boosting models (XGBoost, LightGBM)
Build a Streamlit app for interactive price prediction
