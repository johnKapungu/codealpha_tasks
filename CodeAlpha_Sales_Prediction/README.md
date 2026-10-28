# Sales Prediction Using Python 📊

### CodeAlpha Data Science Internship Project

**Author:** John Afwilile Kapungu  
**Project Type:** Machine Learning — Regression  
**Dataset:** `Advertising.csv`  
**Selected Model:** Tuned Gradient Boosting Regressor

---

## 📌 Project Overview

This project applies machine learning techniques to predict sales based on advertising expenditure across three media channels: TV, radio, and newspaper.

Using Python and its data science ecosystem, the project follows a structured workflow involving data auditing, data cleaning, exploratory data analysis (EDA), feature preparation, regression modelling, cross-validation, hyperparameter tuning, and model evaluation.

Several regression algorithms were evaluated, and the **Tuned Gradient Boosting Regressor** was selected based on its performance on the held-out test set.

The project demonstrates how machine learning can support sales prediction and provide useful insights for marketing analytics and business planning.

## 🎯 Objectives

- Inspect and understand the dataset structure.
- Identify missing values, duplicate records, irrelevant columns, and unusual observations.
- Perform exploratory data analysis and visualize relationships between advertising expenditure and sales.
- Prepare data for supervised machine learning.
- Train and compare regression algorithms.
- Apply cross-validation and hyperparameter tuning.
- Evaluate the selected model using MAE, RMSE, and R².
- Discuss practical applications, limitations, and opportunities for improvement.

## 📂 Dataset Description

The project uses `Advertising.csv`, containing **200 observations and 5 columns** in the source file.

| Column | Description | Role |
|---|---|---|
| `Unnamed: 0` | Sequential row identifier | Excluded from model features |
| `TV` | TV advertising expenditure | Predictor |
| `Radio` | Radio advertising expenditure | Predictor |
| `Newspaper` | Newspaper advertising expenditure | Predictor |
| `Sales` | Observed sales value | Target |

The model uses TV, Radio, and Newspaper as input features to predict Sales.

> **Note:** The exact measurement units should be confirmed from the dataset documentation.

## 🛠️ Technologies and Libraries

The project uses the Python data science ecosystem.

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Scikit-learn | Regression, preprocessing, cross-validation, tuning, and evaluation |
| Jupyter Notebook | Interactive analysis and experimentation |

## ⚙️ Project Workflow

### 1. Data Auditing and Cleaning

- Inspected dataset dimensions, columns, data types, and descriptive statistics.
- Checked missing values and duplicate records.
- Reviewed unusual observations.
- Identified `Unnamed: 0` as an index-like column to exclude from model features.
- Retained plausible outlier observations rather than removing them automatically.

### 2. Exploratory Data Analysis

The EDA stage investigates:

- Distributions of advertising expenditure and sales.
- Potential outliers using boxplots.
- Relationships between advertising channels and sales.
- Correlations among numerical variables.
- Patterns that may inform model selection.

### 3. Feature Preparation

The input variables are:

`TV`, `Radio`, and `Newspaper`

The target variable is:

`Sales`

The dataset was divided into training and test sets, with 40 observations reserved for final evaluation.

### 4. Model Development

Regression algorithms were compared to identify an appropriate model for sales prediction. The modelling workflow included baseline approaches and tree-based ensemble methods.

The Gradient Boosting Regressor was subsequently tuned using cross-validation.

### 5. Model Evaluation

The final model was evaluated on the held-out test set using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Coefficient of Determination (R²)

## 🏆 Final Model Results

The selected model was the **Tuned Gradient Boosting Regressor**.

| Metric | Final Result |
|---|---:|
| Test MAE | 0.6481 |
| Test RMSE | 0.7935 |
| Test R² | 0.9801 |
| Test samples | 40 |

### Interpretation

