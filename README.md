Non-technical presentation link
https://docs.google.com/presentation/d/1cRVMd6wrzUx6FiBuDOHpAzaf8X1wXDzvX_vbrRXAXec/edit?usp=sharing


# MovieLens Recommendation System

### Objective:
Tasked with working on a new growing movie platform looking to compete with other giants such as Netflix, Hulu, and HBO. Your aim is to create a unique experience for each of our customers while subtly increasing company ROI, aim to achieve this by building a tailored, unique recommendation system that can effectively suggest movies to our users, in order to continue to engage them with our platform. 

I want to be able to make predictions for our existing clients, as well as use our recommendation system as a product, to attract new users to our platform. Additionally, as we continue to build up our recommendation systems, and expand the platform by investing in newer and relevant content for users to enjoy.


## Data
using the “MovieLens” database, developed by the GroupLens research lab at the University of Minnesota.

The initial data set consisted of ~100,000 user ratings; then was reduced to 64456  once both users and movies with low number of ratings were removed to combat high matrix sparsity of around 99%.
Our final dataset included information on userId, movieId, rating, title, genres, and year.

## Goal
1. Use Collaborative Filtering to predict what users would rate movies that have not been seen before.
2. Find the optimum model to use
3. apply the model to the data
4. Draw conclusions based on our data and model results.

### Exploratory Data Analysis
I wanted to emphasize the spread of movie ratings by looking at distributions and also how they would be visualized across each genre. 
To help understand this, we looked at a variety of different graphs using MatPlotLib to help get a better understanding of our data and to prepare for modeling.

Some observations/steps we had:
-Created genre labels in order to determine the most popular genres in the dataset; the top 3 were Comedy, Drama, and Action  
-Analyzed the distribution of ratings: a rating of 4 was the most frequent 
-Analyzed the top 10 movies overall, as well as by genre, to use as a future comparison to post-model EDA to determine the presence of popularity bias 

## Recommendation Modeling
After thorough cleaning and exploratory data analysis, I began to run our recommender models. Beginning with a baseline KNN-baseline model. Without tuning any hyperparameters, they produced a root mean squared error (RMSE) of 0.8776,
MAE:  0.6675.
Which i determined that on a rating scale of 0-5, this performance was expected and was a good start. Moving forward, we explored other recommender algorithms within the Surprise library. In particular, I examined the performance of models influenced by K-Nearest Neighbors(KNN) that took a nearest neighbors approach based on similarity metrics. We tested KNNBasic, KNNWithMeans, and SVD and their performance against the KNN-baseline model; even after tuning.

To help validate our models, we incorporated GridSearchCV while also running K-folds Cross Validation (3-folds). This helped us validate our model, but more importantly, efficiently tune the hyperparameters we fed in the model.

FINAL Model: Our final was the tuned GridSearchCV-SVD model with an RMSE of 0.853513 MAE OF 0.650359 which is improved from our baseline and other model tests.

#### Conclusions: 
Overall, our model does a fairly decent job of estimating users’ ratings, with an approximate error of 0.8563
Our model is a purely collaborative filtering model, and therefore does not address the “cold start problem”

Our future work would: look to incorporate aspects of a content-based filtering model to address this,
Incorporation of features, such as genres and year, into our matrix factorization models

