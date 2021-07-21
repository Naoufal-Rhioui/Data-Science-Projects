# Web APIs & Classification

![](https://www.thedataschool.com.au/wp-content/uploads/2018/10/text-classification-1080x545.png)

**Content:**

- Dataset created after web scrapping two subreddits.
- Project code.
- Powerpoint presentation.

**Introduction:**

Our goal is to collect 2000 posts from two subreddits (sports and politics) using reddit's API. For this binary classification problem, we will be using NLP to train a classifier on which subrredit a given post came from.

**Overview:**

- Libraries:
    - Pandas
    - Sklearn
    - Request
    - Time
    - Numpy
    - CSV
    
- Data: 
Data collected through webcrapping reddit's API. Since reddit only provide 25 posts per request, we used a for loop to request 40 times to get to Approximately 1000 posts from each subreddit. 
    - 983 posts collected from politics subreddit 906 of which were       unique posts.
    - 978 posts collected from sports subreddit 339 of which were       unique posts.
    - We put the data from each subreddit into dataframes and merged them to one.
    - Since CountVectorizer does not take dataframe, we had to set X to be a pandas Series. so we assigned       X to new column which combines 'title' and 'selftext' columns.
    
- Code showing:
    - Spam Classification Model
    - Model prep
    - Scikit-Learn CountVectorizer
    - Modeling
    - Baseline accuracy
    - GridSearchCV
    - Model evaluation    


- Methodology:

    - We first conducted web scraping for politics and sports subreddits. This was the most time consuming       part of the project due to the 400s errors we constantly got.
    - Created a for loop to request json multiple times to get the maximum posts reddit offers.
    - After we successfully scraper the subreddits, we put the data into a dataframe.
    - Created 'label' column to differentiate the two dataframes and merged them.
    - Created a new column which combined the title and selftext columns so we could use a pandas series         for our CountVectorizer.
    - We loaded pipeline object into our GridSearchCV model to tune over the countVectorizer. We also tried       logistic regression model to compare our scores.
    
    

      
**Reflection:**
We successfully created a close to prfect model with a 0.98 score.



 
