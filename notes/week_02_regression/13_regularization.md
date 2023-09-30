>[Back to Week Menu](README.md)
>
>Previous Theme: [Categorical variables](12_categorical_variables.md)
>
>Next Theme: [Tuning the model](14_tuning_model.md)

## Regularization
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=24)_


### Problem Description - Linear Combination

The formula for the normal equation is:

$w = (X^TX)^{-1} \cdot X^Ty$

Sometimes we can get an incorrect result for $w$.

The problem arises when $(X^TX)^{-1}$ doesn't exist. This can happen when matrix $X$ has duplicate columns (features).

Sometimes we don't get an error due to small numerical noise (e.g., one column contains '5', and another contains '5.000000001').

### Problem Solution - Regularization

To solve this problem, **add** a small number $\alpha$ to the diagonal of the matrix $(X^TX)$:


![alpha](images/13_regularization_01_alpha.png)

**Regularization** controls the weights to prevent them from growing too large.

We add to our $(X^TX)$ matrix an Identity matrix multiplied by a small number (parameter). The larger the number on the diagonal, the smaller the values in the Inverse matrix.

![regularization](images/13_regularization_02_regularization.png)

### Regularization Implementation

Modify the function **train_linear_regression(X, y)** to include regularization:

```python
def train_linear_regression_reg(X, y, r=0.001):
    ones = np.ones(X.shape[0])
    X = np.column_stack([ones, X])

    XTX = X.T.dot(X)
    XTX = XTX + r * np.eye(XTX.shape[0]) 
    
    XTX_inv = np.linalg.inv(XTX)

    w_full = XTX_inv.dot(X.T).dot(y)
    
    return w_full[0], w_full[1:]
```

Train the model with regularization:
```python
X_train = prepare_X(df_train)
w0, w = train_linear_regression_reg(X_train, y_train, r=0.01)

X_val = prepare_X(df_val)
y_pred = w0 + X_val.dot(w)

rmse(y_val, y_pred)
```

The result has improved:

![regularization_train](images/13_regularization_03_regularization_train.png)

The next step is to find the optimal value for the regularization parameter $r$.

_[Back to the top](#regularization)_