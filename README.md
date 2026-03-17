# Analysis of Nutrition, Physical Activity, and Obesity Trends in the United States

**Programming for Data Science Project**

A data analysis project exploring obesity prevalence across the United States using CDC public health survey data, with a focus on identifying trends, disparities, and contributing factors across demographic and geographic dimensions.

---

## Dataset

| Detail | Info |
|--------|------|
| **Source** | U.S. Centers for Disease Control and Prevention — [data.cdc.gov](https://data.cdc.gov) |
| **Survey** | Behavioral Risk Factor Surveillance System (BRFSS) |
| **Period** | 2011 – 2024 |
| **Records** | 110,880 observations across 33 variables |
| **Unit** | State × Year × Population subgroup |

**Key measures covered:**
- Obesity / Weight Status — % of adults classified as obese (BMI ≥ 30)
- Physical Activity — aerobic activity levels and leisure-time inactivity
- Nutrition — fruit and vegetable consumption frequency

**Demographic stratifications:** Age, Sex, Race/Ethnicity, Income, Education

---

## Project Structure

```
├── analysis_improved.ipynb       # Main analysis notebook
├── data_science_ppt.pptx         # Presentation slides
└── README.md
```

---

## Setup & Requirements

```bash
pip install pandas numpy matplotlib seaborn scipy
```

The notebook expects the CDC BRFSS dataset CSV in the same directory:
```
Nutrition__Physical_Activity__and_Obesity_-_Behavioral_Risk_Factor_Surveillance_System.csv
```

Download from: [https://data.cdc.gov](https://data.cdc.gov/Nutrition-Physical-Activity-and-Obesity/Nutrition-Physical-Activity-and-Obesity-Behavioral/hn4x-zwk7)

---

## Analyses Performed

| # | Analysis | Method |
|---|----------|--------|
| 1 | Data Loading, Cleaning & EDA | Missing value audit, type enforcement, standardisation |
| 2 | National Obesity Trend (2011–2024) | Annual mean with 95% CI, linear regression |
| 3 | State-wise Obesity Comparison | Top 10 / Bottom 10 state averages |
| 4 | Physical Inactivity vs Obesity | Pearson correlation, OLS scatter |
| 5 | Obesity by Gender | Independent t-test, trend lines |
| 6 | Obesity by Age Group | Bar chart + year × age heatmap |
| 7 | Obesity by Race / Ethnicity | Ranked averages + trend lines |
| 8 | Obesity by Income Level | Socioeconomic gradient, Pearson r |
| 9 | Obesity by Education Level | Educational attainment gradient |
| 10 | Poor Nutrition vs Obesity | Scatter + regression, state-level |

---

## Key Findings

### National Trend
- Obesity rose from **27.6% (2011) to 34.0% (2024)** — a consistent increase of ~0.5 percentage points per year
- The upward trend is statistically significant (p < 0.001)

### Geographic Disparity
- **Highest:** West Virginia (37.9%), Mississippi (37.8%), Louisiana (36.6%)
- **Lowest:** Colorado (22.8%), DC (23.5%), Hawaii (24.1%)
- ~15 percentage point gap between highest and lowest states

### Physical Inactivity ↔ Obesity
- Strong positive correlation: **r = 0.65**, p < 0.001
- Inactivity explains ~42% of state-level variance in obesity

### Gender
- Female: **31.1%** | Male: **30.8%** — small but consistent difference
- Both sexes show a rising trend over the study period

### Race / Ethnicity
- **Highest:** Hawaiian/Pacific Islander (40.8%)
- **Lowest:** Asian (11.6%)
- ~29 percentage point gap highlighting significant health disparities

### Socioeconomic Gradient
- **Income:** Lowest earners (<$15k): 35.8% vs highest (≥$75k): 29.0%
- **Education:** Less than high school: 34.7% vs College graduates: 25.4%
- Clear inverse relationship — higher income and education consistently linked to lower obesity

### Nutrition ↔ Obesity
- Positive correlation between poor diet and obesity, though weaker than the inactivity relationship
- Low fruit and vegetable intake associated with higher state-level obesity rates

---

## Data Cleaning Notes

- **Missing values (~11.9%):** `Data_Value` was missing for ~13,214 rows — these correspond to suppressed cells where subgroup sample sizes were too small to report reliably. Rows were dropped for numeric analysis.
- **Stratification overlap:** To avoid double-counting in national averages, analyses filter to `StratificationCategory1 == 'Total'` unless stratified breakdowns are the focus.
- **Column standardisation:** String columns stripped of whitespace; trailing space in `High_Confidence_Limit` column renamed; data types enforced.

---

## Limitations

1. **Self-reported data** — BMI and behaviours are self-reported via telephone survey, introducing social desirability bias. Obesity prevalence is likely underestimated.
2. **Ecological fallacy** — State-level correlations cannot be used to make causal individual-level inferences.
3. **Suppressed subgroups** — ~11.9% of records dropped may underrepresent minority or rural populations.
4. **No causal modelling** — Correlations do not establish causality. Confounders such as poverty simultaneously driving inactivity and poor diet are not controlled for.

---

## Conclusions

This analysis reveals a consistent, multi-dimensional obesity crisis across the United States. Geography, physical activity, race, income, and education all show strong associations with obesity prevalence. The findings suggest that effective interventions need to be multi-pronged — targeting nutrition education, activity promotion, and structural socioeconomic factors — and geographically targeted given the significant regional variation.

---

## Author

**Niranjan Kumaraswamy**
MSc Business Analytics — University of York
[GitHub](https://github.com/niranjankumaraswamy47) 
