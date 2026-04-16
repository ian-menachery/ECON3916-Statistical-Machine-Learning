# Clustering World Economies with K-Means & PCA

**Objective:** Apply unsupervised learning techniques to segment ~160 national economies by structural development indicators and evaluate how algorithmically derived clusters align with established World Bank income classifications.

---

## Methodology

- Retrieved 10 macroeconomic and human-development indicators for approximately 160 countries via the World Bank API (`wbgapi`), covering dimensions such as GDP per capita, life expectancy, access to electricity, and trade openness.
- Standardized all features using `StandardScaler` to neutralize scale disparities and ensure equal contribution to distance-based clustering.
- Fit a K-Means model with K=4 and projected the high-dimensional feature space onto two principal components via PCA for visualization.
- Conducted elbow method analysis (inertia vs. K) and silhouette scoring across K=2 through K=10 to identify the optimal number of clusters.
- Cross-tabulated algorithmically assigned cluster labels against the World Bank's four-tier income classification (Low, Lower-Middle, Upper-Middle, High) to quantify agreement between data-driven segmentation and institutional groupings.
- Replicated the full pipeline on California Housing census-tract data to test generalizability of the clustering workflow on a geographically granular, domestic dataset.

## Key Findings

- **Optimal K:** <!-- TODO: fill in optimal K from elbow/silhouette analysis -->
- **Cluster–Income Alignment:** <!-- TODO: fill in how well algorithmic clusters mapped to World Bank income groups, e.g. "K=4 clusters exhibited strong correspondence with World Bank tiers, with X% of high-income nations concentrated in a single cluster" -->
- PCA's first two components captured a substantial share of total variance, confirming that national development indicators exhibit a low-dimensional structure amenable to visual inspection.
- The California Housing extension demonstrated that the same standardize → cluster → evaluate pipeline transfers effectively to sub-national geographic data, though optimal K and cluster interpretability differed from the cross-country context.

## Tools & Libraries

Python · `wbgapi` · `scikit-learn` (K-Means, PCA, StandardScaler, silhouette_score) · `matplotlib` · `pandas`
