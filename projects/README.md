🎬 Movie Recommendation System
A hybrid content-based + ratings-based recommender

📌 Project Overview
This project builds a hybrid Movie Recommendation System that uses both movie genres (content-based filtering) and average user ratings (collaborative insight) to recommend movies similar to a user-selected title. The system transforms movie genres into numerical vectors, computes cosine similarity between films, and then enhances those similarity scores with normalized average rating data to generate meaningful and high-quality recommendations.
By combining thematic similarity and community feedback, this approach helps produce recommendations that are both relevant and trustworthy.

📁 Dataset
This project uses two datasets:
1. movies.csv
movieId
title
genres (pipe-separated)
Example:
movieId    title                       genres
1          Toy Story (1995)            Adventure|Animation|Children|Comedy|Fantasy
2          Jumanji (1995)              Adventure|Children|Fantasy
3          Grumpier Old Men (1995)     Comedy|Romance

2. ratings.csv
userId
movieId
rating
timestamp

🧠 Methodology
1. Content-Based Filtering
Genres are split using | and transformed into vectors using CountVectorizer.
Cosine similarity is computed between all movies to quantify how thematically similar two films are.

2. Ratings Integration
Average rating per movie is calculated (avg_ratings = ratings.groupby('movieId')['rating'].mean()).
A hybrid final score is computed:
final_score=0.7⋅similarity+0.3⋅(avg_rating/5)

3. Recommendation Function
The recommend() function:
Matches the selected movie title
Retrieves similarity scores
Excludes the movie itself
Ranks similar movies by hybrid score
Prints top recommendations

🔍 Example Output
Recommending movies similar to Toy Story (1995) returns titles that share Adventure / Animation / Children / Comedy / Fantasy genres and strong ratings, such as:
Legends of Valhalla: Thor (2011) | Rating: 4.50  
The Magic Crystal (2011)        | Rating: 3.50  
Boxtrolls, The (2014)           | Rating: 3.33  
...
This demonstrates effective alignment between genre similarity and quality filtering. 

▶️ How to Run the Project
1. Install Requirements
pip install pandas numpy scikit-learn
2. Place movies.csv and ratings.csv
3. Run the Notebook
Open in Jupyter/VS Code and run all cells.

⭐ Key Takeaways
The recommender system combines genre similarity and average rating to generate balanced, hybrid recommendations.
Using cosine similarity and CountVectorizer enables scalable content-based analysis.
Integrating ratings prevents genre-only recommendations that might be low quality.
Output results align well with thematic style and community preferences.

🚀 Future Improvements
Add TF-IDF weighting for genres
Build a full collaborative filtering model
Implement a web-based interface (Flask/Streamlit)
Add movie descriptions or keywords for deeper content analysis
Include user-based personalization
