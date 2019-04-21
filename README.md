# Human-Resources-Analytics based on Random Forest

### Introduction 
This repo is my EE-551-Spring individual project. | Name: Bowen Li

### Proposals
In this project, I will use the relevant data set on Kaggle website to establish a Random Forest model to find out the key factors that affact the turnover of employers in an enterprise.Combining these variables into a single indicator will help the company to understand which employees need to be focused on and forecast the employees on the job, and judge the probability of their leaving. At the end, I used K-means to do a further analysis.

## Dataset
https://www.kaggle.com/jiangzuo/hr-comma-sep/version/1

## Tools
Anaconda, Jupyternotebook

## Library
Numpy, Pandas, Matplotlib, Seaborn, Scitlearn

## Model
Random Forest, K-means

## TODO List
Step1: Exploratory Data Analysis   
- Find out the type of features.   
```
Total amount of data is 14,999 which contains 9 independent variables and 1 dependent variable
```
- View the basics of the data.   
```Python
df.info()
df.describe()
```

Step2: Data Preprocessing
- Process missing values.
- Process categorical features.

Step 3: Feature Engineering
- Feature selection

Step 4: Model Selection and Training
- Choose model (Random Forest)
- Train model (Cross Validation)

Step 5: Evaluate Model
- Define importance score.

Step 6: Other Models
- K-means, Logistic Regression or other models.
