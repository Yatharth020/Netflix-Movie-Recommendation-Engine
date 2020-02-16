# Netflix-Movie-Recommendation-Engine
Collaborative filtering approach for recommneding movies

<img src = https://github.com/yatscool007/Netflix-Movie-Recommendation-Engine/blob/master/netflix-q.jpg>

<h2>Case Study and approach</h2>
<p>In this case study, the business problem we wre trying to solve is how to improve the netflix
alogrithm for recommending movies to the users,so the analysis was done in keeping in mind that
how netflix has laid down certain norms and the winning solution of the team lead by professor
'Yehuda koren'.</p>
<p>So we approached this problem both as regression problem and a recommendation problem by
primarily converting for the sparse matrix where every user has given some or the other rating to a
movie and not given rating to most of the movies,which we are trying to find through our approach
and thus recommneding movies which user is likely to give maximum rating thus making it a matrix
completing(recommender systems) and a Regression problem (reducing the mean absolute
percentage error).</p>
</p>
<br>
> Credits: Kaggle 
</p>

<h2>Featurization technique</h2>
Each row in the train dataframe will consist of a user, the movie he/she has rated, the global
average of all ratings given by all the 25K users, it will also contain the ratings of top 5 similar users
who has rated the movie (sur1,sur2...sur5). It has the ratings of the top 5 most similar movies to the
given movie(smr1,smr2...smr5). Each row will also contain the user's average rating on all the
movies he/she has watched, the average rating for the given movie and lastly the rating given by
the query user on this movie.

<h2>Overview of modelling strategy</h2>
For recommendation systems there is an extremely fast and scalable library that we will use in
order to build our models. At first, we have posed this movie recommendation problem as a
regression problem. Then we use the surprise library to create a baseline model, we will use the
output of this as a feature to our regression model.
We have 13 handcrafted features. We have 1 feature from the output of the surprise baseline
model. We have one feature from the output of the baseline KNN model. We have another feature
from the KNN movie movie similarity. We have two features from the outputs of the baseline SVD
and SVD++ models. We will use all these outputs as features to the regression model we will build.
One important note we have to keep in mind is that we cannot use the test data for feature
engineering. Suppose there's a new user who has subscribed to Netflix. We don't have prior data
about the user, so it's a cold start problem. This means we cannot use his/her data for feature
engineering. In case of a new user we will put the value of engineered features to be zero. Logically
it is the right thing to do.
-  <b>1. performed XGboost with 13 features 
  
- <b>2. Then on XGBoost with initial 13 features + Surprise Baseline predictor.
  
- <b>3. Then on XGBoost with initial 13 features + Surprise Baseline predictor + KNNBaseline
predictor.
  
- <b>4. Also XGBoost with initial 13 features + Surprise Baseline predictor + KNNBaseline predictor +
SVD.
  
- <b>5. Also XGBoost with initial 13 features , SVD ,SVD++, Surprise Baseline predictor +
KNNBaseline predictor.
  
## Results
<img src = https://github.com/yatscool007/Netflix-Movie-Recommendation-Engine/blob/master/Capture.PNG>

## Sources 
<ul>
<li> https://www.netflixprize.com/rules.html</li>
<li> https://www.kaggle.com/netflix-inc/netflix-prize-data</li>
<li> Netflix blog: https://medium.com/netflix-techblog/netflix-recommendations-beyond-the-5-stars-part-1-55838468f429 (very nice blog)</li>
<li>surprise library: http://surpriselib.com/ (we use many models from this library)</li>
<li>surprise library doc: http://surprise.readthedocs.io/en/stable/getting_started.html (we use many models from this library)</li>
<li>installing surprise: https://github.com/NicolasHug/Surprise#installation </li>
<li> Research paper: http://courses.ischool.berkeley.edu/i290-dm/s11/SECURE/a1-koren.pdf (most of our work was inspired by this paper)</li>
<li> SVD Decomposition : https://www.youtube.com/watch?v=P5mlg91as1c </li>
</ul>
