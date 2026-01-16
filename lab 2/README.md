# Lab 2: The Illusion of Growth & The Composition Effect

## Objective

Built a Python data pipeline to ingest live economic data from the Federal Reserve Economic Data (FRED) API, analyze 50+ years of U.S. wage trends, and systematically correct for statistical biases that distort conventional labor market narratives.

## Methodology

### 1. Data Ingestion & Real Wage Calculation
- Connected to the FRED API via `fredapi` to fetch Average Hourly Earnings (AHETPI) and Consumer Price Index (CPIAUCSL) time series
- Constructed a real wage series by deflating nominal wages against CPI, revealing inflation-adjusted purchasing power trends from 1964 to present

### 2. Anomaly Detection
- Identified a statistically significant spike in real wages during Q2 2020
- Hypothesized this reflected a **Composition Effect**—a statistical artifact rather than genuine wage growth

### 3. Composition Effect Correction
- Fetched the Employment Cost Index (ECIWAG) from FRED as a control measure
- The ECI uses a fixed-weight methodology that holds workforce composition constant, isolating true wage changes from demographic shifts in employment
- Rebased both series to a common index (2015 = 100) for direct visual comparison

## Key Findings

### The Money Illusion
Despite decades of nominal wage increases, real wages have remained essentially **flat since the 1970s**. Workers experience the illusion of progress through rising paychecks while actual purchasing power stagnates.

### The Pandemic Paradox
The apparent 2020 "wage boom" was a **statistical artifact**, not a labor market victory:

| Metric | 2020 Behavior | Interpretation |
|--------|---------------|----------------|
| Standard Average Wages | Sharp spike | Misleading—composition bias |
| Employment Cost Index | Stable growth | True underlying wage trend |

**Mechanism:** When COVID-19 lockdowns disproportionately displaced low-wage service workers, the remaining employed population skewed toward higher earners. This shifted the *average* upward without any individual receiving a raise—a textbook composition effect.

## Tech Stack

`Python` · `fredapi` · `pandas` · `matplotlib`
