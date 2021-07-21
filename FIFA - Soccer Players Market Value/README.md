# FIFA - Soccer Players Market Value

![](https://cdn.britannica.com/51/190751-050-147B93F7/soccer-ball-goal.jpg)

Welcome to FIFA project! 

**Content:**

- Dataset downloaded from https://www.kaggle.com/stefanoleone992/fifa-20-complete-player-dataset.
- Project code.
- Tableau analysis.
- Powerpoint presentation.

**Introduction:**

With investors pouring more money into soccer, especially in Europe, the players' price tag have increased drastically the past few years and it has become more difficult to predict a player's market value. Our goal is to create a model that predicts the soccer players' market value based on their skills and currenct contracts. 

**Overview:**

-Libraries:
    -Pandas
    -Sklearn
    -Numpy
    -Seaborn
    -Sklearn
    
- Data: 
Data retrieved form kaggle (link provided above) is composed of 7 independent datasets. 
    - players_15.csv (used for EDA and Tableau)
    - players_16.csv (used for EDA and Tableau)
    - players_17.csv (used for EDA and Tableau)
    - players_18.csv (used for EDA and Tableau)
    - players_19.csv (used for EDA and Tableau)
    - players_20.csv (Used for EDA and Tableau and to create the predective model)
    - teams_and_leagues.csv
    
- Code showing:
    - Data exploration
    - Data cleaning
    - Feature engineering
    - Exploratory data analysis 
    - Model prep
    - PowerTransformer
    - Model evaluation


- Methodology:

    - We first conducted a data exploration to check the quality of the data found on kaggle. During this step we were able to draft an inital plan for the project.
    - We first dropped columns that were missing a significant amount of data. Second, we dropped the rows with missing value. Last, we cleaned up several columns and converted them to integers.
    - We used feature engineering techniques to binarize and dummify columns.
    - Compared the average value by age between FIFA 2016 through 2020.
    - Compared the average rating by age between FIFA 2016 through 2020.
    - Compared the average value by team position between FIFA 2016 through 2020.
    - Created scatterplots to see how our stronger predictors correlate to our target.
    - Compared our strongest predictors to the target.
    - Used PowerTransformer and fitted 6 models.
    
    

      
**To Do List:**
- Rewrite few codes (data cleaning section) to make it more efficient
- Learn and implement flask.




