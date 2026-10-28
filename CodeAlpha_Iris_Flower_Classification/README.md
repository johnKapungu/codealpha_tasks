# Iris Flower Classification Using Machine Learning

## Project Overview

This project develops and evaluates machine learning classification models to predict the species of Iris flowers based on their physical measurements. Using Python and Scikit-learn, the project explores data preprocessing, exploratory data analysis (EDA), model training, evaluation, and hyperparameter tuning.

The objective is to identify a reliable classification model that can distinguish among three Iris species:

- Iris-setosa
- Iris-versicolor
- Iris-virginica

## Objectives

- Explore and understand the Iris dataset.
- Perform data quality checks and exploratory data analysis.
- Visualize feature distributions and relationships.
- Prepare features and target variables for machine learning.
- Train and evaluate multiple classification algorithms.
- Tune SVM hyperparameters using cross-validation.
- Compare model performance and identify the best-performing candidate.

## Dataset Description

The dataset contains 150 flower observations and six original columns, including an identifier.

| Feature | Description |
|---|---|
| `Id` | Observation identifier; excluded from model training |
| `SepalLengthCm` | Sepal length in centimeters |
| `SepalWidthCm` | Sepal width in centimeters |
| `PetalLengthCm` | Petal length in centimeters |
| `PetalWidthCm` | Petal width in centimeters |
| `Species` | Target class representing the Iris species |

The dataset contains 150 observations, with 50 observations per species.

**Target variable:** `Species`

**Input features:** Sepal length, sepal width, petal length, and petal width.

The `Id` column is excluded because it identifies observations rather than describing flower characteristics.

## Technologies and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Machine Learning Algorithms

Five classification algorithms are investigated:

### 1. K-Nearest Neighbors (KNN)

Classifies flowers based on the labels of their nearest observations. Feature scaling is used because KNN relies on distances.

### 2. Decision Tree Classifier

Learns a sequence of feature-based decision rules to classify flowers. Feature scaling is generally unnecessary.

### 3. Logistic Regression

Learns relationships between flower measurements and species probabilities. Feature scaling is applied to support optimization.

### 4. Random Forest Classifier

Combines multiple decision trees to improve predictive robustness and reduce the limitations of relying on a single tree.

### 5. Support Vector Machine (SVM)

Learns decision boundaries that separate the flower species. The RBF kernel is used to model potentially nonlinear boundaries.

## Project Workflow

1. **Data loading:** Import the dataset using Pandas.
2. **Data understanding:** Inspect dimensions, column names, data types, and summary statistics.
3. **Data quality assessment:** Check missing values, duplicates, and potential outliers.
4. **Exploratory data analysis:** Investigate feature distributions, class balance, pairwise relationships, and correlations.
5. **Feature and target separation:** Remove `Id` and separate `Species` from the predictor variables.
6. **Train/test split:** Divide the dataset into training and testing sets while preserving class proportions.
7. **Feature scaling:** Standardize features for distance- and scale-sensitive models.
8. **Model training:** Train KNN, Decision Tree, Logistic Regression, Random Forest, and SVM.
9. **Model evaluation:** Compare accuracy, precision, recall, F1-score, and confusion matrices.
10. **Hyperparameter tuning:** Use `GridSearchCV` with stratified five-fold cross-validation to tune SVM's `C` and `gamma`.
11. **Model selection:** Select the leading candidate based on mean cross-validation accuracy and evaluate it on the held-out test set.

## SVM Hyperparameter Tuning

The SVM model uses an RBF kernel. Grid search evaluates the following parameter values:

- **C:** `[0.1, 1, 10, 100, 1000]`
- **Gamma:** `[0.001, 0.01, 0.1, 1, 10]`

This produces 25 parameter combinations. With five-fold cross-validation, each combination is evaluated across five validation folds.

A Scikit-learn pipeline ensures that feature scaling is fitted separately within each fold, helping prevent data leakage.

The best parameter combination is selected using mean cross-validation accuracy. The selected model is then evaluated on the held-out test set.

## Evaluation Metrics

| Metric | Purpose |
|---|---|
| Accuracy | Proportion of correctly classified observations |
| Precision | Reliability of predictions for each species |
| Recall | Proportion of actual observations correctly identified |
| F1-score | Harmonic mean of precision and recall |
| Confusion matrix | Shows correct predictions and classification errors |
| Cross-validation accuracy | Estimates model performance across multiple validation folds |

## Exploratory Data Analysis

The project explores:

- Feature distribution plots
- Pairplots for relationships between measurements
- Correlation heatmaps
- Species-level feature comparisons
- Potential outliers in numerical measurements

Petal length and petal width show strong relationships with one another and are particularly useful for distinguishing Iris species. Iris-setosa is generally more separable than Iris-versicolor and Iris-virginica.

## Project Structure

A recommended repository structure is:


'''text
CodeAlpha_Iris_Flower_Classification/
│
├── data/
│   └── Iris.csv
│
├── notebooks/
│   └── iris_classification.ipynb
│
├── figures/
│   ├── svm_classification_metrics.csv
│   ├── svm_predictions_report.csv

│
├── models/
│   └── best_svm_model.joblib
│
├── README.md
├── requirements.txt
└── .gitignore
'''

## Installation and Setup

### Prerequisites

Install Python 3.10 or a compatible version supported by your selected Scikit-learn release.

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/iris-flower-classification.git
cd iris-flower-classification
```

Replace `YOUR_USERNAME` with your GitHub username and update the repository URL as necessary.

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
pip install -r requirements.txt
```

### 4. Run the notebook

```bash
jupyter notebook
```

Open `notebooks/iris_classification.ipynb` and execute the cells in order.

## Expected Results

The project produces:

- Data exploration and visualization outputs
- Trained classification models
- Classification reports and confusion matrices
- Cross-validation results for model comparison
- Best SVM hyperparameters
- Test-set evaluation results for the selected model

Actual model scores should be reported after executing the notebook. No specific accuracy is claimed here because results depend on the split, model configuration, and tuning procedure.

## Key Findings

The analysis is designed to investigate how effectively the four flower measurements distinguish the three Iris species.

The project examines whether:

- Petal measurements provide stronger discrimination than sepal measurements.
- Ensemble methods improve predictive consistency.
- SVM performance changes with different `C` and `gamma` settings.
- Cross-validation provides a more reliable basis for model selection than a single split alone.

Conclusions should be finalized using the measured results from the completed experiment.

## Limitations

- The dataset is small and contains only three Iris species.
- Results may vary with the train/test split and model configuration.
- High accuracy on this dataset does not guarantee equivalent performance on other flower datasets.
- Feature importance is model-dependent and should not be interpreted as proof of causation.
- Hyperparameter tuning is limited to the specified search grid.

## Future Improvements

- Tune hyperparameters for KNN, Decision Tree, and Random Forest.
- Compare all algorithms using the same cross-validation folds.
- Investigate permutation feature importance.
- Save the final fitted model using Joblib.
- Build a Streamlit application for interactive species prediction.
- Add automated tests and a reproducible training script.

## Conclusion

This project demonstrates an end-to-end machine learning classification workflow using the Iris dataset. It combines exploratory analysis, preprocessing, multiple classification algorithms, evaluation metrics, and cross-validated SVM hyperparameter tuning.

The final model should be selected based on cross-validation performance, verified using held-out test data, and documented with actual evaluation results.

## Author

**John Afwilile Kapungu**

- Location: Dodoma, Tanzania
- LinkedIn: [John Kapungu](https://linkedin.com/in/john-kapungu)
- GitHub: Add your GitHub profile or repository URL here.

## License
