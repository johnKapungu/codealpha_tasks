# Unemployment Analysis with Python

## Project Overview

This project analyzes unemployment rate data using Python to identify long-term trends, seasonal patterns, unusual observations, and potential changes associated with the COVID-19 pandemic. It also evaluates time-series forecasting methods to determine how accurately future unemployment rates can be estimated from historical data.

The project combines exploratory data analysis (EDA), data visualization, statistical analysis, and machine learning.

## Objectives

- Clean and prepare unemployment rate data for analysis.
- Explore changes in unemployment rates over time.
- Investigate potential impacts of COVID-19 on unemployment.
- Identify seasonal patterns and trends.
- Detect and investigate statistical outliers.
- Build and evaluate unemployment forecasting models.
- Communicate findings that may inform economic and social policy discussions.

## Technologies and Libraries

- **Python** — programming and analysis
- **Pandas** — data manipulation and cleaning
- **NumPy** — numerical computations
- **Matplotlib** — data visualization
- **Seaborn** — statistical visualization
- **Scikit-learn** — machine learning and model evaluation
- **Statsmodels** — ARIMA time-series forecasting
- **Jupyter Notebook** — interactive analysis environment

## Project Structure

text
CodeApha_Unemployment_In_India_Analysis/
│
├── data/
│   ├── Unemployment in India/
│   └── Unemployment_Rate_upto_11_2020/
│   └── unemployment_cleaned/
│
├── figures/
│   ├── step4_trend_covid/
│   ├── step5_seasonal_analysis/
│   └── step6_insights/
│   └── step7_prediction/
│   └── step8_model_improvemen/
│   └── step11_final/
│   └── unemployment_eda_outputs/
│
├── notebooks/
│   └── Unemployment_Data_Cleanings.ipynb
│   └── EDA.ipynb
│   └── Trend_Analysis_and_COVID_19_Impact.ipynb
│
├── FINAL_REPORT_UNEMPLOYMENT_ANALYSIS_WITH_PYTHON.docx
├── Unemployment_Analysis_Professional_Presentation.ppt
├── README.md
├── requirements.txt
└── .gitignore


## Analysis Workflow

### 1. Data Collection and Understanding

- Load the unemployment dataset.
- Inspect its dimensions, column names, data types, and statistical summaries.
- Identify missing values and duplicate records.

### 2. Data Cleaning and Preprocessing

- Convert the date column to an appropriate datetime format.
- Handle missing and invalid values.
- Sort records chronologically.
- Check for duplicates and prepare the dataset for time-series analysis.
- Save the cleaned dataset for subsequent analysis.

### 3. Exploratory Data Analysis

- Examine the distribution of unemployment rates.
- Visualize changes over time.
- Compare unemployment across years and months.
- Investigate possible relationships and unusual observations.

### 4. COVID-19 Impact Analysis

Compare unemployment trends before, during, and after the COVID-19 period, where the available data permits.

This analysis investigates whether the pandemic period coincides with notable changes in unemployment. Observed changes should not automatically be interpreted as proof that COVID-19 caused them.

### 5. Seasonality and Outlier Analysis

- Analyze unemployment rates by month and quarter.
- Use visualizations such as monthly trend plots and heatmaps to investigate recurring patterns.
- Apply statistical techniques such as the interquartile range (IQR) to flag unusual observations.

Outliers are investigated in context rather than automatically removed, since extreme unemployment values may represent meaningful economic events.

### 6. Forecasting and Model Evaluation

The project evaluates the following approaches:

| Model | Description |
|---|---|
| Mean Baseline | Predicts using the average unemployment rate in the training data |
| Persistence Baseline | Uses the previous month's observed unemployment rate as the next month's prediction |
| Random Forest Regressor | Learns nonlinear relationships from engineered historical features |
| ARIMA | Models time-series behavior using autoregressive, differencing, and moving-average components |

A chronological train/test split is used to respect the time order of observations. Model performance is evaluated using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE).

## Preliminary Model Results

The following are the previously obtained evaluation results. They should be treated as preliminary until all models are evaluated on the same test dates.

| Model | MAE | RMSE |
|---|---:|---:|
| Persistence Baseline | 9.049 | 10.603 |
| ARIMA(1,1,1) | 9.738 | 11.342 |
| Tuned Random Forest | 9.895 | 11.474 |
| Mean Baseline | 10.319 | 11.860 |

**Preliminary finding:** The persistence baseline achieved the lowest reported MAE and RMSE. This suggests that using the previous month's unemployment rate is a strong benchmark for short-term forecasting in this dataset.

If unemployment rates are expressed in percentage units, these error values are measured in percentage points.

## Evaluation Metrics

**Mean Absolute Error (MAE)** measures the average absolute difference between actual and predicted values. Lower values indicate better average predictive accuracy.

**Root Mean Squared Error (RMSE)** penalizes larger prediction errors more heavily. Lower values indicate better performance, particularly when large misses matter.

Both metrics should be interpreted in the context of the units and scale of the target variable.

## Key Deliverables

- Cleaned unemployment dataset
- Exploratory data analysis and statistical summaries
- Visualizations of unemployment trends
- COVID-19 period analysis
- Seasonal pattern and outlier analysis
- Forecasting model comparison
- Saved figures and model evaluation results
- Final conclusions and recommendations

## Installation and Setup

### Prerequisites

Install Python 3.10 or a compatible version supported by your selected package releases.

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd unemployment-analysis
```

Replace `<your-repository-url>` with your actual GitHub repository URL.

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

On Linux or macOS:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the notebook containing the analysis and run its cells in order.

## Limitations

- Forecast accuracy depends on the quality, frequency, and historical coverage of the dataset.
- A chronological holdout period may not represent all future economic conditions.
- Outlier detection does not establish the cause of unusual unemployment values.
- COVID-19 impact analysis is observational and does not, by itself, establish causation.
- Forecasting results should be compared using identical test observations before selecting a final model.

## Future Improvements

- Evaluate all models on an identical holdout period.
- Test additional forecasting approaches, including exponential smoothing.
- Tune model parameters using time-series cross-validation.
- Compare forecasts across multiple evaluation windows.
- Incorporate relevant economic indicators where suitable data is available.
- Develop an interactive dashboard using Power BI, Tableau, or Streamlit.

## Conclusion

This project demonstrates a Python-based workflow for analyzing unemployment data, exploring economic trends, and evaluating forecasting methods.

The preliminary results show that a simple persistence baseline outperformed the tested ARIMA and Random Forest models. This highlights the importance of using strong baselines and validating forecasting models rigorously rather than assuming that greater model complexity guarantees better results.

## Author

**John Kapungu**

Data Science | Machine Learning | Python | Data Visualization

