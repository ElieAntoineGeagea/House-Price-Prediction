# House Price Prediction

## Project Overview

This project predicts house sale prices using the Kaggle Ames Housing dataset: **House Prices - Advanced Regression Techniques**.

The goal of this project is to build a complete machine learning regression workflow, starting from raw data and ending with a final Kaggle submission file.

## Dataset

Dataset used: Kaggle House Prices - Advanced Regression Techniques

The target variable is:

```text
SalePrice
```

## Problem Type

This is a **supervised regression problem**.

The model learns from houses with known sale prices and predicts sale prices for unseen houses.

## Project Workflow

The project was completed in the following phases:

1. Data acquisition and project setup
2. Data understanding
3. Exploratory data analysis
4. Data preprocessing and feature preparation
5. Baseline modeling
6. Advanced modeling
7. Model tuning
8. Final prediction and submission

## Exploratory Data Analysis

During EDA, the target variable `SalePrice` was found to be right-skewed.

Several features showed strong relationships with house price, including:

- `OverallQual`
- `GrLivArea`
- `GarageCars`
- `GarageArea`
- `TotalBsmtSF`
- `1stFlrSF`
- `FullBath`
- `YearBuilt`

The analysis showed that higher-quality, larger, and newer houses generally sell for higher prices.

## Preprocessing

The preprocessing phase included:

- Handling missing values
- Filling missing categorical values where `NaN` represented absence
- Filling numerical missing values
- Encoding ordinal quality features
- One-hot encoding remaining categorical features
- Aligning train and test datasets
- Applying log transformation to the target variable
- Applying log transformation to selected skewed numerical features
- Creating new engineered features

Engineered features included:

- `TotalSF`
- `TotalBath`
- `HouseAge`
- `RemodAge`
- `HasGarage`
- `HasBasement`
- `HasPool`

## Models Tested

The following models were trained and evaluated:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regressor
- Gradient Boosting Regressor

## Model Results

| Model | RMSE_log | R² |
|---|---:|---:|
| Linear Regression | 0.122468 | 0.919628 |
| Ridge Regression | 0.121067 | 0.921455 |
| Lasso Regression | 0.134539 | 0.903003 |
| Random Forest | 0.143376 | 0.889842 |
| Gradient Boosting | 0.136969 | 0.899468 |

## Best Model

The best model was:

```python
Ridge(alpha=0.1)
```

After tuning Ridge Regression, the best alpha value was:

```text
alpha = 0.1
```

## Final Results

The tuned Ridge Regression model achieved:

| Metric | Value |
|---|---:|
| Validation RMSE_log | 0.120909 |
| Validation R² | 0.921660 |
| Cross-validation mean RMSE_log | 0.138800 |
| Cross-validation standard deviation | 0.019000 |

The final model was trained on the full processed training dataset and used to generate predictions for the Kaggle test dataset.

The final submission file was saved as:

```text
data/processed/submission.csv
```

Submission shape:

```text
(1459, 2)
```

## Tools Used

- Python
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- Git
- GitHub
- Jupyter Notebook
- VS Code

## Project Structure

```text
house-price-prediction/
├── data/
│   ├── raw/
│   └── processed/
├── models/
├── notebooks/
│   ├── 01_data_understanding.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_preprocessing.ipynb
│   ├── 04_baseline_modeling.ipynb
│   ├── 05_advanced_modeling.ipynb
│   └── 06_model_tuning.ipynb
├── README.md
└── .gitignore
```

## How to Run the Project

1. Clone the repository.
2. Download the dataset from Kaggle.
3. Place the raw files inside:

```text
data/raw/
```

4. Run the notebooks in order:

```text
01_data_understanding.ipynb
02_eda.ipynb
03_preprocessing.ipynb
04_baseline_modeling.ipynb
05_advanced_modeling.ipynb
06_model_tuning.ipynb
```

5. The final submission file will be created in:

```text
data/processed/submission.csv
```

## Conclusion

This project demonstrates a full machine learning regression workflow for predicting house prices.

The best-performing model was Ridge Regression with `alpha=0.1`. Regularized linear regression performed better than the tested tree-based models, showing that the processed features captured strong linear relationships with house prices.