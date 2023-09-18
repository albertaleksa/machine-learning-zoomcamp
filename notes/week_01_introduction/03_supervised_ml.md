>[Back to Week Menu](README.md)
>
>Previous Theme: [ML vs Rule-Based Systems](02_ml_vs_rule_based.md)
>
>Next Theme: [CRISP-DM](04_crisp_dm.md)

## Supervised Machine Learning
_[Video source](https://www.youtube.com/watch?v=j9kcEuGcC2Y&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=4)_

_[Slides](https://www.slideshare.net/AlexeyGrigorev/ml-zoomcamp-13-supervised-machine-learning)_


### Explanation
![explanation](images/03_supervised_ml_01_feature_matrix.png)


Train a **Model (function g)** using the **Feature Matrix (X)** to approximate the **Target (y)** as closely as possible

![definition](images/03_supervised_ml_02_definition.png)

For example, consider spam emails:
![spam](images/03_supervised_ml_03_spam.png)


### Types of Supervised Machine Learning problems
* **Regression**
<br> The *Target* is a **value**. The model (g) returns a value (y). This type is used to predict numerical values, like price.
![regression](images/03_supervised_ml_04_regression.png)

* **Classification**
<br> Tee *Target* ia a **category**. For instance, classifying an image as a picture of a car.
![classification](images/03_supervised_ml_05_classification.png)
    * *Binary classification*. 2 categories.
    * *Multiclass classification*. More than 2 categories.
    ![classification_types](images/03_supervised_ml_06_classification_types.png)

* **Ranking**
<br> Used in scenarios where ranking is essential, such as recommender systems.
![ranking](images/03_supervised_ml_07_ranking.png)


_[Back to the top](#supervised-machine-learning)_