🎤 Taylor Swift Spotify Song Popularity Prediction
A machine learning project analyzing what makes a Taylor Swift song popular

📌 Overview
This project uses predictive analytics and machine learning to uncover which musical and contextual features influence the popularity of Taylor Swift’s songs on Spotify. Using a dataset of 582 tracks, the analysis explores patterns in audio attributes, release timing, and album metadata and evaluates three regression models, Ridge, Random Forest, and Gradient Boosting, to predict Spotify popularity scores.
The best model, Gradient Boosting, achieved strong predictive accuracy, explaining 86% of the variance in popularity.

📁 Dataset
The dataset includes 18 columns describing each track, such as:
acousticness
danceability
energy
instrumentalness
loudness
tempo
valence
liveness
speechiness
album
release_date
track_number
duration_ms
popularity (target variable)
As shown in the dataset preview and df.info() output, all attributes are complete with no missing values and no duplicates. 
ts_song_popularity

🧹 Data Cleaning & Feature Engineering
Steps included:
✔️ Dropped unnecessary columns
Unnamed: 0, name, id, uri, and raw release_date removed to avoid leakage and noise.
✔️ Parsed release date
Converted release_date to datetime and extracted:
release_year
release_month
✔️ Identified numeric vs. categorical features
13 numeric audio and structural features
1 categorical feature: album
✔️ No missing values
The dataset required zero imputation on raw inspection, but imputers were included in the pipeline for robustness.

📊 Exploratory Data Analysis
Popularity Distribution
The histogram shows a unimodal distribution, with most songs between 40–80 popularity, and very few at the extreme low or high ends. 
ts_song_popularity
Correlation Heatmap
The heatmap reveals:
Strong positive correlation between energy and loudness
Negative correlation between acousticness and high-energy features
Popularity does not strongly correlate with any single feature, but has:
Slight positive relationships with valence, danceability, energy
Slight negative correlation with acousticness
Small positive correlation with release_year, indicating newer songs are more popular.
Top Feature Relationships
Scatterplots show:
Release year has the strongest relationship with popularity (r = 0.63).
Track number and release month show weak negative correlations.
Musical features individually have weak relationships, confirming popularity is multifactorial. 
ts_song_popularity
Popularity by Album
A boxplot highlights that albums like:
The Tortured Poets Department: Anthology
1989 (Taylor’s Version) [Deluxe]
have consistently high popularity, while earlier or deluxe editions show more variability. 
ts_song_popularity

🤖 Modeling
A full preprocessing + modeling pipeline was built using ColumnTransformer, StandardScaler, and OneHotEncoder, with GridSearchCV applied to three models:
1. Ridge Regression
Test RMSE: 6.219
Test MAE: 4.328
Test R²: 0.834
2. Random Forest Regressor
Test RMSE: 6.006
Test MAE: 4.341
Test R²: 0.846
3. Gradient Boosting Regressor ⭐ Best Model
Test RMSE: 5.718
Test MAE: 4.253
Test R²: 0.860
Best parameters:
learning_rate = 0.03
max_depth = 2
n_estimators = 600
(Results table shown at the end of the notebook.) 
ts_song_popularity
Interpretation
Gradient Boosting builds many shallow trees and optimizes errors iteratively, capturing subtle nonlinear interactions between audio features, release metadata, and popularity. Its strong R² and low error metrics indicate excellent real-world predictive performance.

🧠 Key Insights
Based on EDA and model findings:
Release year is the strongest predictor — more recent songs tend to be more popular.
Musical attributes like energy, valence, and danceability help but are not dominant individually.
Popularity is shaped by contextual factors, including recency, album release cycles, and streaming algorithm behavior.
Gradient Boosting best captures these multivariate patterns.

🚀 Future Enhancements
Add lyric sentiment analysis using NLP.
Incorporate Spotify playlist data (e.g., featured playlists, editorial boost).
Test advanced models like XGBoost, LightGBM, or CatBoost.
Build a Streamlit app to explore predictions interactively.
