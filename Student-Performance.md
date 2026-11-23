# Student Performance Prediction Using Machine Learning

## 1. Introduction

Student performance is an important aspect of education. Identifying students who may be at risk of failing can help educators provide academic support earlier.

This project uses supervised machine learning to predict whether a student will Pass or Fail based on selected academic and behavioural information.

A Decision Tree Classifier was developed using Python and Scikit-learn.

## 2. Project Objectives

The objectives are to:

- Explore and understand student performance data.
- Identify patterns in student academic information.
- Prepare data for machine learning.
- Build a classification model to predict Pass or Fail.
- Evaluate the model using appropriate performance metrics.
- Use the trained model to make predictions for sample students.

## 3. Dataset Description

The project uses the Portuguese language student performance dataset (`student-por.csv`).

The dataset contains:
- 649 student records.
- 33 original columns.
- Academic, demographic and behavioural information.

Each row represents one student.

The target variable, `result`, was created from the final grade (`G3`):

- Pass: G3 greater than or equal to 10.
- Fail: G3 below 10.

The resulting class distribution was:

| Result | Students |
|---|---:|
| Pass | 549 |
| Fail | 100 |
| Total | 649 |

## 4. Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Joblib
- Jupyter Notebook

## 5. Data Preparation

The dataset was loaded using Pandas and inspected to understand its structure.

Exploratory checks were performed for missing values and duplicate records. No missing values or duplicate records were reported in the dataset checks.

Five features were selected for model training:

1. `studytime`
2. `absences`
3. `failures`
4. `G1`
5. `G2`

The target variable was `result`.

The final grade (`G3`) was excluded from the input features because it was used to create the target variable. Including it would reveal the answer the model is supposed to predict.

The data was divided into:
- 80% training data: 519 students.
- 20% testing data: 130 students.

Stratified splitting was used to preserve the approximate Pass/Fail proportions.

## 6. Exploratory Data Analysis

Exploratory data analysis was performed to understand the dataset and identify relevant patterns.

The analysis included:

- Distribution of Pass and Fail students.
- Distribution of students by study-time category.
- Correlation between G1, G2 and G3 grades.
- Distribution of student absences.

These visualizations helped explore the relationship between student information and academic performance.

## 7. Model Development

A Decision Tree Classifier was selected for the classification task.

An initial unrestricted Decision Tree achieved:
- Training accuracy: 98.84%.
- Testing accuracy: 89.23%.

The difference between training and testing performance suggested overfitting.

The maximum depth was therefore adjusted and several tree configurations were compared.

A maximum depth of 4 produced the strongest testing accuracy among the configurations evaluated.

## 8. Cross-Validation

Five-fold stratified cross-validation was performed on the training dataset to examine model consistency.

The average results were:

| Metric | Average |
|---|---:|
| Accuracy | 91.3% |
| Fail Precision | 73.7% |
| Fail Recall | 72.5% |
| Fail F1-score | 72.0% |

These results provide an estimate of performance across five different validation folds.

## 9. Model Evaluation

The selected depth-4 Decision Tree produced the following confusion matrix on the test set:

| | Predicted Fail | Predicted Pass |
|---|---:|---:|
| Actual Fail | 15 | 5 |
| Actual Pass | 5 | 105 |

The model correctly classified 120 out of 130 students.

Test-set accuracy: **92.31%**

For the Fail class:
- Precision: 75%.
- Recall: 75%.
- F1-score: 75%.

The model correctly identified 15 of the 20 students who actually failed.

## 10. Decision Tree Interpretation

The Decision Tree visualization showed that `G2` was selected as the root feature.

The first split was:

`G2 <= 8.5`

The model then used other features, including `G1`, `failures`, `studytime` and `absences`, to make further classification decisions.

This indicates that earlier academic grades played an important role in the model's prediction process.

The tree provides an interpretable representation of how the classifier makes decisions.

## 11. Sample Predictions

The trained model was tested using three hypothetical student records.

| Studytime | Absences | Failures | G1 | G2 | Prediction |
|---:|---:|---:|---:|---:|---|
| 2 | 2 | 0 | 14 | 15 | Pass |
| 3 | 5 | 0 | 10 | 11 | Pass |
| 1 | 15 | 2 | 5 | 6 | Fail |

The model successfully generated predictions for all three sample records.

## 12. Limitations

- The dataset contains students from Portuguese secondary schools. Its results cannot automatically be generalized to Nigerian students or university populations.
- The dataset contains only 649 records.
- The class distribution is imbalanced, with more Pass cases than Fail cases.
- Predictions are not guarantees of future academic outcomes.
- The test set was used during the comparison of different tree depths. Therefore, its final accuracy should be treated as a provisional estimate rather than a completely independent final evaluation.

## 13. Conclusion

This project demonstrated how supervised machine learning can be applied to student performance classification.

A Decision Tree Classifier was developed using five selected features to predict student outcomes.

The selected depth-4 model achieved 92.31% accuracy on the test split, while five-fold cross-validation produced an average accuracy of 91.3%.

The model also achieved an average Fail recall of 72.5% during cross-validation, showing its ability to identify a useful proportion of students who may be at risk of failing.

The project demonstrates the potential of machine learning as a tool for academic performance analysis and early identification of students who may need additional support.