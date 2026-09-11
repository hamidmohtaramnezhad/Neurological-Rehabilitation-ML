# Predicting Functional Outcomes in Neurological Rehabilitation Using Machine Learning

## Overview

Functional improvement is one of the main goals of neurological rehabilitation. Predicting a patient's functional status after rehabilitation may help clinicians better understand expected outcomes and identify factors related to recovery.

In this project, I applied machine learning regression methods to predict the **discharge Barthel Index (BI)** using information available at the beginning of rehabilitation.

The main research question was:

> Can machine learning predict discharge functional status from demographic, clinical, and functional information collected at admission?

---

## Dataset

This project used the neurological rehabilitation dataset published by Seccia et al [1].

The dataset includes information from **1,575 patients undergoing neurological rehabilitation**, including:

- Demographic characteristics
- Main neurological diagnosis
- Associated pathologies
- Impairment-related variables
- Barthel Index measurements at admission and discharge

The target variable was:

- **Discharge Barthel Index (`COD_26`)**

The predictor variables included information available at admission:

- Demographic variables
- Clinical characteristics
- Impairment variables
- Admission Barthel Index (`COD_25`)

To avoid data leakage, all discharge-related variables were excluded from the prediction models.

---

## Why this project?

As an occupational therapist interested in the application of data science in rehabilitation, I wanted to explore how routinely collected rehabilitation data can be used with machine learning methods.

This project focuses on a clinically meaningful outcome (functional independence) while providing practical experience in preparing real-world healthcare data and developing predictive models.

---

## Methods

The following regression models were compared:

1. Mean baseline model
2. Linear Regression using admission Barthel Index only
3. Linear Regression using all admission variables
4. Random Forest Regression
5. Regularized Random Forest Regression

The dataset was divided into training and testing sets using an 80/20 split.

Model performance was evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² score

Additional analyses included:

- Feature importance analysis
- Evaluation of model overfitting
- Residual analysis

---

## Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Mean baseline | 19.90 | 23.43 | -0.005 |
| Linear Regression (Admission BI only) | 13.95 | 16.81 | 0.482 |
| Linear Regression (All admission variables) | 13.36 | 16.38 | 0.509 |
| Random Forest | 12.91 | 16.11 | 0.524 |
| **Regularized Random Forest** | **12.96** | **15.90** | **0.537** |

The regularized Random Forest achieved the best overall performance on the test set.

The model explained approximately **54% of the variance** in discharge Barthel Index, with an average prediction error of approximately **13 BI points**.

---

## Main Findings

Admission Barthel Index was the strongest predictor of discharge Barthel Index.

Other variables, including age, neurological diagnosis, and impairment-related characteristics, provided additional information, but their contribution was considerably smaller.

This suggests that the patient's functional status at admission contains most of the predictive information about their functional status at discharge within this dataset.

---

## Visualizations

The project includes:

- Distribution of admission and discharge Barthel Index
- Relationship between admission and discharge functional status
- Actual vs. predicted discharge BI
- Residual analysis
- Feature importance analysis

---

## Limitations

This dataset had already been processed by the original authors before being used in this project. Their preprocessing procedure excluded some patients based on rehabilitation-related outcomes, including patients who did not improve or whose Barthel Index decreased.

Therefore, the dataset may not represent all patients receiving neurological rehabilitation.

Another limitation is that model evaluation was performed using a single train-test split. Cross-validation and external validation with independent rehabilitation populations would provide a more reliable evaluation.

Therefore, this model should be considered an exploratory machine learning analysis rather than a clinically validated prediction tool.

---

## What I Learned

Through this project, I gained practical experience in:

- Preparing clinical rehabilitation data for machine learning
- Exploratory data analysis
- Regression modeling
- Comparing machine learning algorithms
- Detecting and reducing overfitting
- Interpreting model predictions
- Connecting machine learning methods with rehabilitation questions

---

## Tools

- Python
- pandas
- NumPy
- matplotlib
- scikit-learn
- Jupyter Notebook

---

## Reference

[1] Seccia, et al. (2020). *Data of patients undergoing rehabilitation programs*. Data in Brief, 30, Article 105419. https://doi.org/10.1016/j.dib.2020.105419

The dataset is publicly available through Figshare.

---

## Project Structure

Neurological-Rehabilitation-ML/

│
├── Neurological_Rehabilitation_ML.ipynb
│
├── README.md
│
├── figures/
│   ├── admission_discharge_bi.png
│   ├── actual_vs_predicted.png
│   ├── feature_importance.png
│   └── residual_plot.png
│
└── requirements.txt