- **MAE = 0.6481:** The average absolute prediction error was approximately 0.6481 sales units.
- **RMSE = 0.7935:** The model achieved a relatively low squared-error-based prediction loss on the test set.
- **R² = 0.9801:** The model explained approximately 98.01% of the variation in test-set sales relative to a mean-only baseline.

These results indicate strong predictive performance on the evaluated test split. Performance may vary on other datasets or under different market conditions.

## 💡 Key Findings

- Advertising expenditure variables provide useful information for predicting sales in this dataset.
- Data auditing and feature selection help establish a reliable modelling workflow.
- Outlier detection should be followed by investigation rather than automatic removal.
- Model comparison and hyperparameter tuning provide a structured approach to selecting a predictive algorithm.
- Gradient Boosting achieved strong performance under the reported evaluation setup.

**Important:** Predictive associations do not establish that increasing expenditure on a particular advertising channel will cause sales to increase. Causal budget recommendations require additional evidence.

## 📈 Business Applications

The resulting model could support:

- Preliminary sales estimation.
- Marketing analytics and historical campaign analysis.
- Sales planning and forecasting experiments.
- Comparisons of predicted outcomes across advertising expenditure scenarios.
- Further investigation of relationships between advertising channels and sales.

The model should be validated on relevant new data before being used for operational decisions.

## ⚠️ Limitations

- The dataset contains only 200 observations.
- The model uses only three advertising expenditure variables.
- The dataset does not account for all possible influences on sales, such as pricing, seasonality, customer characteristics, and competitor activity.
- The reported metrics come from a single 40-observation test set.
- Strong predictive performance does not establish causal relationships.
- Additional validation is needed to assess performance stability and generalization.

## 🚀 Future Improvements

- Evaluate performance using repeated cross-validation or multiple train/test splits.
- Compare Gradient Boosting against simpler baseline models.
- Add model interpretation using permutation importance or partial dependence.
- Incorporate additional relevant features and larger datasets.
- Investigate time-aware forecasting if chronological campaign data become available.
- Record exact model hyperparameters and package versions for reproducibility.
- Monitor model performance if deployed.

## 💻 Installation and Usage

### Prerequisites

Install Python 3 and Git. A virtual environment is recommended.

### 1. Clone the Repository

Replace the example URL with your actual GitHub repository URL.

```bash
git clone https://github.com/YOUR_USERNAME/CodeAlpha_SalesPrediction.git
cd CodeAlpha_SalesPrediction
```

### 2. Create a Virtual Environment

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

**Linux/macOS:**

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the project's notebook and run the cells in sequence.

> Ensure `Advertising.csv` is placed in the data directory expected by your notebook, or update the file path accordingly.

## 📁 Suggested Project Structure

```text
CodeAlpha_SalesPrediction/
│
├── data/
│   └── Advertising.csv
│
├── notebooks/
│   └── sales_prediction.ipynb
│
├── figures/
│   └── [Saved EDA figures]
│
├── models/
│   └── [Saved trained model, if applicable]
│
├── reports/
│   └── project_report.pdf
│
├── requirements.txt
├── .gitignore
└── README.md
```

This is a suggested structure. Adjust the paths and filenames to match the actual files in your repository.

## 🔬 Reproducibility

For reproducible results:

1. Document the Python and package versions.
2. Record the train/test split configuration and random seed.
3. Keep the test set separate from hyperparameter selection.
4. Record the best Gradient Boosting parameters.
5. Preserve the final evaluation output and relevant EDA figures.

The final model results documented in this README are based on the reported project evaluation.

## 👨‍💻 Author

**John Afwilile Kapungu**

Data Science | Machine Learning | Python | Data Analytics

**Programme:** CodeAlpha Data Science Internship

**GitHub:** [Add your GitHub profile URL]

**LinkedIn:** [Add your LinkedIn profile URL]

## 🙏 Acknowledgements

Thanks to CodeAlpha for providing the opportunity to develop practical data science skills through a machine learning project.

## 📄 License


