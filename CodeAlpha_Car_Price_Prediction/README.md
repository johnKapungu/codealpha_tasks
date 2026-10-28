# Car Price Prediction with Machine Learning

**Author:** John Afwilile Kapungu  
**Project:** Car Price Prediction with Machine Learning  
**Status:** Model development and evaluation completed; final model selection remains subject to residual analysis.

## 1. Project Overview

This project applies machine learning regression algorithms to predict the selling prices of used cars based on characteristics such as present price, manufacturing year, mileage, fuel type, transmission, selling type, and previous ownership.

The objective is to develop a predictive model that can help analyze used-car pricing patterns and support more informed pricing decisions.

## 2. Objectives

- Explore and clean the used-car dataset.
- Perform exploratory data analysis (EDA).
- Engineer additional features to improve model performance.
- Prepare numerical and categorical variables for machine learning.
- Train and compare regression algorithms.
- Tune Random Forest and Gradient Boosting hyperparameters.
- Evaluate prediction performance using MAE, RMSE, and R².
- Analyze residuals and identify large prediction errors.

## 3. Dataset Description

The dataset is provided in `car data.csv`.

The initial dataset contains **301 rows and 9 columns**, before any confirmed duplicate removal.

| Feature | Description |
|---|---|
| `Car_Name` | Name or model identifier of the car |
| `Year` | Manufacturing year |
| `Selling_Price` | Actual selling price; prediction target |
| `Present_Price` | Recorded present price |
| `Driven_kms` | Distance driven in kilometers |
| `Fuel_Type` | Fuel category |
| `Selling_type` | Dealer or individual selling category |
| `Transmission` | Transmission type |
| `Owner` | Previous ownership count/category |

The dataset was checked for missing values, duplicate records, invalid values, and potential outliers.

**Note:** Potential outliers were investigated rather than automatically removed, since extreme prices and mileage values may represent legitimate vehicles.

## 4. Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Joblib

## 5. Project Workflow

### Step 1: Data Loading and Inspection

Loaded the dataset and examined its dimensions, data types, feature distributions, and basic statistics.

### Step 2: Data Cleaning

- Checked for missing values.
- Identified duplicate records.
- Examined invalid or inconsistent values.
- Investigated potential outliers.

### Step 3: Exploratory Data Analysis

Explored relationships between selling price and other variables using descriptive statistics, correlation analysis, and visualizations.

### Step 4: Feature Engineering

Created additional features:

- `Car_Age`: calculated relative to the dataset's reference year, 2018.
- `Mileage_Per_Year`: estimated mileage per year of car age.

These features were introduced to help capture vehicle age and usage patterns.

### Step 5: Data Preparation

- Selected numerical and categorical features.
- Split the dataset into training and test sets using an 80/20 ratio.
- Imputed missing numerical values using the median.
- Scaled numerical features.
- One-hot encoded categorical variables.
- Used pipelines to integrate preprocessing with model training.

### Step 6: Model Training and Comparison

Trained and evaluated four regression algorithms:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosting Regressor

### Step 7: Hyperparameter Tuning

Applied `RandomizedSearchCV` with five-fold cross-validation to tune Random Forest and Gradient Boosting.

### Step 8: Residual Analysis

Examined actual versus predicted prices, residual distributions, and large prediction errors to assess model limitations.

## 6. Model Evaluation Results

### Initial model comparison

| Model | CV RMSE | Test MAE | Test RMSE | Test R² |
|---|---:|---:|---:|---:|
| Linear Regression | 1.5878 | 1.4342 | **2.7120** | **0.7146** |
| Gradient Boosting | 1.5740 | 1.2915 | 3.1271 | 0.6206 |
| Decision Tree | 2.2666 | 1.3608 | 3.2031 | 0.6019 |
| Random Forest | 1.5110 | 1.4633 | 3.5790 | 0.5030 |

### Results after hyperparameter tuning

| Model | CV RMSE | Test MAE | Test RMSE | Test R² |
|---|---:|---:|---:|---:|
| Linear Regression baseline | — | 1.4342 | **2.7120** | **0.7146** |
| Gradient Boosting (Tuned) | **1.3662** | **1.1845** | 2.9670 | 0.6584 |
| Random Forest (Tuned) | 1.5839 | 1.6303 | 4.0671 | 0.3582 |

*Lower MAE and RMSE indicate better performance; higher R² indicates better explanatory performance.*

### Interpretation

Linear Regression achieved the lowest test RMSE and highest test R² in the reported experiments. Tuned Gradient Boosting achieved the lowest test MAE and cross-validation RMSE among the tuned models.

