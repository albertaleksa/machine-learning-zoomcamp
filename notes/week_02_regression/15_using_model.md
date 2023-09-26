>[Back to Week Menu](README.md)
>
>Previous Theme: [Tuning the model](14_tuning_model.md)
>
>Next Theme: [Car price prediction project summary](16_summary.md)

## Using the model
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=26)_


### Training final model on full dataset

We splitted our Dataset into 3 parts:
* TRAIN
* VALIDATION
* TEST

Then we were training our Model on the **TRAIN**ing dataset, applying this Model on **VALIDATION** dataset and then getting **RMSE**.

![train_val](images/15_using_model_01_train_val.png)

Now we instead of that we train a Model on the entire part that we use for both **TRAIN**ing and **VALIDATION** (**FULL TRAIN**), apply this Model on **TEST** dataset and get **RMSE**.


![full_train](images/15_using_model_02_full_train.png)


### Combine train and test data frames

Combine **TRAIN** and **VAL** datasets and reset indeces

```python
df_full_train = pd.concat([df_train, df_val])

df_full_train = df_full_train.reset_index(drop=True)
```

Prepare **Feature Matrix X**:
```python
X_full_train = prepare_X(df_full_train)
```

Concatenate **Targets** from **TRAIN** and **VAL**:

```python
y_full_train = np.concatenate([y_train, y_val])
```

Train our Model using combined datasets:

```python
w0, w = train_linear_regression_reg(X_full_train, y_full_train, r=0.001)
```

Prepare **TEST** dataset and validate:

```python
X_test = prepare_X(df_test)
y_pred = w0 + X_test.dot(w)

score = rmse(y_test, y_pred)
score
```

![score_test](images/15_using_model_03_score_test.png)

Our Model is not too different from previous. RMSE is almost the same. It means that our Model can generalize well, that this score didn't get by chance.


### Use Final Model to predict

We can use our Model to predict a price for car.

We have a car. Then we extract Feautures from the car and put it in our Final Model. Then we should predict a price.

![predict_price](images/15_using_model_04_predict_price.png)

### Predict a car price

We can utake any car from **TEST** dataset (It's OK, because we haven't seen this car during training):

![car_info](images/15_using_model_05_car_info.png)

![web_example](images/15_using_model_06_web_example.png)


```python
car = df_test.iloc[20].to_dict()
car
```

Create DataFrame for 
```python
df_small = pd.DataFrame([car])
df_small
```


```python
X_small = prepare_X(df_small)
```

```python
y_pred = w0 + X_small.dot(w)
y_pred = y_pred[0]
y_pred
```

Predicted price:
```python
np.expm1(y_pred)
>> 34983.19702059413
```

Real price:
```python
np.expm1(y_test[20])
>> 35000.00000000001
```

![car_price](images/15_using_model_07_car_price.png)

_[Back to the top](#using-the-model)_