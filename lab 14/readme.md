# AI Capex Diagnostic Modeling

**Objective:** To rigorously diagnose and resolve structural econometric failures within Ordinary Least Squares (OLS) estimations predicting AI Software Revenue from capital expenditure deployments.

## Methodology
* **Data Ingestion & Processing:** Structured and analyzed the 2026 Nvidia AI Capital Expenditure and Deployment dataset utilizing `pandas`.
* **Baseline Estimation:** Specified an initial naive OLS regression model via `statsmodels` to establish baseline parameters for AI Software Revenue.
* **Diagnostic Testing:** Evaluated the model for classical linear regression assumption violations, specifically isolating and testing for multicollinearity and heteroscedasticity.
* **Visual Diagnostics:** Mapped residual variance expansions and structural relationships across high-tier expenditure distributions using `matplotlib` and `seaborn`.
* **Econometric Correction:** Implemented HC3 (heteroscedasticity-consistent) robust standard errors to recalibrate the model and correct for downward bias in the initial standard error estimations.

## Key Findings
Diagnostic testing of the naive OLS model revealed severe heteroscedasticity, characterized by aggressively expanding residual variance at the highest capital expenditure tiers. This structural failure resulted in artificially deflated p-values, projecting false statistical confidence in the baseline estimation. The subsequent application of HC3 robust estimators successfully corrected this bias, appropriately widening the standard error bounds and exposing the true, uninflated statistical significance of the underlying deployment metrics.

**Technologies Used:** Python, pandas, statsmodels, matplotlib, seaborn
