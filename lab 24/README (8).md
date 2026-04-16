# Causal ML — Double Machine Learning for 401(k) Policy Evaluation

## Objective

Estimate the causal effect of 401(k) eligibility on household net financial assets using Double Machine Learning, demonstrating why naïve regularized estimators produce biased treatment effects and how cross-fitted nuisance models recover consistent causal parameters.

## Methodology

- **Regularization bias demonstration.** Simulated a data-generating process with a known true ATE of 5.0 to show that LASSO shrinks the treatment coefficient toward zero when applied directly to a causal estimation problem — illustrating the core motivation for orthogonal / debiased ML estimators.
- **Double Machine Learning (PLR).** Implemented the Partially Linear Regression framework from Chernozhukov et al. (2018) via the `DoubleML` library. Random Forest learners were used as nuisance models for both the outcome and treatment equations, with 5-fold cross-fitting to avoid overfitting bias.
- **ATE estimation.** Applied the PLR model to observational 401(k) pension plan data to estimate the Average Treatment Effect of plan eligibility on net financial assets, with standard errors derived from the DML influence-function representation.
- **Conditional ATE analysis.** Stratified the sample by income quartile and re-estimated the treatment effect within each subgroup to assess heterogeneity in the policy's impact across the income distribution.
- **Visualization.** Plotted CATE point estimates with 95% confidence intervals across income quartiles to characterize where the treatment effect is strongest and where it attenuates.

## Key Findings

<!-- TODO: Fill in your actual estimates below -->

- **Average Treatment Effect:** 401(k) eligibility is associated with an estimated increase of approximately **$X,XXX** in net financial assets (p < 0.0X).
- **Heterogeneity by income:**
  - *Q1 (lowest income):* [estimate ± CI] — [brief interpretation]
  - *Q2:* [estimate ± CI]
  - *Q3:* [estimate ± CI]
  - *Q4 (highest income):* [estimate ± CI] — [brief interpretation]
- The CATE analysis reveals [increasing / decreasing / non-monotonic] treatment effects across the income distribution, suggesting that [interpretation — e.g., higher-income households capture a disproportionate share of the policy's wealth-building effect].

## Tools & Frameworks

Python · DoubleML · scikit-learn (Random Forest) · NumPy · Pandas · Matplotlib
