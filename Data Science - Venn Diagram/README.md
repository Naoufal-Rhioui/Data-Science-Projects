# Data Science - Venn Diagram



**Introduction:**

By its very nature, data analysis is limited by a myriad of factors. Anyone deciding to embark upon the path of advanced analytics will always be constrained by the limited resources available to them.
The objective of every analytics project is:

    -To be of high quality
    
    -To be completed quickly
    
    -To be executed at a low cost
    
As the below Venn diagram shows, meeting all of the above objectives is impossible. Any project can at best encompass two of the three objectives.
![](https://berkonomics.com/wp-content/uploads/2015/11/goodfastcheap1-1.png)


**The Problem:**

I, along with my team of fellow aspiring data scientists, were provided a dataset of 32,561 rows and 14 columns. The dataset provided insight into the financial and employment status of 32,561 individuals. We were expected to use this data to construct a model that could predict the salary of any given individual. More specifically, the model was intended to accurately predict whether an individual made more or less than $50,000.
     
**Limitations:**

In order to make the exercise more realistic, limitations were put on the data we were able to use in our analysis. We were forbidden to use more than 20 columns to inform the predictive model. While perhaps not as limiting as some other potential handicaps, it did force us to be more discerning with the data we used, and more creative in how we used it.

**Exploratory Analysis:**

Immediately after opening the data set, we proceeded to conduct exploratory data analysis. This allowed us to get an overview of the data we had available, and how the various data points interacted with one another.
The most illuminating revelation came from looking at the correlations of the various data points with salary (our y variable). This gave us important insight into which features would be most important when we constructed our model.

**Model Overview:**

Following our exploratory analysis, we proceeded to analyze the different models we had available, and how accurate they were at predicting whether or not any given individual had a salary exceeding $50,000.
We performed a Train-Test split on the data, and looked at the following classification models:

    -Logistic Regression
    
    -Naïve Bayes
    
    -KNN
    
    -Lasso
    
    -Ridge
    
Ultimately, we decided to use a Logistic Regression model. The model had high train and test scores. Additionally, there was a small delta between the two values, indicating an excellent bias-variance trade off.

**Limitations:**

Once we had decided to use a logistic regression model to determine whether an individual’s income was greater than $50,000, our next step was to refine the model. Because of our constraint of only having access to 20 feature columns, we had to be conscious of the X variables used to inform our final model. We ultimately decided that the best strategy to pursue was to include only those variables that had the most substantial impact on the model’s output.
We wanted to determine the impact that every individual feature had on the model. We then engaged in a multi-step process to address this:

    -Firstly, we wanted to ensure that the degree of impact was standardized across all features. In this way, we could ensure that the degree of impact was measurement agnostic. In order to do this, we applied a Standard Scaler to the X variables.
    
    -After standardizing all of the X variables, we wanted to see the coefficient of each variable in the logistic regression model. We ran the below code in order to create a DataFrame showing the X variable and its corresponding coefficient.
    
    -Once this was complete, we were able to look through the list of X variables, and remove those that, according to their coefficients, had the least impact on the model. This left us with only the 20 most impactful variables.
    
Ultimately, our hypothesis was that by removing those variables that were least impactful, we would be able to create a highly accurate model, despite having a limited number of features at our disposal. This hypothesis appeared to be validated by the accuracy of the finished model.
        
**Outcome and Conclusion:**

Ultimately, through a combination of selecting the right model and the most important 20 features, we were able to create a model with an AUC of 0.997. This means that in 99.7% of instances, the model was able to accurately separate the positive classes from the negative classes.

Despite the limitation of only being allowed 20 feature columns, we were able to create a model with a high degree of accuracy. However, it took substantially more effort for us to create an accurate model than it would have had we not been operating with any limitations. Therefore, it is likely that if we were operating under more stringent limitations, our model would have been less effective.

In essence, this experience proves what one would intuitively assume about data science. It is always better, both in terms of accuracy and ease of workflow, to operate with an infinite amount of data and an infinite amount of ways to manipulate said data. However, due to the nature of the industry, this is impossible for the vast majority of instances. Therefore, it is important to work to mitigate the negative influence that less than ideal data has on model construction.




