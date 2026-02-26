# SwiftPass Loyalty Program: Causal Inference Audit

## Project Overview
The SwiftCart marketing team initially reported that SwiftPass subscribers spend significantly more per month than non-subscribers. However, this naive comparison fails to account for **Selection Bias**. High-volume "power users" naturally self-select into the program to save on delivery fees. This project utilizes applied econometrics to separate existing user behavior from the actual treatment effect of the loyalty program.

## The Business Problem
Marketing requested a 100% increase in the acquisition budget based on a Naive Simple Difference in Means (SDO). As an audit, we prove that the SDO overestimates the program's impact by crediting the loyalty program for spending that would have occurred regardless of subscription.

## Dataset: `swiftcart_loyalty.csv`
The audit utilizes the following features for 1,000 unique accounts:
* `subscriber`: Binary indicator (1 = Treatment, 0 = Control).
* `pre_spend`: Historical monthly spend before the program launch.
* `account_age`: Number of days since account creation.
* `support_tickets`: Total customer support interactions.
* `post_spend`: Monthly spend after the treatment period (The Outcome).

## Methodology

### 1. Naive Simple Difference (SDO)
We first calculate the baseline difference between subscribers and non-subscribers. This metric is "naive" because it ignores the fact that subscribers were likely bigger spenders before joining.

### 2. Propensity Score Matching (PSM)
To eliminate bias, we architected a control group using:
* **Logistic Regression**: To predict the probability of a user joining the program based on their `pre_spend`, `account_age`, and `support_tickets`.
* **Nearest Neighbors Matching**: To pair each subscriber with a "look-alike" non-subscriber who had a nearly identical probability of joining.

### 3. Balance Diagnostics (Love Plot)
We validate the matching process using a Love Plot. This visualization ensures that all covariates are balanced between the groups, meaning the Standardized Mean Difference (SMD) for every feature falls within the required ± 0.1 threshold.

## Key Findings

| Estimator | Value | Interpretation |
| :--- | :--- | :--- |
| **Naive SDO** | **$17.57** | Overestimates impact by including pre-existing habits. |
| **Causal ATT** | **$9.91** | The true incremental spend caused by SwiftPass. |
| **Selection Bias** | **$7.66** | The amount of "lift" that was actually pre-existing behavior. |

**The Conclusion:** The SwiftPass program is effective, but nearly 44% of the reported "lift" is a result of selection bias. Marketing budgets should be optimized based on the **ATT ($9.91)** rather than the naive figures.

## Setup and Requirements
To reproduce this analysis, ensure you have the following Python libraries installed:

```bash
pip install pandas numpy scikit-learn seaborn matplotlib
```

## Execution
Run the provided Python script to generate the causal metrics and the final Love Plot diagnostics.

```python
# Load the dataset and run the PSM engine
# The script will output the ATT and save 'love_plot_final.png'
python swiftpass_audit.py
```
