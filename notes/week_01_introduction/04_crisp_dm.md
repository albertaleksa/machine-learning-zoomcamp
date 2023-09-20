>[Back to Week Menu](README.md)
>
>Previous Theme: [Supervised Machine Learning](03_supervised_ml.md)
>
>Next Theme: [Model Selection Process](05_model_selection_process.md)

## CRISP-DM
_[Video source](https://www.youtube.com/watch?v=dCa3JvmJbr0&list=PL3MmuxUbc_hIhxl5Ji8t4O6lPAOpHaCLR&index=5)_

_[Slides](https://www.slideshare.net/AlexeyGrigorev/ml-zoomcamp-14-crispdm)_


### Explanation
CRISP-DM (Cross-Industry Standard Process for Data Mining) is a methodology that outlines how ML projects should be organized.
![methodology](images/04_crisp_dm_01_methodology.png)

There are 6 steps in this methodology:
1. **Business understanding**
<br>Identify the problem we want to solve. Ask a question: Do we actually need ML here?
![business_problem](images/04_crisp_dm_02_business_problem.png)
Define the goal. The **goal** should be *measurable*.
![business_goals](images/04_crisp_dm_03_business_goals.png)

2. **Data understanding**
<br>Analyze available data sources and determine if more data is needed.
![data_understanding](images/04_crisp_dm_04_data_understanding.png)
Understanding the data can provide insights into the business problem, influencing the goal. We can then revisit the previous step and adjust it.
![data_understanding2](images/04_crisp_dm_05_data_understanding2.png)

3. **Data preparation**
<br>Transform data to be compatible with ML algorithms.
![data_preparation](images/04_crisp_dm_06_data_preparation.png)
Clean the data, remove noise, and build a data pipeline.
![data_preparation_ex](images/04_crisp_dm_07_data_preparation_ex.png)
The result of this step will be **X (Featues)** and **y (Target)**.

4. **Modeling**
    * Training a model:
        * Try different models
        * Select the best one
    * Which model to choose?
        * Logistic regression
        * Decision tree
        * Neural network
        * Or many others
    * Sometimes, we may go back to data preparation:
        * Add new features
        * Fix data issues


5. **Evaluation**
<br>Measure how well the model solves the business problem.
![evaluation](images/04_crisp_dm_08_evaluation.png)
Compare the result with the goal set during the *Business understanding* phase. If necessary, adjust the goal or terminate the project.
![evaluation_2](images/04_crisp_dm_09_evaluation2.png)

6. **Deployment**
<br>Often *Evaluation* and *Deployment* comes together.
![evaluation_deployment](images/04_crisp_dm_10_evaluation_deployment.png)
<br>Typically, evaluate the model on a subset of users (e.g., 5%). If the model performs well, roll it out to the remaining users.
![deployment](images/04_crisp_dm_11_deployment.png)


**Iterate**
<br>After deployment we iterate (maybe want to improve goal or find new goals for *Business understanding*)
![iterate](images/04_crisp_dm_12_iterate.png)

Iteration process
![iteration_process](images/04_crisp_dm_13_iteration_process.png)

### Summary
![summary](images/04_crisp_dm_14_summary.png)
![summary2](images/04_crisp_dm_15_summary2.png)

_[Back to the top](#crisp-dm)_