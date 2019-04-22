# Human-Resources-Analytics based on Random Forest

## Introduction 
This repo is my EE-551-Spring individual project. | Name: Bowen Li

## Proposals
In this project, I will use the relevant data set on Kaggle website to establish a Random Forest model to find out the key factors that affact the turnover of employers in an enterprise. Combining these variables into a single indicator will help the company to understand which employees need to be focused on and forecast the employees on the job, and judge the probability of their leaving. At the end, I used K-means to do a further improvement.

## Preparation
- Dataset   
https://www.kaggle.com/jiangzuo/hr-comma-sep/version/1
- Tools   
Anaconda, Jupyternotebook
- Library   
Numpy, Pandas, Matplotlib, Seaborn, Scitlearn
- Model   
RandomForest, K-means

## Main Process
### Step1: Data Exploratory 
- Find out the type of features.   
```
Total amount of data is 14,999 which contains 9 independent variables and 1 dependent variable.
```
- View the basics of data.   
```Python
df.info()
df.describe()
```
- Compute correlated coefficient matrix.
```Python
df.corr()
```

### Step2: Data Visualization
- Plot the distributions of left using catplot.
```Python
plot = sns.catplot(x='department', y='left', kind='bar', data=df)
plot = sns.catplot(x='salary', y='left', kind='bar', data=df)
plot = sns.catplot(x='Work_accident', y='left', kind='bar', data=df)
plot = sns.catplot(x='promotion_last_5years', y='left', kind='bar', data=df)
```
- Plot the distributions of salary using pie.
```Python
df[df['department']=='management']['salary'].value_counts().plot(kind='pie', title='Management salary level distribution')
df[df['department']=='RandD']['salary'].value_counts().plot(kind='pie', title='R&D dept salary level distribution')
```
- Plot the distributions of left and stay using hist.
```Python
plt.hist(df[df['left']==1]['satisfaction_level'], bins=bins, alpha=0.7, label='Employees Left')
plt.hist(df[df['left']==0]['satisfaction_level'], bins=bins, alpha=0.5, label='Employees Stayed')
```

### Step 3: Feature Engineering
- One-hot Encoding.
```Python
salary_dummy = pd.get_dummies(df['salary'])
department_dummy = pd.get_dummies(df['department'])
```
- Split data into train set and test set.
```Python
from sklearn.model_selection import train_test_split
```
- Standardize data through StandardScaler.
```Python
from sklearn.preprocessing import StandardScaler
```
- Set cross-validation through ShuffleSplit to avoid overfitting.
```Python
from sklearn.model_selection import ShuffleSplit
```

### Step 4: Model Training and Selection
- Train the model through RandomForest
```Python
from sklearn.ensemble import RandomForestClassifier
```
- Select the best parameter through GridSearchCV
```Python
from sklearn.model_selection import GridSearchCV
```
- Compute the best test score.
```Python
print('Test score:', best_rf.score(X_test, y_test))
```

### Step 5: Find Out Key Factors
- Compute importance score.
```Python
feature_importances = best_rf.feature_importances_
```
- Create a new dataframe to obtain importance oder.
```
features_df = pd.DataFrame({'Features': features, 'Importance Score': feature_importances})
features_df.sort_values('Importance Score', inplace=True, ascending=False)
```

### Step 6: Further Analysis and Reproduction
- Make a classification through K-means
```
from sklearn.cluster import KMeans
```

