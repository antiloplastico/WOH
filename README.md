# Weighted One-Hot
Weighted One-Hot encoding model
Based on this set: https://archive.ics.uci.edu/ml/datasets/adult, but can be probabilly applied to anyone.

```python
#estimation of the weight of each categorical variable to the actual possibility of the income can be <=50K 
categorical = ['workclass','education', 'marital-status'] #All variables are not needed now, this is just a sample
for feature in categorical:
  for value in np.unique(training_set[[feature]].values):
    avg_income = training_set.loc[df_train[feature] == value, 'income'].mean() #calculates the mean of each possibility for every categorical feature
    training_set[feature].replace([value],[avg_income],inplace=True) #replace the name of the variable with calculated value
    test_set[feature].replace([value],[avg_income],inplace=True)
```
