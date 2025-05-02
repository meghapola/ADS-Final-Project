# Team 10 ADS Final Project

## Project Installation
1. Clone the Repository
```{python} 
git clone https://github.com/meghapola/ADS-Final-Project
```
2. Navigate to the project directory:
```{python} 
cd ADS-Final-Project
```

## Prerequisites & Dependencies
To run this project, ensure you have the following installed:
- Python 3.x
- Jupyter Notebook
- numpy
- pandas
- matplotlib
- seaborn
- sklearn
- scipy
- xgboost
- time
- dateuil
- datetime
- urllib
- urllib3
- bs4
- requests
- re
- json
- os
- zipfile

## Data Acquisition and Preparation
- **data_processing.ipynb** is Jupyter Notebook containing code to acquire and preprocess data
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
 
### Data Sources
- [Harvard Dataverse Election Dataset](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/NT66Z3 
)
- [2020 US Census Data](https://data.census.gov/table/ACSDP5Y2020.DP05?q=voting+precinct&g=010XX00US$0500000&y=2020
)
- [FIPS IDs](https://transition.fcc.gov/oet/info/maps/census/fips/fips.txt)
- [The New York Times](https://developer.nytimes.com/get-started)
- Fox News/Wayback Machine

We utilized election data from the Harvard Dataverse database as well as 2020 US Census data and webscraped Fox News and New York Times news piece information. The overall code for this step is in data_processing.ipynb. The unaggregated data is in the data folder and the raw data is in the raw.zip file. The final data set before preprocessing is in final_data.csv.zip


## EDA
The file 'ADS_Final_Project_(EDA).ipynb' contains the code used for performing the exploratory data analysis, including initial investigation of the data, visualizations, and unsupervised learning methods. This file uses 'final_data.csv' from 'final_data.csv.zip'.

## Feature Engineering & Preprocessing
The file 'ADS_Final_Project_(Feature_Engineering_&_Preprocessing).ipynb' contains the code used for performing feature engineering and preprocessing, including creating, transforming, and encoding variables, as well as applying preprocessing techniques where needed. This file uses 'final_data.csv' from 'final_data.csv.zip'. It results in a new csv file named 'final_preprocessed_data.csv' that contains the newly preprocessed dataset reduced to 42 features and the target.

## Model Development
- **Model Development 04282025New.ipynb**: The model development without tuning hyperparameter: Decision Tree, Random Forest, Logistic Regresion
- **Mo-Copy1.ipynb**: Final Model Development, with three supervised learning models: Decision Tree, Random Forest, Logistic Regression using grid search and cross validation to tune the hyperparameter.
- **old_models** contains old models used in the course of development:
  - **Model_Development_Logistic_Regression_and_XGB.ipynb** is initial exploration of logistic regression and XGBoost models
  - **Decision_Tree_and_Random_Forest_.ipynb** is initial exploration of decision tree and random forest models 


After tuning the hyperparameters, the accuracy did not change a lot but were relatively close to each other

Since the target variable is binary, we tried logistic regression model. However, the model is performing worse than the tree models, for example, decidion tree. With decision tree and random forest, the result is much more better. The best accuracy is 0.915 for decision tree and 0.918 for random forest meaning we have a decent model. We also tried Grident Bosting and XGBoost, however, the dataset is too large to run those two models. We also did grid search and cross validation to find the best hyperparameters. Here are the result: Even with a relatively small number of trees, Random Forest achieved the best accuracy. Both Decision Tree and Random Forest used a max_depth of 15, which seems to balance complexity and overfitting. Despite tuning,the accuracy for logistic regression was far behind tree-based models, possibly indicating nonlinear relationships or complex interactions in the data that linear models can't capture well.
Thus we conclude that simple model works just well. Sicne random forest is more stable than dicision tree, we chose random forest as our final model.

After visualing the feature importance, we found out that Media features dominate prediction power across most models. All models rank media mentions as top predictive features. This suggests strong correlation between media coverage and whether candidate won the voting or not. The feature "percent total population two or more races white and American Indian and Alaska Native" appears in the top 2 for both Decision Tree and Logistic Regression.This suggests racial demographic composition plays a meaningful role in prediction. Decision Tree and Logistic Regression consider gender-specific voting-age citizen population (male/female) as top 3 features. This suggests gender demographic composition also plays a meaningful role in prediction.




