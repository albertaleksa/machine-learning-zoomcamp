>[Back to Week Menu](README.md)
>
>Previous Theme: [CRISP-DM](04_crisp_dm.md)
>
>Next Theme: [Setting up the Environment](06_environment.md)

## Model Selection Process
_[Video source](https://www.youtube.com/watch?v=OH_R0Sl9neM&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=6)_

_[Slides](https://www.slideshare.net/AlexeyGrigorev/ml-zoomcamp-15-model-selection-process)_

### Introduction
The process of selecting the best model.


### Holdout + Train
Take a portion of DATA (e.g., 20%) and hide it. Use only remaining 80% for **Training**. The 20% is used for **Validation**.
![hide](images/05_model_selection_process_01_hide.png)


### Making Predictions
Extract the  **Feature Matrix (X)** and **Target (y)** from *Training DATA* and train our **Model(g)**.
<br>Then, from the *Validation DATA* extract another **Feature Matrix ($X_v$)** and **Target ($y_v$)** which our Model hasn't seen.
<br>After that, apply our **Model(g)** to the *Validation* dataset and get some predictions $\hat{y}$ and compare them with **Target($y_v$)**.
<br>
<br>$g(X_v)=\hat{y}_v$
![making_predictions](images/05_model_selection_process_02_making_predictions.png)

As a result of camparing, we obtain accuracy for our model:
![model_accurate](images/05_model_selection_process_03_model_accurate.png)


### Scoring
Repeat the process for different types of models and choose the model with the best accuracy:
* Logistic Regression
* Decision Tree
* Random Forest
* Neural Network

![accuracy](images/05_model_selection_process_04_accuracy.png)

### Multiple Comparisons Problem
A model might be lucky and achieve good predictions by chance since these methods are probabilistic.
![probabilistic](images/05_model_selection_process_05_probabilistic.png)


### Train + Validation + Test
To address the above problem, instead of holding 1 dataset, we hold 2 datasets. We split the dataset into:
* Training
* Validation
* Test

Then, find the best Model using the **Trining** and **Validation** datasets.Apply this Model to the **Test** dataset to ensure that the Model chosen is actually the best one.

![train_val_test](images/05_model_selection_process_06_train_val_test.png)

### Further scoring
![further_scoring](images/05_model_selection_process_07_further_scoring.png)

### Model Selection (6 steps)
1. **Split** the Dataset into 3 parts.
2. **Train** a model.
3. Apply the Model to the **Validaion** dataset.
4. Repeat steps 2 and 3 multiple times for different Models and **Select** the best one.
5. Apply the best Model to the **Test** dataset.
6. **Check** if everything is satisfactory.
![model_selection](images/05_model_selection_process_08_model_selection.png)

In this approach, we use the **Validation** dataset only once. Thus, we combain the **Training** and **Validation** datasets and retrain our best model with them (between steps 4 and 5). This should help improve the model.
![combain](images/05_model_selection_process_09_combain.png)


_[Back to the top](#model-selection-process)_