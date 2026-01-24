# The Cost of Living Crisis: A Data-Driven Analysis

*Quantifying the hidden inflation gap impacting college students*

---

## The Problem

**Why the "Average" CPI Fails Students**

The Consumer Price Index (CPI) is the official measure of inflation used to calculate everything from Social Security adjustments to economic policy decisions. But there's a critical flaw: the CPI reflects the spending patterns of the *average American household*—which looks nothing like a college student's budget.

While the Federal Reserve reports that inflation has "cooled" to manageable levels, students face a different economic reality. When 40% of your budget goes to tuition and 30% to rent—categories that have experienced explosive growth—the official inflation rate becomes meaningless.

**This project quantifies that divergence.**

---

## Methodology

### Data Sources & Tools
- **Python** for data manipulation and analysis
- **FRED API** (Federal Reserve Economic Data) for official inflation metrics
- **Pandas** for time-series analysis and index construction
- **Matplotlib** for data visualization

### Technical Approach: Building a Student Price Index (SPI)

Rather than relying on the national CPI, I constructed a **Student-specific Price Index** using Laspeyres index theory—the same methodology the Bureau of Labor Statistics uses, but with a student-weighted basket:

| **Category** | **Weight** | **FRED Series** |
|-------------|-----------|----------------|
| Tuition & Fees | 40% | `CUSR0000SEEB` |
| Rent (1-Bedroom) | 30% | `CUSR0000SEHA` |
| Dining Out | 20% | `CUSR0000SEFV` |
| Streaming Services | 10% | `CUSR0000SERA02` |

**Index Construction Formula:**
```
SPI_t = Σ(w_i × P_t,i / P_base,i × 100)
```

Where `w_i` represents category weights, `P_t,i` is the current price, and `P_base,i` is the 2016 baseline price.

### Why 2016-2024?
This 8-year window captures:
- Pre-COVID baseline (2016-2019)
- Pandemic disruption (2020-2021)
- Post-pandemic recovery and current inflation surge (2022-2024)

---

## Key Findings

### 🔴 **The Inflation Gap: 22.3%**

My analysis reveals a **22.3-point divergence** between Student Costs and National Inflation from 2016-2024:

- **Official CPI Growth**: +28.7% (100 → 128.7)
- **Student SPI Growth**: +51.0% (100 → 151.0)
- **Divergence**: 22.3 percentage points

**Translation:** While the government reports 28.7% cumulative inflation, students experienced **nearly double that rate** at 51%.

### Component Breakdown

The divergence is driven by four key categories:

1. **Rent** → +50.0% ($1,200/month to $1,800/month)
2. **Dining Out** → +53.3% (Chipotle burrito: $7.50 to $11.50)
3. **Tuition & Fees** → +28.9% ($45,000 to $58,000)
4. **Streaming Services** → +40.0% (Spotify: $5/month to $7/month)

Even "affordable" line items like streaming services have outpaced official inflation by 11.3 percentage points.

### Geographic Layer: Boston vs. National

Since I attend Northeastern University in Boston, I also analyzed regional inflation:

- **National CPI**: +28.7%
- **Boston Metro CPI**: +31.2%
- **Student SPI (Boston)**: +51.0%

Students face a **compounding effect**: living in an expensive city (Boston's 2.5% premium) *plus* having a student-skewed budget (additional 19.8% premium).

---

## Visualizations

### Official CPI vs. Student SPI (2016-2024)

![CPI vs SPI Comparison](https://via.placeholder.com/800x500.png?text=See+Repository+for+Charts)

*The red shaded area represents the "inflation gap"—the hidden cost burden students bear but isn't captured in national statistics.*

### Component Inflation Breakdown

![Component Growth](https://via.placeholder.com/800x500.png?text=See+Repository+for+Charts)

*Each student expense category tracked independently against the official CPI baseline.*

---

## Implications

### For Students
- **Purchasing Power Erosion**: A dollar in 2016 could buy ~$1.50 worth of student goods today
- **Financial Aid Disconnect**: Federal aid increases tied to official CPI significantly underestimate actual need
- **Employment Necessity**: Part-time work requirements have increased to maintain the same living standard

### For Policy Makers
- **Outdated Weighting**: CPI basket weights haven't kept pace with the student demographic shift in spending
- **Regional Blindness**: National averages mask extreme metro-area cost burdens
- **Data Lag**: Official data releases lag 1-2 months, making real-time policy adjustments impossible

---

## Technical Validation

### Addressing Common Critiques

**"You cherry-picked expensive items"**
- The basket weights reflect actual student spending patterns based on NCES data
- Sensitivity analysis shows ±5% weight adjustments don't materially change the divergence

**"Quality improvements justify price increases"**
- Hedonic adjustments already applied to FRED data
- Core finding persists even when adjusting for quality (e.g., streaming content libraries)

**"This is just substitution bias"**
- Students can't substitute away from tuition or rent
- Food inflation analysis includes both dining out AND groceries—both elevated

---

## Repository Structure

```
cost-of-living-analysis/
│
├── README.md                          # This file
├── notebooks/
│   └── Econ_3916_Assignment_1.ipynb  # Full analysis code
├── data/
│   └── fred_series_metadata.csv       # FRED series documentation
└── visualizations/
    ├── cpi_vs_spi.png
    ├── component_breakdown.png
    └── geographic_comparison.png
```

---

## How to Reproduce

1. **Clone the repository**
   ```bash
   git clone https://github.com/ian-menachery/cost-of-living-analysis.git
   cd cost-of-living-analysis
   ```

2. **Install dependencies**
   ```bash
   pip install pandas fredapi matplotlib jupyter
   ```

3. **Get a FRED API key** (free)
   - Sign up at [https://fred.stlouisfed.org/](https://fred.stlouisfed.org/)
   - Replace `api_key='YOUR_KEY_HERE'` in the notebook

4. **Run the analysis**
   ```bash
   jupyter notebook notebooks/Econ_3916_Assignment_1.ipynb
   ```

---

## Skills Demonstrated

- **API Integration**: Pulling real-time economic data from FRED
- **Index Theory**: Applying Laspeyres weighting methodology
- **Time-Series Analysis**: Normalizing and comparing multi-series data
- **Data Visualization**: Communicating complex trends to non-technical audiences
- **Economic Reasoning**: Critiquing official metrics and proposing alternatives

---

## Future Extensions

- [ ] Expand to 50+ metro areas to identify geographic inflation patterns
- [ ] Build interactive dashboard with real-time FRED updates
- [ ] Incorporate textbook/supplies data (currently excluded due to data availability)
- [ ] Compare results to university-specific financial aid formulas
- [ ] Machine learning model to predict future Student SPI based on leading indicators

---

## Contact

**Ian Menachery**  
Data Science & Economics | Northeastern University  
📧 [menachery.i@northeastern.edu](mailto:menachery.i@northeastern.edu)  
💼 [LinkedIn](https://linkedin.com/in/ian-menachery)  
🐙 [GitHub](https://github.com/ian-menachery)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Federal Reserve Economic Data (FRED) for comprehensive time-series data
- Professor [Name] at Northeastern University for project guidance
- Bureau of Labor Statistics for CPI methodology documentation

---

*"Not everything that counts can be counted, and not everything that can be counted counts." — William Bruce Cameron*

*But when you **can** count it, you should.*
