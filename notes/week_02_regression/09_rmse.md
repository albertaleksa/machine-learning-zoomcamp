>[Back to Week Menu](README.md)
>
>Previous Theme: [Baseline model for car price prediction project](08_baseline_model.md)
>
>Next Theme: [Using RMSE on validation data](10_car_price_validation.md)

## Root Mean Squared Error
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=20)_

To evaluate the performance of our model, we use Root Mean Squared Error (RMSE) as a metric.

### RMSE Formula

$$RMSE = \sqrt{ \frac{1}{m} \displaystyle\sum_{i=1}^m {(g(x_i) - y_i)^2}}$$

- $g(x_i)$ - the prediction for $x_i$
- $y_i$ - the actual value
- $m$ - the number of observations in the dataset (e.g., the number of cars)

![rmse](images/09_rmse_01_rmse.png)

### RMSE Python Implementation

```python
def rmse(y, y_pred):
    se = (y - y_pred) ** 2
    mse = se.mean()
    return np.sqrt(mse)
```

Using this function, we can calculate RMSE for our training data:

```python
rmse(y_train, y_pred)
>> 0.7554192603920132
```

_[Back to the top](#root-mean-squared-error)_