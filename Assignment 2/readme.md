# Audit 02: Deconstructing Statistical Lies

## Overview
Three case studies exposing how companies manipulate metrics to hide the truth.

---

## 1. Latency Skew: The Mean is a Vanity Metric

**The Claim:** NebulaCloud advertises "Mean Latency = 35ms"

**The Reality:** 
- 98% of requests: 20-50ms (excellent)
- 2% of requests: 1000-5000ms (unacceptable)
- Standard Deviation = 327ms (exploded by outliers)
- MAD = 9ms (robust, stable measure)

**Key Insight:** In heavy-tailed distributions, SD is dominated by rare extreme values through squared amplification. MAD remains stable by using the median of absolute deviations, which outliers can't shift.

**Takeaway:** For SLAs and reliability, use P95/P99 percentiles and MAD instead of mean and SD.

---

## 2. False Positives: The Base Rate Fallacy

**The Claim:** IntegrityAI's plagiarism detector is "98% accurate" (Sensitivity=98%, Specificity=98%)

**The Reality (Honors Seminar, 0.1% base rate):**
- P(Cheater | Flagged) = **4.76%**
- 95% of flagged students are actually innocent

**Key Insight:** Even highly accurate tests produce mostly false positives when the base rate is low. Posterior probability depends heavily on prior probability.

**Takeaway:** Always apply Bayes' Theorem. High accuracy ≠ high positive predictive value in low base rate scenarios.

---

## 3. Survivorship Bias: The Memecoin Graveyard

**The Claim:** Crypto platforms showcase "successful" tokens

**The Reality (10,000 token simulation):**
- Mean market cap (all tokens): $8,234
- Mean market cap (top 1% survivors): $89,456
- **Bias multiplier: 10.9x**

**Key Insight:** Analyzing only survivors inflates expected returns by excluding the 99% of failed tokens. The Pareto distribution creates massive inequality that gets hidden when failures are deleted.

**Takeaway:** Always ask "What am I not seeing?" Survivorship bias makes bad strategies look profitable.

---

## Technical Stack
- Python (NumPy, Pandas, Matplotlib)
- Bayesian inference
- Robust statistics (MAD)
- Power law distributions (Pareto)

## Skills Demonstrated
- Critical evaluation of vendor claims
- Statistical robustness testing
- Probabilistic reasoning
- Data generating process simulation
