# Movie Recommendation System for Couples

This project is a recommendation system designed specifically for couples. By inputting the user IDs of two individuals, the algorithm recommends a movie that both users might enjoy watching together.

## 1. Preprocessing

### Initial Datasets
Initially, there were five datasets:
1. Movie ratings
2. Movie details
3. IMDb titles
4. User details
5. IMDb names (removed due to resulting dataframe size)

### Steps Taken
1. **Merge Ratings and Movie Details**: Merged ratings with movie details using the `MovieID`.
2. **Merge with IMDb Titles**: Merged the resulting dataframe with IMDb titles using `titles` and `year of release` to ensure accuracy.
3. **Merge with User Details**: Merged the dataframe with user details using `UserID`.

## 2. User-Item Interaction Matrix

Created an interaction matrix to facilitate easy access to movies that were rated and unrated by each user.

## 3. Prediction Model

### Features Used
The model uses the following seven columns to predict ratings for each movie for a specific user:
- `Gender`
- `Genres`
- `Age`
- `Occupation`
- `Year`
- `runtimeMinutes`
- `isAdult`

### Data Preparation
- Normalized, encoded, and filled NaN values to ensure clean data for training.

### Model Choice
- **RandomForest** was chosen for the prediction model. 
- **Metrics**: *TODO: Specify the metrics used to evaluate the model performance*

## 4. Recommendation Algorithm

### Function Overview
Given two user IDs, the function performs the following steps:
1. Retrieves the age, gender, and occupation for both users.
2. Compiles a list of all movies that neither user has rated, including movie details such as year, runtime, isAdult, and genres.
3. Predicts ratings for the unrated movies for each user using the model.
4. Calculates the average rating for movies that both users have not rated, excluding movies rated by at least one user.
5. Identifies the movie with the highest average rating and returns it as the recommended movie.

## Reasoning Behind Choices

### Model Choice
- **RandomForest**: Selected for its faster training time compared to neural networks and its superior prediction performance. 
- **Classification and Regression**: Initial attempts with classification yielded an accuracy of around 30%, which was too low. Regression results were frequently greater than 5, making normalization impractical, leading to its abandonment.

### Methodology
- Opted against using only the user-item interaction matrix with methods like SVD, as they did not leverage additional information and details, resulting in less personalized recommendations.
- RandomForest provided the best predictions and was straightforward to implement.