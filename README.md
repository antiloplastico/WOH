# WOH
Weighted One-Hot encoding model
Based on this set: https://archive.ics.uci.edu/ml/datasets/adult, but can probabilly be applied to anyone

```python
#estimation of the weight of each categorical variable to the actual possibility of the income can be <=50K 
categorical = ['workclass','education', 'marital-status', 'occupation', 'relationship','race', 'sex','native-country', 'age', 'hours-per-week', 'capital-diff']
for feature in categorical:
  for value in np.unique(df_train[[feature]].values):
    avg_income = df_train.loc[df_train[feature] == value, 'income'].mean() #calculates the mean of each possibility for every categorical feature
    training_set[feature].replace([value],[avg_income],inplace=True) #replace the name of the variable with calculated value
    test_set[feature].replace([value],[avg_income],inplace=True)
```
