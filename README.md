# Rain Prediction Using Machine Learning

This repository contains a Machine Learning course project focused on predicting whether it will rain based on weather-related features. The project applies an end-to-end machine learning workflow, including exploratory data analysis, preprocessing, model training, hyperparameter tuning, evaluation, and feature importance analysis.

## Project Overview

The objective of this project is to build a binary classification model that predicts the target variable `Rain`, which has two classes:

- `rain`
- `no rain`

The dataset contains 2,500 observations and 6 variables. Five variables are numerical input features, while one variable is the target label. The input features include:

- Temperature
- Humidity
- Wind_Speed
- Cloud_Cover
- Pressure

The project was developed as part of a Machine Learning course.

## Dataset Summary

The dataset includes:

| Item | Description |
|---|---|
| Number of observations | 2,500 |
| Number of input features | 5 |
| Target variable | Rain |
| Task type | Binary Classification |
| Missing values | 0 |
| Duplicate records | 0 |

The target variable is imbalanced:

| Class | Count | Percentage |
|---|---:|---:|
| no rain | 2,186 | 87.44% |
| rain | 314 | 12.56% |

Because of this class imbalance, the project does not rely only on accuracy. Additional metrics such as Precision, Recall, F1-score, and ROC-AUC are used to evaluate model performance.

## Exploratory Data Analysis

The EDA process includes:

- Checking dataset structure and data types
- Detecting missing values and duplicate records
- Analyzing class distribution of the target variable
- Computing descriptive statistics of numerical features
- Visualizing feature distributions using histograms and boxplots
- Analyzing correlations between input features and the target variable
- Comparing feature distributions between `rain` and `no rain` classes

The EDA results show that the most informative features for rain prediction are:

- Humidity
- Cloud_Cover
- Temperature

These features show clearer differences between the `rain` and `no rain` classes compared with Wind_Speed and Pressure.

## Data Preprocessing

The preprocessing workflow includes:

1. Encoding the target variable:
   - `no rain` → 0
   - `rain` → 1

2. Defining input features and target variable:
   - `X = Temperature, Humidity, Wind_Speed, Cloud_Cover, Pressure`
   - `y = Rain`

3. Splitting the dataset:
   - 80% training set
   - 20% test set

4. Using stratified splitting to preserve class distribution.

5. Applying Stratified K-Fold Cross-Validation with `K = 10`.

6. Applying feature scaling for scale-sensitive models such as SVM and Neural Network.

## Model

The main model used in this project is:

- Random Forest Classifier

Random Forest was selected because it performs well on tabular data, can capture non-linear relationships, does not require feature scaling, and provides feature importance for model interpretation.

## Hyperparameter Tuning

GridSearchCV was used to tune the Random Forest model.

The tested hyperparameters include:

- `n_estimators`: 100, 200
- `max_depth`: None, 5, 10
- `min_samples_split`: 2, 5, 10
- `min_samples_leaf`: 1, 2, 4

The tuning process used F1-score as the main scoring metric due to the class imbalance in the dataset.

## Evaluation Metrics

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix

## Results

The Random Forest model achieved the following performance on the test set:

| Metric | Score |
|---|---:|
| Accuracy | 1.00 |
| ROC-AUC | 1.00 |
| Precision | 1.00 |
| Recall | 1.00 |
| F1-score | 1.00 |

Confusion Matrix:

```text
[[437, 0],
 [  0, 63]]