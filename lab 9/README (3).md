# Recovering Experimental Truths via Propensity Score Matching

## Objective

This project demonstrates how propensity score matching can recover credible causal estimates from observational data that would otherwise produce severely biased treatment effects due to non-random selection into treatment.

## Methodology

- **Diagnosed Selection Bias:** Analyzed the observational subset of the Lalonde (1986) dataset, where naive comparison of treated and control groups yields a deeply misleading estimate of the effect of job training on earnings — a direct consequence of systematic differences between groups in pre-treatment covariates.
- **Estimated Propensity Scores:** Fit a logistic regression model on pre-treatment characteristics (age, education, prior earnings, employment history, race, marital status) to estimate each individual's probability of receiving treatment, capturing the selection mechanism that generates confounding.
- **Applied Nearest-Neighbor Matching:** Constructed a matched comparison group by pairing each treated individual with the control unit closest in estimated propensity score, effectively simulating the balance that randomization would have achieved.
- **Validated Against Experimental Benchmark:** Compared the matched estimate to the known experimental treatment effect from the original Lalonde RCT to assess how well the observational correction recovered the true causal parameter.

## Key Findings

| Estimator | Estimated Treatment Effect |
|---|---|
| Naive Observational Difference | −$15,204 |
| Propensity Score Matched Estimate | ≈ +$1,800 |
| Experimental Benchmark (RCT) | ≈ +$1,794 |

The naive comparison of treated and untreated groups produces a large, negative, and entirely spurious estimate — driven by the fact that program participants had systematically lower baseline earnings than the comparison population. Propensity score matching eliminates the vast majority of this bias, recovering a treatment effect within close range of the experimentally validated result. This confirms that when the selection-on-observables assumption is plausible and the propensity model is well-specified, matching methods can credibly approximate experimental findings from non-experimental data.

## Tech Stack

Python · Pandas · Scikit-Learn · Logistic Regression · Nearest-Neighbor Matching
