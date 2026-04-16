# FedSpeak Analysis — NLP on FOMC Minutes

**Objective:** Quantify the evolution of Federal Reserve communication tone over two decades of FOMC meeting minutes using domain-specific sentiment lexicons, TF-IDF representations, and unsupervised clustering.

## Methodology

- Ingested and preprocessed 20+ years of FOMC meeting minutes, applying tokenization, lemmatization, and domain-aware stopword removal to produce clean document corpora.
- Constructed a TF-IDF document-term matrix incorporating both unigrams and bigrams to capture multi-word policy phrases (e.g., "inflation expectations," "labor market").
- Scored each document using the Loughran-McDonald financial sentiment lexicon, computing net sentiment (positive − negative word share) and an uncertainty index from the dictionary's uncertainty word list.
- Visualized sentiment and uncertainty trajectories over time, annotated against known macroeconomic regimes (GFC, taper tantrum, COVID shock, rate-hiking cycles).
- Applied K-Means clustering on PCA-reduced TF-IDF vectors to identify latent rhetorical regimes across FOMC documents.
- Conducted distributional comparison of pre-COVID vs. post-COVID sentiment scores to assess structural shifts in Fed communication.

## Key Findings

- **[FILL IN — e.g., "K-Means surfaced three distinct rhetorical clusters corresponding roughly to accommodative, transitional, and restrictive policy stances."]**
- **[FILL IN — e.g., "Net sentiment dropped sharply during the GFC and COVID windows, while the uncertainty index spiked to multi-decade highs in both episodes."]**
- **[FILL IN — e.g., "Post-COVID FOMC language exhibited persistently elevated uncertainty relative to the pre-COVID baseline, suggesting a durable shift in communication posture."]**

## Tools

Python · scikit-learn · NLTK · Loughran-McDonald Lexicon · Matplotlib · PCA · K-Means
