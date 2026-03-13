# Data Wrangling & Engineering Pipeline

## Objective

Design and execute a reproducible data preparation pipeline that diagnoses missingness structures, engineers categorical features without introducing multicollinearity, and compresses high-cardinality variables to produce a regression-ready dataset from raw, chaotic HR-economics data.

## Methodology

- **Missingness Diagnosis:** Used `missingno` to generate nullity matrices and heatmaps, visually confirming that salary gaps were conditionally dependent on department — consistent with a Missing at Random (MAR) mechanism rather than MCAR or MNAR.
- **Conditional Median Imputation:** Imputed missing numeric fields using group-level medians (stratified by department) to preserve within-group distributional properties, avoiding the variance-collapsing bias of unconditional mean imputation.
- **Dummy Variable Encoding & Trap Avoidance:** Converted categorical department labels into binary indicator columns via one-hot encoding. Intentionally demonstrated the dummy variable trap (perfect multicollinearity with an intercept term), then resolved it by dropping one reference category (`drop_first=True`), restoring full column rank in the design matrix.
- **Target Encoding for High-Cardinality Features:** Replaced ~800 unique ZIP codes with a single continuous vector representing each ZIP's mean target value (base salary), using `category_encoders.TargetEncoder` to avoid the dimensionality explosion that standard one-hot encoding would produce.

## Key Findings

- The nullity correlation heatmap confirmed that `base_salary` missingness was systematically associated with specific departments, ruling out a simple MCAR assumption and justifying conditional (rather than global) imputation.
- Including all *k* dummy columns alongside an intercept produced a singular design matrix, as expected from the dummy variable trap. Dropping one reference class restored identifiability and yielded stable OLS coefficient estimates.
- Target encoding compressed geographic granularity from hundreds of sparse binary columns into a single feature, retaining predictive signal while dramatically reducing model complexity — a practical necessity for any downstream regression or regularized model.

## Tech Stack

Python · pandas · statsmodels · missingno · category_encoders
