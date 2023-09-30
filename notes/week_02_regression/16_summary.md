>[Back to Week Menu](README.md)
>
>Previous Theme: [Using the model](15_using_model.md)
>
>Next Theme: [Explore more](17_explore_more.md)

## Car Price Prediction Project Summary
_[Video source](https://www.youtube.com/watch?v=vM3SqPNlStE&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=27)_


### Project Summary

In this project, we predicted car prices (MSRP) using various characteristics such as the model, make, year, engine horsepower, etc. Here's a summary of the 

1. Cleaned the dataset by replacing spaces with underscores and converting text to lowercase.
2. Conducted Exploratory Data Analysis and identified that the price has a long-tail distribution. We applied a logarithmic transformation to the data to address this, as machine learning models often struggle with long-tail distributions.
3. Established a Validation Framework by splitting the data into **TRAIN**, **VALIDATION**, and **TEST** datasets.
4. Implemented Linear Regression. The outcome of Linear Regression is a vector of weights.
5. Utilized this implementation to train the model.
6. Implemented a metric (Root Mean Squared Error, or RMSE) to measure the model's performance. RMSE is commonly used for evaluating the quality of regression models.
7. Built a Validation Framework by creating a function **prepare_X()**. This function standardizes the way we prepare the Feature Matrix for different datasets (TRAIN, VALIDATION).
8. Engaged in simple Feature Engineering, creating new features from existing ones.
9. Integrated categorical variables by using binary features.
10. Noticed a significant degradation in model performance, indicated by a high RMSE, likely due to numerical instability.
11. Applied regularization to address the numerical instability, adding a small number to the diagonal of the $X^T X$ matrix before inverting it. This improved the model's performance.
12. Experimented with different values for the regularization parameter to identify the optimal setting.
13. Combined the **TRAIN** and **VALIDATION** datasets to train the final model. We validated the model on the **TEST** dataset and compared the RMSE to previous results.
14. Finally, we applied the model to a car from the TEST dataset whose price was unknown, and compared the predicted price to the actual price.

_[Back to the top](#car-price-prediction-project-summary)_