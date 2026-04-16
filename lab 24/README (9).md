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

- **Regularization bias (simulation).** On a simulated DGP with TRUE_ATE = 5.0, naïve LASSO recovered an estimate of 4.94 — a −1.2% bias — confirming that ℓ₁ regularization does not distinguish the causal variable from nuisance covariates and shrinks the treatment coefficient toward zero.
- **Average Treatment Effect.** The DML-PLR estimate of the effect of 401(k) eligibility on net financial assets is **−$867** (SE = $481, 95% CI [−$1,810, $76], *p* = 0.072). The effect is **not statistically significant at the 5% level**, though the point estimate is economically non-trivial. Sensitivity analysis (Chernozhukov et al. robustness values: RV = 1.48%, RVα = 0.13%) indicates the result is fragile to even modest confounding.
- **Heterogeneity by income quartile (CATE):**
  - *Q1 (≤ $19,413):* **+$384** [−$430, $1,198] — the only subgroup with a positive point estimate; confidence interval spans zero.
  - *Q2 ($19,416 – $31,476):* **−$1,546** [−$4,691, $1,599] — large negative point estimate with a wide CI reflecting high variance.
  - *Q3 ($31,488 – $48,582):* **−$865** [−$2,086, $357] — tightest CI of the upper quartiles; still spans zero.
  - *Q4 (≥ $48,585):* **−$1,658** [−$4,210, $893] — largest negative point estimate, again statistically insignificant.
- The CATE analysis reveals a weakly negative, non-monotonic pattern: the lowest-income households show a small positive effect while the three upper quartiles exhibit negative point estimates, though no subgroup estimate is individually significant. This suggests that 401(k) eligibility may induce asset reallocation rather than net wealth creation for middle- and upper-income households — consistent with the "reshuffling" hypothesis in the 401(k) literature — while offering a modest (if noisy) positive effect for the lowest earners.

## Tools & Frameworks

Python · DoubleML · scikit-learn (Random Forest) · NumPy · Pandas · Matplotlib
