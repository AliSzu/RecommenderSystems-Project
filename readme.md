#Recommender System's Project
The Aim of this project was to create a content-based recommender which, for given users, would recommend the best possible hotels.
The main goal was to beat Amazon's recommender which was trained on the same dataset.

##Preparing data
```users_df``` was one-hot encoded and then the ```user_features``` were normalized by calculating probability for each value\
```items_df```was also one-hot encoded the same way as users_df. ```item_features```  was normalized by summing row's weights to 1.

Without normalizing ```items_features```, my recommender wasn't able to score higher than Amazon's recommender. Sometimes when ```items_features``` weren't normalized the recommender would also recommend NaNs.

##Training
The Recommender was trained on two different ML algorithms

- Linear Regression 
- XGBoost

There were plans for SVR based recommender but the training took too long to learn. After 2 hours there wasn't any progress.

##Tuning
In the final tuning there were the scores and best parameters chosen by the hyperopt:
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
      <th></th>
      <th>Recommender</th>
      <th>HR@1</th>
      <th>HR@3</th>
      <th>HR@5</th>
      <th>HR@10</th>
      <th>NDCG@1</th>
      <th>NDCG@3</th>
      <th>NDCG@5</th>
      <th>NDCG@10</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>LinearRegressionCBUIRecommender</td>
      <td>0.049219</td>
      <td>0.130007</td>
      <td>0.175492</td>
      <td>0.243381</td>
      <td>0.049219</td>
      <td>0.094502</td>
      <td>0.113541</td>
      <td>0.135065</td>
    </tr>
    <tr>
      <th>1</th>
      <td>XGBoostCBUIRecommender</td>
      <td>0.013917</td>
      <td>0.029192</td>
      <td>0.083842</td>
      <td>0.18296</td>
      <td>0.013917</td>
      <td>0.02231</td>
      <td>0.043943</td>
      <td>0.076412</td>
    </tr>
  </tbody>
</table>

##Final Result
The LinearRegressionRecommender was able to beat Amazon's Recommender on the same dataset.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
      <th></th>
      <th>Recommender</th>
      <th>HR@1</th>
      <th>HR@3</th>
      <th>HR@5</th>
      <th>HR@10</th>
      <th>NDCG@1</th>
      <th>NDCG@3</th>
      <th>NDCG@5</th>
      <th>NDCG@10</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>LinearRegressionCBUIRecommender</td>
      <td>0.049219</td>
      <td>0.130007</td>
      <td>0.175492</td>
      <td>0.243381</td>
      <td>0.049219</td>
      <td>0.094502</td>
      <td>0.113541</td>
      <td>0.135065</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AmazonRecommender</td>
      <td>0.044128</td>
      <td>0.118805</td>
      <td>0.160557</td>
      <td>0.223693</td>
      <td>0.044128</td>
      <td>0.086755</td>
      <td>0.104216</td>
      <td>0.124468</td>
    </tr>
  </tbody>
</table>

#Requirements
To run this notebook without issues you need to install the following libraries:
- numpy
- pandas
- matplotlib
- seaborn
- hyperopt\
all the necessary data is in the repository