These results illustrate that the model with the best average validation performance does not necessarily achieve the best performance on a particular test split.

**Current leading candidate:** Linear Regression, based on the reported test RMSE and R². Final model selection should consider residual analysis and additional validation.

The reported price metrics use the dataset's original price scale; the monetary unit should be confirmed from the dataset documentation.

## 7. Residual Analysis

Residuals were calculated as:

`Residual = Actual Selling Price - Predicted Selling Price`

The Linear Regression residual plot showed:

- Many residuals clustered around zero.
- Some substantial positive residuals, indicating underpredicted prices.
- Some substantial negative residuals, indicating overpredicted prices.
- At least one negative predicted selling price, which is not realistic for a car sale.

These findings suggest that the model may struggle with certain vehicles and that its predictions should be interpreted cautiously.

Potential next steps include inspecting the largest prediction errors, comparing residual patterns across models, and testing suitable transformations or alternative regression approaches.

## 8. Project Structure

The project can be organized as follows:

```text
car-price-prediction/
│
├── car data.csv
├── README.md
├── requirements.txt
├── .gitignore
└── notebook/
|   ├── car_price_prediction.ipynd
|   ├── EDA.ipynd
|   ├── Car_Price_Data_Cleaning.ipynb
│
└── car_price_outputs/
    ├── car_data_cleaned.csv
    ├── car_data_engineered.csv
    ├── model_comparison.csv
    ├── tuned_model_comparison.csv
    ├── model_comparison_rmse.png
    ├── tuned_model_comparison.png
    ├── actual_vs_predicted.png
    ├── linear_regression_residuals.png
    ├── linear_regression_residual_analysis.csv
    ├── largest_prediction_errors.csv
    ├── residual_comparison.png
    ├── best_model_predictions.csv
    └── best_tuned_car_price_model.joblib
```

The exact files in `car_price_outputs/` depend on which notebook cells have been executed successfully.

## 9. Installation and Setup

### Prerequisites

- Python 3.10 or newer recommended.
- Jupyter Notebook or JupyterLab.
- Git (optional, for version control).

### Clone the repository

```bash
git clone https://github.com/johnKapungu/CodeAlphaCar_Price_Prediction.git
cd CodeAlpha_Car_Price_Prediction
```

Replace `YOUR_USERNAME` with your GitHub username and adjust the repository URL to match your actual repository.

### Create a virtual environment

Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

Linux or macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Install dependencies

```bash
pip install -r requirements.txt
```

### Run the notebook

```bash
jupyter notebook
```

Open `car_price_prediction.ipynb` and execute the cells in order.

Ensure `car data.csv` is located in the expected directory before running the notebook.

## 10. Requirements

The principal Python dependencies are:

```text
pandas
numpy
matplotlib
scikit-learn
joblib
jupyter
```

For reproducible results, record the exact package versions used in the completed environment.

## 11. Limitations

- The dataset is relatively small, limiting the reliability of generalization estimates.
- Car name, brand reputation, condition, accident history, location, and other relevant factors may not be fully represented.
- Extreme observations can substantially influence RMSE.
- Negative predictions indicate that unconstrained Linear Regression may produce unrealistic estimates.
- The reported test results depend on the chosen train/test split.
- Predictions reflect the dataset's historical market context and should not be assumed to represent current market prices.

## 12. Future Improvements

- Perform more robust validation, including repeated or nested cross-validation.
- Investigate the largest prediction errors and verify data quality.
- Compare additional models, such as HistGradientBoostingRegressor.
- Evaluate log-transformed target regression if the price distribution is strongly skewed.
- Consider non-negative prediction constraints or other approaches that respect the nature of selling prices.
- Add explainability through feature importance or SHAP where appropriate.
- Develop a Streamlit web application for interactive car-price estimates.
- Monitor performance on newer, independently collected vehicle listings.

## 13. Conclusion

This project demonstrates a complete introductory machine learning regression workflow, from data cleaning and feature engineering through model training, hyperparameter tuning, and residual analysis.

Based on the current test results, Linear Regression is the leading candidate by RMSE and R², while tuned Gradient Boosting performs best by MAE and cross-validation RMSE among the tuned models. Further validation is recommended before declaring a final production model.

## Author

**John Afwilile Kapungu**  
Machine Learning | Data Science | Python

GitHub:  https://github.com/johnKapungu/CodeAlphaCar_Price_Prediction.git 
LinkedIn: https://www.linkedin.com/in/john-kapungu/

---

