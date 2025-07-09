# Rotten Tomatoes Study Case
## Sentiment Analysis, clustering and a recommendation system using movie reviews
This project analyzes movie reviews scraped from Rotten Tomatoes and builds a content-based movie recommendation system using natural language processing techniques and sentiment analysis.
The goals are to classify review sentiment, recommend movies to a user based on their previous positive experiences, using movie metadata (genres, directors, actors, etc.) and create clusters of movies.

#### Dataset
Source: Publicly available Rotten Tomatoes website, scraped as of 31/10/2020. Available on Kaggle.com.
- Movies Dataset: 17,712 movies
- Critics Dataset: 1,130,017 reviews

## Sentiment Analysis
Used the TextBlob Python library for sentiment analysis.

#### Polarity Metrics:
- Ranges from -1 (negative) to +1 (positive)
- Based on the PatternAnalyzer lexicon

Disclamer: This approach is rule-based and may miss sarcasm or irony, but it's simple and fast.

## Recommendation System
Approach: Content-Based Filtering

Recommends movies based on their content features, creating a profile of what the user likes.

### Item Features Used
- Genres
- Actors
- Directors
- Authors
- Production companies

### Methods
- TF-IDF Vectorization: Converts movie features into numerical vectors
- k-Nearest Neighbors (k-NN): Finds similar movies based on vector distance

### Workflow
1. Feature Combination: Merge relevant features (genre, actors, etc.) into a single text string per movie.
2. Vectorization: Transform the combined features using TF-IDF.
3. Movie ID Mapping: Create mappings between movie IDs and matrix indices.
4. Model Training: Train a k-NN model on the TF-IDF matrix.
5. User Selection: Choose a user and identify the movies they liked (reviews with positive polarity).
6. User Profile: Build an average TF-IDF vector from the liked movies.
7. Movie Recommendations: Use k-NN to find movies closest to the user’s profile and recommend the top 10 movies the user hasn’t seen yet.

### Results
The system provides personalized movie recommendations that align with a user’s positive past experiences, using interpretable features and simple, effective algorithms.

