>[Back to Week Menu](README.md)
>
>Previous Theme: [Using the model](15_using_model.md)
>
>Next Theme: [Explore more](17_explore_more.md)

## Car price prediction project summary
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=27)_


### Summary project

We did the project that predicting the prices of cars (MSRP) using other characteristics (Model, make, year, engine hp, ..).

1. Cleaned dataset (replaced spaces to '_', convert to lower case)
2. Did Exploratery Data Analysis and identify that we have a long tail distribution of the price. Removed a long tail by applying the logarithmic transformation to data. Because Usually ML Models has problems with a long tail distribution.
3. Did a Validation Framework. Split data between **TRAIN**, **VALIDAION** and **TEST** datasets.
4. Implemented Linear Regression. The result of Linear Regression is the weights vector.
5. Implemented the train ML Model using Normal equation formula.
6. Used this implemetation to train a Model.
7. Implemeted the metric to measure the performance of a Model (Root mean squared error). it's a metric for evaluating the quality of a regression model.
8. Build a Validation Framework. Created a function **prepare_X()**, which allowed to have the same way of preparing Feature Matrix for different datasets (TRAIN, VAL).
9. Did simple Feature engineering - the process of creating new features from existing ones.
10. Looked how to integrate the categorical variables, using bunch of binary features.
11. Then performance of our Model degrated significantly (a huge RMSE), because of the numerical instability.
12. We used regularization to solve he numerical instability. We added a small number to the diagonal of Matrix XTX before inverting it. Performance of the Model was increased.
13. We tried different values of the regularization parameter to find out the best one.
14. Combined **TRAIN** and **VAL** datasets to train a Final Model. Validated Model on the **TEST** dataset and compared RMSE with previous.
15. Applied a Model to car which we don't know the price (from TEST dataset) and compared a predicted price with real.


_[Back to the top](#car-price-prediction-project-summary)_