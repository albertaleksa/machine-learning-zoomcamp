>[Back to Week Menu](README.md)
>
>Previous Theme: [Training linear regression: Normal equation](07_linear_regression_training.md)
>
>Next Theme: [Root mean squared error](09_rmse.md)

## Baseline model for car price prediction project
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=19)_


### Building a baseline car price model.

Extract all numerical columns from **Train** dataset:

![num](images/08_baseline_model_01_num.png)

### Extracting basic features for linear regression.

```python
base = ['engine_hp', 'engine_cylinders', 'highway_mpg', 'city_mpg', 'popularity']

# Extract NumPy array
X_train = df_train[base].values
```

Try to train a Model 

```python
train_linear_regression(X_train, y_train)
>> (nan, array([nan, nan, nan, nan, nan]))
```

And we have a problem with NaN values because of the missing values.

### Dealing with missing values in data modeling

![missing](images/08_baseline_model_02_missing.png)

The easiest thing that we can do with them is just fill them with '0'. Filling them '0' we make our Model ignore these features.

![zeroes](images/08_baseline_model_03_zeroes.png)

### Replacing missing values with zeros for training.

Zeroes is not always the best way to deal with missing values. For replacing such values like 'Engine HP' with zeroe doesn't make much sense but from practical point of view when it comes to ML sometimes '0' works fine.

```python
X_train = df_train[base].fillna(0).values

train_linear_regression(X_train, y_train)
>> (7.927257388070117,
 array([ 9.70589522e-03, -1.59103494e-01,  1.43792133e-02,  1.49441072e-02,
        -9.06908672e-06]))
```

### Training data predictions plotted for comparison.

Now we have weights:
```python
w0, w = train_linear_regression(X_train, y_train)
```

We can use these weights to make predictions using our train dataset:
```python
y_pred = w0 + X_train.dot(w)
```

Create a plot with prediction and target values for comparison:
```python
sns.histplot(y_pred, color='red', alpha=0.5, bins=50)
sns.histplot(y_train, color='blue', alpha=0.5, bins=50)
```

![plot](images/08_baseline_model_04_plot.png)

Now we need to evaluate the performance of our Model.


_[Back to the top](#baseline-model-for-car-price-prediction-project)_