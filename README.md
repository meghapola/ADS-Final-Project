# ADS-Final-Project


### Data Acquisition and Preprocessing Files
- **final_proj.ipynb** is Jupyter Notebook containing code to acquire and preprocess data
- **final_data.csv.zip** is zip file which contains final CSV to be used in EDA and model development 
- **data** contains:
  - **combined1.csv.zip** is zip file which contains intermediate CSV before final_data before missing values were handled 
  - **2020_election_results_top6.csv.zip** has results for who won each race in the 2020 election by precinct for top 6 states by electoral college votes 
  - **census_data_top6.csv** has data from 2020 census for top 6 states by electoral college votes 
  - **election_census_combined_top6.csv.zip** zip file with merge of census_data.csv and 2020_election_vote_results.csv on state column for top 6 states by electoral college votes 
  - **fox_mentions.csv** aggregates number of times each candidate was mentioned in the title of a Fox news piece from 1/1/2020 - 11/3/2020
  - **nyt_mentions.csv** aggregates number of times each candidate was mentioned in the title of a NYT news piece from 1/1/2020 - 11/3/2020
  - **fox_data.csv** has title of article/video news piece and date of piece from Fox News from 1/1/2020 - 11/3/2020
  - **nyt_data.csv** has title of articles and date of piece from New York Times from 1/1/2020 - 11/3/2020
  -  **raw.zip** zip file of raw data files used to generate the above CSV files 


Model Development

Since the target variable is binary, we tried logistic regression model. However, the R2 is negative meaning the model is performing worse than the baseline. We also tried decidion tree. The result is much more better. The R2 is 0.68 and the MSE is 0.08 meaning we have a decent model. Then we tried random forest. The R2 and MSE are exactly the same as the decision tree. We also tried more complicated model--Grident Boosting. However, Gradient Boosting not only has worse R², but double the error (MSE) of Random Forest. Thus we conclude that simple model works just well. Sicne random forest is more stable than dicision tree, we chose random forest as our final model.

After visualing the feature importance, we found out that Media features dominate prediction power across most models. For example, fox headline mentions (log) appears to be the top one feature for three out of four models. Also, Demographic features are only picked by Decision Trees, possibly because a single split on demographics gave good enough performance at a node. In the end, we conclude that Media exposure plays the major role in predicting whether US presidential candidate won a voting precinct. 



