## NEED TO EDIT SEE REPORT

# Predicting Home Tax-Assessed Value with Ensemble Regression (Zillow Dataset)

Predicting a home's tax-assessed value (`taxvaluedollarcnt`) from property characteristics, using a 77,613-row, 55-feature subset of the Zillow "Zestimate" dataset (Kaggle, 2017). Built as a group project for a Machine Learning Fundamentals course; this repo documents the full workflow from raw data to a tuned ensemble model.

**My contribution:** *(fill in — e.g., "led feature selection and hyperparameter tuning for the Bagging and Random Forest models; built the validation-curve analysis in Fig. 1")*

## Results

| Model | Mean CV RMSE | Std. RMSE | Notes |
|---|---|---|---|
| Decision Tree Regressor | $608,789 | $26,989 | Baseline; overfit, no tuning |
| Gradient Boosting Regressor | $450,328 | $20,579 | Baseline |
| Random Forest Regressor | $445,518 | $20,298 | Baseline; best of the initial 7 models |
| **Bagging Regressor (tuned)** | **$437,636 → $414,148*** | — | Final model, after feature engineering + hyperparameter tuning |

\* *Further reduced to ~$414K–$416K CV RMSE after revisiting Milestone 1 cleaning decisions (removing 199 duplicate parcel IDs, loosening the null-value drop threshold from 20% to 40%).*

RMSE was chosen over MSE specifically so error stays interpretable in dollars — a $437K RMSE is a business-legible number in a way squared error isn't.

**Key finding:** engineered features didn't move the needle much — `calculatedfinishedsquarefeet`, its squared term, and `finishedsquarefeet12` were consistently the top predictors across models, and they largely share variance rather than add independent signal. That's a useful negative result: more engineered features ≠ automatically better in a low-feature-count regime.

## What's in this repo

```
├── Project_Milestone_One_Zillow_EDA/          # EDA, cleaning, imputation, feature relationships
├── Project_Milestone_Two_Modeling_Feature_Engineering/  # Baseline models, feature engineering, feature selection
├── Zillow_Final_Report/                       # Final model + full technical report
├── Zillow_Housing_Project_Presentation/        # Non-technical summary deck (PDF)
├── Diagrams/
├── zillow_cleaned.csv                          # Cleaned dataset used for modeling
└── README.md
```

## Methodology

**Data cleaning**
- Dropped 199 duplicate parcel IDs (verified as true duplicates, not distinct records)
- Dropped 35 rows with a missing target value — imputing the label itself would have manufactured fake variance in the thing we're trying to predict
- Dropped features with >20% missing values (later revisited to 40% as a tuning experiment, which improved final RMSE)
- Dropped non-regressable / redundant columns: raw IDs, free-text fields, lat/long (unusable without geospatial encoding), and categorical fields with too few observations per group to be statistically meaningful
- Median imputation for numeric features, mode for categorical — median was chosen specifically because most numeric features were heavily right-skewed with outliers, where mean imputation would have distorted the distribution

**Feature engineering & selection**
- Log-transformed `yearbuilt` to reduce skew — improved RMSE modestly across nearly all 7 models and reduced variance in most
- Interaction term: bedroom count × bathroom count
- Polynomial feature: `calculatedfinishedsquarefeet²`
- Feature selection via `SequentialFeatureSelector` (forward/backward) and univariate F-statistics (`f_regression`), cross-checked against each other
- Correlation analysis surfaced expected collinearity (e.g., 0.99 between full-bath count and calculated bathroom count) and confirmed `calculatedfinishedsquarefeet` (r = 0.61) and bathroom count (r = 0.51) as the strongest single predictors of tax value

**Modeling**
- Evaluated 7 regression algorithms: Linear, Lasso, Decision Tree, Random Forest, Gradient Boosting, and Bagging Regressor, among others
- Model comparison via repeated k-fold cross-validation, tracking both mean and standard deviation of RMSE (a low mean with high variance is not a reliable model)
- Hyperparameter tuning via `GridSearchCV` / `RandomizedSearchCV`, guided by validation curves for parameters like `n_estimators`, `max_samples`, and `max_features` — plotting train vs. validation RMSE and its std. dev. side by side to catch overfitting before committing to a grid search range, which kept tuning runtimes down
- Final model: **Bagging Regressor** — narrowly outperformed Random Forest and Gradient Boosting on RMSE while being more interpretable

## Tools
Python · Pandas · NumPy · Scikit-learn (ensemble methods, `GridSearchCV`/`RandomizedSearchCV`, `SequentialFeatureSelector`) · Matplotlib · Seaborn · Jupyter

## Limitations & possible extensions
- Hyperparameter tuning across 3 ensemble models was computationally expensive — a real constraint on iteration speed
- No geospatial modeling despite location clearly mattering for home value; lat/long were dropped rather than properly encoded
- No external data sources (school ratings, crime rates, local market trends) that likely explain variance the current features can't capture
- *(If extending independently)*: this is a natural place to add SHAP-based feature importance, try LightGBM/XGBoost, or build a small geospatial feature (e.g., distance to city center, ZIP-level median price) as a follow-up

## Team
*(Add team member names here)*

---
*Completed as part of DS 603, Spring 2025.*
