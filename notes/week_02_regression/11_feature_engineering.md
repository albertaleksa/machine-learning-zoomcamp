>[Back to Week Menu](README.md)
>
>Previous Theme: [Using RMSE on validation data](10_car_price_validation.md)
>
>Next Theme: [Categorical variables](12_categorical_variables.md)

## Feature engineering
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=22)_


### Adding the Car Age Variable to the Model

![age](images/11_feature_engineering_01_age.png)

### Modifying the DataFrame to Add the Feature

We add a new feature, **age**, to our model in the function `prepare_X(df)`:

```python
def prepare_X(df):
    df['age'] = 2017 - df.year
    features = base + ['age']
    
    df_num = df[features]
    df_num = df_num.fillna(0)
    X = df_num.values
    return X

X_train = prepare_X(df_train)
```

However, this approach modifies our DataFrame by adding a new column, 'age'.

![modify](images/11_feature_engineering_02_modify.png)

### Creating a Copy to Avoid DataFrame Modification

To prevent modification of the input DataFrame, we create a copy at the beginning of the prepare_X(df) function:

```python
def prepare_X(df):
    df = df.copy()
    
    df['age'] = 2017 - df.year
    features = base + ['age']
    
    df_num = df[features]
    df_num = df_num.fillna(0)
    X = df_num.values
    return X
```

### Improved Model with Validation Data Set

We now train our model using the modified **prepare_X()** function:

```python
X_train = prepare_X(df_train)
w0, w = train_linear_regression(X_train, y_train)

X_val = prepare_X(df_val)
y_pred = w0 + X_val.dot(w)

rmse(y_val, y_pred)
>> 0.5172055461058335
```

We observe an improvement in our model:
* New RMSE = 0.5172055461058335
* Previous RMSE = 0.7616530991301601

Now see the plot:
```python
sns.histplot(y_pred, color='red', alpha=0.5, bins=50)
sns.histplot(y_val, color='blue', alpha=0.5, bins=50)
```
![plot](images/11_feature_engineering_03_plot.png)

_[Back to the top](#feature-engineering)_