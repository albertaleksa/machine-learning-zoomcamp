>[Back to Week Menu](README.md)
>
>Previous Theme: [Regularization](13_regularization.md)
>
>Next Theme: [Using the model](15_using_model.md)

## Tuning the Model
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=25)_


### Finding the Best Regularization Parameter

We will use the validation dataset to find the best value for the regularization parameter. We'll try a range of different values: \([0.0, 0.00001, 0.0001, 0.001, 0.1, 1, 10]\).

```python
for r in [0.0, 0.00001, 0.0001, 0.001, 0.1, 1, 10]:
    X_train = prepare_X(df_train)
    w0, w = train_linear_regression_reg(X_train, y_train, r=r)

    X_val = prepare_X(df_val)
    y_pred = w0 + X_val.dot(w)

    score = rmse(y_val, y_pred)
    
    print(r, w0, score)
```
![find_r](images/14_tuning_model_01_find_r.png)

The regularization parameter $r=0.001$ appears to be a good choice.

Train the model using this optimal regularization parameter:
```python
r=0.001
X_train = prepare_X(df_train)
w0, w = train_linear_regression_reg(X_train, y_train, r=r)

X_val = prepare_X(df_val)
y_pred = w0 + X_val.dot(w)

rmse(y_val, y_pred)
```

The next step is to validate the model using the **TEST** dataset.

_[Back to the top](#tuning-the-model)_