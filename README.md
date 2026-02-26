# Diabetes Progression Prediction (Scikit-Learn Diabetes Dataset)

## Objective
Build a machine learning report to **predict diabetes disease progression one year after baseline** (a numeric target).  
This can be used as a simple **screening-style tool** to help identify patients who may be at higher risk.

## Dataset Source
- Dataset: **Scikit-Learn Diabetes dataset**
- Loaded using:
  - `from sklearn import datasets`
  - `diabetes = datasets.load_diabetes(as_frame=True)`
  - `X = diabetes.data`
  - `y = diabetes.target`
- Note: The notebook also prints and summarizes `diabetes.DESCR`.

## Models Included
### Regression (numeric prediction)
1. **Univariate Polynomial Regression (BMI only)**
   - Uses only the `bmi` feature
   - Polynomial degrees: **0, 1, 2, 3, 4, 5**
   - Pipeline: `PolynomialFeatures` + `LinearRegression`

2. **Multivariate Polynomial Regression**
   - Uses multiple features (usually all)
   - Two polynomial degrees (example: **degree 2 and degree 3**)
   - Pipeline: `StandardScaler` + `PolynomialFeatures` + `LinearRegression`

3. **Decision Tree Regressor**
   - Two settings (example: **max_depth=3** and **max_depth=6**)

4. **kNN Regressor**
   - Two k values (example: **k=3** and **k=15**)
   - Pipeline: `StandardScaler` + `KNeighborsRegressor`

### Classification (high-risk screening)
5. **Logistic Regression Classifier**
   - Creates a “high risk” label:
     - `y_class = 1 if y >= threshold else 0`
     - Threshold is based on training data (example: **75th percentile** or median)
   - Two settings (example: different **C** values)
   - Pipeline: `StandardScaler` + `LogisticRegression`

## Evaluation Metrics
### Regression Metrics
Used for polynomial regression, decision trees, and kNN regression:
- **R² (R-squared):** how much variance is explained
- **MAE:** average absolute error (same units as target)
- **MAPE:** average percent error (can be sensitive when y is near 0)

### Classification Metrics (Logistic Regression Only)
Used for the high-risk label model:
- **Accuracy**
- **Precision**
- **Recall**
- **F1-score**
- **ROC-AUC**

> Note: Regression metrics (R², MAE, MAPE) do **not** apply to logistic regression because it is a classifier.

## Files in This Repo
- `diabetes_sklearn_report.ipynb` — Main Jupyter Notebook report
- `README.md` — Project overview (this file)
- `requirements.txt` — Python packages needed to run locally

## How to Run (Local)
### 1) Create and activate a virtual environment
**Windows (PowerShell):**
```bash
python -m venv .venv
.venv\\Scripts\\Activate.ps1