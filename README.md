# diabetes-prediction-ml

# Diabetes Status Classification Using Machine Learning and Deep Learning

## Project Overview

This project compares traditional machine-learning and deep-learning models for classifying diabetes status using demographic, lifestyle, and health-related indicators. It explores how data-driven insights might inform awareness-oriented wellness assessment as part of a broader mission to improve chronic disease awareness, prevention, and management.

The project is an educational machine-learning study. Its models are not clinically validated and should not be used to diagnose diabetes or guide individual medical decisions.

## Research Question

How effectively can traditional machine-learning and deep-learning models classify diabetes status using demographic, lifestyle, and health indicators, and how might data-driven insights from these models inform awareness-oriented wellness assessment?

## Dataset

The project uses the publicly available [Diabetes Prediction Dataset on Kaggle](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset).

The original dataset contains 100,000 records and nine columns: eight input features and one binary target variable, `diabetes`.

**Input features**
- Gender
- Age
- Hypertension
- Heart disease
- Smoking history
- Body mass index (BMI)
- HbA1c level
- Blood glucose level

**Target variable:** `diabetes` (0 = no diabetes, 1 = diabetes).

### Data preparation

Exploratory data analysis was used to inspect missing values, duplicates, feature distributions, and class balance. The dataset contained no missing values. After removing 3,854 exact duplicate rows, 96,146 records remained.

The cleaned data was divided into stratified training, validation, and test sets. Categorical features were one-hot encoded, and numerical features were standardized. Preprocessing was fitted on the training data to avoid information leakage from the validation and test sets.

## Models and Experiments

Seven experimental configurations were compared:

1. Logistic Regression baseline
2. Random Forest baseline
3. Tuned Random Forest
4. Histogram-based Gradient Boosting baseline
5. Threshold-tuned Histogram-based Gradient Boosting
6. Neural Network baseline
7. Class-weighted Neural Network

Randomized hyperparameter search was applied to the Random Forest model. Neural networks were implemented using TensorFlow/Keras. Class weighting was explored to address the imbalance between the two target classes. A decision threshold was selected using validation data for the Histogram-based Gradient Boosting model.

## Evaluation Metrics

Models were assessed using:

- Accuracy
- Precision
- Recall (sensitivity)
- F1-score
- ROC-AUC
- Confusion matrices

Precision and recall were considered alongside accuracy because the target classes were imbalanced and the consequences of false-negative predictions are important in a health-related classification problem.

## Key Results

The selected threshold-tuned Histogram-based Gradient Boosting model achieved the following results on the held-out test set:

| Metric | Test result |
|---|---:|
| Accuracy | 97.18% |
| Precision | 97.48% |
| Recall (sensitivity) | 69.89% |
| F1-score | 81.41% |
| ROC-AUC | 97.70% |
| Specificity | 99.83% |

The model classified most negative examples correctly and had high precision. However, it missed 383 diabetes-positive examples in the test set. Therefore, accuracy alone does not provide a complete picture of model performance.

See the notebook for the full experimental comparison, visualizations, confusion matrices, and evaluation details.

## Mission Alignment

This work aligns with the broader goal of improving chronic disease awareness, prevention, and management through accessible, data-driven health solutions. It investigates how patterns in health data can be analyzed as a potential contribution to awareness-oriented wellness assessment.

The dataset does not directly measure health awareness, wellness knowledge, or future diabetes onset. Therefore, this project does not establish that its models improve awareness or prevent diabetes.

## Limitations and Future Work

- HbA1c and blood glucose levels are strongly associated with diabetes status and may provide diagnostic signals rather than early pre-diagnostic risk information.
- The dataset has not been established as representative of Rwanda or any particular local population.
- The selected model has not undergone external clinical validation.
- The decision threshold reflects a trade-off between precision and recall; the model missed 383 positive test examples at the selected threshold.
- Further work could explore appropriate pre-diagnostic features, local data validation, model calibration, interpretability, and collaboration with healthcare professionals and communities.

## Repository Contents

- `diabetes_prediction.ipynb` — notebook containing data preparation, experiments, model evaluation, and visualizations.
- `README.md` — project overview and documentation.
- `requirements.txt` — Python library dependencies and versions.
- `model_comparison_validation.csv` — validation results comparing the seven experimental configurations, if included in the repository.

Trained models and the raw dataset are stored separately in Google Drive rather than committed to this repository.

## Reproducibility and Access

- **Notebook:** Available in this repository.
- **Dataset:** [Kaggle Diabetes Prediction Dataset](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset)
- **Google Drive artifacts and raw dataset ZIP:** (https://drive.google.com/drive/folders/1phQsq_0yVsNzvCBRrdY6D_jAjTSog6i3?usp=sharing)
- **Demonstration video:** [Insert your video link when available]

To reproduce the experiments, download the dataset from Kaggle, install the dependencies listed in `requirements.txt`, and run the notebook in an environment compatible with the listed library versions.

--END--
